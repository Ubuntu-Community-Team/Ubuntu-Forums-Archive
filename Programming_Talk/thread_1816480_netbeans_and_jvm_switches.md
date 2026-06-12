---
title: "netbeans and jvm switches"
date: 2011-08-02
forum: Programming Talk
---

### Post by jmartrican on 2011-08-02
hello,

I am developing a program on netbeans 6.9.1.  When executing the program via netbeans I would like to set some jvm switches for it, specifically some of the GC switches, -J-verbose:gc -J-XX:+PrintGCTimeStamps -J-XX:+PrintGCDetails.

How can this be done?  I tried setting these switches in the netbeans.conf file, but it did nothing noticeable and I do not know if those switches in that file are only for netbeans itself and not the applications launched by netbeans.

Anyone have any experience with this?

thanks
jose

---

### Post by SevenMachines on 2011-08-02
netbeans.conf options are for netbeans jvm
For running projects, on netbeans 7 you would go to,
```
 Run->Set Project Configuration->Customize
```Then in this new window go to
```
 Run->VM Options
```Heres where the options go but not with the -J you mention
```
 -verbose:gc -XX:+PrintGCDetails -XX:+PrintGCTimeStamps 
```Should be right anyway

---

### Post by jmartrican on 2011-08-02
Dude thanks a lot man.  I wish this forum had a point system for people who answered questions.

I did not find "VM Options" but found "JVM Arguments" instead.  It worked.

thank again bro!
jose

---

