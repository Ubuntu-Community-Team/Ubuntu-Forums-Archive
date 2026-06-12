---
title: "VLC does not start"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by hoangtu69 on 2011-09-18
I installed VLC via Ubuntu Software Center.  After that I selected it under Applications -> Sound & Video but it does not start. 
 
Do you have any idea?
 
I'm using 11.04

---

### Post by TeoBigusGeekus on 2011-09-18
Give 
```
vlc
``` 
in a terminal and post us any error messages.

---

### Post by hoangtu69 on 2011-09-18
it said VLC can't be run as root.

---

### Post by TeoBigusGeekus on 2011-09-18
What?
Can you give us the whole session, ie. the command you gave and the exact message?
Oh... include also the command prompts of your shell...

---

### Post by hoangtu69 on 2011-09-18
I typed in vlc at the comand prompt and here's what I got
 
VLC is not supposed to be run as root. Sorry.
If you need to use a real-time priorities and/or privildged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and cannot be run by non-trusted usrs first).
 
 
I logged in as root

---

### Post by TeoBigusGeekus on 2011-09-18
I thought the root account was disabled by default in ubuntu...

Anyway, vlc cannot be run as root as its developers felt that noone would have any reason to do this.
See [this]("http://forum.videolan.org/viewtopic.php?f=13&t=48356") for more info.

---

### Post by dniMretsaM on 2011-09-18
> **hoangtu69 said:**
> I typed in vlc at the comand prompt and here's what I got
 
VLC is not supposed to be run as root. Sorry.
If you need to use a real-time priorities and/or privildged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and cannot be run by non-trusted usrs first).
 
 
I logged in as root

Why are you logged in as root in the first place? Never a good idea (that's why Ubuntu has it disabled by default). If you want a root shell, run this in Terminal:
```
sudo -i
```@TeoBigusGeekus: Something I picked up about you from stuff you've said and other subtleties: You want Autocad Civil 3d to work on Linux.

---

### Post by marginal39 on 2012-01-11
> **dniMretsaM said:**
> **Why are you logged in as root in the first place? Never a good idea (that's why Ubuntu has it disabled by default).** If you want a root shell, run this in Terminal:
```
sudo -i
```@TeoBigusGeekus: Something I picked up about you from stuff you've said and other subtleties: You want Autocad Civil 3d to work on Linux.
Why so?

---

### Post by cortman on 2012-01-11
> **marginal39 said:**
> Why so?

With root you have complete editing, deleting, executing, everything control over every file on your system. Any slight mistake (or any malware that you might inadvertently activate) can total your system. For root there are no barriers at all.
Use a regular account for your normal usage, and if you need to run a GUI program as root, open a terminal and type 

```
gksu app_name
```

for the command line

```
sudo command_here
```

---

### Post by marginal39 on 2012-01-11
> **cortman said:**
> **With root you have complete editing, deleting, executing, everything control over every file on your system. Any slight mistake (or any malware that you might inadvertently activate) can total your system. For root there are no barriers at all.**
Use a regular account for your normal usage, and if you need to run a GUI program as root, open a terminal and type 

```
gksu app_name
```for the command line

```
sudo command_here
```
I know that, I even formatted my whole backup partition as root (it was no big deal though, I has almost all I lost on other backups), but it is really unpleasant to have to enter the password every time I want to install or uninstall even the most insignificant software.

---

### Post by cortman on 2012-01-11
> **marginal39 said:**
> I know that, I even formatted my whole backup partition as root (it was no big deal though, I has almost all I lost on other backups), but it is really unpleasant to have to enter the password every time I want to install or uninstall even the most insignificant software.

Logging in as root is your prerogative; but I (and every other person on this forum) would strongly recommend putting up with the inconvenience of using sudo in exchange for a secure system. When you're habitually logged in as root all the security advantages that Linux naturally possesses are pretty much nullified.

---

### Post by marginal39 on 2012-01-11
> **cortman said:**
> **When you're habitually logged in as root all the security advantages that Linux naturally possesses are pretty much nullified.**
Like what, besides the damage I can do myself?

---

### Post by cortman on 2012-01-11
> **marginal39 said:**
> Like what, besides the damage I can do myself?

You surf the web? Download stuff? Use USB flash drives? Use CDs? Any rogue malware, spyware, phishing, etc., on the web has 100% access to everything on your system. Any virus or malicious script can execute automatically with nothing to stop it.
Even if you're not doing or using any of those things (which seems unlikely) anything sitting dormant on your system, that you might have acquired a long time ago will be allowed to run and wreak havoc.

---

### Post by marginal39 on 2012-01-11
> **cortman said:**
> You surf the web? Download stuff? Use USB flash drives? Use CDs? Any rogue malware, spyware, phishing, etc., on the web has 100% access to everything on your system. Any virus or malicious script can execute automatically with nothing to stop it.
Even if you're not doing or using any of those things (which seems unlikely) anything sitting dormant on your system, that you might have acquired a long time ago will be allowed to run and wreak havoc.
OK, than you for the information.
I never knew there are viruses and malware made for Linux (if so, why aren't there antiviruses for Linux?).
Is there a topic on that matter?

Regards.

---

