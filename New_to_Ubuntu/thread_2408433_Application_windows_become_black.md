---
title: "Application windows become black"
date: 2018-12-18
forum: New to Ubuntu
---

### Post by jcourt2006 on 2018-12-18
I have upgrade Ubuntu into 18.04. After installing I experience that if I open calculator or other application the windows is black. Please help, i love Ubuntu but I cannot enjoy it.

---

### Post by vfr750 on 2018-12-31
I have the same problem - first application does OK, then usually the following app will show a black box. I can close the black box by clicking in the upper right corner where "X" would be. The laptop is not frozen; I can move the mouse, etc.


Thinkpad T60, Duo-core 2, 2 GB mem, RV515, Ubuntu 18.04.01 LTS. I don't recall this problem with 16.04.

TIA!  

Ed

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]jcourt2006[/COLOR]**]("https://ubuntuforums.org/member.php?u=2109825") and [**[COLOR=#000000]vfr750[/COLOR]**]("https://ubuntuforums.org/member.php?u=2110951"),

This might be a long shot but your issue could be due to a hardware acceleration setting change following your upgrade to Ubuntu 18.04.

First, can you please check if you have a file called 50_check_unity_support located under /etc/X11/Xsession.d/
If yes, it should be safe to remove it as it was only used by Unity which is not present on 18.04 anymore.

Second, can you please check if you have a "Use Hardware Acceleration" option or similar in the Settings panel. If yes, is the option ticked or not?
If it is ticked, please try unchecking it and see if this helps (you might have to perform step one then reboot first).

Third, can you please run the following commands in Terminal and ensure all updates have been completed:
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
```

---

### Post by vfr750 on 2019-01-02
Hi, ClementC - Thanks for your reply! I did find and rm the "50_check_unity_support" file. I also ran the "sudo apt ..." commands. I was not able to find a "Use Hardware Acceleration" option anywhere in the Settings panel or sub-panels even though I'd swear I'd seen such in the past. Then I rebooted.

I am happy to report that even with Vivaldi and a couple of other applications running, the "black box" did not appear. I'm hoping that the problem, with your help, is solved, but life being the way it is, I'll wait a few more sessions before I cheer. Yet, again, thanks for your suggestions! If the problem resurfaces, I'll be back! [And I'm not marking this as "Solved" as I was not the OP - hope s/he sees your reply and has the same good result as I seem to have!]

Ed

---

### Post by clementc on 2019-01-02
Hi Ed,

Thank you for your feedback! Let's hope that this will be the end of your issues.

Please do not hesitate to let us know in a few days if the issue re-occurred or not.

---

