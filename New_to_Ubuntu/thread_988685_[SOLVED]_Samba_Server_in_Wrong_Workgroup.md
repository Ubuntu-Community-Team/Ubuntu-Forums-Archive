---
title: "[SOLVED] Samba Server in Wrong Workgroup"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2008-11-20
I'm new to Linux and ubuntu; but, after trying for days to correct this problem I given in to this request for help from the pros.

In MY NETWORK PLACES, I have two Microsoft Windows  Networks - MSHOME and WORKGROUP.

IN MSHOME I have a NASLite Server.

I want the new build of my SAMBA SERVER using Ubuntu 8.04.1 LTS Server Edition to be listed under MSHOME, but, it keeps showing up under WORKGROUP.

I have changed the workgroup = MSHOME in the smb.conf file

I have restarted samba using /etc/init.d/samba force-reload.

I have re-booted both the Win XP computer where I'm viewing the network and the SAMBA SERVER. And I have done these actions several times without any resolution.

Anyone have any ideas on resolving this and getting the SAMBA SERVER to show up under MSHOME.

CarolinaGuy

---

### Post by paultag on 2008-11-20
its been a long time since I used Samba, but I think there is a second file. That one might be for client interaction?

I am not too sure, but hunt around, also consider resetting the uptime ( give it the 'ol reboot )

Cheers,
Tag

---

### Post by Kellemora on 2008-11-20
Hi CG

As illogical as this sounds, try it anyway!

Put msHome as your workgroup as planned, BUT, reboot the system three times in a row and see if that fixes it.

My reason for saying that is Ubuntu does NOT look at the smb.conf file when it boots up!  Instead it looks to a /var/lib/samba configuration which is a binary file, not editable by us humanoids.

What APPEARS to be happening here is when you boot up, Ubuntu looks to /var/lib/samba and uses the configuration file in it.

However, if you boot up a second time within a short time period it says, hummmm wonder why the user did that, maybe I should look at the smb.conf file he/she's expecting me to look at.
So it does and boots up like you want, but for that one session only.  The next time you boot up it's back to the /var/lib/samba file for it's directions again.

But, if you boot up a third time in quick succession, it overwrites the /var/lib/samba file with the smb.conf file.

I may not be explaining it right and some Guru will say that's impossible as computers can't think about what the user is doing, hi hi.........

But I have 8 computers here, and the ONLY way to keep the network running correctly is to reboot the computer a change was made to three times, after that it will work just fine, until another update comes down the pike, then we start all over again rebooting each computer 3 times to get things humming along again as they should.

I figure, since it works consistently, on 8 different computers, there must be some truth behind it, no matter how illogical it may sound!

TTUL
Gary

---

