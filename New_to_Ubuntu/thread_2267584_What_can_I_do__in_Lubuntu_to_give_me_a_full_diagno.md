---
title: "What can I do  in Lubuntu to give me a full diagnostic profile of my computer"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by jerry38 on 2015-03-02
hello

       I recently upgrade from Windows Xp to Lubuntu 14.04.  As I post serveral days ago in the forum.  I can not sign into LX Terminal with my  password as this  things to do after a clean install of Lubuntu.  Making it impossible to download anything  outside of what is already  preinstalled.    Considering  switching  back to Windows possibly  Windows 7.  In windows I can type  the command "dxdiag"  (without the quotes) in the run dialog box  and it will  get a full profile of my drivers --  hardware and  a full diagnosis of everything installed  on my computer.   Is there something similar  I can try in Lubuntu to give me the same diagnostic  outcome.  After typing  in dxdiag in the run box it  will not work in Lubuntu.   Please any sugestions.  Thank you.

---

### Post by arochester on 2015-03-02
>  I can not sign into LX Terminal with my password  As a security measure (Imagine someone looking over your shoulder) the password DOES NOT APPEAR in the Terminal. It is there, but you just can't see it. Type your (invisible) password and hit ENTER.

For diagnostics look at something like: [http://www.binarytides.com/linux-commands-hardware-info/](http://www.binarytides.com/linux-commands-hardware-info/)

---

### Post by yetimon_64 on 2015-03-02
> **jerry38 said:**
> hello

       I recently upgrade from Windows Xp to Lubuntu 14.04.  As I post serveral days ago in the forum.  I can not sign into LX Terminal with my  password as this  things to do after a clean install of Lubuntu.  Making it impossible to download anything  outside of what is already  preinstalled.    Considering  switching  back to Windows possibly  Windows 7.  In windows I can type  the command "dxdiag"  (without the quotes) in the run dialog box  and it will  get a full profile of my drivers --  hardware and  a full diagnosis of everything installed  on my computer.   Is there something similar  I can try in Lubuntu to give me the same diagnostic  outcome.  **After typing  in dxdiag in the run box it  will not work in Lubuntu.**   Please any sugestions.  Thank you.

Dxdiag is a Windows tool/command mainly for testing the directX (Windows proprietary stuff, that isn't used in Ubuntu) graphics system, so of course that command won't work in any Linux distro. Linux and Windows are very different "beasts", what works in one may be done by entirely different methods in the other. What I'm saying is instead of expecting the same tool you use there to work here follow instructions here for working on the problem in "the Linux way".
From mastablasta's last post in your other thread, [http://ubuntuforums.org/showthread.php?t=2266678](http://ubuntuforums.org/showthread.php?t=2266678)
> copy what is in terminal (all output) and post it here using the code tags (the # icon in the thread menu)

terminal can be replaced with another one if for some reason it is not  working well. **it's hard to say from the information you provided what is  wrong**...


Note what I have "bolded" in the quote. Please provide any terminal output you see, then someone may possibly have a chance at providing the help you need. "Crystal balls" don't work real well when trying to diagnose OS problems remotely ;). 

Note lisati's 1st post in the other thread and arochester's post above, the replies are virtually identical, starting another thread with the same problem instead of replying with the sort of output asked for there is not going to help you much I'd guess. 
>  I am very much interested to see what you did in terminal.

Same here. Regards, yetimon_64.

---

### Post by mastablasta on 2015-03-03
> **jerry38 said:**
>   After typing  in dxdiag in the run box it  will not work in Lubuntu.   Please any sugestions.

you can install Ubuntu system testing. it could be that it will install without certain library (maybe cause it was made for Ubuntu?!). this can be found out if you try to run it from terminal. I think it's run by: ```

checkbox-gui
```


anyway dxdiag offers diagnostics for directX which is a windows thing. and it mainly tests graphic drivers. maybe directx sound as well.

Ubuntu system testing will test it all - including: network, RAM (very long test), disk, monitor...: [https://apps.ubuntu.com/cat/applications/precise/checkbox-qt/](https://apps.ubuntu.com/cat/applications/precise/checkbox-qt/)

Another testing suite but without GUI as I understand it is Phoronix Testing Suite. this one downloads what it needs. so if you test gaming it then downloads some games. like 8 GB of them. but then there are other smaller tests only a few MB big. anyway more for the pro testing....: [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

but if you want to test your graphics and OpenGL a bit then glmark will do. find the package *glmark**2 *and install it then run it in terminal. screen will get some photos to be tested (just like in dxdiag) and in the end it will give the result in points. easier to compare I guess.
[http://packages.ubuntu.com/search?keywords=glmark2](http://packages.ubuntu.com/search?keywords=glmark2)

---

