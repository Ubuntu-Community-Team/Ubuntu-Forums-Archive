---
title: "Firefox 7 and Chrome 15 Hang on Ubuntu 11.10"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by sonupv on 2011-12-20
Hi All,

I'm a newbie to Ubuntu and Linux in general. Have been using Windows Vista primarily and installed Ubuntu 11.10 on my Vista machine a week back. Everything is going well, except this one serious problem.

Couple of times a day ( on random web pages ), the FF 7 and Chrome 15 browsers would just stop responding and the only option is to restart the computer ( sometimes by manually pulling the plug ). 

Any ideas how I can fix this ? I have installed all the updates on the OS.

Another problem I see is that my cursor jumps around randomly while I'm typing. 

Thanks in advance for the help.

Sonu

---

### Post by Lisiano on 2011-12-20
[LIST=1]
[*]What are you using? (Desktop PC/Laptop/Notebook/Netbook)
[*]Do you use both browsers at the same time?
[*]Are you using Chrome or Chromium? There is a slight difference between the two.
[*]Do you see some sort of trend with the freezes? ("Usually after 50 minutes after I start browsing" OR "Usually when I visit image galleries/Watch videos")
[*]Does the WHOLE system freeze up or just FF/Chrome?
[*]Do you have a external mouse? (If you don't use a Desktop PC)
[*]Do you use a mat for your mouse?
[*]Look at the bottom of the mouse where the laser is, try to see if you can spot any hair or any thin objects in the lasers path or close to it.
[/LIST]


In case I forget to visit again later, here are possible problems depending on what was your answer.
[LIST=1]
[*]Depending on the system, you might be plainly running out of memory (Desktops generally have more [Personally mine has 8GB] while the rest have less, decreasing in that order [My netbook has only 1GB])
[*]Same as above, having a lot of tabs open in both browsers could make you run out of memory
[*]This is just for clarification.
[*]Depending when the freezes occur, we could correlate the freezes to overheating of your system or stress (High usage)
[*]Vital, directly points if this is memory running low or heating problems
[*]You might be touching the touchpad when you are typing
[*]Some mice and surfaces don't go along, for example some mice could be fine on fabric while others will fail, some can be lifted, others can't be.
[*]Even something as small as a hair can cause the mouse to have VERY poor accuracy and even "Ghost moving"
[/LIST]

EDIT: If you answered to 5 as only the browsers freeze, try opening a terminal (Ctrl+Alt+T) or the Run menu (Alt+F2, note, to run, you must click the icon, not press Enter) then just enter these commands
```
killall -9 chrome
killall -9 firefox
``` What they will do is kill chrome and firefox in a brutal way. Note, if the system becomes SO sluggish you can't even open a terminal, press Ctrl+Alt+F1-F6 (Any numbered F key from 1 to 6), type in your username and password (The password will not be displayed, this is normal and is a security measure), after that, enter the commands above. To get back to your desktop, press Ctrl+Alt+F7

---

### Post by sonupv on 2011-12-21
Lisiano,

Thanks for the detailed reply. I will watch out for the things you pointed about the cursor jumping problem. I have checked some of the things and they seem fine, but I'll keep watching.

About the problem with FF and Chrome, here is some of the information you asked for:

1. It is Chromium 15 ( and not Chrome as I mentioned earlier ). Thanks for pointing out.
2. When FF/Ch hang, both are not running at the same time. Also I haven't open more than 4-5 tabs so far.
3. I'm running on a laptop. System Info shows: 
          Memory: 2.9GiB, 
          Processor: Intel® Core™2 Duo CPU T5750 @ 2.00GHz × 2
          OS Type: 64 bit.
4. When the browser freezes, the whole system freezes. Nothing ( not even proper restart ) can be done.
5. I haven't noticed any trends for freezing, but I'll keep an eye on that.
6. Doesn't seem like overheating. Could be memory problems ( if there leaks and other issues ), although the system is equipped with ample amount of memory.

Next time it happens, I'll try to get more information. Also thanks for posting the commands to kill stuff.

-Sonu

---

### Post by marl30 on 2011-12-21
Sounds like you also need to run the update manger and get your computer up to date.

---

### Post by sonupv on 2011-12-21
The update manager does show some new updates, but when I try to download and install those, I get the following errors:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.2.2-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.2.2-0ubuntu2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failaed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee_2.2.1-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee_2.2.1-1ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-soundmenu_2.2.1-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-soundmenu_2.2.1-1ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.2.1-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/banshee/banshee-extension-ubuntuonemusicstore_2.2.1-1ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9-common_9.04~dfsg-0ubuntu11.3_all.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_9.04~dfsg-0ubuntu11.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_9.04~dfsg-0ubuntu11.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs9_9.04~dfsg-0ubuntu11.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_9.04~dfsg-0ubuntu11.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]

---

### Post by sonupv on 2011-12-21
I had to do  the "Check" in the Update Manager before installing the updates and that took care of the problem I mentioned in my last post. So now my computer is fully updated, as per the Update Manager. We'll see if that takes care of the problem.

-Sonu

---

