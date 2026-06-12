---
title: "Shell script"
date: 2010-06-10
forum: Programming Talk
---

### Post by bonzi on 2010-06-10
I'm a N00b in shell scripting. What does this script do?
NUMJOB=${NUMJOB#*=}

---

### Post by DaithiF on 2010-06-10
Hi,
it strips everything from the variable up to and including the first '=' sign.

so if NUMJOB was something=somevalue
then after the operation NUMJOB would be left with just somevalue

**man bash** to learn more (section Parameter Expansion)

---

### Post by bonzi on 2010-06-10
Thanks you very much for the reply. I have one more question regarding sed

How do I get the string after teh 3rd occurance of :. In this case C1:EF:00
18:A9:05:C1:EF:00

---

### Post by trent.josephsen on 2010-06-10
The version requiring no thought would be `awk -F: '{ print $4 }'` but if you wanted a bash-only version it will be more involved.

---

### Post by Trumpen on 2010-06-10
```

$ foo=18:A9:05:C1:EF:00
$ echo ${foo#*:*:*:}
C1:EF:00

```

---

### Post by geirha on 2010-06-10
```

# bash
$ IFS=: read -r -a array <<< '18:A9:05:C1:EF:00'
$ echo "${array[3]}"
C1
$ (IFS=:; echo "${array[*]:3}")
C1:EF:00

```

Probably overkill for your case though. I'd go with Trumpen's solution.

---

### Post by bonzi on 2010-06-10
Thank you all [trent.josephsen]("http://ubuntuforums.org/member.php?u=763491") solution woked perfectly for my scenario. Thanks once again

---

