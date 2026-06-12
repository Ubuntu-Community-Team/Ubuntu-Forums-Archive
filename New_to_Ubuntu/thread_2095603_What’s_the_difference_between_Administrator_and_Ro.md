---
title: "What’s the difference between Administrator and Root (Super user?) privileges?"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by columbus2012 on 2012-12-17
Hi, I’m currently using 12.04LTS – system restrictions won’t let me change it in my profile yet.
   
  (Sorry if this post is a bit long it’s grown as I’ve tried to make it clear and comprehensive.)
   
  I’ve just installed a Samsung CLP-415NW/SEE as a network printer (WiFi) on my home network. Works fine on the mixed Win PC’s & Android systems on the network. One PC is dual boot Ubuntu / Win.
   
  In Ubuntu System settings I chose Printing/add printer and the system located and identified the new printer, it searched for drivers and came up recommending Samsung printers but this list did not include the CLP-415. (It’s a fairly new colour laser – 6 months or so).
   
  There are no drivers for Ubuntu/Linux on the install disk; it just says to download a printer specific Linux driver from their website. 

Which I did: 
  Unified Linux driver CLP-410_0.86.tar.gz
   
  The installation Instructions say;
   
  1.    Make sure that the machine is connected to your computer and powered on.
   
  2.        When the Administrator Login window appears, type “root” in the Login field and enter the system password.
   
  (*This don’t work on Ubuntu and I log in as administrator anyway)*
  
  *There is a note in the instructions:*
      You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
   
  3.    From the Samsung website, download the Unified Linux Driver package to your computer.
   
  4.    Right-click the Unified Linux Driver package and extract the package.
  Double click cdroot > autorun. 

  *I do this and chose RUN from the menu that appears. (Choosing Run in terminal produces the same result);*
  *At this point  a pop up message appears saying;*
  
  [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG][COLOR=Red]* You are not authorised to install the driver package. *[/COLOR]
[COLOR=Red]*Only user with Root privileges is allowed to do this *[/COLOR]
  
  *So the rest below does not happen*
   
  5    When the welcome screen appears, click Next.
   
  6    When the installation is complete, click Finish.
   
  The installation program added the Unified Driver Configurator desktop icon and the Unified Driver group to the system menu for your convenience. If you have any difficulties, consult the on-screen help that is available through your system menu or from the driver package Windows applications, such as Unified Driver Configurator or Image Manager.
   
  Any ideas please what I do next?
   
  Thanks in advance for any help.


Chris

---

### Post by audiomick on 2012-12-17
It sounds like you are trying to run the installer from the file manager, Nautilus. You could try starting an instance of Nautilus using
```
gksudo nautilus
```

from the terminal.

A couple of things, though. I tried the samsung unified linux drivers for my CLP-300, and if I recall rightly, I wasn't impressed. I don't remember what the problem was, but I am not using it anymore.

I also believe that the drivers for Linux on the CD from the printer left files belonging to root on the desktop. I had to use sudo to get rid of them. That is a bit of a vague memory, though. It was a few years back.

What you could try is to use one of the other drivers out of the list that Ubuntu offers. You might get lucky. I should add that the drivers for mine (foomatic something or other) don't do a very good job with colour. Black and white is ok.

What is behind this
> 2. When the Administrator Login window appears, type &#8220;root&#8221; in the Login field and enter the system password.

(This don&#8217;t work on Ubuntu and I log in as administrator anyway)


is that the root account is disabled in Ubuntu. The sudo mechanism is used to give the users who are allowed to use it root privileges. When the window pops up asking for your password, that is sudo working. To evoke sudo in  a terminal, you need to type sudo before the command. You will be asked for your password, but will not see it as you type it.

---

### Post by oldfred on 2012-12-17
I still do not remember to type sudo with commands that need it. But if I get that error message I know I need sudo.

       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by columbus2012 on 2012-12-18
Thanks Guys! the gksudo nautilius tip solved it. 

I had tried running it in terminal under sudo but for whatever reason it was unsuccessful. Which was when I posted for help.

In Nautilius it ran OK, identified the printer as a network device, installed the driver & printed a colour/B&W  test page. with no problems.

I had read some of the post's here about the problems with Samsung's Unified printer driver so time will tell.

---

### Post by The Cog on 2012-12-18
Just answering the question in the title,

The root account is sometimes called superuser, perhaps because on many systems the **su** command is used to change your identity to root. As you probably know, sudo is used in ubuntu rather than su, because in ubuntu the rooot account password is locked so you can't login as root or su to root (sudo asks for your password, not the root password). Sometimes people refer to the root account as the administrator account, because administrator is the closest thing to root on windows.

In ubuntu, there is an **admin** group and it os only members of this group who are allowed to use the sudo command. Sometimes, people refer to members of this group as administrator accounts. So an "administrator" account in ubuntu could mean a couple of different things depending on who you are talking to.

Oh, and I gather that on windows, the administrator account does not have full rights to the machine. I have been told that there is a system account that only microsoft can make use of, that has rights that administrator account does not.

---

### Post by audiomick on 2012-12-18
Thanks Cog. I knew all that vaguely, but would not have been able to formulate it so well. ;)

---

### Post by haqking on 2012-12-18
> **The Cog said:**
> Just answering the question in the title,

The root account is sometimes called superuser, perhaps because on many systems the **su** command is used to change your identity to root. As you probably know, sudo is used in ubuntu rather than su, because in ubuntu the rooot account password is locked so you can't login as root or su to root (sudo asks for your password, not the root password). Sometimes people refer to the root account as the administrator account, because administrator is the closest thing to root on windows.

**In ubuntu, there is an admin group and it os only members of this group who are allowed to use the sudo command.** Sometimes, people refer to members of this group as administrator accounts. So an "administrator" account in ubuntu could mean a couple of different things depending on who you are talking to.

Oh, and I gather that on windows, the administrator account does not have full rights to the machine. I have been told that there is a system account that only microsoft can make use of, that has rights that administrator account does not.

The account in Windows aside from Administrator is known as the System account, and it can be used though usually for underhanded purposes ;-)
Just to be picky ;-) "**In ubuntu, there is an admin group and it os only members of this group who are allowed to use the sudo command" ** is a legacy thing,  Since 12.04 I think ? the sudo group is used as opposed to admin previously, the admin group remains for compatability

Edit: yeah i thought so, found a source [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Common_Infrastructure](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Common_Infrastructure)

---

### Post by GordThompson on 2012-12-18
> **The Cog said:**
> Oh, and I gather that on windows, the administrator account does not have full rights to the machine. I have been told that there is a system account that only microsoft can make use of, that has rights that administrator account does not.
Do you have a source you could cite? I've certainly never heard that. Yes, the "real" Administrator account is disabled by default, but that's no different than Ubuntu disabling 'root'. As for a secret Microsoft-only account, that sounds to me like one for the tinfoil-hat crowd.

---

### Post by haqking on 2012-12-18
> **GordThompson said:**
> Do you have a source you could cite? I've certainly never heard that. Yes, the "real" Administrator account is disabled by default, but that's no different than Ubuntu disabling 'root'. As for a secret Microsoft-only account, that sounds to me like one for the tinfoil-hat crowd.

read my post above.

There is the admin account to which the user has access and there is a system account which services rely on, the fact you switch to tinfoil hat as an assumption makes you paranoid ;-)

Open up your task manager in windows and look at the processes, some are using SYSTEM as the owner

The Cog was not implying some corporate underhand backdoor access

Edit: if you want a source apart from my vast array of experience, knowledge and above all my humility then here you go [http://support.microsoft.com/kb/120929](http://support.microsoft.com/kb/120929)

---

### Post by GordThompson on 2012-12-18
> **haqking said:**
> read my post above.

There is the admin account to which the user has access and there is a system account which services rely on, the fact you switch to tinfoil hat as an assumption makes you paranoid ;-)

Open up your task manager in windows and look at the processes, some are using SYSTEM as the owner

The Cog was not implying some corporate underhand backdoor access
Okay, thanks. (Your reply snuck in before mine. I was typing it on my phone and it took *way *longer than it should have.) My apologies to The Cog for misinterpreting the post.

As for being paranoid, I'd love to chat about that but I gotta run. I'm being followed, you see.... ;)

---

### Post by haqking on 2012-12-18
In addition, there is often confusion about the Administrator account in Windows.

For example in Windows 7 the administrator account is not the one you login with, and it exists it is just disabled and has a blank password by default.

This fact along with the SYSTEM account allows many tools and people ;-) to take advantage of it to gain elevated privelege and system access.

---

### Post by The Cog on 2012-12-18
> Edit: yeah i thought so, found a source [https://wiki.ubuntu.com/PrecisePango...Infrastructure](https://wiki.ubuntu.com/PrecisePango...Infrastructure)Thanks for that link. I wasn't aware of that change.

> Do you have a source you could cite? I've certainly never heard that. No I can't remember where I heard it. I have a feeling that's what account windows updates use but it's all rumour and hearsay.

As for tin foil hats, you need to be very careful. If you get the shiny side in, it can create a resonant cavity that actually amplifies the mind control waves rather than protecting you from them. And then you can't see the black helicopters at all - it's not that they've gone away.

---

### Post by haqking on 2012-12-18
> **The Cog said:**
> Thanks for that link. I wasn't aware of that change.

 No I can't remember where I heard it. I have a feeling that's what account windows updates use but it's all rumour and hearsay.
.

not rumour at all, it has always been that way as i posted above.

When a user installs Windows they create an account(contrary to popular belief this is not the Administrator account) it is an account which is in the Administrator group with Admin privelege and gets prompted with UAC when authorising.

There is also a Administrator account which is disabled by default and has no password by default when it is enabled (the user needs to go to local users and groups to enable it if they want it for a specific purpose)

There is also the SYSTEM account used by the OS and many processes and services and access to the file system, this account can be used maliciously and is done so often with many tools but i wont discuss that here ;-)

The SYSTEM account is not MS backdoor into your computer though, it is used much like in Linux for system process which are owned and run by root.

Peace

---

### Post by GordThompson on 2012-12-18
> **The Cog said:**
> As for tin foil hats, you need to be very careful. If you get the shiny side in, it can create a resonant cavity that actually amplifies the mind control waves rather than protecting you from them. And then you can't see the black helicopters at all - it's not that they've gone away.
Brilliant. Thanks for the tip! :D

---

### Post by audiomick on 2012-12-18
> **haqking said:**
> ...

There is also a Administrator account which is disabled by default and has no password by default when it is enabled (the user needs to go to local users and groups to enable it if they want it for a specific purpose)

Ah, that might explain something that has puzzled me a little. My laptop, dual boot with Vista, went back to the manufacturer for a warranty job a while back. When I got it back, there was a user on there that I hadn't created called "admin" or "administrator". I reckon they must have activated that Administrator account. I haven't tried to log in there, but maybe I should try. If there is no password on it, I think I'd better disable it again.

---

### Post by haqking on 2012-12-18
> **audiomick said:**
> Ah, that might explain something that has puzzled me a little. My laptop, dual boot with Vista, went back to the manufacturer for a warranty job a while back. When I got it back, there was a user on there that I hadn't created called "admin" or "administrator". I reckon they must have activated that Administrator account. I haven't tried to log in there, but maybe I should try. If there is no password on it, I think I'd better disable it again.

highly likely, though I expect they put a password on it.

try with blank.

If not go back into your account and then disable it again or at least give it a complex password, it is a handy way of getting access to your machine if you screw something up but make sure the account has a strong password.

Peace

---

### Post by audiomick on 2012-12-18
> **haqking said:**
> highly likely, though I expect they put a password on it.

try with blank.

If not go back into your account and then disable it again or at least give it a complex password, it is a handy way of getting access to your machine if you screw something up but make sure the account has a strong password.

Peace
Thanks for the tip.

---

