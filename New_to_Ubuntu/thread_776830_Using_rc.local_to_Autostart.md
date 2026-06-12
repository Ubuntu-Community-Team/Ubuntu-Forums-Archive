---
title: "Using rc.local to Autostart"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by wedgiey1 on 2008-05-01
Thought I'd try starting a new thread.  This community seems pretty active but I wasn't getting much response.

I'm trying to run a command '/usr/bin/synergyc <SRVR>' as root on login.  I've read you can use rc.local to do this, but I have NO idea where to start.  Any help?

FYI:  Adding to session doesn't work, crontab doesn't work.

Thanks

---

### Post by Monicker on 2008-05-01
> **wedgiey1 said:**
> Thought I'd try starting a new thread.  This community seems pretty active but I wasn't getting much response.

I'm trying to run a command '/usr/bin/synergyc <SRVR>' as root on login.  I've read you can use rc.local to do this, but I have NO idea where to start.  Any help?

FYI:  Adding to session doesn't work, crontab doesn't work.

Thanks

/etc/rc.local is the file.  You would put your command in that file.

For specifics about that application, this may be worth a look:

[http://synergy2.sourceforge.net/autostart.html]("http://synergy2.sourceforge.net/autostart.html")

---

### Post by wedgiey1 on 2008-05-01
Thank you for the reply!

Curious, does rc.local run on bootup or login?

---

### Post by Monicker on 2008-05-01
> **wedgiey1 said:**
> Thank you for the reply!

Curious, does rc.local run on bootup or login?

At each boot.  If you want to control it by login you can use /etc/bashrc (global) and ~/.bashrc (user specific) for that.

---

### Post by wedgiey1 on 2008-05-01
Ok, tried adding the following to rc.local

"/usr/bin/synergyc 192.168.1.103"

This doesn't seem to do anything.

I tried following the instruction in the programs autostart guide.  It works, but when you run synergyc as the user (not root) it has MAJOR lag.  From what I can tell there's something about the new kernel that breaks it unless you run it as root.  That's where I am.  I don't want to have to open a terminal and type "sudo /usr/bin/synergyc 192.168.1.103" before I can use the software; I don't have room for 2 keyboards on my desk, lol!

Any other ideas?

---

### Post by Monicker on 2008-05-01
"\usr\bin\synergyc 192.168.1.103"  ?


Aren't those the wrong slashes ?

---

### Post by wedgiey1 on 2008-05-01
Yes, they are only wrong on my forum post though; I have them correct in rc.local.  So to correct, the line read:

"/usr/bin/synergyc 192.168.1.103"

Sorry, I'm used to Windows....

---

### Post by Monicker on 2008-05-01
> **wedgiey1 said:**
> Yes, they are only wrong on my forum post though; I have them correct in rc.local.  So to correct, the line read:

"/usr/bin/synergyc 192.168.1.103"

Sorry, I'm used to Windows....

No idea what is wrong then.  I would go through that autostart guide very carefully.

---

### Post by wedgiey1 on 2008-05-01
Ok, thanks for not abandoning me anyway.

I found this:

"I added the following to my /etc/gdm/PreSession/Default to work-around this issue:

#Synergy Server (root)
/usr/bin/synergys --config /etc/synergy.conf &

This starts synergy automatically before login, as root. This also give me the ability to log out of my X session and still traverse to my mac.

:)

"

Here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194029)

I'm going to try replacing '/usr/bin/synergys --config /etc/synergy.conf &'

with

'/usr/bin/synergyc 192.168.1.103' and see what happens.

---

### Post by wedgiey1 on 2008-05-02
Ok, a combination of putting the command 2 places fixed my problem.

I edited '/etc/gdm/Init/Default' to include:

/usr/bin/synergyc <HOST NAME>

Then edited the file I mentioned above to include the command and this made it run as root!

---

### Post by Oldsoldier2003 on 2008-05-02
i'm glad you found a working solution it just goes to show you that there's more than one way to skin a cat :) I prefer to use the /etc/init.d and create a script starting the service as root then  ```
update-rc.d <scriptname> defaults
```

That way the service actually starts on boot not GDM login.

[http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/](http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/) has a little more in depth info and background if you are interested.

---

### Post by wedgiey1 on 2008-05-02
What you've written looks familiar.  I may have read about it; is it the deal where you have to know the run level you're on?

Suppose I could just check the link you attached, lol!

---

### Post by Oldsoldier2003 on 2008-05-02
> **wedgiey1 said:**
> What you've written looks familiar.  I may have read about it; is it the deal where you have to know the run level you're on?

Suppose I could just check the link you attached, lol!

Debian/Ubuntu workstations and servers almost NEVER leave runlevel 2 except for boot and shutdown. if they do it's because somewhere you've configured a runlevel change. So using defaults works well. Its really not that complex, the link I gave just gives a lot of background info so that if you run into an issue you can understand the process to better troubleshoot it.

---

