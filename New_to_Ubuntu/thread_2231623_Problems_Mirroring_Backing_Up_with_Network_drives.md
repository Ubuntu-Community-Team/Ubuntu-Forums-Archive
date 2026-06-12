---
title: "Problems Mirroring/ Backing Up with Network drives"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by kellyvotrenom on 2014-06-26
I am having problems mirroring to and from Network drives in Ubuntu.  I have tried multiple back up solutions but get very inconsistent results (Grsync, Lucky BackUp, BackUp and a couple others).  I can mirror fine between USB drives (like between a couple of flash drives I use for financial info), but when I try to mirror to/ from Network drives the programs want to copy files in the destination directory that already exist. I also have a lot of trouble getting backup programs to even recognize the Network drives.

I got Grsync to copy the directories correctly once or twice, but if I run the same profile, the results change drastically.  I have tried various combinations of the switches available to me in all the backup programs - like time, permissions and size - to get it mirrored correctly but still get varying results

The two sync patterns I have issues with are 1) from a NAS drive (another Ubuntu machine used only as NAS) to a USB drive and 2) another, different USB drive to an UnRaid server.  I don't backup just mirror, in case of drive failure.  (It's setup like this because it evolved that way from different problems - like expanding the UnRaid server - and I needed to be sure my data was backed up)

The USB drives are both formatted FAT (I used to be a Windows user) so I'm sure that doesn't help. But I used to use Sync Back in Windows and it was easy, quick and trouble free (I tried to run Sync Back under Wine but it doesn't work well).

But the main question is:  why the difficulty with Networked drives?  I keep my data on external drives and plan to keep doing it this way except to change the NAS drive to a USB drive that will get backed up the to UnRaid server as well.  

Any suggestions or help greatly appreciated,

Mark Springer
industrial arts

---

### Post by collisionystm on 2014-06-26
I'm not familiar with GRSYNC, but why not use RSYNC from the command line? It's quite simple and you can place it into a .sh file and crontab it. rsync -rqa <source> <destination>. If you are backing up between Linux boxes you can exchange ssh pub keys and setup crontab to rsync over ssh.

---

