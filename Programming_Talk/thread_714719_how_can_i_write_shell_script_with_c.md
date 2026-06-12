---
title: "how can i write shell script with c"
date: 2008-03-04
forum: Programming Talk
---

### Post by shanyx on 2008-03-04
how can i use c language in ubuntu shell script. is it possible to run c code in shell script. and i need to know how to convert Ascii code to character with shell script code. i know how to do it in c language.

---

### Post by ghostdog74 on 2008-03-04
c language is c language. shell script is shell script. What exactly are you trying to do?

---

### Post by ruy_lopez on 2008-03-04
```
echo -e "\043"
```

prints ascii character 35 (\043 is 35 in octal).

Or capture into a variable:

```
var=`echo -e "\043"`
echo $var
./test.sh
#
```

---

### Post by pedro_orange on 2008-03-04
You can run shell commands from a c application using the:

```
system("ps -C pedro_orange")
```

Or, do you mean a C program to generate a .sh file?

---

