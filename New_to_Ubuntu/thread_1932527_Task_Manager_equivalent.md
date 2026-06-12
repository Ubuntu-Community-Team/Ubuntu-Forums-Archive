---
title: "Task Manager equivalent"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by tazz4vr on 2012-02-27
What would be the equivalent to Windows Task Manager in Ubuntu 11.10?

---

### Post by howefield on 2012-02-27
Try System Monitor.

---

### Post by tazz4vr on 2012-02-27
Should that be under System Settings?  If so, I am unable to find it....

---

### Post by HeroOfCanton on 2012-02-27
You can use the Unity search to look for it.

---

### Post by tazz4vr on 2012-02-27
Thank you, found it.  Is there anyway to have it show up by pressing the ctrl/alt/del as with the Windows Task Manager?

Reasoning for question... was uploading videos and system froze up, my first response was to hit ctrl/alt/del....

---

### Post by wildmanne39 on 2012-02-27
Hi, this is the method of safely shutting down or reboot.

Hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly (3-5 seconds between presses), one after the other. On some keyboards/systems, you need to use the AltGr key. 
Thanks

---

### Post by tazz4vr on 2012-02-27
If the system freezes up as it did with the video upload, is it better to shut down/reboot or can I end the process using the system monitor and continue on with what I was doing?

---

### Post by wildmanne39 on 2012-02-27
Hi, if you have access to the terminal you can kill the process, but you must have the process number.
Thanks

---

### Post by tazz4vr on 2012-02-27
So I couldn't end a process via the System Monitor?

---

### Post by mcduck on 2012-02-27
> **tazz4vr said:**
> If the system freezes up as it did with the video upload, is it better to shut down/reboot or can I end the process using the system monitor and continue on with what I was doing?

Killing just the frozen app is always the best solution (and yes, if you are able to do it with System Monitor, then by all means do that. :)).

The second option would be killing/restarting the apps/services required to get the system working again (for example restarting your desktop environment, SysRq+K does that if the desktop isn't responding to anything), then comes a safe reboot (SysRq+REISUB if you aren't able to do it through the GUI or by changing to a terminal), and the last thing on the list would be a forced reboot (using power button or similar method, might result in data loss or filesystem errors).

"Minimum force required" is always a good guideline, and applies here as well. ;)

---

### Post by tazz4vr on 2012-02-27
Thank you... I will definitely keep these suggestions in mind (and written down) the next time I have an issue with a process.  I will admit that since switching over to Linux, this is the first time I have had an issue with my computer freezing up.

Hmmmmmm, wish I had done the switch over a long time ago, would have saved myself alot of frustration time felt with Windows!

---

### Post by tazz4vr on 2012-02-27
oh wait... almost forgot!

So is there a way to put the steps to access the System Monitor into a short cut using the keyboard?

---

### Post by yetiman64 on 2012-02-27
As mcduck notes. Also if your SysRq key has "Print Screen" on it as well you will need to add the Alt key to both of mcduck's keyboard combinations eg "Alt + PrintScreen/SysRq + K" and "Alt + PrintScreen/SysRq + REISUB".

On keyboards with Print Screen on the same key as SysRq the Alt key is used as a modifier to access the SysRq function. Some keyboards supply two separate keys for this. With this in mind note which key setup you have to use mcducks instructions.

---

### Post by tazz4vr on 2012-02-27
Ahhhhhhhhh, okay, I got it now.... sorry, long day and the Think-Tank was close to empty!

I did the "Alt + PrintScreen/SysRq + K" and, well it does what was specified by mcduck... 

Thank you for all the help and information.

---

### Post by yetiman64 on 2012-02-27
> **tazz4vr said:**
> oh wait... almost forgot!

So is there a way to put the steps to access the System Monitor into a short cut using the keyboard?
Nearly missed the above, just in case you haven't set this yet :)

  To set Ctrl + Alt + Del to bring up system monitor, go to the Power  button > System Settings > Keyboard > Shorcuts tab, click on  custom shorcuts, click the add button, add to Name: System Monitor and  Command: gnome-system-monitor, click apply. 
In the main custom window it  will show as "Disabled", click on the word "Disabled" when "New  Shorcut" appears press the combination "Ctrl + Alt + Del" to set it.  Good luck.

---

### Post by tazz4vr on 2012-02-27
Tried the above for adding a shortcut, do I need to restart puter for changes to take or should it work immediately?

---

### Post by yetiman64 on 2012-02-27
> **tazz4vr said:**
> Tried the above for adding a shortcut, do I need to restart puter for changes to take or should it work immediately?

After setting that here I could use it straight away. Mainly make sure the command and key combination are done right, the name doesn't really matter.

---

### Post by tazz4vr on 2012-02-27
Woo hoo... it works!  Thank you, thank you!

---

