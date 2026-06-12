---
title: "Location of shutdown log"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by GCapo on 2012-11-14
I cannot get my Ubuntu 12.04 system to shutdown properly even using terminal commands.  I am not using any proprietary drivers and I know the ISO I used to install it works because another desktop runs fine.

**Question &#8211;** Where can I find the log to see what is going wrong with the shutdown process?  Is there something that could tell me if there is a hardware problem?

I have exhausted all of the suggestions I have found on the forum, so I am hoping someone could point me in the right direction.  

Couple facts I am not sure are relevant.
1)	Ubuntu is the only OS on the Dell DM051 Desktop
2)	I have a Maxtor external hard drive connected using Firewire formatted in NTFS
3)	My BIOS clock is always wrong by a couple hours
a.	I changed the CMOS battery already
b.	If I change it and go into Ubuntu it will be wrong again after I restart
4)	If I use sudo shutdown now Ubuntu will freeze during shutdown and the GUI only restarts

Any help would be appreciated, I really need a new lead to continue researching. Note, I am a total beginner.

---

### Post by acimi66 on 2012-11-14
Have a look here.
 /var/log/messages

Let us know

---

### Post by GCapo on 2012-11-15
Thanks for the response.  When I go to var\log I do not see anything referencing messages.  Even tried to find it in the terminal too.

---

### Post by Bashing-om on 2012-11-17
GCapo; Hi !

I have a couple other threads taking up my resources at this time, but let me make these suggestions.
Can you operate temporarily with out the external NTFS drive ? (maybe /etc/fstab and NTFS not playing nicely ?)
bios clock: I have the same situation on my system (AMD64) but my system is solid and stable through three upgrade versions)
shut-down logs: as I understand it, once the system begins shutting down, there are no means available to log.

As you are examining the logs in /var/log/ and find nothing pertinent, it is possible to get some messages at shutdown by removing the "quiet splash" terms in the grub file and on my 12.04 I also edited to this "GRUB_GFXMODE=text" -> on my system I am able to pause the shut-down by pressing the pause/break key. -this enables boot messages ! --

Terminal shut down: sudo shutdown -r now  ->reboot[INDENT][INDENT][INDENT]sudo shutdown - P now -> power down turn off gracefully.
see: man shutdown
[/INDENT][/INDENT][/INDENT][INDENT][INDENT]let us know how we can help <== BDQ

[/INDENT][/INDENT]

---

### Post by GCapo on 2012-11-20
Well did try, sudo shutdown -P and the system only restarts.  I searched the logs and did not find anything yet.  Keep researching, any other ideas would be appreciated.

Note I got the external hard drive to mount just fine.

---

### Post by Bashing-om on 2012-11-20
GCapo;

At the present time I do not understand why "sudo shutdown - P now" does not power your system down ... A config file somewhere ???

Another log to look at: In your home directory .xsessions-errors. Notice the "." -> hidden file; ctl+h to see the hidden files.
[INDENT]hth <== BDQ

[/INDENT]

---

### Post by GCapo on 2012-11-23
Not sure how this "fixed" the shut down problem, but after several shutdowns it is working.

Story goes:

I bought another external hard drive because I was filling up everything here.  I decided to format the new one to ext4, transferred files from the old one (NTFS) to the new one then formatted the old on ext4.  I am only using Linux now so why not, I will use thumb drives if I have to transfer something to windows.  I then mounted the hard drives using these instructions:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Now shutdown works when I am logged in under the Administrator account.  Only problem now is how to share external hard drives with other users on the same machine and with another Ubuntu desktop in the house used as a media center running xmbc.

Think I am going to look into Samba, but if anyone has a suggestion I am completely open.  Obviously, super new but I do enjoy learning it.

---

### Post by Bashing-om on 2012-11-23
Glad ya got it sorted out --seemingly a mounting issue prior; alls well that ends well.
on samba-- to talk with windows machines is the preferred method. If you have difficulties ask - start another thread- .....

Please mark this thread as solved. Marking so aides in many ways.

[INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

### Post by GCapo on 2012-11-23
Don't want to say this, but how do I show it as "solved" per Basing-om' request?

Thanks for the input on the sharing.  It will probably take all December for me to figure out given the time I will spend on it.

Regards,
George

---

### Post by Bashing-om on 2012-11-23
My pleasure.
Mark as solved by thread tools at the top of the post.

Filesharing -> ubuntu 2 ubuntu ..right click a folder to share; select the option "share folder" ..nautilus: choose network -> ip address (from ipconfig) and the <share folder name> and that folder is available in nautilus. Windows is a bit more complicated with samba ..iirc...edit the samba.config file for workgroups and accesses.

best to start another thread, get better responses.

[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by GCapo on 2012-12-02
Just an update.  I thought the shutdown was fixed, but it is not consistent.  Will post if I find anything for other people.

---

