---
title: "Setting Up BackupPC"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by meflowers331 on 2012-07-25
Setting up BackupPC (Xubuntu 8.04) and trying to see if it will be a good local backup system for our office.

Having some difficulty though.

I've followed through this resource: [http://taksuyama.com/howto/set-up-backuppc-in-a-mixed-os-environment/backuppc-setup-server/](http://taksuyama.com/howto/set-up-backuppc-in-a-mixed-os-environment/backuppc-setup-server/)

(did not set up SSH or any clients yet, still trying to get the site to come up before any of that)

twice now and still when I go to view the site on the local machine I get a Page Not Found error. I can however see the site that is posted on localhost, so apache is working, I guess.

I've restarted the machine, backuppc, and apache multiple times and am finally out of ideas. Thanks for your help!

---

### Post by 2F4U on 2012-07-25
Any special reason why you are using Xubuntu 8.04, since this version is out of support for a long time now?

---

### Post by meflowers331 on 2012-07-25
Anything higher doesn't seem to run well on the test computer (also a very old machine that's not supported anymore a.k.a. all that there is to spare around the office).

---

### Post by JKyleOKC on 2012-07-25
> **meflowers331 said:**
> twice now and still when I go to view the site on the local machine I get a Page Not Found error. I can however see the site that is posted on localhost, so apache is working, I guess.I used BackupPC for almost a year and found it to be a good backup system. However while trying to make it handle some Windows machines on my LAN I misconfigured things with the result that my LAN got invaded and I had to reformat and reinstall. I left out BackupPC at that time because I didn't want to risk damage to my existing backups, and simply never put it back in place.

As I recall, there's one item that installs into the BackupPC directory but needs to be in the /var/www-data directory to connect BackupPC to the Apache server it installs. However I don't remember the exact details; it was more than two years ago that I did the original installation.

Hope this at least gives you a hint of the right direction in which to look for an answer...

---

### Post by JKyleOKC on 2012-07-26
Just an additional thought: I used "The Official Ubuntu Server Book" (ISBN-10 0-13-703603-5, $39.99 US) for instructions on setting up BackupPC, and there's a quite active mailing list for the program at [email]backuppc-users@lists.sourceforge.net[/email]. Several regulars on that list are extremely helpful to newcomers who are having problems; it's worth a look.

---

