---
title: "HELP!!! Affter some updates, machine is just BLANK"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by tommyfeds on 2008-06-09
Hi all, 

I just ran some updates to my HH install on an HP nc6230. I had lost network connection during the download however the updates started to install (I must have hit something) anyway, the machine was fine a required a reboot, upon rebooting the machine I now only get a Blank white screen. If if ctrl+Alt+Backspace it will reset and then prompt me for my username and password, after I enter my creds it goes to an all white screen with a mouse. :( 

Is there a "safe mode" in Ubuntu?

Any help would be Awesome! Thanks in advance. 

Tommy

---

### Post by Cypher on 2008-06-09
In the GRUB menu, there is a (Recovery Mode) option that you should be able to login to. That will drop you to a shell, there run
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by tommyfeds on 2008-06-09
Thanks for the quick response, I was able to get in by switching the session (not sure what I did there) it was GNOME *something*...... anyway it booted up fine at thet point. So what Im doing now is running update manager again and it seems to be redownloading all of the packages this time. Im hoping this works, if not I will try the command posted. In the meantime I'm downloading 55 updates. (Fingers crossed)

Tommy

---

### Post by philinux on 2008-06-09
> **tommyfeds said:**
> Thanks for the quick response, I was able to get in by switching the session (not sure what I did there) it was GNOME *something*...... anyway it booted up fine at thet point. So what Im doing now is running update manager again and it seems to be redownloading all of the packages this time. Im hoping this works, if not I will try the command posted. In the meantime I'm downloading 55 updates. (Fingers crossed)

Tommy

If you're running Hardy the above command only sorts out keyboard and mouse now. It's System>prefs>Screen resolution. I know you're thinking hey I have to be logged in. Your right they took away the reconfig xserver in Hardy.

There is xfix from recovery mode though. Never had to use ot yet though.

---

