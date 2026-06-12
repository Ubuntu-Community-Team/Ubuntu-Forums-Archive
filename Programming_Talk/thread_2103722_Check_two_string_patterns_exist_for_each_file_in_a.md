---
title: "Check two string patterns exist for each file in a list of files."
date: 2013-01-11
forum: Programming Talk
---

### Post by cginf0s3c on 2013-01-11
So, I've got this question and I've been googling around to find an answer. Anyone willing to throw me a bone on this?

I basically need to write a script that will check each file for the existence of two strings. If only one string or neither strings exists I need to echo out which file only has one or neither string. Sounds simple but for some reason can't figure it out. 


logFiles=`find /var/log -name '.log'`

for i in logFiles do

grep string1 logFiles    #grep string1 in each file
grep string2 logFiles    #grep string2 in each file

if [ -z string1 ] -o [ -z string2] then  
echo $logFiles file does not contain string1 and string2. 
fi

Thanks.

---

### Post by ofnuts on 2013-01-11
> **cginf0s3c said:**
> So, I've got this question and I've been googling around to find an answer. Anyone willing to throw me a bone on this?

I basically need to write a script that will check each file for the existence of two strings. If only one string or neither strings exists I need to echo out which file only has one or neither string. Sounds simple but for some reason can't figure it out. 


logFiles=`find /var/log -name '.log'`

for i in logFiles do

grep string1 logFiles    #grep string1 in each file
grep string2 logFiles    #grep string2 in each file

if [ -z string1 ] -o [ -z string2] then  
echo $logFiles file does not contain string1 and string2. 
fi

Thanks.
```

(grep -l -v string1 $logfiles; grep -l -v string2 $logfiles) | sort -u

```

---

### Post by vasiliscnisrok on 2013-01-11
```

logFiles=`find /var/log -name '.log'`

for i in logFiles 
do

  o1=`grep string1 ${logFiles}` #grep string1 in each file
  o2=`grep string2 ${logFiles}` #grep string2 in each file

  if [ -n o1 ] -a [ -n o2] then 
       echo $logFiles file  BOTH string1 and string2. 
  else
       echo $logFiles file  has one or neither string. 
  fi
done

```

---

### Post by cginf0s3c on 2013-01-11
Ok. I think I got it. I made some edits and it should be working. Thanks all.

---

### Post by sisco311 on 2013-01-12
In bash, I'd try something like:
```

while read -r -d '' file
do
    if grep 'string1' "$file" > /dev/null 2>&1 && grep 'string2' "$file" > /dev/null 2>&1
    then
        printf '%s\n' "$file: contains both strings"
    else
        printf '%s\n' "$file: " does not contain both strings"
    fi
done < <(find /var/log -iname '*.log' -type f -print0)

```

---

