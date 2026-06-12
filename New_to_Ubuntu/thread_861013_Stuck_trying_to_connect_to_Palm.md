---
title: "Stuck trying to connect to Palm"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-16
I haven't been able to get JPilot to recognise my Palm, so I can't sync the Palm.

I found a helpful post on getting Linux and the Palm to see each other:
[http://ubuntuforums.org/showthread.php?t=835839](http://ubuntuforums.org/showthread.php?t=835839)

I followed the instructions on the link:
[http://www.pilot-link.org/README.usb](http://www.pilot-link.org/README.usb)

Unfortunately, when I get to the chapter entitled, "Talking to your Palm over USB", I get the following unhelpful results.
> When you hit the HotSync button on the cradle or by tapping on
your HotSync icon on the Palm itself, you should see something
similar to the following in the system logs (/var/log): *<cut>*My only results in /var/log/messages are:
```
Jul 16 10:31:22 paddy-ubuntu kernel: [  363.539406] usb 1-2: new full speed USB device using uhci_hcd and address 2
Jul 16 10:31:23 paddy-ubuntu kernel: [  363.707597] usb 1-2: configuration #1 chosen from 1 choice
Jul 16 10:32:09 paddy-ubuntu kernel: [  410.173824] usb 1-2: USB disconnect, address 2
```The next instruction is to use pilot-dlpsh. I get the following results.
```
[COLOR=Navy]$ pilot-dlpsh -i -p /dev/pilot[/COLOR]
   Unable to bind to port: /dev/pilot
   Please use --help for more information

[COLOR=Navy]$ pilot-dlpsh -i -p /dev/ttyUSB1[/COLOR]
   Unable to bind to port: /dev/ttyUSB1
   Please use --help for more information

[COLOR=Navy]$ pilot-dlpsh -i -p /dev/ttyUSB0[/COLOR]
   Unable to bind to port: /dev/ttyUSB0
   Please use --help for more information
```Now I'm stuck. I have no idea how to progress.

Can anyone help?

---

### Post by Paddy Landau on 2008-07-16
Bump?

---

### Post by nowshining on 2008-07-16
u need to setup ur port in the prefs of jpilot - ie: the com/usb port.

go to: file - prefs - settings tab - and slect ur serial port from the drop-down box or type it in if it doesn't exist.

keep trying until u get it. :)

---

### Post by Paddy Landau on 2008-07-16
Thanks for the reply.

> **nowshining said:**
> go to: file - prefs - settings tab - and slect ur serial port from the drop-down box or type it in if it doesn't exist.

I'm afraid that I don't understand.

[LIST]
[*]The Palm's cradle is connected via the USB port. Will it still work on serial?
[*]File -> Preferences -> Settings: There is no drop-down box for the serial port. Instead, I need to type it in. I've tried /dev/ttyUSB0, /dev/ttyUSB1 and /dev/tty/pilot. They don't work. That's as I expected because of the previous error with pilot-dlpsh.
[/LIST]
Errors from JPilot:
```
pi_bind error: /dev/pilot No such file or directory
pi_bind error: /dev/ttyUSB0 No such file or directory
pi_bind error: /dev/ttyUSB1 No such file or directory
```In similar vein, System -> Preferences -> PalmOS Devices also fails. It gives the following error:
> Failed to connect using device 'Crade', on port '/dev/ttyUSB0'. Check your configuration, as you requested old-style usbserial 'ttyUSB' syncing, but do not have the usbserial 'visor' kernel module loaded. You may need to select a 'usb:' device.I imagine that that last error relates to the fact that I could not complete the instructions on the page [www.pilot-link.org/README.usb]("http://www.pilot-link.org/README.usb") (as in my first post).

---

### Post by nowshining on 2008-07-16
i found this:

[http://ubuntuforums.org/archive/index.php/t-351029.html](http://ubuntuforums.org/archive/index.php/t-351029.html)

---

### Post by Paddy Landau on 2008-07-16
> **nowshining said:**
> i found this:

[http://ubuntuforums.org/archive/index.php/t-351029.html](http://ubuntuforums.org/archive/index.php/t-351029.html)
Thanks for all your help, nowshining. There have been many suggestions through that link.

Sadly, none of them works.

I attempted to use PlayOnLinux (Wine) to install the Windows software for the Palm, but for some reason it won't install.

So now I'm really stuck.

Maybe I have to buy a different PDA? (Mine is a Palm m130.)

---

### Post by nowshining on 2008-07-16
well um, i have an older palm but serial, it should work, try pressing the hotsync button on your palm before you press the jpilot hotsync button. Alas when u do get it working the hotsync and backup button will backup ur contents - all of them on your palm. 

Also what version of jpilot do you have? if you have an ol' 0.99 version - when I tried hardy the jpilot I compiled worked without a hitch..

the newest version fixes some issues. :)

u can find my compile here:[http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html](http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html)

---

### Post by Paddy Landau on 2008-07-17
> **nowshining said:**
> well um, i have an older palm but serial, it should work, try pressing the hotsync button on your palm before you press the jpilot hotsync button.
I've tried that, and I'll try it again. I also have an older Palm.

> **nowshining said:**
> Alas when u do get it working the hotsync and backup button will backup ur contents - all of them on your palm.
Um, I don't quite understand. I have nothing in JPilot at present; I want to use it solely for the Palm. Is that OK then?

> **nowshining said:**
>  Also what version of jpilot do you have? if you have an ol' 0.99 version - when I tried hardy the jpilot I compiled worked without a hitch..

the newest version fixes some issues. :)

u can find my compile here:[http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html](http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html)
Cool, thanks for the link. I had problems compiling 1.6.0, so I reverted back to 0.99. I will attempt with your compile.

Here's the thing: Must I use usb:, /dev/pilot, /dev/ttyUSB0, or /dev/ttyUSB1? When I try to use pilot-dlpsh for any of the last three, I get the message that it is unable to bind to that port. It makes me think that somehow my machine isn't set up to recognise /dev/pilot, /devUSB0, or /dev/ttyUSB1.

Thanks yet again for your input.

---

### Post by nowshining on 2008-07-17
I personally use a IIIxe with a serial cradle, 

What I meant is that basically if you don't do a hotsync and backup - u won't get any backups or be able to restore from jpilot, except for your memos, etc..  all programs won't restore. :) - u don't need if you use an SD card as a backup device. :)

as for the /dev/ thing

itta be most likely USB and not pilot which is serial.

as for the .99 version of jpilot - it has bugs where timestamps are incorrect, i filed a bug report, but they got it fixed before I did and asked me to test and so it won't drain the battery trying to re-sync all programs - especially if you have large ones...

as for the bind thing, now that I remember - i've had the same problem before - after re-trying for awhile it worked - u can always try switching USB ports :)

altho i never used a USB pilot on linux before but I did read places where pressing hotsync first then sync on the jpilot program would work.

---

### Post by Paddy Landau on 2008-07-17
> **nowshining said:**
> u can find my compile here:[http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html](http://www.4shared.com/file/49608346/dc8cdcc6/jpilot_160-1_i386.html)
The first time I attempted to install your copy, it failed on dependency errors. The second time, JPilot 1.6.0 installed successfully.

Unfortunately, I still get zero results.

Looking at the various other posts, I wonder (again) if I need to somehow get /dev/pilot or /dev/ttyUSB1 registered on my system. My computer just doesn't recognise those paths at all.

Would you know how to get my computer to recognise those paths?

My last resort would be to purchase a new PDA, something that I don't look forward to (transferring all my data by hand!).

---

### Post by nowshining on 2008-07-17
hehe to transfer everything - just backup to an SD card - put it in ur new pda and restore from the card ;)

again /dev/pilot u won't need, u did try initiating the hotsync from within the palm before hitting the jpilot hotsync button right?

alas u can try my port from my system:
```

/dev/ttyS0
```

---

### Post by Paddy Landau on 2008-07-17
> **nowshining said:**
> again /dev/pilot u won't need, u did try initiating the hotsync from within the palm before hitting the jpilot hotsync button right?
Yes, indeed, I did that.

> **nowshining said:**
> alas u can try my port from my system:
```
/dev/ttyS0
```
Nope, it doesn't recognise that:

"pi_bind error: /dev/ttyS0 Invalid argument"

I'm becoming convinced that there's something else I need to do, at a lower level than JPilot. JPilot can't connect the the Palm unless Linux can connect to the Palm.

---

### Post by nowshining on 2008-07-17
u did in the terminal do 

```
sudo modprobe visor
```

edit: if that doesn't work - reboot - then do that again or just try rebooting and syncing to hopefully undo anything u did before then in terminal do the above if it doesn't work on a reboot and try again.

---

### Post by Paddy Landau on 2008-07-17
> **nowshining said:**
> ```
sudo modprobe visor
```
Yes, that was one of the many things I did.

What, specifically, is that command supposed to enable? usb: or /dev/pilot or what?

---

### Post by nowshining on 2008-07-17
it's suppose to enable the visor module - visors used USB. :) - modules = driver.

---

### Post by nowshining on 2008-07-17
i found this also: read the second post:[http://ubuntuforums.org/showthread.php?t=201736](http://ubuntuforums.org/showthread.php?t=201736)

---

### Post by Paddy Landau on 2008-07-17
> **nowshining said:**
> i found this also: read the second post:[http://ubuntuforums.org/showthread.php?t=201736](http://ubuntuforums.org/showthread.php?t=201736)
Unfortunately, it didn't give me anything.

I will probably have to give up and purchase a different PDA. :(

I do appreciate the efforts you've taken over these posts.

---

### Post by lazyart on 2008-07-17
Don't buy a new PDA. I used a Palm T|X and now a Palm Treo 680 with JPilot 0.99 and without issue.  I believe the port i used was usb:any.

Will get back with you on this when I'm home in front of my machine.  I even have software on my Palm to let me access the SD card directly from my desktop.

What model is your Palm?

---

### Post by lazyart on 2008-07-17
oops... i doubled up.

---

### Post by nowshining on 2008-07-17
n/m

---

### Post by Paddy Landau on 2008-07-17
> **lazyart said:**
> Don't buy a new PDA. I used a Palm T|X and now a Palm Treo 680 with JPilot 0.99 and without issue.  I believe the port i used was usb:any.

Will get back with you on this when I'm home in front of my machine.  I even have software on my Palm to let me access the SD card directly from my desktop.

What model is your Palm?
I have a Palm m130.

I found out how to add /dev/pilot to my system:
[http://ubuntuforums.org/showthread.php?p=4106175#post4106175](http://ubuntuforums.org/showthread.php?p=4106175#post4106175)

But, aargh! J-Pilot still recognises none of them.
usb: still gives the same zero result (it sits and waits, and eventually the Palm times out).

An [old community page]("https://help.ubuntu.com/community/PortableDevices/PalmOS") says:
"You can run the Palm Desktop software under VMWare and use the Palm [HotSync]("https://help.ubuntu.com/community/HotSync") Manager. USB syncing can be elusive to get working."

Well, I did try Palm Desktop (for Windows, which works perfectly on this machine when I boot in Windows) using both PlayOnLinux. It didn't install. I found that [CodeWeavers ]("http://www.codeweavers.com/compatibility/search?name=palm+desktop&company=&medal=&date_start%5B1%5D=1&date_start%5B2%5D=1&date_start%5B0%5D=2000&date_start%5B3%5D=0&date_start%5B4%5D=00&date_end%5B1%5D=7&date_end%5B2%5D=18&date_end%5B0%5D=2008&date_end%5B3%5D=16&date_end%5B4%5D=47&search=app")confirms that Palm Desktop doesn't work under Wine.

I'll look up VMWare to find out what it is and how to run it. It sounds as though it may be overkill, however.

---

### Post by nowshining on 2008-07-17
have u tried installing the latest stable wine 1.0 from winehq.org?

---

### Post by Paddy Landau on 2008-07-18
> **nowshining said:**
> have u tried installing the latest stable wine 1.0 from winehq.org?
I have Ubuntu's version 1.0.0. I haven't tried a new version of Wine, but frankly, if  [CodeWeavers]("http://www.codeweavers.com/compatibility/search?name=palm+desktop&company=&medal=&date_start%5B1%5D=1&date_start%5B2%5D=1&date_start%5B0%5D=2000&date_start%5B3%5D=0&date_start%5B4%5D=00&date_end%5B1%5D=7&date_end%5B2%5D=18&date_end%5B0%5D=2008&date_end%5B3%5D=16&date_end%5B4%5D=47&search=app") (which makes money from supporting Windows programs on Linux) confirms that Palm Desktop won't work on Linux, I'll leave it at that.

I'd rather have the native Linux program working, anyway; it makes better sense to me.

---

