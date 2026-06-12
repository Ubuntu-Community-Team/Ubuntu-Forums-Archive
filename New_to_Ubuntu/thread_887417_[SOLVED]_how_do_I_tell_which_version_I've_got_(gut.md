---
title: "[SOLVED] how do I tell which version I've got (gutsy fiesty hardy etc)"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by bouncingmolar on 2008-08-12
Hi. 

This might sound pathetic, but how do I tell whether I'm gutsy or not, 

Is there some information window I can load up that i'm missing?

---

### Post by muteXe on 2008-08-12
might tell you in the system monitor information.
think it's system->admin->system monitor.

mute

---

### Post by ShavenBaby on 2008-08-12
Open a terminal and run "lsb_release -a", that should give you the version number and name.

---

### Post by Dill on 2008-08-12
ShavenBaby, thanks for that-- I had always done

```
cat /etc/lsb-release
```

But your way is faster and provides cleaner output. Cheers!

---

### Post by zipperback on 2008-08-12
Click **System -> About Ubuntu **

That should tell you.

There are several ways to see what version you have installed.

If you would like additional information about your system, you can install a small utility called sysinfo.

Install it with the following:

```

sudo apt-get update && sudo apt-get install sysinfo

```

Once that is installed, issue  **sysinfo** into a terminal window and it will launch the application for you.

- zipperback
:popcorn:

---

### Post by freak42 on 2008-08-12
easiest way is
System-> About Ubuntu

---

### Post by bouncingmolar on 2008-08-12
cool thanks so many ways of doing it. Shaven baby's way works well, but I"m not going to remember that again, so I installed sysinfo, thanks zipperback

---

