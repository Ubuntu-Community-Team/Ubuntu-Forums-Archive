---
title: "Low Graphics Mode"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by Gigabitten on 2012-08-26
So, I recently completely replaced 11.04 with 12.04.  Fresh install.  The computer works for a while, then, when I reboot after some routine software installation, just to be sure that it sticks, I get this:

Ubuntu is running in low graphics mode.

I click ok, then get to a screen with a bunch of options.  Actually, four options.  Naturally, I tried to boot into low graphics mode.  The computer stands there for ten minutes.  No change.  Cold shutdown.  Restart.  I do that again, but try to reach the command prompt. Ten minutes.  No change.  Cold shutdown.  Restart.  I try holding shift on startup, to get to GRUB2.  Brings up the prompt about the low graphics mode.  Click run in low graphics mode.  Ten minutes.  No change.  Cold shutdown.  Restart.  I try pressing Ctrl-Alt-T, and Ctrl-Alt-F1, on the part where nothing happens.  Ten minutes.  No change.  Cold shutdown.  Restart.  So, now the computer's kind of hovering at the low graphics mode prompt, waiting for me to tell it what to do.  

So, what do I tell it to do?

[Oh, yeah, and I'm running with an nVidia graphics card.]

---

### Post by pqwoerituytrueiwoq on 2012-08-26
[FONT=Courier New]sudo nvidia nvidia-xconfig[/FONT]
if it does notr work reinstall [FONT="Courier New"]nvidia-current[/FONT]

---

### Post by Gigabitten on 2012-08-26
Huh.  Well, like I said, in case I wasn't clear enough, was that I can't access anything.  Including a command line interface.  At least not using any of the methods I stated above.  Right now, I'm looking for a way to access a gui or command line interface.

---

### Post by pqwoerituytrueiwoq on 2012-08-26
ctrl + alt + f1 or recovery mode from grub

---

### Post by Gigabitten on 2012-08-27
I also mentioned that I tried that in my previous post.  Did you read  the whole post?  Because, if I didn't make it understandable, I can rephrase.

---

### Post by mastablasta on 2012-08-27
> **Gigabitten said:**
>  I try holding shift on startup, to get to GRUB2. Brings up the prompt about the low graphics mode. Click run in low graphics mode. 
 
not low graphics but recovery mode.: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
 
-->drop to root shell prompt = CLI

---

### Post by Wim Sturkenboom on 2012-08-27
Edit the grub entry from within grub

When the boot menu shows, select the entry that you want to boot and at the end of the kernel line (the line that usually ends with 'quiet splash'), add the keyword 'text' (line should now end with 'quiet splash text)' and press <ctrl>x to boot. This should get you to a console where you can login and do the maintenance.

Can't tell you what to do to fix the problem though (but the answer might be in post #2).

PS I'm not using 12.04, advise based on 10.04

---

