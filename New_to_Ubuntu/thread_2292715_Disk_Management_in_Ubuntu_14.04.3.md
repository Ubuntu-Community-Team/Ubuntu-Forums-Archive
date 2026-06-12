---
title: "Disk Management in Ubuntu 14.04.3"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by incurablegeek on 2015-08-30
Again, I am a bit embarrassed to post such an infantile question.

Background: I am in the processing of migrating to Ubuntu on all 5 of my computers from Win 7 64 bit Ultimate, for 2 reasons: 1) I feel that Windows has taken the Sarah Palin "Road to Nowhere"; 2) All of my future work must be done on Linux, and I happen to like Ubuntu with an XFCE desktop - as well as the cordial atmosphere on these forums.

Question: I just installed Ubuntu but have no clue how I can find what Windows calls "Disk Management". I wish to partition 2 3 TB GPS Western Digital hard drives, but have no clue as to how to do so. Stupidly easy on Windows in which I have 25 years of experience.

Do I need a separate add-on for Ubuntu 14.04.3. I recall this being quite easy on Ubuntu 12.

---

### Post by Dennis N on 2015-08-30
For disk partitioning and related tasks, I suggest the application **gparted**. You may have to install it from the Ubuntu repository or Software Center.

---

### Post by incurablegeek on 2015-08-30
Dennis, thank you so much. I will do so.

---

### Post by Dennis N on 2015-08-30
You're welcome. Come back again if you have any questions. You can mark your thread 'solved' with the thread tools just above post #1.

---

### Post by incurablegeek on 2015-08-30
OMgoodness, I went to the gparted site which said I needed "Aptitude" to download gparted. So I downloaded and installed Aptitude but without a Start Menu I sure cannot even find it to download gparted.

Has Ubuntu taken 1 step forward and 5 steps backward? I remember Ubuntu 12 to be quite simple.

---

### Post by ajgreeny on 2015-08-30
To actually do very much with gparted you will have to run it from a live DVD or USB as you can not work on partitions that are mounted, and, of course, your OS partitions will be mounted when the OS is running. Gparted is available on a live system by default; you will not need to install anything to the live system.

You will also already have a program called Disks on your installed OS, but I am not sure how it will appear in an XFCE menu on a Ubuntu OS, so search for it and I'm sure you'll find it.  Play around in there for a while to see what it can do; it will certainly tell you a lot about your current partitions, but it can also do a lot more than that.

For partition management and edits, however, gparted would still be my chosen application, used in a live system, as I said before.

PS:  I have just read your post #5 in the thread.
You do not have to go to the gparted website nor do you *need* aptitude on a system to install anything, so I don't have a clue where that message came from.  Open a terminal and run command ```
sudo apt-get install gparted
``` or use synaptic or software-centre, all of which will do the same thing.

I never use aptitude; always terminal or synaptic for me.  Synaptic used to be the default package manager for Ubuntu but was removed from default installs some time ago.  It is still the best package manager in my opinion and is always the first application I install after installing a new OS.

---

### Post by incurablegeek on 2015-08-30
OK, thank you.

My information was incomplete. My OS (ubuntu) is mounted on a 128 GB SSD where my installed programs will of course also reside, and the 2 X 3 TB WD HDD's are for storage. Have not installed XFCE yet. 

"***You will also already have a program called Disks on your installed OS***". And where might this be hidden?

Sorry to be so "high maintenance" but this version of Ubuntu is a whole 'nother beast from earlier versions.

---

### Post by Dennis N on 2015-08-30
In your situation, you can install gparted to your OS on your SSD, and safely work on the other two new drives to partition them.

Do you have gparted installed? If not, just run
```
sudo apt-get install gparted
```
in your terminal.

I personally don't use "Disks", but of course you can use it if you like. I would instead take a few minutes to install gparted.

---

### Post by grahammechanical on 2015-08-30
> Is it OK if I download gparted via my Win7 computer? And must I do so in the future with all installs?

No, and No, again. A default install of Ubuntu does not include Gparted because (a) it will refuse to change mounted partitions and (b) we can really mess up an OS with tools like Gparted and (c) it comes as part of the Ubuntu live session and it is better to use Gparted from a live session. It makes us think about what we are doing.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you wish to migrate from Windows to Linux then get in the mind set of working in Linux/Ubuntu. Ubuntu 14.04.3 is as "simple" as Ubuntu 12.04. It is you that are complicating things. Ubuntu 12.04 does not have Gparted installed by default. I cannot remember if it had Disks or some other similar utility. But it most certainly had the Dash and the Applications lens. It also had the Ubuntu Software Centre just as 14.04 does today. And Gparted is in the Software Centre. 

My advice would open the Software Centre and remove Aptitude. You do not need it. You have the Software Centre and the apt-get command. There is also a Disk Usage Analyser in the Dash.

Regards.

---

### Post by ajgreeny on 2015-08-30
You said you liked the xfce desktop which does have the equivalent of the windows start menu, but if you have not yet installed the xfce desktop and are still using unity with the column of launch icons on the left hand edge of the screen use the top icon, the dash as it's known, and start typing **disks** and icons will appear that match what you type.

However, rather than use Ubuntu and unity, as you seem to be at the moment, I suspect you might be much happier with Xubuntu instead, and depending on how much you have used you Ubuntu install so far and how many files you might have on it, it could be much quicker and simpler for you to start again from scratch and install Xubuntu 14.04, which is an LTS version supported until April 2017, where 15.04 is supported only until Jan 2016.  You can use the command in terminal ```
sudo apt-get install xubuntu-desktop
``` to add xubuntu to your ubuntu, but that can make the menus confusing and will mean you have several applications that duplicate the same job and can be a bit of a pain.

If you really start to use Ubuntu you must forget the "Windows" ways that you used to install applications. In Ubuntu we use repositories of applications that you get to from either the terminal with various apt-get commands or by using software-centre or synaptic as I said last time; **do not go to an application's website** to download it and install it that way as you will normally find that it is very complicated, particularly for a new user.  You should certainly not consider downloading an application using windows with what appears to be a very limited knowledge of Linux and Ubuntu.
See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for details of all of this.

---

### Post by ajgreeny on 2015-08-30
Things have moved very quickly in this thread so I advise you to step back a bit, take a few deep breaths, and firstly forget all you used to do in Windows; you are now using Linux and specifically Ubuntu, or as I suggested above for ease of transition, Xubuntu, so everythin is going to be new, strange and possibly challenging to you.

But don't despair; we are here to try to help, and if you are anything like me it will fairly soon all come as second nature to you and you will start to think how cumbersome and difficult Windows is.  I have not "used" Windows for about 10 years, other than my virtual install of XP which I need for updating a satnav device, and I probably feel similarly about Windows to the way you feel about Ubuntu, ie, often lost.

Everything that other forum users have said in their answers is correct, and this is one of the possible problems that you are facing; there are often several ways of doing the same thing which can confuse someone used to Windows. If I remember correctly Windows seldom had many alternative ways of doing something, and certainly never had repositories of applications for installation, all of which are guaranteed to be safe and tested.

---

### Post by incurablegeek on 2015-08-30
[PHP]It is you that are complicating things.[/PHP] Gosh, I really love that.

When I can't find the C prompt or command line, I get a bit frustrated.

I diid download gparted, but it shows me only the SSD - nothing else.

Since in my business I have nothing but time on my hands, I will try xubuntu.

But please excuse me here: I did use Ubuntu 12.04 and I never had any problems finding anything. Anyway, it's been a long day and I will give xubuntu a shot. Thanks to all!

Just read this kind post: > But don't despair; we are here to try to help, and if you are anything  like me it will fairly soon all come as second nature to you and you  will start to think how cumbersome and difficult Windows is.  I have not  "used" Windows for about 10 years, other than my virtual install of XP  which I need for updating a satnav device, and I probably feel similarly  about Windows to the way you feel about Ubuntu, ie, often lost.

I sincerely appreciate your kind words. First of all, I do not like Windows, not since NT 4.0. It has become bloated and slow - and I have 6-8 core processors, 16 GB of RAM. And Windows is still slow; and it is getting worse as we all know.

Second of all, I ascend learning curves rather quickly, so I will review all the referred documentation suggested. My apologies for being so burdensome on you guys.

---

### Post by Dennis N on 2015-08-30
> I diid download gparted, but it shows me only the SSD - nothing else.
Excellent choice. As to seeing only the SSD, it may be because gparted only shows one drive at a time in its window. There is a selector in the upper right of the gparted window to switch your view to other connected drives. See attached screenshot.

---

### Post by incurablegeek on 2015-08-30
Thank you, Dennis N. You are a real gentleman and most helpful.

I took the advice of ajgreeny and installed Xubuntu. It is intuitive, almost self-explanatory, and it comes with XFCE GUI **and not** the Unity desktop which, well I won't say it ....

---

### Post by ajgreeny on 2015-08-31
So is your particular problem solved for now?

If so please mark this thread as SOLVED from the Thread Tools menu at the top.

---

