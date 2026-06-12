---
title: "Xbox 360 burning script [linux]"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by M4R0V3R on 2011-10-10
well ive written this script to help burning xbox 360 backups but am having trouble 

> #!/bin/sh -f

echo "This script will help you burn Xbox 360 games with no hassle"

echo "This script requires growisofs to as a prerequisite"

echo " 1 = XGD2 and 2 = XGD3"

echo "Usage: burning.sh <1/2> <gameisoname> <dvddrive> <speed>  "



if $0 -eq 1 

then 

growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=$3 -Z /dev/$2=$1

fi

if $0 -eq 2

then

truncate --size=8547991552 $1

growisofs -use-the-force-luke=dao -use-the-force-luke=break:2086912 -dvd-compat -speed=$3 -Z /dev/$2=$2

fi

echo "Burning Complete"



the scripts repeats the echo commands again and again and again and I have no idea how to stop it :(

---

### Post by Lisiano on 2011-10-10
```
#!/bin/sh -f
echo "This script will help you burn Xbox 360 games with no hassle"
echo "This script requires growisofs to as a prerequisite"
echo " 1 = XGD2 and 2 = XGD3"
echo "Usage: burning.sh <1/2> <gameisoname> <dvddrive> <speed> "
echo "Example: ./burning.sh 1 game.iso sr0 8"

if [ $1 -eq 1 ]
then
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=$4 -Z /dev/$3=$2
fi

if [ $1 -eq 2 ]
then
truncate --size=8547991552 $2
growisofs -use-the-force-luke=dao -use-the-force-luke=break:2086912 -dvd-compat -speed=$4 -Z /dev/$3=$2
fi

echo "Burning Complete"
``` You had incorrect if statements and wrong variables. $0 is the filename of the script, I adjusted every variable to be +1 from what they were, also added an example. Also this is a touchy subject (Burning backups), IDC either way but keep that in mind that you should ask stuff regarding that on the iXtreme forums instead ([http://www.ixtreme.net/](http://www.ixtreme.net/))

---

### Post by M4R0V3R on 2011-10-10
thanks for that, i found error and adjusted it. when i use the first option the script works fine. but the second option it gives the error 

[: 38: missing ]


> #!/bin/sh -f

echo "This script will help you burn Xbox 360 games with no hassle"

echo "This script requires growisofs to as a prerequisite"

echo " 1 = XGD2 and 2 = XGD3"

echo "Usage: burning.sh <1/2> <gameisoname> <dvddrive> <speed>  "

if [ $1 -eq 1 ] 

then 

echo "Setting Layer Break"
echo "Setting Speed"
echo "Setting Device"
echo "Selecting Image"

growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=$4 -Z /dev/$3=$2

fi

if [ $1 -eq 2]

then

echo "Truncating Image"
echo "Setting Layer Break"
echo "Setting Speed"
echo "Setting Device"
echo "Selecting Image"

truncate --size=8547991552 $1

growisofs -use-the-force-luke=dao -use-the-force-luke=break:2086912 -dvd-compat -speed=$4 -Z /dev/$3=$2

fi

echo "Burning Complete"

and I would but there not that responsive

ah it was a simple space causing me all that trouble in the end, cheers for your help been great.

---

### Post by dave01945 on 2011-10-10
> **M4R0V3R said:**
> thanks for that, i found error and adjusted it. when i use the first option the script works fine. but the second option it gives the error 

[: 38: missing ]




and I would but there not that responsive

ah it was a simple space causing me all that trouble in the end, cheers for your help been great.


i would say this line has the wrong vairable as it is for option 1 or 2

```
truncate --size=8547991552 **$1**
```

also this if statement should have a space after the 2


```
if [ $1 -eq **2]**
```

---

