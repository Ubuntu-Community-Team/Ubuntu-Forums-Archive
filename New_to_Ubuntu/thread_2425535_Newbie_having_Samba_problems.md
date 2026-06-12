---
title: "Newbie having Samba problems"
date: 2019-08-26
forum: New to Ubuntu
---

### Post by brisingre on 2019-08-26
I'm trying to use Ubuntu for a home fileserver. I have no real Linux experience to speak of.

It's nothing at all fancy -- just a software raid1 on a pair of giant drives, with some shared folders I can access from the other machines (mostly Windows) on my LAN. 

I installed the server flavor of Ubuntu, but installed Ubuntu Desktop with apt-get since I'm a scrub and like a GUI when I can. 

I used mdadm to set up the raid1, then used the GUI "Disks" utility to format it as EXT4 and change the mount settings to mount on startup to somewhere relatively easy to type (/mnt/memory_alpha:mirror_a).

I installed samba, and set up some shares on this disk. (I set up one for the root of the disk as an experiment, and one for my video library, so far.)

I added them as network folders in windows, it connected, I started copying stuff over. Everything seemed to be working.


A few hours into the big copy, Samba died. Restarting smbd didn't fix it, but eventually rebooting the server did. Since then, it has happened several times since. I can't even keep it up for 24 hours without it breaking, usually. 


After Samba dies:
-I can still ping the server and SSH into it so it isn't the network connection dropping.
-The raid
-The smbd services still seem to be running.
-Connections from windows to the share time out very slowly.
-Restarting smbd takes an unusually long time.
-Restarting smbd doesn't fix the issue, but it does kill any connections Windows is waiting for a timeout on instantly -- which suggests something we already sort of knew, that Samba is running and accepting connections, but not handling them properly. 
-Reboot hangs trying to stop samba, hangs even longer and eventually fails to unmount the software raid, eventually spits out a bunch of stuff like this: "systemd-shutdown[1]: Sending SIGKILL to PID 6109 (smbd)" and eventually "systemd-shutdown[1]: rebooting" but it never finishes shutting down or reboots. I have to use the power button.

Restarting smbd and rebooting the server both work correctly and at reasonable speeds before I lose the share, so I think it's connected to this failure. Sadly, I have no real idea what is actually failing. Until I try to reboot, there's no obvious evidence on the Ubuntu side that anything is wrong at all. And all Windows knows is that the share is no longer available.

Does anyone have any idea what might be going on? 

I freely admit I'm in a little bit over my head here -- I don't even know where Samba keeps its log files, much less how to read one, and I'm not 100% sure it's a Samba problem and not an mdadm problem, a networking problem, or even a Windows problem. 

Thanks for your help!

-Lou

---

### Post by jeremy31 on 2019-08-27
Duplicate of [https://ubuntuforums.org/showthread.php?t=2425557](https://ubuntuforums.org/showthread.php?t=2425557)
Closed

---

