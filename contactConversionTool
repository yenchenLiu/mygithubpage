import re

print("輸入資料檔名:")
input_text = input()
input_file = open(input_text)
print("輸出檔名:")
output_text = input()
output_file = open(output_text, "w")
output_file.writelines("Name,Given Name,Additional Name,Family Name,Yomi Name,Given Name Yomi," +
                       "Additional Name Yomi,Family Name Yomi,Name Prefix,Name Suffix,Initials," +
                       "Nickname,Short Name,Maiden Name,Birthday,Gender,Location,Billing Information," +
                       "Directory Server,Mileage,Occupation,Hobby,Sensitivity,Priority,Subject,Notes,Group Membership," +
                       "Phone 1 - Type,Phone 1 - Value,Organization 1 - Type,Organization 1 - Name,Organization 1 - Yomi Name," +
                       "Organization 1 - Title,Organization 1 - Department,Organization 1 - Symbol,Organization 1 - Location,Organization 1 - Job Description\n")
# output_file.writelines("name,title,skill,表現,生活,電話,備註,類別,其他\n")
data = {"姓名": "", "稱謂": "", "技術": "", "表現": "", "生活": "", "電話": "", "備註": "", "類別": "", "資料": False}
for line in input_file.readlines():
    temp = line.strip().replace(",", "，")
    if temp:
        if (re.match(r"([\s\w]+)[:]([\W\w]+)", temp)) or (re.match(r"([\s\w]+)[:]", temp)):
            m = re.match(r"([\s\w]+)[:]([\W\w]+)", temp) or (re.match(r"([\s\w]+)[:]", temp))
            col = m.group(1).strip()
            if len(m.groups()) >= 2:
                cell = m.group(2).strip()
            else:
                cell = ""
            if col.lower() == "ntitle":
                data["稱謂"] = cell
            elif col.lower() == "nname":
                data["姓名"] = cell
            elif col.lower() == "nskill":
                data["技術"] = cell
            elif col.lower() == "nshow":
                data["表現"] = cell
            elif col.lower() == "nlife":
                data["生活"] = cell
            elif col.lower() == "ntel":
                data["電話"] = cell
            elif col.lower() == "nremark":
                data["備註"] = cell
            elif col.lower() == "nclass":
                data["類別"] = cell
        data["資料"] = True
    else:
        if data["資料"]:
            data["Notes"] = "技術:{}\t表現:{}\t生活:{}\t備註:{}\t類別:{}".format(data["技術"], data["表現"], data["生活"], data["備註"], data["類別"])
            output_file.writelines("{0},,,,,,,,,,,,,,,,,,,,,,,,,{1},,{2},{3},,,,{4},,,,\n".
                                   format(data["姓名"], data["Notes"], "Other", data["電話"], data["稱謂"],))
        data = {"姓名": "", "稱謂": "", "技術": "", "表現": "", "生活": "", "電話": "", "備註": "", "類別": "", "資料": False}

output_file.close()
input_file.close()
