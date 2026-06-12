---
title: "No Signal Flash on Monitor with Ubuntu (Not sure what version, but will check)"
date: 2014-10-27
forum: New to Ubuntu
---

### Post by hopper2 on 2014-10-27
Hello, I am quite new to Ubuntu as I just installed it on my computer today. It seemed no one else had this problem, so here I am. I can start Ubuntu and have it working fine, then it will turn on my monitor (not completely just has nothing to display) and then says no signal. This will not stop until I reboot and then it will repeat after some time. This only happens when I run bigger applications, so not if I'm using the terminal or command script or whatever you would like to call it. Any help on fixing this would be great. Also, since I'm new to Ubuntu, I put it in this section opposed to others. Thanks for reading and I hope you can help. ):P

-----
EDIT
-----
I am running Ubuntu 14.10!

---

### Post by grahammechanical on 2014-10-27
> [COLOR=#000000]I can start Ubuntu and have it working fine, then it will turn on my monitor (not completely just has nothing to display)[/COLOR]

I do not understand that comment. Ubuntu will load without a monitor being switched on. Any operating system will do that. But I always turn my monitor on before I switch on the computer. If I do not, then Ubuntu will not switch (turn) the monitor on. 

Could it be that what you are describing is Ubuntu's method of screen saving? It is activated by default when we install and if the screen is inactive for more than 5 minutes the screen will go dark. Some monitors may display a "no signal" message.

Go to System Settings>Brightness and Lock and change the setting labelled "Turn screen off when inactive for." The Lock setting will also turn the screen off.

Regards.

---

### Post by buzzingrobot on 2014-10-28
> **hopper2 said:**
>  I can start Ubuntu and have it working fine, then it will turn on my monitor (not completely just has nothing to display) and then says no signal.


Did you mean everything works fine, including the display, then, after a while the display goes blank?  Follow GM's suggestions about the Lock setting.  While you are in System Settings, take take a look at the Power Managment settings.  The Lock function hides the screen after a designated time, while everything else remains as it is.  Think of it as a privacy feature you might use in an office environment.  The Suspend function, which is configurable in Power Management, also results in a blank screen, but, in effect, puts the machine to sleep until you wake it up, with any open applications, etc., restored.

In my experience, a "no signal" message on a display means no data is coming from the video card through the cable to the display. This can happen, of course, if the video card is malfunctioning (perhaps as it gets warmer) or if the cable becomes loose. (You'd also see it if the monitor were set, say, for HDMI, while you actually were using DisplayPort, or vice versa. But then, you'd see no display at all.)

---

### Post by hopper2 on 2014-10-28
> **grahammechanical said:**
> I do not understand that comment. Ubuntu will load without a monitor being switched on. Any operating system will do that. But I always turn my monitor on before I switch on the computer. If I do not, then Ubuntu will not switch (turn) the monitor on. 

Could it be that what you are describing is Ubuntu's method of screen saving? It is activated by default when we install and if the screen is inactive for more than 5 minutes the screen will go dark. Some monitors may display a "no signal" message.

Go to System Settings>Brightness and Lock and change the setting labelled "Turn screen off when inactive for." The Lock setting will also turn the screen off.

Regards.

I am sorry, I think I made an error when I was typing. So what happens (full rundown from computer bootup) is I turn on my computer (with monitor on), and then it lets me choose to boot Ubuntu 14.10 or Windows 7. I choose Ubuntu, and after some loading, it shows the login screen. I login, and the monitor is still on. After I open something like the Ubuntu App Store or Firefox, what will happen is my mouse will be able to move around but will not be able to click on anything to close etc. While this is happening, Every 5 or 7 seconds the monitor will say no signal, and then it will go back to having the mouse move around but not be able to click anything. This keeps happening until I reboot. Thanks for trying to help, I hope I was much clearer this time.

---

### Post by hopper2 on 2014-10-28
> **buzzingrobot said:**
> Did you mean everything works fine, including the display, then, after a while the display goes blank?

Somewhat. It'll be working fine, then I can't click anything, and the display says no signal for about 5-7 seconds, then goes back to not being able to click anything, then repeats.

---

### Post by hopper2 on 2014-10-28
I would also like to note that if I go into Advanced Ubuntu Options on the operating system select screen, then go into recovery mode, select dpkg and after its done resume, it goes to a lower resolution but works properly.

---

### Post by hopper2 on 2014-11-08
I also tried installing Linux Mint and the screen is doing this in the Live USB version so I can't install it either. If anyone wants I can make a video of it happenning.

---

### Post by buzzingrobot on 2014-11-09
> **hopper2 said:**
> I would also like to note that if I go into Advanced Ubuntu Options on the operating system select screen, then go into recovery mode, select dpkg and after its done resume, it goes to a lower resolution but works properly.

That might point to an issue with the video driver.  Monitors display "No signal" when they aren't getting any video data. Recovery mode uses a generic unoptimzed approach to video so it works in as many situations as possible.  

What kind of hardware are you using, expecially the video card?  If you can keep it workig long enough, System Settings -> Details will show you how Ubuntu has identified the hardware.

---

### Post by hopper2 on 2014-11-10
> **buzzingrobot said:**
> That might point to an issue with the video driver.  Monitors display "No signal" when they aren't getting any video data. Recovery mode uses a generic unoptimzed approach to video so it works in as many situations as possible.  

What kind of hardware are you using, expecially the video card?  If you can keep it workig long enough, System Settings -> Details will show you how Ubuntu has identified the hardware.

I will just give you my specs, as well as with you were talking about video drivers I was thinking the same thing.
OS: Windows 7 Home Edition and Linux Mint (at the moment, I used to have Ubuntu but have the same problem in Mint)
32 bit or 64 bit: 32 bit
Graphics Card: ATI Radeon HD 2900 Pro
Processor: Intel Pentium 4
CPU 3.20 GHz (Single core)
RAM: 2GB

If there is anything else you want to know, just ask. Thanks for helping so far! :D

---

### Post by buzzingrobot on 2014-11-10
Just guessing here, but does "No Signal" appear when you haven't used the mouse?  That is, if you boot up, load the usual applications, and then do nothing else and just walk away, what happens?

"No signal", though, means the display isn't getting a signal from the video card over the cable, and that's hardware related. I'm at a loss to explain why it happens intermittently, though. Video cards are often sensitive to heat; have you noticed increased fan noise?  A faulty cable could be an issue, or a good cable that's not correctly attached. (Jiggle the cable and see what happens.) Sometimes video cards need to be reseated, i.e., pushed securely into place.

---

### Post by Mike_Walsh on 2014-11-10
Just out of curiosity, are you using a wired mouse, or a wireless one? The wireless dongles for these mice can sometimes malfunction, which would account for the fact that your mouse won't click on anything.

Just a thought; if it IS wireless, when were the batteries last replaced? You can reasonably expect between 6 - 9 months on a decent set of alkalines.....but they won't last for ever.

Regards,

Mike.

---

### Post by buzzingrobot on 2014-11-10
I'll add that I have a wireless Logitech mouse and keyboard that use the same Logitech dongle. The mouse in that circumstance frequently stops working.  I don't though, see the 'No Signal' message.

Just to be sure, does the screen go black when 'No Display' appears?

---

### Post by hopper2 on 2014-11-10
> **buzzingrobot said:**
> Just guessing here, but does "No Signal" appear when you haven't used the mouse?  That is, if you boot up, load the usual applications, and then do nothing else and just walk away, what happens?

"No signal", though, means the display isn't getting a signal from the video card over the cable, and that's hardware related. I'm at a loss to explain why it happens intermittently, though. Video cards are often sensitive to heat; have you noticed increased fan noise?  A faulty cable could be an issue, or a good cable that's not correctly attached. (Jiggle the cable and see what happens.) Sometimes video cards need to be reseated, i.e., pushed securely into place.

If I walk away, it will stay the same and will work if I come back. If I use the mouse, it's still fine. Whenever this occurs, there is an increase in fan noise, but my computer is very quiet right up until this happens, so I don't think it's overheating. Also my video card and cable work fine with Windows, so I don't think there's a problem there. One thing I did find out, is that AMD stop supporting Linux and Ubuntu at least a year ago, probably more.

---

### Post by hopper2 on 2014-11-10
> **Mike_Walsh said:**
> Just out of curiosity, are you using a wired mouse, or a wireless one? The wireless dongles for these mice can sometimes malfunction, which would account for the fact that your mouse won't click on anything.

Just a thought; if it IS wireless, when were the batteries last replaced? You can reasonably expect between 6 - 9 months on a decent set of alkalines.....but they won't last for ever.

Regards,

Mike.

I'm using a wired mouse, and when this problem occurs, I can move my cursor around but I can't click on anything.

---

### Post by hopper2 on 2014-11-10
> **buzzingrobot said:**
> I'll add that I have a wireless Logitech mouse and keyboard that use the same Logitech dongle. The mouse in that circumstance frequently stops working.  I don't though, see the 'No Signal' message.

Just to be sure, does the screen go black when 'No Display' appears?

The screen goes black, and then says no signal in the top right corner.

---

### Post by buzzingrobot on 2014-11-11
> **hopper2 said:**
> If I walk away, it will stay the same and will work if I come back. If I use the mouse, it's still fine. Whenever this occurs, there is an increase in fan noise, but my computer is very quiet right up until this happens, so I don't think it's overheating. Also my video card and cable work fine with Windows, so I don't think there's a problem there. One thing I did find out, is that AMD stop supporting Linux and Ubuntu at least a year ago, probably more.

AMD does provide drivers for Linux but I don't believe their drivers support cards of that vintage.

The open source driver was installed by default when you first installed the system.  Those drivers may be less effective in terms of heat and fan control (AMD doesn't release their source code, just the binary driver, so it's a bit of a guessing game for FOSS developers). I agree it seems unlikely, but it's possible the card is periodically overheating.

---

### Post by Mike_Walsh on 2014-11-11
> **buzzingrobot said:**
> AMD does provide drivers for Linux but I don't believe their drivers support cards of that vintage.

The open source driver was installed by default when you first installed the system.  Those drivers may be less effective in terms of heat and fan control (AMD doesn't release their source code, just the binary driver, so it's a bit of a guessing game for FOSS developers). I agree it seems unlikely, but it's possible the card is periodically overheating.

That's STRANGE. My old Compaq desktop uses AMD stuff throughout; in fact the graphics chip is an ATI (pre- the buyout by AMD) Xpress200, and that works perfectly. I just occasionally get the odd brief glitch when I'm booting-up my Kubuntu flash drive install.....but as we all know, the Plasma desktop IS quite demanding! Ubuntu NEVER gives me any trouble like that, even though Unity IS fully 3D. The Gallium 0.4 does an exemplary job; just goes to show what an amazing feat the devs have managed to pull off, considering they haven't got all the code to play with.

As it's integrated, it doesn't have a built-in fan, of course; but there's so much space inside this Compaq tower, and everything runs SO cool, I can't EVER see this thing overheating. The CPU (an Athlon 64) rarely tops 45C.....even in the middle of summer.

Regards,

Mike.

---

### Post by hopper2 on 2014-11-11
> **buzzingrobot said:**
> AMD does provide drivers for Linux but I don't believe their drivers support cards of that vintage.

The open source driver was installed by default when you first installed the system.  Those drivers may be less effective in terms of heat and fan control (AMD doesn't release their source code, just the binary driver, so it's a bit of a guessing game for FOSS developers). I agree it seems unlikely, but it's possible the card is periodically overheating.

It may be, but I also saw yesterday on the site that there was an available legacy driver but I can't run it properly. Also any Linux desktop shouldn't be causing an overheat. If anything Windows would overheat before a Linux desktop does. I would also like to note (although this may not be important) that I can run Minecraft on Windows at 50 FPS flat and my computer makes little noise.

---

### Post by hopper2 on 2014-11-20
I also tried it again and had the same issue but my computer stayed at it's low state of noise.

---

### Post by JeQhdMD on 2014-11-20
Maybe I missed it . . . but did you try installing the proprietary drivers via the Settings Manager?   When you click on the "additional drivers" tab (System Settings>Software & Updates>Additional Drivers tab) . . . . do any driver packages show available for install?
.............................................................................

Just in case - as it seems the open source driver not cutting it . . . did you try a less intensive desktop such as Mate or XFCE (Ubuntu Mate or Xubuntu)?

---

### Post by hopper2 on 2014-11-23
> **JeQhdMD said:**
> Maybe I missed it . . . but did you try installing the proprietary drivers via the Settings Manager?   When you click on the "additional drivers" tab (System Settings>Software & Updates>Additional Drivers tab) . . . . do any driver packages show available for install?
.............................................................................

Just in case - as it seems the open source driver not cutting it . . . did you try a less intensive desktop such as Mate or XFCE (Ubuntu Mate or Xubuntu)?

I'll try that now.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
EDIT
What is the equivalent to that for Linux Mint? I looked at the drivers setting in Mint and nothing showed up.

---

### Post by hopper2 on 2014-11-29
I'm looking into upgrading my system soon and I will see if that changes anything.

---

### Post by hopper2 on 2014-12-08
I have upgraded my system! Still having the error but I changed to VGA (I have a DVI to VGA in right now, used to have DVI to HDMI) just to see if anything changed.

My New Specs:
OS: Windows 8.1
32 bit or 64 bit: 64 bit
Graphics Card: ATI Radeon HD 2900 Pro
Processor: AMD A8 5600K
CPU 3.6 GHz (Quad core)
RAM: 8GB

I'm not sure if this helps or not but I'm not sure so I thought it was a good idea to post it anyway.

---

### Post by hopper2 on 2014-12-08
I'll try to get a USB and make a version of Ubuntu so I can try that again...

---

### Post by hopper2 on 2014-12-14
Tried using the onboard graphics chip and it worked. *Sigh* I guess the card was just too old.

---

