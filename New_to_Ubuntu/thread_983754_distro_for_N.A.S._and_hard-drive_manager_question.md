---
title: "distro for N.A.S. and hard-drive manager question"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Knacker on 2008-11-16
I have a desktop computer that I've been using as Network Attached Storage and media center...pretty familiar setup (pile of hard-drives, projector, attached to router, etc.). It's last thing I own that still runs windows. I'm hoping that a person or two could help me overcome a couple of problems: 

1) I've never been as confident in the management of hard drive health with linux as I am with Windows. Hard drive management never quite works  *exactly* as it's supposed to with linuxes I've tried - i.e. HDs not spinning down when they should(n't), not staying asleep when they should, weird bugs where HDs are clicking and non-stop-reading, polled every second etc. etc.. Are my worries totally unfounded? Is there a really polished, really stable, really sure and (especially:) really easy to use graphical tool to manage hard drives for linux? 

2) Is there any problem or down-sides to running NTFS drives (which is what I have) from a linux OS?

3) Any other thoughts or recommendations re: distributions or packages that might be worth my while to check out? 

Finally, bear in mind that I'm not a super-user...still more or less a newbie.    
Sorry for the length. Always grateful for everyone's thoughts and help!

---

### Post by jimmy the saint on 2008-11-16
As far as I know, most issues with HDs and linux come with new features associated with the drive technology and is quickly accounted for in new kernels.  Its been a while since Ive seen anyone complain about it, at least here in the forums.  I have a box that I set up with Gutsy that serves as my file server, as well as a few other purposes.  I use it to stream music, store video for my xbox/xbmc, and store backups as well.  
I chose to run it headless, learn the few commands I needed on a regular basis (mostly related to the individual services) and suffer the pain of set-up.  Once I did that it was pie.  I have had it for over a year and it runs great and hasn't needed a restart once.  
As for NTFS, it is better to use a file system that is native to linux like ext3.  You will need to install samba to share files with windows machines or I use an ftp program for most things.  That is not to say that you cannot use NTFS.  Ubuntu has been able to handle NTFS out of the box for a while now.

---

### Post by Knacker on 2008-11-17
cool. thanks. as i've looked into it again, i think that i'll need to leave some windows somewhere at least until i can get things moved off the ntfs drives.... it seems there is still no software to defragment ntfs hard drives in linux (at least, nothing that's free). 

thanks a bunch for taking the time to reply!

---

