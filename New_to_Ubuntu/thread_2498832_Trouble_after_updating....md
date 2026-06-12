---
title: "Trouble after updating..."
date: 2024-06-29
forum: New to Ubuntu
---

### Post by Innernet on 2024-06-29
Hi.
About 8 of 10 updates done cause problems to my compfuser.  Always delay as much as possible the very often pushes for updating as when set to automatic it is worse; hangs up processes without telling what is going on to the point of need to power-off.
Today, it was a small ~500KB download; seemed quick and simple, went for it.  Corrupted a bunch of something in the hard drive, messed up the Whatsapp for Ubuntu, halted facebook marketplace, refusing to work. 
Unable to access software 'stores' , now crappyly renamed 'snaps' for who knows what reason.  First were programs, later software, then applications, now 'snaps'  ](*,)

The only browser I use 'Brave' fully disappeared.  Totally unaccessible.  Never understood why does never show by clicking the 9 dots at bottom right.   Another browser 'Web' did not respond.   
Did not reboot-up.  Had to do the terminal fsck -whatever that is usually fixes the corruptions- (But never tell it is done or how to reboot from there.  Took a photograph I will try to attach later.  
Attempted to update Whatsapp;  found no way to update.  Delete yes, install yes, but no update. And do not know if it is the same software I have or from a different source that will make things worse.  If I delete and install again, do I risk losing whatever I had on it before ?  **No, I do not know.**  The browser resurrected itself after a lenghty fsck surgery.
Had Whatsapp for one year working well; now it kills all messages I try to send.  What is the magic to understand what is going on ?

The once wonderful Ubuntu getting too elaborated ? :cry:

---

### Post by 0f4d0335 on 2024-06-30
No, I think this is a problem with your update (perhaps something to do with a PPA or another repository) or hardware. 

If it's a problem with your update, it's likely better to reformat your install and use a USB to re-install Ubuntu desktop.

If the problem is with your hardware, perhaps a new SSD would fix it.

---

### Post by Impavidus on 2024-06-30
I've had an upgrade do something bad to my system twice, in 18 years of using Ubuntu. Your 8 of 10 is well above average.

If fsck fixes things, the upgrades trigger some filesystem damage. Just changing, creating and deleting some files (I assume you don't force a power-off regularly) won't damage your filesystem. So I suspect there's a hardware problem with your harddrive/SSD.

Do you monitor smart data of your drive? It may show some problem. The solution is, unfortunately, installing a new drive.

---

### Post by Innernet on 2024-06-30
Thanks, Impavidus.

Trying to fix with fsck  also **my** external backup-data-only hard drive with **no** operative system in it, pushed to use sudo and then the fsck command. It is not mounted;  If now am 'root',  now asks me for r/w access.  Is that obtained with chmod ? 
 
Tried e2fsck  as  e2fsck -p /dev/sdb1   too, got more confused.

Installed   sudo snap install root-framework  ,got nowhere.

Am the only operator of my computer, nobody else touches it, am the only rightful owner, there is no groups nor other users and want all accesses granted with zero restrictions so I can attempt to fix any and all drives and files in them or whatever got corrupted by a wrong power-off.   How do I get **all** these permissions out of my way, permanently?

---

### Post by TheFu on 2024-06-30
> **Innernet said:**
>  
Am the only operator of my computer, nobody else touches it, am the only rightful owner, there is no groups nor other users and want all accesses granted with zero restrictions so I can attempt to fix any and all drives and files in them or whatever got corrupted by a wrong power-off.   How do I get **all** these permissions out of my way, permanently?

Allowing a normal user account to have root all the time is a security failure. That's why Ubuntu doesn't come that way. If you set this up, you are likely to destroy your computer and data, so I'll let you search for the answer.  

I get that you are frustrated. We've all been there.  For me, frustration usually causes mistakes, so I step away.

From the reading, I think you need a new HDD/SSD.  You shouldn't need to manually run an FSCK more than once every 4+ yrs.  Anything more than that and you are doing something wrong or your hardware is failing.  If you don't pull the power plug randomly (or too soon after requesting the system to "shut down", then it is a hardware issue 99%.  If you are using the BRS [https://en.wikipedia.org/wiki/Big_red_switch](https://en.wikipedia.org/wiki/Big_red_switch) too often, then this is your fault - stop it.

By default in Ubuntu, every ext4 file system will automatically run an fsck every 30 reboots. That is normally sufficient. Non-EXT4 file systems usually have different methods  - "scrub" is a term used by ZFS, but you probably don't have ZFS.

In the meantime, you can run Ubuntu from a flash drive using the ISO as you research how todo things.  A number of my friends choose to run their Linux OS directly from flash drives directly and never use the installed SSD for anything.

---

### Post by Innernet on 2024-06-30
> **TheFu said:**
>  ...you can run Ubuntu from a flash drive using the ISO as you research how todo things.  A number of my friends choose to run their Linux OS directly from flash drives directly and never use the installed SSD for anything.

Thanks, TheFu.  I think am not in need of a USB flash drive ISO.  My laptop runs nearly fine after the fsck 'surgery' successful repair caused by some weird event when updated.  

Now am trying to apply the same repair treatment to the **external USB-data-only-backup hard drive** that failed weeks ago on a power outage. Get the 'no r/w access' trying to run fsck.  confused:

---

### Post by TheFu on 2024-06-30
If the power it cut to any device that is expected to be available and the OS is running, of course the file systems can become corrupt.  Don't do that.  Perhaps you needs a cheap UPS that will prevent short power issues from corrupting your data?

I don't understand why you'd be confused.  You aren't using the storage devices in the way they are intended to be used.  They expect to be powered until the OS shuts them down.  Anything else is a user error.

Bad power will make computer components fail/break sooner.

---

