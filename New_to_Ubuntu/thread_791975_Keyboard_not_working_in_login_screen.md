---
title: "Keyboard not working in login screen"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by purnama on 2008-05-12
Hello,

I'm really depserate with this problem, i'm trying to search in the web for similar problem. but what i found can not solve the problem.

my problem is:

i have an english version of ubuntu Hardy Heron on my pc installed together with windows xp. i'm using german keyboard. i set the keyboard in installation and its working fine.

but there is always time where my keyboard not functioning at the login screen. i can use my keyboard on bios startup, grub loading, but as i come on the login screen i can't use my keyboard.

i have test it with 4 different germen keyboards, usb and ps/2 keyboard. sometimes it does functioning but sometimes it doesn't. i'm really desperate because i cant log in to my ubuntu.

i have read a thread about disabling the usb legacy support in bios, but it doesn't solve the problem. as i say sometimes the problem not appear, i can log in and use ubuntu. but when the problem appear, i can only restart my ubuntu till the problem not occur. but sometimes the problem do always occur, and i canÄt use ubuntu for that time.

please help thank you

---

### Post by bluefrog on 2008-05-12
you could use autologin to bypass the problem if you don't find an answer to it.

system/administration/login window [security tab]

---

### Post by ethoxyethaan on 2008-05-12
do you get absolutely no text from your keyboard?
or does it have a wrong language input?

---

### Post by purnama on 2008-05-12
> **ethoxyethaan said:**
> do you get absolutely no text from your keyboard?
or does it have a wrong language input?

i get absolutely no text. to test it i press the numlock and caps lock button on the keyboard to make the numlock and capslock lamp blinking, to see that the keyboard functioning, as i reach the login screen all the lamp turns off and it didnt turn on even if i press the numlock and capslock button.

---

### Post by purnama on 2008-05-13
> **bluefrog said:**
> you could use autologin to bypass the problem if you don't find an answer to it.

system/administration/login window [security tab]

hi again, today i have the chance to log in to my ubuntu, and i do what you said right away. after i done, i do a restart.

now i can not completely run my ubuntu. when  it finish showing the loading screen, it only showing the ubuntu background (yellow brows or somethin) then come an error message at the top left. saying

There was an error starting the GNOME Settings Daemon

Some things, such as themes, sound, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

i do a hard reset but the problem still come.

please help i'm really desperate. how can i move to ubuntu, when i just get this kind of message :(

Thank You.

---

### Post by bluefrog on 2008-05-20
wondering if your OS is correctly installed.
can go in recovery mode to finalize that but it might be too much for a first comer.

have you done a memtest (last option of the grub boot)?

otherwise try to reinstall.

---

### Post by oleoleole on 2009-08-25
I have the same problem here with a laptop, sometimes it work, sometimes not, and only a reboot (restarting X doesn't work) does solve the problem. The laptop uses kubuntu. I wonder if it could be some HAL problems? I heard the keyboard and mopuse can be a little buggy, but I dunno.

edit:
after browsing a little I found the problem if using KDM (KDE):
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/256261](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/256261)
> 
ran

update-rc.d -f kdm remove
update-rc.d kdm defaults 99 01

and the bug is fixed for me. Reassigning to kdebase-workspace


---

### Post by itmanvn on 2011-05-28
me too, using 11.04 gnome 3 after an update yesterday, my laptop's keyboard cant work both login screen and desktop. touch pad not work too, if I plug usb mouse it work ok. please help

---

### Post by itmanvn on 2011-06-23
bump, still not fixed!

---

### Post by mifi on 2011-09-16
Same here with 11.04. It was working before today, so perhaps some update reintroduced this problem?

m

---

### Post by TonyPursell on 2011-10-09
Make sure the option "Slow Keys" is not enabled in the Accessibility options - usually an icon with a man in a ring on the right side of the bottom panel at the login screen.

---

### Post by Maragues on 2012-01-13
The "Slow Keys" thing worked for me, thank you so much!

Now, I wonder how I turned it on...

---

### Post by synplague on 2012-03-01
I'm using Ubuntu 11.04 and can't believe that I lost more than 2 days trying to fix this.... Just disabling the "slow keys" worked for me.

Thanks you all!!

---

