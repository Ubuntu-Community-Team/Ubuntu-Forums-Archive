---
title: "Frustrated newb with questions"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by stuartv on 2013-03-11
I just installed Ubuntu 12.10 x64 as a guest OS in a VMWare Workstation 9.0.2 VM, with a host OS of Win 7 x64. Laptop is a Dell Precision M6400 with 16GB RAM and 1.5TB HDD. Guest OS is assigned 1 CPU, 1 Core, 2GB RAM, and 80GB HDD.

I feel like I've spent my whole afternoon chasing down ratholes of forum searches trying to figure out things that seem like they should be intuitively obvious.

1) When I first installed, Ubuntu kept telling me my Wired Connection has broken (or something like that) and I am now Offline. I would check in the System Settings/Network tool and it would show my Wired connection as turned Off. I would turn it back on and have Internet access again for a few minutes. Rinse. Repeat. After an hour or so of messing with it and doing forum searches from my host OS, I couldn't find anything helpful, but the Wired connection stabilized and has been working for the last couple of hours. Any idea what's up with that?

2) I need a mail client that will connect to MS Exchange using ActiveSync, but doing it over an HTTP proxy. Outlook runs on my host OS and connects that way. I installed Evolution and the Exchange add-on and it does not seem to have support for connecting over an HTTP proxy. Is there any client that will do this?

3) My Logitech wireless mouse has 5 buttons and a scroll wheel. I want my thumb button to perform a Back in the browser. I can't seem to find anywhere in the settings to configure this. The Scroll wheel works, but I don't see any configuration option for that, either. After some searching, I found a recommendation to use the dconf Editor. So, I went into the Ubuntu Software Center and searched for it and it says it's already installed. But, I don't see an icon for it in the tool bar and it doesn't show up when I click on the Dash Home button, either. So, how is a new user supposed to know that this program is already installed and how to run it? How DO I run it?

4) When I was messing around with trying to get Wired networking working, I wanted to go out to a command line and see if I could check my configs for obvious problems. I am a software developer by trade and I used Unix back in the 80s, and have occasionally hacked around in a terminal session on my g/f's Mac or on my Android devices, so was somewhat hopeful. But there's not even a terminal app accessible from the system tool bar or under the Dash Home button. WTF??

5) I hate to bring up the "if this were Windows...." thing. I'm sure that is not a popular drum around here. But, geez, all but the most obscure tools in Windows at least are accessible through the Start menu. So, if you don't know exactly what you're looking for, you at least have a prayer of finding it just by poking around. Right now, I am completely mystified at how anybody could think this OS is fit for use in mainstream, Joe User, desktop environments. My parents, as one example, are not particularly PC savvy. But, even they can figure out how to adjust their mouse button settings in Windows without my help. I'm supposed to be an "expert" and I can't figure it out here! Am I just missing the forest for the trees??

5a) In trying to diagnose my Wired network connection problem, I also could not see anything like the Event Viewer (from Windows) that would let me possibly see messages that might be getting logged regarding the Ethernet interface getting mysteriously turned off. Another tool that, if it does exist, why would it not be shown somewhere in the tool bar or Dash Home area so that mere mortals can actually find it?!

6) I started Thunderbird before I downloaded Evolution, to see if it had Exchange support. It doesn't, so I bailed out of it before completing the first account setup. Now I have a mail message icon in the top right corner of my screen that I can't seem to make go away. If I click on it, I get a drop down list that includes Thunderbird Mail, Compose New Message, and Contacts. I went back into Thunderbird and held down the Alt Key, then chose File/Quit from the menu bar, but this icon is still there. How do I make it go away?

Please help! Thanks!

---

### Post by ManamiVixen on 2013-03-11
It might not seem obious, but on the left bar, the top button is the start menu. Then at the bottom of the menu, there is an icon that looks like a crayon, ruler, ect.. Click that to get your installed apps. Hover over installed an click it to see all installed apps. You should see Dconf there and the Terminal app. BTW, Unity is a new paradyme and throws out the old. If you want Windows-like Desktops . Use KDE or Cinnamon. They may do you better. :) seeing as Unity isn't for the old, but for the new. Not for you, but for your kids. Like if you grew up on command line, but your kids started using that new fangled, not as powerfull "desktop". You wouldn't understand. 

As for other stuff here. Evolution and Thunderbird only support IMAP and POP protocals (as far as I'm aware of). So you can use a GMAIL account for mail. All your mouse settings are in the system settings panel. Unfortuantly, it's really only setup for 2 button mice, but the other three buttons you have are not useless, you just have to manually map them to something using a shortcut tool. 

Heres an Linux network MAN that may help you.
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting#.UT6Kv1Eupk8](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting#.UT6Kv1Eupk8)

Hope I helped.

---

### Post by arpanaut on 2013-03-11
[https://help.ubuntu.com/12.04/ubuntu-help/index.html.en](https://help.ubuntu.com/12.04/ubuntu-help/index.html.en)

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)  

A couple of links to help you get orientated with the Unity Desktop.

---

### Post by stuartv on 2013-03-11
Thanks, ManamiVixen,

Finally! I don't know how I could have missed those tiny little icons at the very bottom of the screen after clicking on something at the top left, and only being shown a short list of icons, also at the top of the screen.

1) So, now I see Dconf editor and Term. I also see the System Log. And, opening that, what do my wondering eyes see? A bunch of log entries with no timestamps on them! How am I supposed to tell if something got logged at the time when my Wired connection got dropped?

2) Long story short, I started the process to reinstall VMWare Tools in Ubuntu. I successfully ran the script that reinstalled them. Then it kicked off the script to configure them. That script found the gcc compiler, but it could not find the kernel header path. So, I went into the Ubuntu Software Center and searched for the kernel headers. I found "Generic Linux kernel headers" and installed that. But now the VMWare script wants me to enter the path to the headers and I have no idea where the Software Center put them! It didn't give me a choice for where to install them and the Software Center doesn't show anywhere (that I can see) where it put them.

More help? :confused:

---

### Post by alphacrucis2 on 2013-03-11
Evolution is supposed to support MS exchange (mapi) but you may need this:

[https://launchpad.net/ubuntu/+source/evolution-mapi](https://launchpad.net/ubuntu/+source/evolution-mapi)

I don't know if that gets installed along with Evolution by default as I have never used it.

---

### Post by DuckHook on 2013-03-11
Perhaps you should approach this learning curve in a different way:


Here are some sites that are great for new users:


[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)


Here are my observations:


1. Your problems may be less to do with Ubuntu and more to do with the way you have set up your VM. You have not assigned sufficient resources to run Ubuntu. For any practical Ubuntu VM, you need a minimum of 2 CPUs and all the video memory you can give it. Ubuntu is designed to run with lots of 3-D effects and needs significant base HW if run in a VM.


2. Again, VMs are usually the culprit in wonky network connections. I also run many OSes in VMs and have run into similar problems in the past. Try a bridged network rather than NAT addressing. The double NAT addressing through your router and then through your VM will often cause wonky behaviour. This is not an Ubuntu problem. My Windows installs act up just as often, and there is no obvious program or app in Windows to address the problem either.


3. The dconf editor is similar to the Windows regedit and is frankly much more versatile (because it addresses config files that are writtten in plain text, and therefore do not even really need dconf editor to change). However, just like regedit it is not easily accessible because it is not meant for "mainstream, Joe User". To run it, you simply open the Dash and type "dconf editor". As soon as you type enough characters for the Dash to make accurate predictions, it will present a selection of apps you can choose.


4. The terminal is called Terminal and is available in the Dash within the apps section , but the easiest way to invoke it is using the shortcut keys, <Ctrl>+<Alt>+<t>. However, there is a better way to view the info you want using the log viewer, again, available in the Dash apps area. However, you can also bring it up by typing "log viewer" in the Dash (you should notice a pattern developing here).


5. I realize that your familiarity with Windows makes that system easier for you to use, but by the same token, my familiarity with Ubuntu makes this system the easier one for me to use. And every time I have to defrag Windows disks, wait ten minutes for Antivirus to finish downloading/scanning, or suffer through fifteen minutes of mystifying disk thrashing, I find myself doing the "if this were Linux..." thing.


6. Evolution supports Exchange, but I don't know how to configure it to work through an HTTP proxy. The first thing you may wish to do is simply ask the gurus on this forum in a separate thread. The Ubuntu community is one of the best features of the OS. To delete T-Bird, you must actually delete it. This is no different than the way Windows works. It is not enough to just delete the icon in either OS. Deleting an app is as simple as searching for Thunderbird in the Software Center and clicking "uninstall".


A final word of unsolicited advice: you are mistaking unfamiliarity with difficulty of use. Ubuntu is not Windows. By bringing a Windows mindset into your approach, you are putting yourself behind the 8-ball before you even start. Any learning curve is difficult and frustration is perfectly understandable. I recommend that before you just dive into Ubuntu, read the resources in the links provided above. It will give you a much better grounding for not only technical knowledge, but a better set of expectations.

---

### Post by cortman on 2013-03-11
Sorry, I don't know anything about VMWare and little about virtualization, but I do know you can find where all files related to an installed package are unpacked on a system by running

```
dpkg-query -L package_name
```

Hope that helps you find the kernel headers.
Also if you want to install software, I find the command line tools to be much more useful than software-center- look up the man pages for apt-get and apt-cache.

---

### Post by stuartv on 2013-03-12
First of all, thank you to all of you for the helpful links.

> **alphacrucis2 said:**
> Evolution is supposed to support MS exchange (mapi) but you may need this:

[https://launchpad.net/ubuntu/+source/evolution-mapi](https://launchpad.net/ubuntu/+source/evolution-mapi)

I don't know if that gets installed along with Evolution by default as I have never used it.

I did install this package along with Evolution. Without this package, Evolution wouldn't let me choose Exchange as my mail provider at all (only POP3 and IMAP, essentially). WITH this package, it let me choose Exchange, but the configuration process did not provide any way to specify using an HTTP proxy (as far as I could tell).

---

### Post by LewisTM on 2013-03-12
For accessing Exchange, I would recommend you try the [DavMail]("http://davmail.sourceforge.net/") Gateway software in combination with Thunderbird+Lightning or Evolution.
DavMail will translate Exchange resources to industry standard IMAP/SMTP (mail), LDAP (Addresses) and CalDav (Calendar). It supports custom proxies.

In its basic incarnation, all you need is an OWA (Exchange) URL. The user authentication is piped from your mail client through the DavMail gateway. The gateway is typically accessed though a local port e.g. [http://localhost:1080/users/](http://localhost:1080/users/)[username]/calendar for CalDav.

Cheers!

---

### Post by stuartv on 2013-03-12
> **DuckHook said:**
> 
Here are my observations:


1. Your problems may be less to do with Ubuntu and more to do with the way you have set up your VM. You have not assigned sufficient resources to run Ubuntu. For any practical Ubuntu VM, you need a minimum of 2 CPUs and all the video memory you can give it. Ubuntu is designed to run with lots of 3-D effects and needs significant base HW if run in a VM.

[B][StuartV] So, you're saying Ubuntu requires more resources than Windows?!?! I often run 3 Windows 7 x64 VMs at the same time (on my quad core laptop), each with 1 core assigned and 2 - 4 GB of RAM assigned. 2 of the VMs will also be running Visual Studio and full-blown SQL Server within them (one VS2005 with SQL 2005 and one VS2010 with SQL 2008). The third VM is just plain Win 7 x64 being used to do test installs and test runs of the application I'm working on. And they all maintain rock solid network connectivity.

Now you're telling me that a machine (my laptop) that can do all that with no noticeable performance degradation or network connectivity problems can't run one VM of Ubuntu on 1 core and get solid performance??[/B]


2. Again, VMs are usually the culprit in wonky network connections. I also run many OSes in VMs and have run into similar problems in the past. Try a bridged network rather than NAT addressing. The double NAT addressing through your router and then through your VM will often cause wonky behaviour. This is not an Ubuntu problem. My Windows installs act up just as often, and there is no obvious program or app in Windows to address the problem either.

**[StuartV] I AM using bridged connections. That is my default and I confirmed it yesterday when I was working on the issue. As I said above, MY Windows installs never display network connectivity problems - even when I'm running 3 Windows VMs at the same time. And I do all my development work in these VMs, so I'm in them full time (during the work day) - and most of the time VPN'd (VPN software running in one of the VMs) into my office.**

**I am baffled that you could say so definitely that this is not a Ubuntu problem.**


3. The dconf editor is similar to the Windows regedit and is frankly much more versatile (because it addresses config files that are writtten in plain text, and therefore do not even really need dconf editor to change). However, just like regedit it is not easily accessible because it is not meant for "mainstream, Joe User". To run it, you simply open the Dash and type "dconf editor". As soon as you type enough characters for the Dash to make accurate predictions, it will present a selection of apps you can choose.

[B][StuartV] One of the reasons I have jumped into Linux is that, with all the things I read and hear about how Linux is finally a viable desktop replacement candidate for Windows, I want to evaluate that claim for myself (besides wanting to do some Linux-based development projects). As such, I am attempting to do everything I can the way I would tell my parents to do it (if I replaced Windows on their PC with Linux). And that means (for one thing) no typing commands. If I can't navigate to an app by clicking through some menus, then I certainly cannot expect my parents to run it. For Joe User, typing is for entering data - not navigating their computer or running programs.

Fortuntely, in this case, I did find the Dconf Editor in the "all apps" tab of the Dash Home button.[/B]


4. The terminal is called Terminal and is available in the Dash within the apps section , but the easiest way to invoke it is using the shortcut keys, <Ctrl>+<Alt>+<t>. However, there is a better way to view the info you want using the log viewer, again, available in the Dash apps area. However, you can also bring it up by typing "log viewer" in the Dash (you should notice a pattern developing here).

**[StuartV] Again, I did find it in Dash apps. And again, having to actually know the name of what you want, and type it in, does not fly with Joe User. Joe User may not need to run Log Viewer - but then again, they might. Regardless, there are plenty of other apps in the Dash apps area that Joe User would want to run - even though they don't know the app's exact name.**


5. I realize that your familiarity with Windows makes that system easier for you to use, but by the same token, my familiarity with Ubuntu makes this system the easier one for me to use. And every time I have to defrag Windows disks, wait ten minutes for Antivirus to finish downloading/scanning, or suffer through fifteen minutes of mystifying disk thrashing, I find myself doing the "if this were Linux..." thing.

**[StuartV] Sure. But, if we were having this same conversation in reverse, at no time would I have ever told you, "go here and TYPE xyz". I would have told you what buttons and menu entries to click on. And THAT is a fundamental difference. And, I would say, until a somewhat computer-savvy Joe User can install and run Ubuntu reliably without requiring help in the form of "go here and type blahblahblah', it's not going to pose a serious threat to Windows.**


6. Evolution supports Exchange, but I don't know how to configure it to work through an HTTP proxy. The first thing you may wish to do is simply ask the gurus on this forum in a separate thread. The Ubuntu community is one of the best features of the OS. To delete T-Bird, you must actually delete it. This is no different than the way Windows works. It is not enough to just delete the icon in either OS. Deleting an app is as simple as searching for Thunderbird in the Software Center and clicking "uninstall".

**[StuartV] I don't want to delete Tbird. It wasn't showing an icon in the top right (the system title bar?) of the screen until I ran it for the first time. i've decided not to use it (at least, for now), so I want that notification icon to go away. Are you saying the only way to get rid of that is to delete Tbird from my system?**


A final word of unsolicited advice: you are mistaking unfamiliarity with difficulty of use. Ubuntu is not Windows. By bringing a Windows mindset into your approach, you are putting yourself behind the 8-ball before you even start. Any learning curve is difficult and frustration is perfectly understandable. I recommend that before you just dive into Ubuntu, read the resources in the links provided above. It will give you a much better grounding for not only technical knowledge, but a better set of expectations.

I expected this comment. But, I don't think I am (mistaking unfamiliarity with difficulty). I want to make my mouse thumb button do a Back in the browser. I found the mouse configuration applet. It just doesn't let me do what I want. That's not my unfamiliarity. That's a shortcoming in Ubuntu. And pretty glaring, considering how long 3+ button mouses have been around. 

I wanted to view the system log. In Windows, you run Event Viewer. In Linux, you run Log Viewer. A person who doesn't know Windows would still (I believe) pretty easily find Event Viewer, just by clicking on Start, knowing generally what he or she wants, and looking through the menus. I could not find Log Viewer because the UI didn't help me (like the Windows UI does). In Windows, you click the Start button and the next things you need to look at are presented on the screen near where you clicked. With the Dash Home button, I clicked on it (at the top left of my screen) and the next thing I NEEDED to look at turned out to be small icons that are grey, on a translucent grey background, at the very bottom of the screen. With 1920x1200 resolution, that's a long way away, visually. As a developer who was been building user interfaces for over 25 years, my assessment is that this particular part of the UI is significantly inferior to what Windows is providing for the same use case.

Now, all that said, I can recognize some things that are superior to Windows, too. Being told that I need the kernel headers and being able to find them and install them, right through the Ubuntu Software Center is great! Much easier than doing the equivalent thing on Windows. But, I still find it barely believable that after installing them, there is nothing to tell me where they were installed. And, the only way I can tell is to run a command line utility that I have to consult a man page just to know how to run it? (thanks, cortman! I do appreciate the info!)

I didn't start this thread to be a Linux vs Windows thing, but I don't see how anybody can take Ubuntu seriously as a candidate to replace Windows (7, anyway - it seems way better than the travesty that is Windows 8) on the average user's PC. I can't think of anybody I've run across who had to be referred to some website to read up on how to use Windows 7 for normal stuff (e.g. basic setup, web browsing, email, Office-type applications). They just start using it and are able to (generally) figure it out. And where they can't figure it out, another average user is able to point them to a menu entry somewhere (Start/Control Panel/Mouse, for example) that gets them to the program or option that they want - no command line typing just to do something as simple as seeing where a particular package (application) is installed. Yet, here I am. 30 years experience developing software on everything from a DEC PDP-11 to a Unisys A-series to a MicroVAX running Ultrix to DOS to Windows to Android - and I can't figure out some of the most basic things (without resorting to expert-level knowledge and a command prompt)? And thus, the "frustrated" part of my post heading...

---

### Post by stuartv on 2013-03-12
> **LewisTM said:**
> For accessing Exchange, I would recommend you try the [DavMail]("http://davmail.sourceforge.net/") Gateway software in combination with Thunderbird+Lightning or Evolution.
DavMail will translate Exchange resources to industry standard IMAP/SMTP (mail), LDAP (Addresses) and CalDav (Calendar). It supports custom proxies.

In its basic incarnation, all you need is an OWA (Exchange) URL. The user authentication is piped from your mail client through the DavMail gateway. The gateway is typically accessed though a local port e.g. [http://localhost:1080/users/](http://localhost:1080/users/)[username]/calendar for CalDav.

Cheers!

Thanks, Lewis! I will check that out!

---

### Post by stuartv on 2013-03-12
> **cortman said:**
> Sorry, I don't know anything about VMWare and little about virtualization, but I do know you can find where all files related to an installed package are unpacked on a system by running

```
dpkg-query -L package_name
```

Hope that helps you find the kernel headers.
Also if you want to install software, I find the command line tools to be much more useful than software-center- look up the man pages for apt-get and apt-cache.

cortman, I executed that command and got this:

```
stuartv@ubuntu:~$ dpkg-query -L linux-headers-generic
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/linux-headers-generic
/usr/share/doc/linux-headers-generic/copyright
/usr/share/doc/linux-headers-generic/changelog.gz


```

I looked in those folders and don't see any actual headers file or any documentation that tells me the path to the installed headers.

---

### Post by Impavidus on 2013-03-12
linux-headers-generic is a metapackage that depends on linux-headers-<some version>-generic, which contains the actual headers.

---

### Post by stuartv on 2013-03-12
Nevermind, cortman.

I found the headers.

/usr/src/linux-headers-3.5.0-25-generic/include

My reinstall of the VMWare Tools appears to be proceeding successfully now. Actually, just finished. Apparently, successfully.

Thanks again for the help.

---

### Post by stuartv on 2013-03-12
> **Impavidus said:**
> linux-headers-generic is a metapackage that depends on linux-headers-<some version>-generic, which contains the actual headers.

Got it. So how would I know what actual package it installed, so that I could run the command to tell me where they are? Looking in the Ubuntu Software Center, it just tells me I installed linux-headers-generic.

---

### Post by stuartv on 2013-03-12
Annnnd... now I'm hosed again.

The first time I installed Ubuntu (yesterday), it came up and was running. Networking was flaky (as described earlier), so I restarted the VM (using the menu at the top right). It started rebooting, displayed the Ubuntu splash screen, then hung with a black screen just showing "[ OK ]" in white, at the upper right. I tried doing a "reset" on the VM and it did the same thing. I ended up deleting the VM and creating a new one and installing again. That's what I was running the rest of yesterday, up until just now.

Just now, the VMWare Tools finished reinstalling and it told me I should reboot. So I did. Again, using the menu at the upper right to do a Restart. It shutdown and started booting up and now it has done the same thing as yesterday. Ubuntu splash screen, then black, with [ OK ] at the upper right.

Oh, and I tried hitting Enter yesterday and today. Nothing. It just sits there, hung. it does show a blinking cursor, and when I hit return, the cursor moves down a line and all the way to the left. But, that's it.

Any more suggestions? I'm going to start a thread on the VMWare support forums on this.

---

### Post by stuartv on 2013-03-12
Sonuvagun! I did VM/Restart Guest about 3 times, and on the third time, it booted back up and let me login. I did another Restart (from the Ubuntu menu) and it did it again - booted to a black screen and hung. Did VM/Restart Guest a couple more times and it booted up again and let me login. 

Also, each time I do VM/Restart Guest, it displays some messages. The first is:

acpid: exiting

then some others

Then:

* Asking all processes to terminate      [OK]
* Killing all remaing processes         [fail]

or words to that effect. Anybody have any idea what's going on??

---

### Post by stuartv on 2013-03-13
Final update on this:

I blew away my VM and created a new one from scratch. This time, I did not do the VMware "easy install". I created an empty VM then "inserted" the Ubuntu VM and powered on the VM, then went through the normal Ubuntu install process. When it finished, everything seemed fine and I logged in then restarted the system 3 or 4 times, with no problems. 

Then I installed the VMware Tools. And my boot problems were back, just like that.

I think I'm going to just blow it away again and create it again without the VMware Tools and leave it that way for now. I started a thread on the VMware support forum about this. Hopefully, VMware will come out with updated Tools soon. Being able to copy and paste between host and guest is pretty handy sometimes....

---

### Post by mastablasta on 2013-03-13
> **stuartv said:**
> A person who doesn't know Windows would still (I believe) pretty easily find Event Viewer, just by clicking on Start, knowing generally what he or she wants, and looking through the menus. I could not find Log Viewer because the UI didn't help me (like the Windows UI does). In Windows, you click the Start button and the next things you need to look at are presented on the screen near where you clicked. With the Dash Home button, I clicked on it (at the top left of my screen) and the next thing I NEEDED to look at turned out to be small icons that are grey, on a translucent grey background, at the very bottom of the screen. With 1920x1200 resolution, that's a long way away, visually. As a developer who was been building user interfaces for over 25 years, my assessment is that this particular part of the UI is significantly inferior to what Windows is providing for the same use case.

Not in windows 8. and in unity everything is about search. so you click dash and type in view log. 

> 
I didn't start this thread to be a Linux vs Windows thing, but I don't see how anybody can take Ubuntu seriously as a candidate to replace Windows (7, anyway - it seems way better than the travesty that is Windows 8) on the average user's PC. I can't think of anybody I've run across who had to be referred to some website to read up on how to use Windows 7 for normal stuff (e.g. basic setup, web browsing, email, Office-type applications). They just start using it and are able to (generally) figure it out. 
yah because everyone is born with that knowledge... they know where things are because they've been using it since probably childhood. and i have plenty of co workers that do not know where to find such things as for example the command prompt.

the commands are given becuase someone else might have same problem as you and these commands work in all desktop environments (the default Unity&Gnome, KDE, XFCE, LXDE, IceWM, Openbox, E17....). furthermore they often work across linux distributions. so even someone not running ubuntu can get help by reading the forums.

i seriously consider linux as windows replacement. there are many here that already did the switch.

now then speaking of various distributions and options and since you desperatelly want windows like interface then have a look at Kubuntu (it's what i use since i do not get along with Unity as well). if you want the XP feel then right click on K and use classic menu. another option is Xubuntu which you can easily modify to look like windows.

i think windows copied a lot of stuff form KDE (kubuntu) and probably vice versa....: [http://www.kubuntu.org/feature-tour](http://www.kubuntu.org/feature-tour)

---

### Post by stuartv on 2013-03-13
> **mastablasta said:**
> Not in windows 8. and in unity everything is about search. so you click dash and type in view log. 

**I agree. I already pointed out that Windows 8 sucks!**

yah because everyone is born with that knowledge... they know where things are because they've been using it since probably childhood. and i have plenty of co workers that do not know where to find such things as for example the command prompt.

**Fortunately, the average Windows user almost never needs to use the command prompt - though you can invoke it from the Start/All Programs/Accessories menu.**

the commands are given becuase someone else might have same problem as you and these commands work in all desktop environments (the default Unity&Gnome, KDE, XFCE, LXDE, IceWM, Openbox, E17....). furthermore they often work across linux distributions. so even someone not running ubuntu can get help by reading the forums.

**This is a Ubuntu forum, right? I'm asking questions about Ubuntu, as it comes out of the box. **

i seriously consider linux as windows replacement. there are many here that already did the switch.

now then speaking of various distributions and options and since you desperatelly want windows like interface then have a look at Kubuntu (it's what i use since i do not get along with Unity as well). if you want the XP feel then right click on K and use classic menu. another option is Xubuntu which you can easily modify to look like windows.

[B]I don't "desperately want" a Windows interface. But, as I said up front, ONE of the reasons I'm jumping into Ubuntu is to evaluate the platform for suitability to replace Windows on the desktops of the various people that use me for support - e.g. my parents. So, I'm asking questions to get answers that would work for those kinds of users. And I can assure you that I will not be putting my parents on a platform where the standard answers to common, ordinary user questions come in the form of "go to a command prompt and type xyz -blahblahblah" Oh, and make sure you get the case exactly right. Oh, and wait, you're using the Bourne shell? Sorry, that command works for csh. I'll have to give you a different command for the shell you're using.

This is the newb subforum, right? For Ubuntu, right? If every newb question cannot be answered without resorting to command line interfaces (with a presumption of Ubuntu, as it comes out of the box), then I'd say that, well, there are other, more user-friendly (or, perhaps, newb-friendly would be more accurate?) operating systems for a newb to use.[/B]

i think windows copied a lot of stuff form KDE (kubuntu) and probably vice versa....: [http://www.kubuntu.org/feature-tour](http://www.kubuntu.org/feature-tour)

My other reasons for jumping into Ubuntu involve, essentially, learning the modern Linux platform as it is the platform for a few different software development projects I have in mind working on in the mobile and embedded systems spaces. So, I'm not particularly concerned about the how-to details of Unity or Gnome or KDE or any of those others, for myself. Like I said, wanting to understand Ubuntu - as it comes out of the box - from an "average user" perspective is just one of my goals.

---

