---
title: "Can't Transition to Lubuntu Because of Keyboard Shortcut Issues"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by adamgolding on 2013-06-07
I am a long-time windows (and autohotkey) user running a fresh lubuntu install inside VMWare Player in an attempt to start using linux.  Currently several keyboard shortcuts do not work as expected, and I cannot continue using lubuntu until I can change at least some of them to desired behaviour, because every second I use the OS this way, I'm breaking years of valuable conditioning.  I don't know which components of the OS (i.e. LXDE) are responsible for which aspects of this behavior.



Currently (from most to least pressing):

- Backspace does not go back in chromium
- Windows+Up does not maximize
- Windows+Left and +Right do not cause the window to be vertically maximized (there is leftover space).
- after pressing 'Win' I cannot type an application name to search the 'start menu'
- Win+Down does not 'restore' the window
- Win+F does not launch a graphical file search utility
- Win+1, Win+2, etc. do not behave as expected


Many of the alternatives to Win+ combinations also do not work as expected:

- Alt+Space+R does not 'restore' the window (instead 'e' is required).
- Alt+Space+X does not 'maximize' the window (you have to first release the Alt and the Space)
- Alt+Space+Enter also does not restore a window

How do I change these behaviours?  More importantly, can they be made into defaults for lubuntu to ease transition from windows for new users?

---

### Post by amjjawad on 2013-06-07
> **adamgolding said:**
> I am a long-time windows (and autohotkey) user running a fresh lubuntu install inside VMWare Player in an attempt to start using linux.  Currently several keyboard shortcuts do not work as expected, and I cannot continue using lubuntu until I can change at least some of them to desired behaviour, because every second I use the OS this way, I'm breaking years of valuable conditioning.  I don't know which components of the OS (i.e. LXDE) are responsible for which aspects of this behavior.



Currently (from most to least pressing):

- Backspace does not go back in chromium
- Windows+Up does not maximize
- Windows+Left and +Right do not cause the window to be vertically maximized (there is leftover space).
- after pressing 'Win' I cannot type an application name to search the 'start menu'
- Win+Down does not 'restore' the window
- Win+F does not launch a graphical file search utility
- Win+1, Win+2, etc. do not behave as expected


Many of the alternatives to Win+ combinations also do not work as expected:

- Alt+Space+R does not 'restore' the window (instead 'e' is required).
- Alt+Space+X does not 'maximize' the window (you have to first release the Alt and the Space)
- Alt+Space+Enter also does not restore a window

How do I change these behaviours?  More importantly, can they be made into defaults for lubuntu to ease transition from windows for new users?

Hello and Welcome to Ubuntu Forums,

I'd like to introduce myself - please check my signature :)

May I humbly request from you to read a link? that link may shade some light and answer some of your questions in a way. It could NOT be the exact same answer you are seeking but it will open a door for you to start answering these Qs.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Having that said, whatever you learned in Windows, may and may not apply to Linux. 
Linux is a different world.
YES, both Windows and Linux are Operating Systems. NO, they are not the same.

Having that said, what you used to do in Windows may and may not apply to Lubuntu. Please, understand that.

If we both agree to the above, I can carry on to help.

Thank you!
[https://wiki.ubuntu.com/amjjawad](https://wiki.ubuntu.com/amjjawad)

---

### Post by vasa1 on 2013-06-07
> **adamgolding said:**
> ...
- Backspace does not go back in chromium
...
From what I read, the only way an ordinary Linux user like you or me can get the backspace key to work to go back a page is by installing an extension for Chromium. That extension is "Backspace As Back/Forward for Linux" and is available from the Chrome Webstore: [https://chrome.google.com/webstore/detail/backspace-as-backforward/aeffggjddcchloadflonilaahpclmbnm](https://chrome.google.com/webstore/detail/backspace-as-backforward/aeffggjddcchloadflonilaahpclmbnm)

Note that after installing the extension, you have to activate the options you need from the Extensions page within Chromium.

---

### Post by adamgolding on 2013-06-07
Hi, that link does not address how to customize this behaviour.  (In Windows, I would customize it using AHK.  Here, I don't know what approach I should use.)

---

### Post by adamgolding on 2013-06-07
Thanks vasa1!  Is there any reason not to include this extension by default in lubuntu?

> **vasa1 said:**
> From what I read, the only way an ordinary Linux user like you or me can get the backspace key to work to go back a page is by installing an extension for Chromium. That extension is "Backspace As Back/Forward for Linux" and is available from the Chrome Webstore: [https://chrome.google.com/webstore/detail/backspace-as-backforward/aeffggjddcchloadflonilaahpclmbnm](https://chrome.google.com/webstore/detail/backspace-as-backforward/aeffggjddcchloadflonilaahpclmbnm)

Note that after installing the extension, you have to activate the options you need from the Extensions page within Chromium.

---

### Post by vasa1 on 2013-06-07
> **adamgolding said:**
> Thanks vasa1!  Is there any reason not to include this extension by default in lubuntu?
In most operating systems, I think that the choice of browser extensions is left to the user. That way, users can install an extension if their work flow requires it.

As for other shortcuts, several are available in [FONT=Courier New]~/.config/openbox/lubuntu-rc.xml[/FONT]. You can read more about this file (and its equivalent, rc.xml or lxde-rc.xml, in other distros) in the links below:
[LXDE: An Overview]("http://pclosmag.com/html/Issues/201009/page02.html")
[LXDE: Meet The Heart & Soul -- lxde-rc.xml]("http://pclosmag.com/html/Issues/201011/page09.html")
[Openbox - Edit rc.xml to Gain Control]("Openbox - Edit rc.xml to Gain Control")
[http://crunchbanglinux.org/forums/topic/13968/aerosnap-in-openbox/](http://crunchbanglinux.org/forums/topic/13968/aerosnap-in-openbox/)
[https://bbs.archlinux.org/viewtopic.php?id=93126](https://bbs.archlinux.org/viewtopic.php?id=93126)
and 
openbox.org/wiki/Help:Contents

---

