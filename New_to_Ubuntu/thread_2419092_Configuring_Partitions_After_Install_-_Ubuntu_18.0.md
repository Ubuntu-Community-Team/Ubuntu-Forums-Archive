---
title: "Configuring Partitions After Install - Ubuntu 18.04 LTS"
date: 2019-05-16
forum: New to Ubuntu
---

### Post by 4576787435tw4w632 on 2019-05-16
I need some help configuring partitions after install.

I'm new to Ubuntu. I'm using it for a home desktop and I am going through a security hardening process. I am using select parts of this guide (see below) to tighten things up.

[https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts](https://www.ncsc.gov.uk/collection/end-user-device-security/platform-specific-guidance/ubuntu-18-04-lts)

The part I need help with is the section entitled "Software restriction". It says:


[I]A separate partition should be created for 

/home defaults,noexec,nosuid,nodev 0 0

none /tmp tmpfs noexec,nosuid,nodev 0 0

none /run/shm tmpfs rw,noexec,nosuid,nodev 0 0[/I]



How do I actually set those partitions up in Ubuntu? I need simple instructions.

I'm using Ubuntu 18.04 LTS.

---

### Post by TheFu on 2019-05-16
What do you have today as the mount options for those?

tmpfs isn't a real partition. I don't know how to change the settings.
```
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
``` is what mine shows.
/tmp is part of the / file system, so I don't have that split off.

I do have a separate /home, modifying the options would be done in the /etc/fstab file for that specific mount. If you don't have  separate HOMES for userids, then you'll need to set those up, as needed first.  There is a guide - [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)  In an enterprise, things usually aren't handled that way, but for a home setup, it is fine.

If you are really new to Linux, please be extremely careful following guides like these. I'm concerned because you said that you need *simple instructions* and some of the recovery techniques if anything goes badly would be beyond that level.

---

### Post by Geoffrey_Arndt on 2019-05-16
Need simple instructions? . . . well, just disregard that link you posted entirely . . . unless you are running an IT Department & WAN out of your house with dozens to thousands of users.   That article is gross over-kill for the home user.

The install process sets up the "required" partitions before install - - which is usually all directories in the root directory (/) . . . OR root and a swap partition (swap).   That's all that is required.   The biggest security threat to an average home Ubuntu install is a admin/user that is overstepping and trying to run Linux without taking 6 months to a year to learn just a few basics (mainly web-related don't do's and using untrusted software (from unvetted sources).

---

### Post by Rubi1200 on 2019-05-17
I don't understand something, perhaps you can clarify: why do you need to harden a home setup like this?

Out of the box, Ubuntu (most Linux distros for home use) are secure.

There are some basic precautions you can take such as enabling the firewall, ufw, not adding sources from untrusted PPAs, and in general practicing the same responsible computing you would on any system; not downloading untrusted content, not opening email attachments from unknown sources etc. etc.

As TheFu pointed out, recovery if something goes wrong is a complex process way beyond the understanding of most users.

You also say you are working on select parts of that link; which parts?

And, just to emphasize the point, if you are the only user on the system why would you need software restrictions in the first place?

There are many good resources here:
[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)

And on his profile page TheFu has some excellent links for administering a system, also relevant to home users.

Hope this helps.

---

### Post by oldrocker99 on 2019-05-17
```
And, just to emphasize the point, if you are the only user on the system why would you need software restrictions in the first place?
```

Indeed, and if nobody else is using your computer, make a four-character password, which can still be hard to guess. Convenience.

---

### Post by TheFu on 2019-05-17
> **oldrocker99 said:**
> Indeed, and if nobody else is using your computer, make a four-character password, which can still be hard to guess. Convenience.

There is no substitute for length and complexity when it comes to passwords for a computer on any network.  
Humans are terrible at picking "random" anything. That fact is exploited when it comes to cracking passwords. 
[https://arstechnica.com/information-technology/2012/12/25-gpu-cluster-cracks-every-standard-windows-password-in-6-hours/](https://arstechnica.com/information-technology/2012/12/25-gpu-cluster-cracks-every-standard-windows-password-in-6-hours/)
> Gosney used the machine to crack 90 percent of the 6.5 million password hashes belonging to users of LinkedIn.
 
Please don't use a Zuckerberg password.

---

