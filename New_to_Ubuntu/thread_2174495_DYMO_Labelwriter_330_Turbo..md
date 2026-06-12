---
title: "DYMO Labelwriter 330 Turbo."
date: 2013-09-14
forum: New to Ubuntu
---

### Post by hilario2 on 2013-09-14
Hi all;

I'm really new to ubuntu (tried many times but for any reason or any software I never made the final step.

Now I'm almost comvinced to move the only thing I need is the following:

I have a DYMO label writter model turbo 330.I need it to my work.
The problem is that untill now I never managed to make it print the labels as it does in windows.

Does anyone in this forum have a solution for me on how to install the right software to make it print correctely.I can make it print but it prints a label that sould be like this:

art. 30.09.28
sizze  L
color: marine 

as a result I get something printed like that:

FILE:/MEDIA
___________

<?=xml version="1
<diecutlabel ver
         <paperOr

??? something like that that makes no sense.

Any ideas how I can get the righr software from dymo ??

tks in advance.

---

### Post by Mark Phelps on 2013-09-14
> Any ideas how I can get the righr software from dymo ??

Sorry to say this, but if they don't offer Linux software (which, evidently they do not), you're most likely, not going to be able to use their product.

There are Linux label apps (last one I used was GLabels), but my own experience with them was that they didn't have anywhere near the features of the MS Windows products -- which is one reason why I kept my Windows install.

---

### Post by QIII on 2013-09-14
Since it's not an "either or" proposition, I do as Mark Phelps does.  I use both Windows and Linux.

You don't have to give up Windows.  Dual boot or run one or the other in a virtual machine.  If you are just getting started with Linux, run it in a VM.  That way if you break it you are not stuck.  And breaking things is often the best way to learn how to use them.

---

### Post by hilario2 on 2013-09-14
That's what I thought.
I also have dual boot with windows and ubuntu.

Thank you both for the  quick replies.

---

### Post by stretch2 on 2013-09-14
Hi, Im quite new to Ubuntu aswell (After 15 years of Microsoft ... Gave up with them after they've decided to get rid of their Technet Subscriptions Lol) ...

I find Wine works really well with a lot of Windows applications, so if you can get the software for your device, and research into how to get Wine to see your printer, using the Windows OR Linux drivers, you may be in luck

---

### Post by Jonathan Precise on 2013-09-14
I agree with stretch2. Use WINE to make use of the windows software.

---

### Post by whitesmith on 2013-09-14
There's also CrossOver, a paid version of Wine. If you need tech support to get your hardware working -- and you can't figure out how to do it on your own -- consider CrossOver if the hardware issue is a deal breaker.

---

### Post by iamjiwjr on 2013-09-14
I googled this question. It seemed to me that CUPS drivers for Linux are available from DYMO.

---

### Post by sam_baker2 on 2013-09-14
DYMO label writter works with XP. Have you got your install CD for XP?
If so, you may want to try Oracle VirtualBox and run XP as a guest and see 
if the writter will work there.
XP will run in it's own workspace in Ubuntu, exactly like another Linux program
in any other workspace. I use VirtualBox to run one XP program that I need.
( if you Get VirtualBox, download it from the VirtualBox website, you will need 
what is called "guest additions" )

---

### Post by mastablasta on 2013-09-15
virtual box is in software center and i believe guest additions are downloaded with it.

---

### Post by oldfred on 2013-09-15
Does your printer accept raw text, or do you know the control codes?

[http://opennomad.com/content/raw-cups-configuration-challenge](http://opennomad.com/content/raw-cups-configuration-challenge)

In the old days we used to send text & escape codes to printers to control them. 

Even with some newer Zebra printers & Windows we used a raw text printer which would have Windows sent nothing and used Zebra's control codes to format label.

---

### Post by CeejRab on 2013-09-15
Hello Hilario2,

You may find wine useful as the others have stated, but i would also offer the idea of install VirtualBox and using a virtual machine with an install of windows on it to further your purposes of printing with windows compatible software. VirtualBox is free, very easy to use, and as long as you have at least 1GB-2GB of RAM it should be able to run your regular OS and the virtual machine as well fairly easily.

Rather than trying to run windows programs in the ubuntu environment, you may find it easier to use a full windows OS naturally in the virtual machine without having to dual boot and have a messy boot load screen every time you start your machine.

Hope this is some help! All the best,

-Christian

---

### Post by hilario2 on 2013-09-15
So to do that  I have to install virtual box or do I have to uninstall ubuntu first and install virtual box and then ubuntu  again ??

---

### Post by fireflower on 2013-09-15
In short, no, you don't have to do that. Virtual Box is a program you run on linux. Within that program is ANOTHER WORLD, like the Matrix. In that other world, you can install Windows. Vice versa is also possible. You could install VMware to a computer running Windows, and within the alternate universe you have created LIKE A GOD, you can run a linux distro.

---

### Post by mastablasta on 2013-09-16
here is one of many guides...: [http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox](http://www.wikihow.com/Install-Windows-XP-on-Ubuntu-with-VirtualBox)

---

### Post by hilario2 on 2013-09-16
Ok I tried VB but didn't like it.

Everything is very slow and ubuntu is a small window with windows 7 on the background.
I prefer the way I have it alongside with windows 7.

Now my next proble is:

I have a HP 2180 printer and scanner that I use only for scanning ( my main printer is working fine with ubuntu).

I woul like to use it also on ubuntu as a scanner but I really don't know how to do it.
Ubuntu detects my 2180 HP but I can do nothing, any ideas on how to installthe software so that I can run it as a scanner ??

---

### Post by oldfred on 2013-09-16
I have a HP Deskjet 3520. The download directly from HP is a lot newer version and just works.
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by JKyleOKC on 2013-09-16
> **mastablasta said:**
> virtual box is in software center and i believe guest additions are downloaded with it.Yes, it's in Software Center and the official repositories, but because of *buntu's "system freeze" policy those versions are now at least six minor revisions out of date. The current version, at Oracle's PPA, is 4.2.18 and works quite well with Xubuntu 12.04.3.

Adding the Oracle PPA to your sources.list file, as described at its web site, makes updating as automatic as the rest of *buntu.

---

### Post by JKyleOKC on 2013-09-16
> **hilario2 said:**
> Ok I tried VB but didn't like it.

Everything is very slow and ubuntu is a small window with windows 7 on the background.
I prefer the way I have it alongside with windows 7.That sounds as if you installed vbox into Win7 and then installed Ubuntu into vbox, which is the exact opposite of what was recommended. Try installing vbox into Ubuntu, then install your old copy of WinXP into vbox. When you create the VM for XP, accept the suggested sizes for RAM and DISK; they pretty well guarantee that it won't be excessively slow. It may be slower than native operation, but you won't have to re-boot to use the printing software; my experience is that with at least 2 GB of RAM on the host and only 512 MB used by the guest, the slowdown is not detectable.

After installing XP, use vbox's Devices menu (at the top of the window that contains XP) to "Install guest additions" with XP up and running. You'll get three "Mother May I?" messages about the drivers; in all three cases, tell it to go ahead anyway. Then reboot the XP VM (NOT Ubuntu itself) to activate all the goodies. The View menu of vbox should then have several options including full screen, seamless, and auto-resize. I select auto-resize so that I can make the XP window any size I want; you may prefer full screen.

I do run one system here as a dual boot with Win7 and Xubuntu 12.04 in place, and several vbox VMs under Xubuntu. One of those VMs, with XP running my email client, runs 24/7 and does not show slowdown. I've only booted into Win7 a half dozen times or so during the past year, and those were all just to run updates.

---

