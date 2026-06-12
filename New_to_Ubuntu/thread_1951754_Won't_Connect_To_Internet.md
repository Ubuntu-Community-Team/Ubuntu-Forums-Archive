---
title: "Won't Connect To Internet"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by rs321 on 2012-04-03
Ubuntu 10.4
HP Pavilion g7

Folks,

Installed 10.4 on a new laptop with dual boot to Win 7.  Everything worked just fine for the first week but then there was no connection to the internet through Ubuntu.  The closest I can get is a dialog box asking for the connection name but I didn't ever assign a name to it; it worked just fine originally and I didn't need to mess with it.  I'm at a loss as to what I did to make it stop functioning and can't find any help within Ubuntu.  I'm a newbie for the most part and don't know what to do so any clues would be appreciated.

Thanks,

Randy

---

### Post by garvinrick4 on 2012-04-03
Tell users if you are using cabled or wifi. 
Run this and post your cards to this thread.
Just the network controller and ethernet controller.
Those are the wifi and wired cards.

```
lspci -k
```

###Mine are below to give you an example to copy and paste to your thread. So users can help you, lots of network guys in this forum.

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 306b
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by rs321 on 2012-04-03
[garvinrick4]("http://ubuntuforums.org/member.php?u=899097"),

I'm afraid you lost me.  I have the computer wired to the internet and I also have wifi and in windows it works either way without any switching of anything on my part.  Should I go back into Ubuntu and run "lspci -k" and see if that does anything?  What cards am I supposed to post to this thread?

-Randy

---

### Post by garvinrick4 on 2012-04-03
> Should I go back into Ubuntu and run "lspci -k" 
Yes go to Ubuntu and open a terminal and run the code and post output.


> What cards am I supposed to post to this thread
The Network Controller
The Ethernet Controller
##Just like mine in previous post.

---

### Post by rs321 on 2012-04-03
[garvinrick4]("http://ubuntuforums.org/member.php?u=899097"),

Okay, I did that and got the message "ispc -k command not found".  Should I just reinstall Ubuntu because it worked initially?

-Randy

---

### Post by garvinrick4 on 2012-04-03
lspci   you forgot the i

---

### Post by rs321 on 2012-04-03
[garvinrick4]("http://ubuntuforums.org/member.php?u=899097"),

Network: Device 8176 (rev 01)
Ethernet: RTL8101E/RTL8101E P

Both are from Realtec.

I also get a message stating my wireless connection is turned off and that I should press the wireless button but I can't find that button on Win or Ubuntu.

-Randy

---

### Post by Vinkus on 2012-04-03
Hello everyone,

Randy, if you does not intend to use ubuntu via WiFi (and for testing), I suggest you to uninstall the "gnome network manager" (the graphical interface) and [COLOR=Blue]_[write the config file manually to connect to the Internet by wire]("http://manpages.ubuntu.com/manpages/lucid/man5/interfaces.5.html")_[/COLOR]. I had myself some problems with this soft and now I can do everything I want simply by editing the config files.
The WiFi card can be **manually** configured by[COLOR=Blue] _[iwconfig]("http://manpages.ubuntu.com/manpages/hardy/man8/iwconfig.8.html")_[/COLOR] command.
If I have an advice for you, all the answers are in the files, and the shell is the best tool to configure your OS! ;)
Of course, it will have no impact on Windows.

Cordially,

---

### Post by rs321 on 2012-04-07
Folks,

I posted something similar to this a few days ago but the thread went away the next morning so I'll try again and be more specific.

HP Pavilion g7 laptop
Ubuntu 10.04
Dual boot: Win 7 & Ubuntu

I'm ttrying to connect to the internet.  It worked fine when I made the original installation a few weeks ago but then stopped.  I can connect just fine through Windows but when I try with Ubuntu I get a box that wants the following information:

Connect to Server
     FTP (with login)
     Public FTP
     Windows Share
     WebDAV (HTTP)
     Secure WebDAV (HTTPS)
     Custom Location
Server
Optional Information
     Port
     Folder
     User Name

Okay, I know what HTTP means but the rest is Greek to me.  Can anybody tell me what information I need to enter and where I can find it?  All I want is a simple internet connection and the setup I'm running used to be able to do it so I doubt it's too technical.

Thanks,

Randy

---

### Post by cortman on 2012-04-07
Your thread didn't "go away" - it's right [here.]("http://ubuntuforums.org/showthread.php?t=1951754") You didn't respond to the last post in it.

---

### Post by Bucky Ball on 2012-04-07
To find your threads click 'Search'>'Find all your threads'.

They don't disappear, they are just not responded to (as you didn't respond to it) and therefore don't show up in your User CP. 

I have asked mods to merge threads. ;)

---

### Post by rs321 on 2012-04-07
cortman,

I'm glad you could find it because I couldn't, not even with a search, and I hope nobody's offended that I posted twice.  The question still remains, though.

-Randy

---

### Post by Bucky Ball on 2012-04-07
Read my last post #3.

---

### Post by cortman on 2012-04-07
> **rs321 said:**
> cortman,

I'm glad you could find it because I couldn't, not even with a search, and I hope nobody's offended that I posted twice.  The question still remains, though.

-Randy

It's an easy mistake to make! The mods frown on it because it dilutes community effort, but yours is an honest mistake. A mod will merge your threads and you'll be sure to get some more help. :)

---

### Post by cariboo on 2012-04-08
Please don't create multiple threads on the same subject, I have merged your two threads.

[offtopic]If you can't find your threads, because they've fallen off of the main page, please use the search function at the top of the page and select *Find All Your Threads* [/offtopic]

---

### Post by rs321 on 2012-04-08
Folks,


Thank you all for your input.  I appreciate it and will apply your suggestions as I am able to interpret them but due to some brain surgery last month I'm not firing on all seven cylinders yet.  Once I get the internet stuff figured out I'll mark this thread as solved.

Thanks again,

-Randy

---

### Post by rs321 on 2012-04-10
Folks,

Thanks for all your help but here's how I fixed it:

R click on the panel at the top of the page, the one that has Applications, System, etc.
Click Add To Panel
Select Notification Area

On the right side of the panel an exclamation mark (!) appeared.  I right clicked on it and it told me my internet was disabled and gave me the option of connecting, which I did.

Poof!  No codes entered, no incantations spoken, it simply solved my problem.

-Randy

---

