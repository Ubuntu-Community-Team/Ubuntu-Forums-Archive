---
title: "dist upgrade frustrations"
date: 2005-03-06
forum: Repositories &amp; Backports
---

### Post by jake55555 on 2005-03-06
Ok, so i just installed worty yesterday and i fell in love with ubuntu right away.  then i got stupid.... having read that ubuntu supports distrubtion upgrades i tried to upgrade it to horay.... and like every other linux distribution i have ever used it crapped out and gave me errors.  

so is there some guideline as to how you're supposed to update ubuntu correctly?  

I would LOVE briandead updates.  To just run apt-get and not have to think about things would be my dream.

also... if you have any ideas on howto fix my errors below i'd appreciate it.


now i get a kernel panic when trying to load 2.6.10-5-686.
noy syncing VFS: Unable to mount root fs  on unknown-block(0,0)

luckily i can boot 2.6.8.1-3-386.... but then X fails to start.  I saw that this is a common issue... so I'm just starting to read up on it.  But quite frustrating none the less.

after logging into the CLI apt-get tells me to do a apt-get -f install to correct some errors.  But after running it i get  another error satubg ut can't install the kernel.

/usr/bin/dpkg returned an error code (1)

---

### Post by poofyhairguy on 2005-03-07
[QUOTE=jake55555]
so is there some guideline as to how you're supposed to update ubuntu correctly?[/QUOTE]

Yep.....wait for hoary to be released!

If stuff broke, file a bug report. The devs would like it.

As far as fixing it, keep upgrading everyday till you get lucky and it works. It won't be long if you take the first bit of advice.

---

### Post by LongTooth on 2005-03-07
Can't help out on the fixing part but I recently upgraded from Warty to Hoary and all went well. Of course I too went through the dist-upgrade bork all experience. But at that time Hoary had just come out. So I guess things weren't ready. I would suggest you install Warty, change the repostiories to read Hoary and apt-get update, upgrade, and finally dist-upgrade. It worked for me and I couldn't be happier. It was only after I had Hoary installed that I added other repositories to my list. But only to get a few things. The rest of the time I have them disabled. Give Hoary another shot. I don't think you'll be disappointed.

May I also suggest you use Synaptic. It a great GUI for Apt-get. Of course I still use the CLI for several things but you can't beat Synaptic for making changes and adding and upgrading programs to your system.

---

