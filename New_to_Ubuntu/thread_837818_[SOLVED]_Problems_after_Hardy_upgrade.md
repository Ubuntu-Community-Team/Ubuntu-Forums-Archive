---
title: "[SOLVED] Problems after Hardy upgrade"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Syndacate on 2008-06-22
I upgraded to 8.04 - was deterred from doing it for such a long time because my friend did it and had problems.  I thought after awhile it would be stable and upgrade fine - I was apparently quite wrong.  I upgraded, and now I have 2 problems.

#1)  The contents of my /etc/network/interfaces file is as follows:

```
auto lo
iface lo inet loopback

auto eth1 
auto eth1 inet dhcp

auto eth0
auto iface eth0 inet dhcp
```

Whenever I boot, my internet doesn't work, I have to edit that file (even if it means just putting a space in it, like below the data or something) and then re-save it, then my internet works fine.  Anybody know the fix to this?

Also, I recently downloaded updates from the update manager (auto-update).  After I updated it needed to restart, so I restarted.  Now, every single time I try to boot it takes about 6-8 minutes of hanging with no action on this screen after I log in and then the following window pops up.  All my themes and stuff that it speaks about in the error msg are indeed deleted.  Anybody know how to fix this problem as well?  I really don't like this extra 6-8 minutes added to my boot time.

The only thing I can think to do in the second problem is re-install the gnome desktop environment and see where I am from there...though maybe there's a better fix - any input?

Here's the window I get on boot:

[IMG]http://i168.photobucket.com/albums/u177/SynForumPhotos/settingsError.png[/IMG]

---

### Post by Syndacate on 2008-06-23
*Bump

Anybody, on either problem?

---

### Post by Syndacate on 2008-06-24
*Bump? 

2 days, nobody knows?

---

### Post by bluepowder7 on 2008-06-24
i've gone from 7.04 to 7.10 to 8.04, and each time i've just done a full clean install and not an upgrade (i TRIED once to upgrade from 7.04 to 7.10 and had tons of problems, which then prompted me to do a fresh 7.10 install)

then again, i store all my files remotely, and make a backup of any special config files or chat logs to make setting up the new install easier.

---

### Post by Troll_the_Great on 2008-06-24
Try to reinstall gdm, and see what happens.I don't know the answer to your problem, I'm still just a noob, but from what I've seen is always better to make a clean install, not to upgrade.My suggestion is, if you can, to back-up your home folder, make a list with all your applications and programs, and do a clean install.The people on this forums will help you, as they once did.
Cheers!

---

### Post by Syndacate on 2008-06-26
> **Troll_the_Great said:**
> Try to reinstall gdm, and see what happens.I don't know the answer to your problem, I'm still just a noob, but from what I've seen is always better to make a clean install, not to upgrade.My suggestion is, if you can, to back-up your home folder, make a list with all your applications and programs, and do a clean install.The people on this forums will help you, as they once did.
Cheers!

Yeah, that's what it looks like I have to do :(.  It seems as though the Ubuntu upgrader didn't work out that well...  Anybody have any fix for my internet problem, though?  Or is it just not finding the file due to the other problem?  Possibly connected?

If you have any info or suggestions feel free to leave 'em so I can try 'em, I don't want to have to format/install hardy manually, but that's what it looks like I'm going to have to do at the present time...

I'll try installing the GDM again, and see what happens from there, any other comments/suggestions are welcome.

---

### Post by Motorhead Kaze on 2008-06-30
Howdy,

I had the same Gnome error message as you do and in my HOME folder, ticked "Show Hidden Files" and deleted everything starting with .g (.gnome2, etc.) that fixed my problem for a few days. Starting, using the computer, shutdown, restart the next day, etc. worked awesome. Then Gnome froze up yesterday for no apparent reason.  No restart of either Gnome or the computer will make Gnome usable. In order to get in to a usable Ubuntu I had to come in through failsafe mode. 

So, I installed a FRESH Hardy, and it was good until I did the Update. After the update, I restarted the computer, came back and Gnome was useless again. This time there were no error messages.  I SEE the top panel and icons, but nothing can be clicked.  I tried that little .g file delete again, but it did nothing...except that now I get the Gnome error message.

My Hardy is jacked up.

So, I tried coming in through a previous kernel, but no dice. Failsafe is it.

---

### Post by caljohnsmith on 2008-06-30
To get clues as to what is causing your long boot time, use the command "dmesg" and look through the log for errors or anything else suspicious. You could post it here and I or someone else could look through it to help find the problem.

About your network problem, have you tried to simply pull up Network Manager (System > Admin > Network) and reconfigure your ethernet interface (and make sure only one interface is selected)? And which interface are you using, eth0 or eth1? Are both interfaces ethernet or is one wireless?

---

### Post by louieb on 2008-06-30
> **Syndacate said:**
> ...
Here's the window I get on boot:
Get the Gnome setting error every now and then. Think its a timing issue. I just log out and log back on - the message  goes away and the  desktop comes up just fine. Go figure.:confused:

---

### Post by Motorhead Kaze on 2008-07-01
My issue didn't go away with restarts so I actually reinstalled Hardy (again) fresh. And this time I did NOT accept the updates which made any mention of Gnome or Libgnome, etc.  Hardy is now running great.  Ah, I even installed the new kernel 19? and Hardy is still fine.  So, I have to assume that one of those updates for Hardy is messing up Gnome.

---

### Post by Syndacate on 2008-07-01
> **caljohnsmith said:**
> To get clues as to what is causing your long boot time, use the command "dmesg" and look through the log for errors or anything else suspicious. You could post it here and I or someone else could look through it to help find the problem.

About your network problem, have you tried to simply pull up Network Manager (System > Admin > Network) and reconfigure your ethernet interface (and make sure only one interface is selected)? And which interface are you using, eth0 or eth1? Are both interfaces ethernet or is one wireless?

The long boot time was because it was looking for the gnome settings and couldn't find them - at least that's in theory, because it was already loaded, it was just waiting for that then throwing an error msg, it wasn't a long boot like the splash screen was taking awhile.

**Veridct:**  Don't bother trying to upgrade via the upgrader.  I backed up what I consider important, (fstab, grub menu.lst, pictures, music, .azureus, .purple (pidgin), and a few other key extras) formatted and installed hardy fresh, and downloaded my stuff off my other computer and now everything works fine.

IMO the Ubuntu upgrade feature simply is not ready.  Formats every 6 months will keep the fragments in line I suppose >.<.  Just do a full format with gparted or something instead of the quick format on the installation CD so you don't have old fragments floating around your "new" OS.

---

