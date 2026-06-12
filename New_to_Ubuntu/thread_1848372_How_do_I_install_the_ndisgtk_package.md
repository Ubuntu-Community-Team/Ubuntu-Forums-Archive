---
title: "How do I install the ndisgtk package?"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by JohnTho on 2011-09-22
Hello,

I am a complete newbie and I'm totally confused already. :confused:

I've just installed Ubuntu 9.10 on a virgin (clean) hard drive and everything went fine except that I can't get my Belkin USB wireless adaptor working. On another thread [here]("http://ubuntuforums.org/showthread.php?t=863591") there is a description of how to resolve this using ndisgtk but I found it was not installed although it appears to be on the CD in the path cdrom0/pool/main/n/ndisgtk where is a Debian package named ndisgtk_0.8.4-1_i386.deb. Right-clicking opens a pop-up offering options to open using, among others, GDebi Package Installer. Selecting this gives the error message

Error: Dependency is not satisfiable: ndiswrapper_utils-1.9

If I open using Archive Manager instead it shows three items: Control.tar.gz (1.1Kb), data.tar.gz (19.9Kb) and debian binary (4 bytes).

I have no idea where to go from here, so I'll be very grateful for any assistance.

Mike.

---

### Post by Paddy Landau on 2011-09-22
May I ask why you used version 9.10?

The latest LTS (stable) release is 10.04, and the latest release (non-stable) is 11.04. They will have more up-to-date wireless drivers. It may be worth trying 10.04 or 11.04. (9.10 is not an LTS version.)

If you can download the CD of either 10.04 or 11.04, boot into "Try it" mode (without installing anything) to check if the wireless works "out the box". If it does, install that version instead.

If you cannot download the latest CD, post back to let us know so someone can help you through ndiswrapper.

---

### Post by MG&amp;TL on 2011-09-22
You can get ndiswrapper in *Synaptic*-(10.04) ....just search for it and click the buttons.

---

### Post by JohnTho on 2011-09-23
Thank you both for your replies. Yesterday I installed 10.04.3. This is the progress (or lack of it) so far :-

I located ndiswrapper-common and and ndiswrapper-utils-1.9 on the CD and installed them using Synaptic package manager. I then ran ndiswrapper from a command line with the -i switch and the path to the Belkin .inf file. This was a different name to the one specified in the original thread ["**Belkin N >MIMO< Wireless USB Adapter Driver"**]("http://ubuntuforums.org/showthread.php?t=863591") but I assumed this was just a later version so went ahead and it appeared to install, no errors were reported.

However the driver doesn't work, even after the system has been switched off overnight and rebooted this morning. I took another look in package manager to confirm that both ndiswrapper packages were installed and noticed ndisgtk listed but not installed, so I installed it. I then ran it and it reports that the driver is installed and the hardware is present, but the USB adaptor is still not working.

Maybe I should now direct my queries to the original thread unless anyone reading here has any ideas.

Mike.

---

### Post by JSchultheis on 2011-09-23
You can give this a shot: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I am new here too, but that is the answer I was given when working on a similar issue. Also, why not run 11.04?

---

### Post by anewguy on 2011-09-23
Some things to keep in mind:

- it would be much better if we can find a solution other than ndiswrapper for you.  If your adapter is USB, plug it in, then post back the outputs from both of these commands:

lspci

lsusb

- if you do use ndiswrapper, be sure to use ndisgtk.  It takes away all of the typing you must do using ndiswrapper at the command line.

- the Windows driver files you use (the .inf and .sys files) *MUST* be Windows XP drivers

- the Windows driver files you use must match the architecture of your Ubuntu installation - 32 or 64 bit.

Failure to get the correct driver for Windows XP *ONLY* and matching your Ubuntu installation architecture (32 or 64 bit) can result in things looking like they "should" work but don't, or just out right failure.

If you do use ndiswrapper/ndisgtk:

First off all, please reverse what you did to install your driver via:

sudo ndiswrapper -l (that's a lower case "L" for "list")

This will list the device.

sudo ndiswrapper -e xxxxxx   where xxxxxx is the device name as shown in the output of ndiswrapper -l.  This will remove the device.

Verify the device has been removed via:

sudo ndiswrapper -l (lower case "L" again)

This should return an empty list.

If you did anything like edit the blacklist file, reverse those edits so the file is back to the way it was.

With Ubuntu running, put the LiveCD in the drive.

Using the file browser navigate to the /pool/main/n/ndisgtk folder.

Double-click on the ndisgtk package that shows there to begin it's install, and wait for it to finish.

Go to system/administration/windows wireless drivers (I *think* that's what it says - it will be obvious).  This will start up ndisgtk.  Click the add/new button, point it to the windows driver .inf file and click ok - everything will be done for you, none of the typing or blacklisting as per other old outdated instructions.

dave ;)

---

### Post by Paddy Landau on 2011-09-23
> **JohnTho said:**
> ... I installed 10.04.3.I take it that the wireless did not work out-the-box?

> **JSchultheis said:**
> ... why not run 11.04?10.04 is the best bet if you are going for an LTS. Version 10.04 is supported until 13.04, whereas 11.04 is supported only until 12.10. The next LTS is due 12.04.

---

### Post by JohnTho on 2011-09-23
> **Paddy Landau said:**
> I take it that the wireless did not work out-the-box?.
Hi Paddy,

No, it didn't I'm afraid. I'm out for a few hours now but will try some of the suggestions above ASAP and post back the results.

Thanks everybody.

Mike.

---

### Post by JohnTho on 2011-09-23
Ok, anewguy,

I tried the lspci and lsusb commands. The lspci produces a lot of output - too much to write down and re-type here, however I did notice that it included 5 channels of USB UHCI Controller. Incidentally I know the USB ports are working because my external hard drive works on the same one that I'm using for the Belkin adaptor

lsusb reports:
Bus 005 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002 ID 050d:815f Belkin Components
Bus 001 Device 001 ID 1d6b:0002 Linux Foundation 2.0 root hub

ndiswrapper -l reports:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
       device (050D:815F) present (alternate driver r8192s_usb)

The ndiswrapper -e command wouldn't work and on typing just ndiswrapper to display the syntax I found it doesn't exist and in fact -r is used to remove an installed driver. However that wouldn't work either. I tried 050D:815F,  (050D:815F) and r8192s_usb as the arguments for both -e and -r but in each case it reports 'no such file or directory'. -l still lists the driver as installed and the device as present.

I had a look at the link posted by JSchultheis and tried a few of the things suggested there but had no success with them either except to find that there was, unsurprisingly, zero traffic on wlan0.

So that's how things stand currently and I seem to be at a brick wall.

Mike.

---

### Post by bkratz on 2011-09-23
> **JohnTho said:**
> Ok, anewguy,

I tried the lspci and lsusb commands. The lspci produces a lot of output - too much to write down and re-type here, however I did notice that it included 5 channels of USB UHCI Controller. Incidentally I know the USB ports are working because my external hard drive works on the same one that I'm using for the Belkin adaptor

lsusb reports:
Bus 005 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 002 ID 050d:815f Belkin Components[/COLOR]
Bus 001 Device 001 ID 1d6b:0002 Linux Foundation 2.0 root hub

ndiswrapper -l reports:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
       device (050D:815F) present (alternate driver r8192s_usb)

The ndiswrapper -e command wouldn't work and on typing just ndiswrapper to display the syntax I found it doesn't exist and in fact -r is used to remove an installed driver. However that wouldn't work either. I tried 050D:815F,  (050D:815F) and r8192s_usb as the arguments for both -e and -r but in each case it reports 'no such file or directory'. -l still lists the driver as installed and the device as present.

I had a look at the link posted by JSchultheis and tried a few of the things suggested there but had no success with them either except to find that there was, unsurprisingly, zero traffic on wlan0.

So that's how things stand currently and I seem to be at a brick wall.

Mike.


I believe your device is natively handled in recent versions of Ubuntu. See this thread, esp. starting with post 7.

[http://ubuntuforums.org/showthread.php?t=1673151](http://ubuntuforums.org/showthread.php?t=1673151)

---

### Post by anewguy on 2011-09-23
I think it should be native as well.  If you are still using the old release and determined to use ndiswrapper, then yes indeed I missed type (e key being next to r key) and it should be r for remove.

========================================
EDIT: forgot to mention:

edit the /etc/modules file and remove ndiswrapper from the end

reboot before installing ndisgtk (no, it's not needed, but I like to be sure all traces of ndiswrapper's previous device def are gone).

THEN install ndisgtk and try again.

END OF EDIT
========================================

If you have any question about ndiswrapper and ndisgtk just ask.  I've dealt with that countless times.

Dave ;)

---

### Post by JohnTho on 2011-09-25
Hi anewguy,

No, I'm certainly not determined to use ndiswrapper. I'll go with the easiest route! :) I'm going to try 11.04 even though it's not LTS.

The only module listed in /etc/modules is lp.

Hi also, bkratz. It's interesting that the results of my lsusb listed only Belkin Components and not the full description of the device as shown in your link. I guess that's likely to be significant?

Mike.

---

### Post by bkratz on 2011-09-25
> **JohnTho said:**
> Hi anewguy,

No, I'm certainly not determined to use ndiswrapper. I'll go with the easiest route! :) I'm going to try 11.04 even though it's not LTS.

The only module listed in /etc/modules is lp.

Hi also, bkratz. It's interesting that the results of my lsusb listed only Belkin Components and not the full description of the device as shown in your link. I guess that's likely to be significant?

Mike.


Actually Mike it gave us what we needed.

 [COLOR=Red]ID 050d:815f  
[COLOR=Black]
This gives us the manufacturer (the first number) and the chipset used the second. Google for that number ([/COLOR][/COLOR][COLOR=Black]050d:815f )[/COLOR][COLOR=Red][COLOR=Black] and you will see what I mean.
[/COLOR]
[/COLOR]

---

### Post by JohnTho on 2011-09-25
Ok, I've installed 11.04 and it works "out of the box" so I think we'll consider this one solved. :D

There is one other minor issue that I would value advice on, though. When resizing windows the active area around the window is very narrow, making it tricky to get a grip on it. Is it possible to do anything about this?

Thanks,

Mike.

---

### Post by bkratz on 2011-09-25
> **JohnTho said:**
> Ok, I've installed 11.04 and it works "out of the box" so I think we'll consider this one solved. :D

There is one other minor issue that I would value advice on, though. When resizing windows the active area around the window is very narrow, making it tricky to get a grip on it. Is it possible to do anything about this?

Thanks,

Mike.


Congratulations!  If you would please go to the thread tools at the top of the page and mark the thread as solved. I'm sorry but I don't know about the resize question, perhaps someone else will.

---

### Post by JohnTho on 2011-09-25
Ok, duly marked. I suppose I had better start a new thread on the window question.

Cheers,
Mike.

---

### Post by Paddy Landau on 2011-09-25
You're not the first to complain about the window border size; it has been raised before.

I think it may be a good idea to raise it as a bug.

---

### Post by anewguy on 2011-09-25
+1 on getting everything installed and working, and welcome to the Ubuntu community!  

I also agree with Paddy Landau about filing a bug report.  As he mentioned, countless people (and that includes me) would really like to see that changed.

Dave ;)

---

### Post by JohnTho on 2011-09-25
Hi Dave,

If those guys at CERN are right you might have to change your sig. :D

Mike.

---

### Post by anewguy on 2011-09-28
> **JohnTho said:**
> Hi Dave,

If those guys at CERN are right you might have to change your sig. :D

Mike.

Sorry it took me so long to check back and see this ;)  Man, throws "everything I ever believed about warp speed" in the trash! :) ;)

Seriously, this could be a very interesting change to physics as we know it - it will be great watching how this all unfolds.

Sorry I didn't catch your reply earlier!

Dave ;)

---

### Post by JohnTho on 2011-09-29
I agree. Potentially very exciting.

Mike.

---

### Post by dalzmc on 2011-12-23
i have a belkin F5D9010, i haven't used ndiswrapper or anything (i just plugged it in) and it can pick up on signal, it sees my network, but when i put in my password (wpa) it does not work. so i'm thinking i need to drivers? but i have no internet on that then, but i need to install ndiswrapper... i have 'ndiswrapper-1.57rc1.tar.gz' from sourceforge, but what do i do with it now?

---

