---
title: "Trouble upgrading to Saucy Salamander"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-02-26
Hello all :) I feel perhaps this should go into the 'Installing/Upgrading' section but as Im a complete beginner I thought here was for the best. Please let me know if this is a problem.

As software updates are no longer available for older versions of Ubuntu I am trying to upgrade to Saucy Salamander. After I use the Software Updater and it tells me that the software is up to date, but I should upgrade, I click 'upgrade' and am asked for my password to authenticate. After that, nothing. The windows disappear, nothing else happens. If anyone could help me that'd be great :)

---

### Post by zvacet on 2014-02-26
Please,give more info.At least can you tell us which Ubuntu version do you run right now?That will be very helpful.

---

### Post by jan_jan_64 on 2014-02-26
Im sorry, im not even sure how to tell you that - my computer was changed to linux by my comp-savvy ex and I have pretty much no idea what im doing oO I have both Ubuntu and LXDE desktops installed, but aside from that I dont know what to tell you or how to get more info for you im afraid..

---

### Post by ibjsb4 on 2014-02-26
Open a terminal (Ctrl + Alt + T) and enter (copy and paste) the following command:

```
sudo apt-get update
```

If you get this far without errors, then do:

```
sudo apt-get dist-upgrade
```

Please post any errors with code tags.

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by zvacet on 2014-02-26
O.K. We will go step-by-step.In **Menu -> Accessories  **open LXTerminal.Type

```
 lsb_release -a
```

and post output here.

---

### Post by whitesmith on 2014-02-26
Hi, **jan_jan_64**! The easiest way to get your Ubuntu version is to click on the gear tool in the notification tray. Then select System -> Details -> Overview. This approach avoids the dreaded command line interface. Don't be discouraged with Linux. We're here to help. Check out the first link in my sig line before you go any further. Cheers!

---

### Post by jan_jan_64 on 2014-02-26
Sorry, seems I cant even work the forums properly!

So..

[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") : I tried this with no error messages, everything seems fine. However if I use the software updater again it still tells me my Ubuntu is out of date and I need to upgrade to 13.10..

[**[COLOR=#000000]zvacet[/COLOR]**]("http://ubuntuforums.org/member.php?u=79320"): Thanks! Here is the output:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

[**[COLOR=#000000]whitesmith[/COLOR]**]("http://ubuntuforums.org/member.php?u=664837"): Great links, Ill check them out when I get chance to sit down and study them! I dont have much problem using the command lines - this is pretty much how ive been using Ubuntu under my old boyfriend's instruction. The only problem is I havent really understood *what *im doing whilst doing so. Anyways, as long as everything is in really basic, simple steps im sure ill do fine :)

---

### Post by ibjsb4 on 2014-02-26
Try using the terminal to upgrade.

```
do-release-upgrade
```

---

### Post by zvacet on 2014-02-27
@  **jan_jan_64 **

   You can not upgrade to 13.10 because your Ubuntu version is not supported any more.In 2 months time new LTS (long term support) version will be out.I suggest you to wait until 14.04 is out and then do fresh install.That version will be supported 5 years. ;)

---

### Post by monkeybrain20122 on 2014-02-27
> **zvacet said:**
> @  **jan_jan_64 **

   You can not upgrade to 13.10 because your Ubuntu version is not supported any more.In 2 months time new LTS (long term support) version will be out.I suggest you to wait until 14.04 is out and then do fresh install.That version will be supported 5 years. ;)

What do you want OP to do, not using his/her computer for 2 months to wait for LTS? Besides the wait is likely longer than that because all new Ubuntu releases are kind of buggy and it usually takes a month or two for the post release bug fixes, I would not advise an inexperineced user to grab an iso right after it is released.

13.10 is supported til July so I think a fresh install is the way to go. By then 14.04 should be solid.

---

### Post by jan_jan_64 on 2014-02-27
I BORKED IT!!    Thank god I still have my notebook... So I tried using the command line as recommended by ibjsb4, the do-release-upgrade thing. It was working perfectly fine - it said that it would probably take a few hours so I was just letting it run. I checked in on the terminal at some point and it was asking me for a choice. Now, bare with me here, because I cant really give perfect details of what it said but ill do my best.  It said there was a new replacement for a certain third party software package and asked me if I wanted to replace it or not. I had no idea what I was looking at, so I decided to press 'D' and compare the old and new package - maybe that way Id know at least what package we were talking about. So I did it, and the info it output didnt realy help me much. But after that, I couldnt continue with anything, I couldnt go back to the initial choice of what to do, nothing that I put into the terminal was doing anything.   So like any stuck computer noob, I did the most obvious and stupid thing - I closed the terminal, and opened a new one to just try the process again. But now it said there was no new upgrade. I used the command line to check of updates, and it spat back a bunch of errors.     So my next best move was to reboot and see if that helped. It did not. Now my screen resolution is totally messed up. I know this has happened before in the past whilst trying to update my Nvidia drivers, but I never had to fix it before myself and now my screen looks like im trying to run Windows in safe mode. Only half my task bar is visible, and whatever happened when I messed up the update seems to be putting a real strain on my CPU cause Ive never seen a computer so sluggish (I have a little CPU monitor thingy in my taskbar). My mouse is unresponsive for 5 minutes at a time and it constantly appears to have crashed.    I cant be more specific right now about what happened unless there is a command you can give me to use to give you a read out of the last things that were in the terminal. Please help! PS. Whenever I reboot, I keep getting a pop up message saying 'system program problem detected: Do you want to report the problem now?' Like, every time. EDIT: Im really sorry about my formatting here, I couldnt get my line breaks to work >_>

---

### Post by ibjsb4 on 2014-02-27
Yep, its borked :(  Lets see whats going on.  What happens when you press "Ctrl + Alt + T" ?  If you get to a terminal enter:
```

sudo apt-get -f install
```

Do you have personal files stored in Ubuntu or do you have backup?

Edit:  Also try "Ctrl + Alt + F1".

---

### Post by jan_jan_64 on 2014-02-27
Hi!  Yes I do have personal files :/ I tried to connect my external harddrive to copy them before I messed it up more but i waited over 20 min for it to mount it and it just crashed and did nothing.  I tried the software updated and it told me the same as you. Thankfully I started taking notes, now.  The software updater said: 'Software index is broken. Must run 'sudo apt-get install -f'  I ran it, got this message in the terminal:  dpkg interrupted. You must manually run 'sudo dpkg --configure -a' to correct the problem'.  Currently doing that now. Manually clicking 'partial upgrade' in the software updater just made everything crash, but the terminal seems to be working OK now. Ill let you know when the dpkg process has finished.. The message window reading 'system program problem detected: do you want to report the problem now?' keeps popping up all the time. Considering how slow the computer is running I dont know if it is messing up the terminal processes atm tho. Terminal currently reads: 'Running depmod' and has done for the last 5 min.

---

### Post by nunecas123 on 2014-02-27
Why don't you download the ISO from Ubuntu's website and store your important files on a partition or make a backup of them? I know it takes time and I know you wish not to do this, but sometimes we've got to be pragmatic - sorry if I seem arrogant, but I'm just trying to help, mate.

---

### Post by jan_jan_64 on 2014-02-27
> **nunecas123 said:**
> Why don't you download the ISO from Ubuntu's website and store your important files on a partition or make a backup of them? I know it takes time and I know you wish not to do this, but sometimes we've got to be pragmatic - sorry if I seem arrogant, but I'm just trying to help, mate.  Not at all, mate, any help is appreciated! Problem is the computer is now running so slow and crashing at the merest mouse movement that I dont think its possible :/

---

### Post by ibjsb4 on 2014-02-27
> **jan_jan_64 said:**
> Hi!  Yes I do have personal files :/ I tried to connect my external harddrive to copy them before I messed it up more but i waited over 20 min for it to mount it and it just crashed and did nothing.  I tried the software updated and it told me the same as you. Thankfully I started taking notes, now.  The software updater said: 'Software index is broken. Must run 'sudo apt-get install -f'  I ran it, got this message in the terminal:  dpkg interrupted. You must manually run 'sudo dpkg --configure -a' to correct the problem'.  Currently doing that now. Manually clicking 'partial upgrade' in the software updater just made everything crash, but the terminal seems to be working OK now. Ill let you know when the dpkg process has finished.. The message window reading 'system program problem detected: do you want to report the problem now?' keeps popping up all the time. Considering how slow the computer is running I dont know if it is messing up the terminal processes atm tho. Terminal currently reads: 'Running depmod' and has done for the last 5 min.

Good for you, keep it up and let us know what happens.

Edit:  This also could take hours.

---

### Post by nunecas123 on 2014-02-27
> **jan_jan_64 said:**
> Not at all, mate, any help is appreciated! Problem is the computer is now running so slow and crashing at the merest mouse movement that I dont think its possible :/

Can't you make a bootable USB or DVD on the computer you're using? (I assume you're working on another computer, as the other is almost impossible to work on).
If yes, try to download an ISO of an Ubuntu LiveCD and see if, at least, you can get some of your files from your broken system.
I hope everything goes alright.

---

### Post by jan_jan_64 on 2014-02-27
Some (minor) success! I appear to have gotten back to the place in the upgrade process that I messed up before.  The terminal reads:  configuration file 'etc/xdg/autostart/zeitgeist-datahub.desktop'  ==>modified (by you or by a script) since installation. ==> package distributor has shipped an updated version. What would you like to do about it? Your options are:  Y or I : install the package maintainer's version N or O: Keep your currently-installed version D: Show the differences between the versions z: start a shell to examine the situation The default action is to keep your current version.  Last time I pressed D and then couldnt work out how to continue with the process. Recommendations of how to proceed much appreciated!

---

### Post by jan_jan_64 on 2014-02-27
> **nunecas123 said:**
> Can't you make a bootable USB or DVD on the computer you're using? (I assume you're working on another computer, as the other is almost impossible to work on). If yes, try to download an ISO of an Ubuntu LiveCD and see if, at least, you can get some of your files from your broken system. I hope everything goes alright.  Im working on a notebook with no CD or DVD drive, and I have no idea how to make a bootable USB - I am a very noobish noob im afraid :/ Thanks for the advice, though! I hope I dont lose my stuff :(

---

### Post by nunecas123 on 2014-02-27
> **jan_jan_64 said:**
> Im working on a notebook with no CD or DVD drive, and I have no idea how to make a bootable USB - I am a very noobish noob im afraid :/ Thanks for the advice, though! I hope I dont lose my stuff :(

What operating system are you using on that notebook?

---

### Post by westie457 on 2014-02-27
> **jan_jan_64 said:**
> Some (minor) success! I appear to have gotten back to the place in the upgrade process that I messed up before.  The terminal reads:  configuration file 'etc/xdg/autostart/zeitgeist-datahub.desktop'  ==>modified (by you or by a script) since installation. ==> package distributor has shipped an updated version. What would you like to do about it? Your options are:  Y or I : install the package maintainer's version N or O: Keep your currently-installed version D: Show the differences between the versions z: start a shell to examine the situation The default action is to keep your current version.  Last time I pressed D and then couldnt work out how to continue with the process. Recommendations of how to proceed much appreciated!

Usually when presented with an options window needing a response it is normally okay to go with the default option.

---

### Post by ibjsb4 on 2014-02-27
> **westie457 said:**
> Usually when presented with an options window needing a response it is normally okay to go with the default option.

I agree with this one, but no to "auto updates" and later in the process you may be asked to install/update grub.  Yes to grub.

---

### Post by jan_jan_64 on 2014-02-27
> **westie457 said:**
> Usually when presented with an options window needing a response it is normally okay to go with the default option.  Thanks! It says the default is No so Ill go with that. New problem - it appears to have crashed after giving me this output and I cant continue. I will reboot and try again.

---

### Post by ibjsb4 on 2014-02-27
> **jan_jan_64 said:**
> Thanks! It says the default is No so Ill go with that. New problem - it appears to have crashed after giving me this output and I cant continue. I will reboot and try again.

When it crashed, is the terminal locked up and not usable?

You say appears to have crashed.  There could be processes running in the background.

---

### Post by jan_jan_64 on 2014-02-27
> **ibjsb4 said:**
> When it crashed, is the terminal locked up and not usable?  Yes, it has done it several times now.. There could be process running in the background but Ive tried to ensure that nothing else is running in the mean time. Its obviously from the processes the terminal is trying to run, I can see the CPU useage in my little monitor continuously spiking to 100%, but Im not running anything else. When it crashed before in my previous post I had not touched the computer for like, 10 min.

---

### Post by ibjsb4 on 2014-02-27
As nunecas123 has said, you can retrieve your files with the live 13.10 dvd, plus fix your computer with it.  But I would still like to give repair another try.  Did you manage to get back to terminal?

---

### Post by jan_jan_64 on 2014-02-27
> **ibjsb4 said:**
> As nunecas123 has said, you can retrieve your files with the live 13.10 dvd, plus fix your computer with it.  But I would still like to give repair another try.  Did you manage to get back to terminal?  Yep! Its still running now, and running much smoother and faster than before now I got past that y/n choice bit. Id like to be able to retrieve my files if I can, but unless I can actually get the PC to run without crashing every 2 seconds I dont think it will be possible. I will let you know when the terminal has finished running everything.  PS. Im getting quite a few of these y/n/d/z questions. I keep going with default (n), I assume this is OK?

---

### Post by nunecas123 on 2014-02-27
I guess that's the fastest way you could do it right now. What operating system are you using? I will assume you have a Windows machine there:
**1.** Download the desirable ISO to your computer.
**2.** Format your USB drive (save your things somewhere before doing this)
**3.** Download Unetbootin from here: [URL="http://unetbootin.sourceforge.net/"]http://unetbootin.sourceforge.net/
[/URL]**4.** Open Unetbootin and you'll see something like this:

[IMG]http://sourceforge.net/apps/trac/unetbootin/raw-attachment/wiki/MiscWikiFiles/unetbootin-windows7.png[/IMG]

**5.** Click on the three dots ("*...*"), next to DiskImage and select the ISO.
**6.** Check if your USB is the one shown on "*Drive:*"
**7.** Click OK.
**8.** Reboot your computer.
**9.** Press F2, F8 or F12 while on the first boot screen and see if you can get a panel to choose which drive to boot from. If you can, choose to boot from your USB stick.
**10.** Done. Now you can "Try Ubuntu" and get your files out of there. Also, you can make a fresh installation out of this method.

I hope I helped.

---

### Post by ibjsb4 on 2014-02-27
> **jan_jan_64 said:**
> PS. Im getting quite a few of these y/n/d/z questions. I keep going with default (n), I assume this is OK?

Got no idea without knowing the question so go with default answer I guess.

---

### Post by jan_jan_64 on 2014-02-27
OK, the terminal has now stopped.. I got a couple of error messages on the way:  WARNING: softwarecentre.db.update:The file: 'usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalogue. Please consider raising a bug report for this issue with the maintainer of that application.'  I dont know if thats relevant but there ya go.  > **nunecas123 said:**
> I guess that's the fastest way you could do it right now. What operating system are you using? I will assume you have a Windows machine there: **1.** Download the desirable ISO to your computer. **2.** Format your USB drive (save your things somewhere before doing this) **3.** Download Unetbootin from here: [http://unetbootin.sourceforge.net/ ]("http://unetbootin.sourceforge.net/")**4.** Open Unetbootin and you'll see something like this:  [IMG]http://sourceforge.net/apps/trac/unetbootin/raw-attachment/wiki/MiscWikiFiles/unetbootin-windows7.png[/IMG]  **5.** Click on the three dots ("*...*"), next to DiskImage and select the ISO. **6.** Check if your USB is the one shown on "*Drive:*" **7.** Click OK. **8.** Reboot your computer. **9.** Press F2, F8 or F12 while on the first boot screen and see if you can get a panel to choose which drive to boot from. If you can, choose to boot from your USB stick. **10.** Done. Now you can "Try Ubuntu" and get your files out of there. Also, you can make a fresh installation out of this method.  I hope I helped.  That is very helpful, but you give me too much credit im afraid - I cant even make it past step one, and no idea how to do step two T_T

---

### Post by nunecas123 on 2014-02-27
Oops, I'm sorry. That is very easy. Go to *My Computer*, right-click on your USB drive and click *Format*.
Done!

---

### Post by ibjsb4 on 2014-02-27
> OK, the terminal has now stopped.. I got a couple of error messages on  the way:  WARNING: softwarecentre.db.update:The file:  'usr/share/app-install/desktop/sonic-visualiser:mad:-sonicvisualiser-layer.desktop'  could not be read correctly. The application associated with this file  will not be included in the software catalogue. Please consider raising a  bug report for this issue with the maintainer of that application.'  I  dont know if thats relevant but there ya go.  

Are you still able to move foward on this?
Re-enter "-f install" command if it has come to a halt.

---

### Post by jan_jan_64 on 2014-02-27
> **ibjsb4 said:**
> Are you still able to move foward on this? Re-enter "-f install" command if it has come to a halt.  Yes, the process finished with no problem :) So, good news is I rebooted and my graphics problem is now fixed - hooray!  Bad news - When I logged in I still got the 'System program problem detected: Do you want to report the problem now?' message. When I click yes and put in my password, I get another error message saying Ubuntu has experienced an internal error. This caused Software Updater to fail and one of my keyboard applications.  When using the -f install command line, it says there is nothing to be installed or upgraded. I ran the 'lsb_release -a' command and YAY! seems I made it to Saucy :) I also ran apt-get update - there were a lot of packages listed but I dont know if I need them all or how to install them all.

---

### Post by nunecas123 on 2014-02-27
So, the problem is now fixed? :D 
And yes, you better get them!

---

### Post by ibjsb4 on 2014-02-27
Good, good, and good :)

Enter:

```
sudo apt-get dist-upgrade
```

And then just use it for a while, see how it acts.

If that popup persists, it can be disabled.

---

### Post by jan_jan_64 on 2014-02-27
> **nunecas123 said:**
> So, the problem is now fixed? :D  And yes, you better get them!  After I use 'sudo apt-get update' and they are listed, how do I install them all? I made a guess with 'sudo apt-get install update' but ofc it couldnt find a package called update to install ;)  I also used sudo apt-get dist-upgrade - doesnt seem to be anything to report...  Thank you all so much for your help! I was seriously so close to putting my fist through the computer screen XD

---

### Post by nunecas123 on 2014-02-27
[COLOR=#000000][FONT=Consolas]sudo apt-get update
sudo [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]apt-get upgrade

[/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-02-27
Later :)

---

### Post by jan_jan_64 on 2014-02-27
> **nunecas123 said:**
> [COLOR=#000000][FONT=Consolas]sudo apt-get update sudo [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]apt-get upgrade  [/FONT][/COLOR]  Oh.. I thought that was is, but when I run sudo apt-get upgrade, it says 0 upgraded, and if I run sudo apt-get update again, it still gives me a list of things to be updated.

---

### Post by nunecas123 on 2014-02-27
That's odd. It should work with no flaws. I do not know how to solve that issue, I'm sorry.

---

### Post by jan_jan_64 on 2014-02-27
No worries, you guys have been a tremendous help anyways :) Thanks so much!

---

### Post by zvacet on 2014-02-27
> What do you want OP to do, not using his/her computer for 2 months to wait for LTS?

No, just think that it can be used for a couple of months.But your solution is also way to go.Just little bit more installing.

---

### Post by zvacet on 2014-02-27
@ **jan_jan_64**
> Oh.. I thought that was is, but when I run sudo apt-get upgrade, it says 0 upgraded, and if I run sudo apt-get update again, it still gives me a list of things to be updated.

That is because command **sudo apt-get update **just sync your repos with one on the server.After that **sudo apt-get upgrade **will install all updates.Reason why sudo apt-get upgrade didn´t work for you is because you didn´t run sudo apt-get update first to sync your source list. ;)

---

### Post by holycow131415 on 2014-02-27
> **nunecas123 said:**
> I guess that's the fastest way you could do it right now. What operating system are you using? I will assume you have a Windows machine there:
**1.** Download the desirable ISO to your computer.
**2.** Format your USB drive (save your things somewhere before doing this)
**3.** Download Unetbootin from here: [URL="http://unetbootin.sourceforge.net/"]http://unetbootin.sourceforge.net/
[/URL]**4.** Open Unetbootin and you'll see something like this:

[IMG]http://sourceforge.net/apps/trac/unetbootin/raw-attachment/wiki/MiscWikiFiles/unetbootin-windows7.png[/IMG]

**5.** Click on the three dots ("*...*"), next to DiskImage and select the ISO.
**6.** Check if your USB is the one shown on "*Drive:*"
**7.** Click OK.
**8.** Reboot your computer.
**9.** Press F2, F8 or F12 while on the first boot screen and see if you can get a panel to choose which drive to boot from. If you can, choose to boot from your USB stick.
**10.** Done. Now you can "Try Ubuntu" and get your files out of there. Also, you can make a fresh installation out of this method.

I hope I helped.

Life would have been so much easier if you just reinstall your OS with Lubuntu.

1. Before following the above, download the x86 iso from [http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso) to your desktop.
2. Have 2 usb drives ready. One of them is for using as a bootable device, the other is for copying your data off your hard drive once you are in a live session.
3. Follow the above. Once complete, insert into the troubled PC
4. Hit f12 (most common for boot device list), select usb. It should start booting.
5. Click live session
6. When you get a desktop, plug in the other usb, and then search on your hdd for files to copy to the usb.
7. Once done, unplug the usb with the data, and start the installer for Lubuntu.

---

### Post by ibjsb4 on 2014-02-28
> Bad news - When I logged in I still got the 'System program problem detected: Do you want to report the problem now?' message. When I click yes and put in my password, I get another error message saying Ubuntu has experienced an internal error.


If things are running ok and your still getting those popups, run this code.

```
echo 'manual' | sudo tee /etc/init/apport.override
```

---

### Post by nunecas123 on 2014-02-28
> **holycow131415 said:**
> Life would have been so much easier if you just reinstall your OS with Lubuntu.

1. Before following the above, download the x86 iso from [http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.10/release/lubuntu-13.10-desktop-i386.iso) to your desktop.
2. Have 2 usb drives ready. One of them is for using as a bootable device, the other is for copying your data off your hard drive once you are in a live session.
3. Follow the above. Once complete, insert into the troubled PC
4. Hit f12 (most common for boot device list), select usb. It should start booting.
5. Click live session
6. When you get a desktop, plug in the other usb, and then search on your hdd for files to copy to the usb.
7. Once done, unplug the usb with the data, and start the installer for Lubuntu.

Pretty much the same, but thankfully there's someone who is up to show more information. Thanks! ;)

---

