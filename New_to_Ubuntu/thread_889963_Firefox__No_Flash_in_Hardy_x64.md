---
title: "Firefox:  No Flash in Hardy x64"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Sam324 on 2008-08-14
Hi.  When I first was asked to install a plugin for Flash, I chose the proprietary Adobe one.  Now, any Flash item just disappears or (in YouTube's case) is a gray box.  I tried unchecking "Shockwave Flash" in the Plugins section of Firefox.  It now will show a message saying "You don't have Flash installed." on YouTube.  I re-enabled it, but now I have no Flash content and no plugin install prompts.  I see no way in the Firefox plugins menu to remove the plugin.  How do I fix this?:confused:

---

### Post by coolbrook on 2008-08-14
Install 32-bit Hardy.

---

### Post by Sam324 on 2008-08-14
> **coolbrook said:**
> Install 32-bit Hardy.
:\ Why?

---

### Post by Titan8990 on 2008-08-14
Most likely because 64bit OSes, in general, are plagued with problems. Mostly because the majority of programmers and companies have not started coding 64bit applications.

---

### Post by Sam324 on 2008-08-14
Interesting, is there any workaround for Firefox flash?  I guess if I need to I could emulate a Windows browser or something.

---

### Post by sayakb on 2008-08-14
Open up a terminal (Applications->Accessories->Terminal) and type in:
```
sudo apt-get install flashplugin-nonfree
```
And reboot once.

---

### Post by Thelasko on 2008-08-14
Next time post your questions in the [64-bit section]("http://ubuntuforums.org/forumdisplay.php?f=343").  You wont get asinine answers like the first two you received here.

The answer LinuxIsInnovation gave you is the correct one.

---

### Post by coolbrook on 2008-08-14
vvv

---

### Post by coolbrook on 2008-08-14
lol @ asinine.  Titan8990 is right on the money.

---

### Post by Sam324 on 2008-08-14
Thanks, I just rebooted without a command and it's working fine now.

---

### Post by Sam324 on 2008-08-15
Well, it showed the same symptoms today so I'ma try my luck with lib-swfplayer.

---

### Post by Paqman on 2008-08-15
> **Titan8990 said:**
> Most likely because 64bit OSes, in general, are plagued with problems. Mostly because the majority of programmers and companies have not started coding 64bit applications.

That's really only an issue for Windows. 64-bit Linux is not a problem at all. The 64-bit and 32-bit repos are almost identical.

Flash used to be a problem for 64-bit Ubuntu, but it was sorted several versions back.

---

### Post by Sam324 on 2008-08-15
> **Paqman said:**
> That's really only an issue for Windows.
Not even on Windows.

---

### Post by Thelasko on 2008-08-15
> **Sam324 said:**
> Not even on Windows.
Yeah, I use XP64 at work.  Some programs aren't 64-bit, but I don't notice a difference.

---

