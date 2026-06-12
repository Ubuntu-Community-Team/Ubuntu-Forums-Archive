---
title: "Could not acquire name on session bus (19.04)"
date: 2019-08-14
forum: New to Ubuntu
---

### Post by sbumgarner on 2019-08-14
Ubuntu Mate 19.04, getting this error after entering password. Can access home screen remotely via Google Remote Desktop, but directly not on desktop monitor. 

Would like to use Linux, but taking a lot of time and effort away from my work just to get it to work properly. Sadly, might have to go back to Windows.

Any suggestions?

Stan

Followup: Installed Nvidia drivers, seems to be working . . . for now.

---

### Post by DuckHook on 2019-08-15
> **sbumgarner said:**
> …Would like to use Linux, but taking a lot of time and effort away from my work just to get it to work properly. Sadly, might have to go back to Windows.
Please have a look at the link in my sig "Linux Is Not Windows". I'm afraid that if you don't have the time to devote to learning the new moves, then your pessimism may likely become a self-fulfilling prophecy.
> Any suggestions?
[LIST]
[*]Why do you wish to move from Windows? This is a genuine question. If it is only for a cheaper OS, then you must measure the value of your time against the up front savings. It may be that you are best served using Windows. Nothing wrong with that. Windows has evolved into a relatively safe and decent OS if the proper measures and precautions are taken.
[*]If you are committed to learning Linux, then a possible strategy is to run it for a time inside a VM hosted on your Windows box, until you become familiar enough with Linux that you can wrestle with any problems on a bare metal install.
[*]You can also try dual booting, although Windows makes this a convoluted and difficult process. I can't really help with that as I no longer run Windows except within VMs.
[/LIST]

---

### Post by sbumgarner on 2019-08-16
Thanks for the info. I'll consider it.

My problem is back. After entering my password, all I see is "Could not acquire name on session bus."

Since I can access everything using Chrome remote desktop, I assume it's some kind of display issue.

Any suggestions on how to fix it? (Have tried searching, no results.)

Stan

---

### Post by Bashing-om on 2019-08-16
sbumgarner; Hello -

How far do you get in the normal boot process ? Do you get to the login screen ? 
 Eschewing the GUI start up - try at this login screen key combo ctl+alt+F2 to gain a console interface.

Login here with user name and password.
What shows for a graphic's driver status:
```

sudo lshw -C display

```

As a place to start the looking,

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by sbumgarner on 2019-08-16
Thank you. I'll give it a try. 

To answer your question, I press power button, enter encryption password, then login password. That's when I get the error message. 

I can access terminal with Ctl+Alt+T. I'll check driver status.

I do like learning new things. for now, I'll keep trying.

Stan

---

### Post by DuckHook on 2019-08-17
[LIST=1]
[*]Is this a pristine Ubuntu-Mate install or is it an additional DE that has been layered on top of an existing one?
[*]If no other DE, was this a network version upgrade from 18.10, or is it a virgin install?
[*]What additional apps did you install?
[*]Has it ever worked properly or is this the behaviour from the get-go?
[*]If it worked at some time in the past, can you recall what you did just prior to it going bad?
[*]Do your logs tell you anything? Especially check syslog dmesg and auth.log
[*]You mention "encryption password". Is this an encrypted install? If so, is it just /home or everything?
[*]Most encrypted installations default to using the login passphrase to also decrypt the volume, and do not require a two-step process. Why does yours?
[/LIST]
As you can see, the lack of background, context and full details is making diagnosis more difficult because every revelation is a surprise. This is clearly not a default install. Please provide all details about how/where it departs from defaults.

---

### Post by sbumgarner on 2019-08-19
First of all, thank you so much for your input. I really appreciate it.
1. I originally did a clean install of 18.04. 
2. 19.04 is a network upgrade from 18.04 (maybe upgraded to 18.10 first, not sure.)
3. I installed quite a few: Google Chrome, Opera Browser, Chromium, Clam TK, Brave Web Browser, Dropbox, Foxit Reader, Handbrake, Plex Media Player, Skype, Thunderbird Mail, Vivaldi Browser, NordVPN
4. It has worked well, with a few hiccups.
5. As I recall, I restarted the computer and, after the encryption pw and login pw, got the error message. I don't remember what I did before the restart. I must have had some reason for the restart, but I don't remember what it was.
6. There is a lot of information in the logs. I'll have to take some time with them.
7. Full disk encryption
8. I just followed instructions as I was installing. Was asked for encryption password, then later for a login password.

Thanks so much,
Stan

---

### Post by sbumgarner on 2019-08-19
Please ignore my last post. I'm doing a clean install of 19.04 rather than try to deal with these issues. 

I'll see if I can make this new install work better. If not . . . .

Thanks for the help.

Stan

---

### Post by DuckHook on 2019-08-19
> **sbumgarner said:**
> Please ignore my last post. I'm doing a clean install of 19.04 rather than try to deal with these issues. 

I'll see if I can make this new install work better. If not . . . .

Thanks for the help.

Stan
Sorry…

Did not see this till just now. If doing a new install, you may wish to consider keeping it as simple as possible and foregoing whole disk encryption. There are other ways to get encryption benefits without the complexity/fragility of whole disk. They aren't generally as secure, but still pretty decent. It all depends on your security needs, but whole disk encryption does come with less fault tolerance and more requirement for knowledge/maintenance.

---

### Post by sbumgarner on 2019-08-19
My company requires full disk encryption.

Problems with this install as well. I put a little more time on it and see what I can do.

Thanks for your replies and encouragement.

Stan

---

### Post by sbumgarner on 2019-08-21
Giving up on Linux. Too many problems taking too much time to confront. Maybe it's the necessary full-disk encryption causing the problems, but I need to earn a living, not spend all day trying to solve computer problems. Sadly going back to Windows 10.
Stan

---

### Post by sbumgarner on 2019-08-28
Final nail in the Linux coffin for me. My company started using an app of which there is no Linux version. It was an interesting experiment.

---

