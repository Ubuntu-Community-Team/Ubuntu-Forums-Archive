---
title: "Why GUI programs look like crap from Windows?"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by genka on 2014-01-21
If I ssh to a remote Linux machine from another Linux PC and run a GUI-driven text-mode application like aptitude it looks great. If I do the same from Windows using Putty or SecureCRT, the interface is drawn with some special characters, the colors are distorted and it is almost unusable. It is difficult to describe, but if you saw it you know what am I talking about. 
Is there a way to fix it?

---

### Post by 1clue on 2014-01-21
ubuntu has an x server, a non-minimal window manager, good fonts and a bunch of other helpful software.

most peoplejust install minimal x servers and window managers on windows .

---

### Post by genka on 2014-01-21
I don't mean X based programs, I'm talking about the menu based applications opened from command line on a terminal. Examples are aptitude and alsamixer.

---

### Post by 1clue on 2014-01-21
Ah, that.

You have to set your terminal type on both ends, preferably set your Windows side because that's most likely to be the worst one.

---

### Post by genka on 2014-01-21
I see this problem for years and years. I tried all possible terminal types in Windows ssh or telnet clients. It always works well from Linux or Mac, never from any flavor of Windows (I'm yet to try Win8).

---

### Post by 1clue on 2014-01-21
I use cygwin from windows, that seems to work OK.

Putty sucks so bad I can't believe it's so popular.  I never tried SecureCRT.

---

### Post by mcduck on 2014-01-22
By "terminal type" 1clue probably didn't mean trying a different program, but actually going in the program's settings and making sure the terminal emulation type & other settings are correct. (say, are you emulating xterm, VT102, VT220 or something else, what character set and typeface you are using, have you set it to support various features of the host operating system you are connecting to etc.).

---

### Post by 1clue on 2014-01-22
That, and making sure the terminal you use in Windows actually has the features of the type you're emulating.

Again, I use Cygwin on Windows and it works fairly well.  In this case, the terminal app is different and you get a lot of Linux commands in Windows, which IMO can't be anything but good.

---

### Post by 1clue on 2014-01-22
Gotta remember this is Windows.  Solidly last place in terms of UI and fonts, lowest possible score on shell scripting.  People make apps to interface with UN*X and are happy when it works at all, because that's light years better than it was before.

The responsibility for command-line apps looking bad rests solidly on the client terminal.  As the OP said, linux-to-linux works fine, mac-to-linux works fine, linux-to-mac works fine.  I go from mac-to-linux and linux-to-mac all the time.  I occasionally have to RDP to a Windows box and then ssh from there to get at something that's not publicly available.  I don't go from mac or linux to windows using a terminal.

---

### Post by genka on 2014-01-22
Thanks for suggesting Cygwin. It does solve my problem, although it is quite an overkill to use as a ssh client.

---

### Post by 1clue on 2014-01-22
Are you sure you JUST need an ssh client on Windows?  I use all sorts of stuff.  find, grep, sed, vim, wget, .....

Even if some of the things in cygwin are already on Windows, they don't have the same command line arguments as Linux.

---

### Post by genka on 2014-01-23
This is a matter of habits. I managed to get by without UNIX enviroment in Windows for years and memorized my own routines of work.

---

### Post by genka on 2014-01-27
Posting in caase someone else will find this useful...

The fix for this problem is to use a combination of Xterm emulation and UTF-8 encoding.

Example of incorrect display:
[IMG]https://dl.dropboxusercontent.com/u/7252489/SecureCRT.png[/IMG]

---

