---
title: "hide/protect folder"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by bariamtak on 2012-01-06
i saw a video  in youtube somthing lyk typing  "sudo gksu nautilus" in the terminal and  one file browser pops up. then it involves right click and from  properties changing the owner and group of the folder to root . The  video was for ubuntu 8.10.But when  i tried the same procedure i could  not change the owner of the folder or any other attributes from user to  root. I am using ubuntu 11.10. is the proccess different for my version  or is it becos i need some softwares or application? Or still is it not  supported ? if it is possible lyk that, someone please help me out.
    I really like ubuntu (i'll be discarding my win7 ultimate soon). its  great that users can help each other.though i dont know much I lyk d  flexibility of linux ! and i learn a lot from u guys...thank u

---

### Post by HermanAB on 2012-01-06
You have the right idea, but need to Google 'chown' and 'chmod'.

$ sudo nautilus

Right click, change owner and mode to root only.

---

### Post by bariamtak on 2012-01-06
I tried to change that but it will not take effect. I can see the option but cannot change to root,it just jump back to user. Do you have any other idea. I'll need more details....m not so good in this stuff...thank you.

---

### Post by jtarin on 2012-01-06
If you just want to hide the folder change the filename to make it hidden by placing a period before the name.....example.....```
pictures becomes .pictures
```to unhide in Nautilus file manager use the Nautilus menu..."View>Show hidden files". To hide again either uncheck "Show hidden files" or close the file manager.

---

### Post by bariamtak on 2012-01-09
Thanks for the information but is there any other way like putting a password in a folder without any other softwares? OR is there any application to protect a folder with password like in windows ? 
Thank you.

---

