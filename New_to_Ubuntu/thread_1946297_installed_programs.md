---
title: "installed programs"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by frstbuntu on 2012-03-24
I have installed GNU Radio, but cannot find the program to run it in either dash or home folder. How do I run it if it does not show up? Software center says it is installed. Probably something I'm overlooking, the installer did not say this software needs to be run from a terminal, as some do. I even installed Python in case it was required.:confused:
Sorry, I have ver 11.10 installed.

---

### Post by cortman on 2012-03-24
Hi, welcome to the forums!

Have you tried searching for it? Windows key and start typing. Also looked at [this page]("http://gnuradio.org/redmine/projects/gnuradio/wiki/HowToUse")?

---

### Post by frstbuntu on 2012-03-24
Hi Cortman,
Yes I have searched for it as you asked. The program is supposed to be installed according to the software center control. It does not show up in dash or home anywhere, all other programs I have installed do show up in them. There are utility add ons that have to be run from a terminal for gnu radio, but the main one should be started from home or dash like all the others. I have read the page you pointed to, and am still reading yet, just don't understand how to access the installed program. I am still working to understand using Ubuntu, just installed it 2 days ago. I have played around with older versions occasionally, and used Suse enterprise a little a while back, but still have a lot to learn. There must be something I'm not doing right when installing it to not be able to find it listed with all the other programs/utilities I have installed. Thanks for your quick reply, I appreciate it.:mad:

---

### Post by cortman on 2012-03-24
> **frstbuntu said:**
> Hi Cortman,
Yes I have searched for it as you asked. The program is supposed to be installed according to the software center control. It does not show up in dash or home anywhere, all other programs I have installed do show up in them. There are utility add ons that have to be run from a terminal for gnu radio, but the main one should be started from home or dash like all the others. I have read the page you pointed to, and am still reading yet, just don't understand how to access the installed program. I am still working to understand using Ubuntu, just installed it 2 days ago. I have played around with older versions occasionally, and used Suse enterprise a little a while back, but still have a lot to learn. There must be something I'm not doing right when installing it to not be able to find it listed with all the other programs/utilities I have installed. Thanks for your quick reply, I appreciate it.:mad:

Sorry it didn't help. Ubuntu can be a bit of a learning curve at first, but it's well worth the effort!
Are you sure it installed correctly? Try running it from the terminal just to be sure. At the prompt just type

```
gnu-radio
```If it is installed properly, you may just need to add it manually. [This page]("http://linuxsagas.digitaleagle.net/2011/05/13/adding-apps-to-unitys-dash/") should step you through the simple process.
Any other questions, post back. Good luck!

---

### Post by frstbuntu on 2012-03-24
Thank you Cortman,
Trying the terminal window only produced "command not found", evidently, though the software center says it is installed, it must not be. Nor could I access the utilities listed for gnu radio through the terminal either. I had already stumbled on the main menu and even added it to the desktop for ease of access. Curiously, gnu radio shows in the main menu under both menus and items, still no executable though. I will uninstall all associated packages for gnu radio and reinstall separately, maybe there is a conflict between one or a couple of the packages. Something I did wasn't right, just have to isolate it. Thanks again, will keep my progress posted.;)

---

### Post by Linux_junkie on 2012-03-24
Whilst searching I found this.

[http://gnuradio.squarespace.com/](http://gnuradio.squarespace.com/)

According to the website GNU Radio is only a development toolkit to be used by other software radios it is not an application in itself.

Hope this helps.

---

### Post by frstbuntu on 2012-03-25
Not resolved, but stopped anyway.
Thanks Linux_jJunkie,

I did read the page you pointed to, the separate applications are supposed to be accessed by command terminal, and a separate Wx gui is also supposed to be available. Following the directions on their web page about how to access it through the terminal has been fruitless for me. Also no gui or other indicator is available to access them. I have been in electronics for more than 50 years and wanted to use the capabilities of gnu radio to develope new SDR applications for hardware I build. Gnu radio is available only on linux, and I know it is used in conjunction with other applications, this is why I wanted to use it. I have Suse enterprise Linux which I purchased in the past, and think I will reinstall it. I had installed gnu radio on it before. Though I didn't get very far into it then, didn't have the time from work to pursue it. I now run win7 pro, win8 beta, winxp pro, and like the capabilities of gnu radio software. Thanks to all who have tried to help me. The software center says gnu radio is installed, but no indication of how to access it. I even uninstalled it totally, rebooted, reinstalled it (did this twice), then uninstalled it again, rebooted, then installed it by command line, watched as it went through each step. But still cannot access it like the software authors say to. Again thanks to all, I will have to go a different route.

---

