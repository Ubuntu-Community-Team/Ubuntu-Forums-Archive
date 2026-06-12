---
title: "Psensor problem"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by james89 on 2014-07-01
I am trying to keep a check on Hard drive temperatures.   One drive has SMART parameters the other does no.    Psensor runs but the graphical imnterface does not make too much sense to me.
Normally on Windows  the main hard drive warms up bewtenn 20 degrees and  40 degrees.
The psensor date shows  temp1:  acpitz - virtual 0 - 0temp1           value at a constant  40 degrees never changes.

Also it3712 -ISa - 0228temp1     value26 degrees and variable on the graphs
and  it3712 -ISa -0228temp2   value   about  76 degrees and  varaible.

Which one is my hard drive please?   If it is the first one  why is it always constant?


Thand for any help you can give.
James

---

### Post by cariboo on 2014-07-01
Have you just tired running hddtemp in a terminal?

```
sudo hddtemp /dev/sda
```

the output should look something like this:

```
sudo hddtemp /dev/sda
/dev/sda: KINGSTON SV300S37A240G: 27°C

```

I have a second drive in my system, so the command would be:

```
sudo hddtemp /dev/sdb
```

and the result looks like this:

```
sudo hddtemp /dev/sdb
/dev/sdb: ST1000DM003-1CH162: 33°C
```

---

### Post by Vladlenin5000 on 2014-07-01
Amazing, thank you, cariboo907.

I just found out that two disks in the desktop I'm currently using (Seagate and Toshiba) have sensors, the third hasn't (WD)  :confused::confused::confused:
Why would a manufacturer not included the sensor? Or could it be a symptom of something?

---

### Post by james89 on 2014-07-02
Thanks Cariboo907

Your first suggestion  did give me a sensible result for the temperature of the hard drive.

I'm still puzzled as to what  psensor  is giving me on the graphical  layout.
Also  would your suggestion have worked without me installing lm-sensors  or psensor or  doing sudo sensors-detect  in the terminal   or does your command depend on those being present?

Regards,
James

---

