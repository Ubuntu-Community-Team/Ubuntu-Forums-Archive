---
title: "Need Help, Running Compiz-Fusion Icon Hosed My Display"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Stephen Wayne Hamilton on 2013-01-23
I'm currently booted into a live usb.

I had posted another topic on these forums a few days back ([http://ubuntuforums.org/showthread.php?t=2106154](http://ubuntuforums.org/showthread.php?t=2106154)), seeking a solution on how to turn on Compiz effects off temporarily so I can increase gaming performance and get games (WINE) to go into fullscreen properly. A user recommended to install CFI from the Ubuntu Software Center. At first I couldnt figure out how to run it, clicking on its' icon did nothing. So I did some Googling and found that I could get CFI to run by entering the command 'compiz-fusion icon &' in a terminal. But as soon as I did the unexpected happened and my display got messed up. I was still able to move the mouse but couldnt figure out what to do so I did a hard reset. Upon reboot I got a message stating that my graphics were running in low settings mode (or whatever, cant remember exactly) with an OK button. But I couldnt click on OK and proceed.

So, what do I need to do to restore my display to proper working order?

Any help is appreciated, thanks!

---

### Post by Frogs Hair on 2013-01-23
If you were using Unity it is a Compiz plugin and though you can disable effects like the cube and others you can't disable Compiz and use Unity.

The fusion icon was used on Gnome 2 versions of Ubuntu to switch between metacity and Compiz and made the use of Emerald themes(obsolete on new versions) possible. 

If you have terminal access remove the CFI and reset unity. 

```
sudo apt-get remove fusion-icon 
```  
12.04 ```
unity --reset
```

12.10 ```
setsid unity
```

---

### Post by Stephen Wayne Hamilton on 2013-01-24
@ Frogs Hair: Thanks for the reply, but unfortunately I do not have access to a terminal in my installation, I tried the Ctrl-Alt-T shortcut, but it does nothing. I should have said this before, but I'm running Ubuntu 12.10 x64. I can access a terminal within the live usb, of course, but that wont help me.

When I boot up into my installation I first see the NVIDIA logo, and then a solid black background with a white notification box in the middle of the screen, and it contains the following text:

"Your screen, graphics card, and input device settings could not be detected correctly. You will need to reset....."

I cant remember the rest of what it said, except that there is an OK button at the bottom of the box, but I cant click it since the mouse cursor doesnt appear at all. The keyboard itself doesnt work either. At that point I'm not even logged in, it doesnt give me any option to do so.

So, how can I reset everything from the live usb, or otherwise access a terminal within my installation?

Thanks for any help!

---

### Post by omeomi on 2013-01-24
Can you access the terminal using CTRL+ALT+F1? This should give you a command line-based login prompt and from there you can do everything you would normally do in the terminal window.

---

### Post by Stephen Wayne Hamilton on 2013-01-24
@ Frogs Hair: Yes, I was using Unity at the time, and I assumed/expected that running CFI would disable Compiz's/Unity's effects. I know that Unity is just a plugin of Compiz, and that by disabling Compiz you're also disabling Unity. I had a program installed called CompizConfig Settings Manager (ccsm), and had been messing around with that to see how Compiz could be tweaked. So what I really meant is that I want to disable the effects of Compiz before starting a game with WINE, and then turn them back on afterwards (preferably automatically), because I have read that Compiz/Unity causes issues with that kind of thing, as well as lowering performance in many games. Is CFI an outdated program? And what are my alternatives? What would happen if I ran CFI in KDE or XFCE? I ask because I have those 2 environments installed as well.

@ omeomi: Thanks for that, I tried that keyboard shortcut and it worked. I was able to log in, and then I removed CFI with the apt-get command listed above. But when I tried to run 'setsid unity', it looked like it was going to succeed, but after a few seconds the following line kept repeating itself over and over again:

compiz (opengl) - Error: FBO is incomplete: GL: : FRAMEBUFFER_UNSUPPORTED (0x8cdd)

I was able to press any button and it stopped for a moment and let me type, I was intending to reboot, but then it just took control back and kept repeating the above error. So I did a hard reset again and I still get the message about my graphics being in a low state, etc. I have no idea what it means, and right now my priority is to get back to a working installation ASAP. I have to use this laptop for alot of important things and I cant afford to be in a state of extended downtime while waiting on help. So I'm just going to reinstall (maybe even Mint) and go from there, but I wont be using CFI. I would like to figure out what the above error means though, if anyone has any idea. Maybe I will install 12.10 x64 inside a VM and see if i can duplicate what I did before. For me the whole idea of using Linux is to learn and makes mistakes, and then learn from those mistakes by figuring out what went wrong.

As an aside, does Ubuntu routinely disable the root account (I mean its' password) if it is enabled when it updates itself? I know that Canonical recommends using sudo as often as possible, and not enabling a password for root. But I do so anyway, and also enable the ability to log in directly as root at the LightDM login screen, because there are situations when being able to log in as root directly is more useful. I rarely do so and usually log in as a nonpriviledged user for most of what I do, only using root directly for the times when that account can more easily do certain things that a standard user cannot do easily. I log in as Administrator all the time on Windows and have never had any significant security issues, but I do know that Linux and Windows are two totally different animals. And I can see Canonical's point, but many distros dont disable root's password. It is just an effort to protect users from themselves. I have the ability to restrain myself from using root unless absolutely necessary, so I dont think that leaving it enabled is a big risk in my case. But getting to my point, I tried to log in as root after using Ctrl-Alt-F1 (above), and then entered my password at least a dozen times, and it refused to accept. I know with 100% certainty that my password was correct, and it just kept saying it couldnt authenticate. When I logged in as the standard user the password was accepted the first time around. I updated last night, and I have reason to believe that the update may have disabled root's password.

Well, thanks for any help!

---

