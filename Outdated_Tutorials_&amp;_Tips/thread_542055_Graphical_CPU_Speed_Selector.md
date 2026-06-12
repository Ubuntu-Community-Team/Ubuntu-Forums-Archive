---
title: "Graphical CPU Speed Selector"
date: 2007-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by InfoSec812 on 2007-09-03
So, recently I saw an article about using the "cpufreq-selector" utility to set the CPU scaling speed of my Core 2 Duo. As a person who likes simplicity, I decided it might be useful to have a graphical interface for Ubuntu users who prefer to avoid the command prompt. Here's what I came up with.

First, Ubuntu installs Zenity by default. Zenity is a utility which allows you to integrated graphical elements into shell scripts. Using Zenity, one could create a selection dialog which allows the user to choose the SpeedStep frequency for their CPU. Here's how:

1. Open a new instance of gedit (Applications->Accessories->Text Editor).

2. Enter the following code:

```

#!/bin/bash
CURRENT=`cat /proc/cpuinfo | grep "^cpu MHz.*" | awk -F": " '{print $2}' | sed 's@\.@@g' | uniq`
if [ "${CURRENT}" == "1000000" ] ; then
    SETA='TRUE';
    SETB='FALSE';
    SETC='FALSE';
fi
if [ "${CURRENT}" == "1333000" ] ; then
    SETA='FALSE';
    SETB='TRUE';
    SETC='FALSE';
fi
if [ "${CURRENT}" == "1667000" ] ; then
    SETA='FALSE';
    SETB='FALSE';
    SETC='TRUE';
fi
ans=$(zenity --list --text "Select CPU Speed" --radiolist --column "" --column "Speed" ${SETA} "1.0 GHz" ${SETB} "1.33 GHz" ${SETC} "1.67 GHz") ;
VALUE=1000000
if [ "${ans}" == "1.0 GHz" ] ; then
    VALUE=100000;
fi
if [ "${ans}" == "1.33 GHz" ] ; then
    VALUE=1333000;
fi
if [ "${ans}" == "1.67 GHz" ] ; then
    VALUE=1667000 ;
fi
gksu "cpufreq-selector -f ${VALUE}"

```

3. Save the new file as "cpuScaler" and give the file execute permissions.

4. Review your CPU steppings for you particular computer. My computer has 3 settings of 1, 1.3, and 1.66 GHz. Yours may differ, but you should easily be able to figure it our using cpufreq-selector and looking at the contents of /proc/cpuinfo.

5. Modify the steppings to suit your computer.

This is my first tutorial on here, so give me some feedback on things you think I should do differently and have a great Labor Day!!

---

### Post by Zigi15 on 2007-09-06
Two strange things happened to me. I have the intel core duo T2250 processor, but I can't find it anywhere on intel's site. And my cpuinfo file is empty.

---

