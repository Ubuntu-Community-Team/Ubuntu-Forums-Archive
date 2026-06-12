---
title: "Need to transfer file from XP Hard drive"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Craig-Vyvyan on 2008-11-17
OK this is probably a total rookie problem but I've spent a couple hours trying to find the solution so....its time to swallow the my pride and ask.

Situation: No admin or other login access to XP laptop with SATA HD.  Suffice to say I blew it up trying to move it out of a Domain environ to a home environ without being on the domain and can't recover because I'm 1000 miles from the Domain (thanks for the nice design MS).  Need to retrieve files before wiping HD clean and reloading OS which is the best thing overall for this new user of the machine.  Perfect situation for Pendrive Xubuntu.

Problem: Xubuntu loads fine.  I've only played a little with Linux variants of the last 10 years so I am a newbie. I can see hard drive in Partitioner (sda1 8mb & sda2 80gb).  Can see it listed in drop down menu in File Manger when I try to type in /dev/sda2 as address but I get a question about how to open program of type "block device".  HD doesn't appear on my desk top.  There is no "Computer" under places.

Under Terminal I ran fdisk -l and got "cannot open /dev/sda/" followed by the USB pendrive info in the partition table.

I have a feeling this is Linux 101 stuff but I'm clueless and I have a client nagging after one day.  My next options cost money to replace HD until I can figure this out or get an outboard case for the HD and try to read it with another XP machine.

Please HELP!!!!

---

### Post by Commander_Keen on 2008-11-17
Hi.
 there are a few different routs you can go with this.
1st d/l Ubuntu8.04 and run the CD on Live mode.
From there you should be able to explore the entire HD, and be able to copy files onto a flash drive.
Option 2 
   Is this a PC or a Hard drive?  Is there any type of security on the HD? PGP, or Safe Gaured Ez Pwd?  If the answer is no.
then you will have to check with Max PC, they list a program called EBD or somehting to that effect.
It will allow you to create ( from Dos) a new Admin account.

---

### Post by handydan918 on 2008-11-17
With a live cd (or flash drive) you will need to mount the hard drive. After it is mounted, all files should be easily read-/writeable.

If you don't know how to do this, post back the output of ```
mount
``` and I feell sure someone will be dable to help. 
(I really don't have a clue about xubuntu and the xfce gui...but that's the nice thing about the terminal. It just works.)

---

### Post by Dedoimedo on 2008-11-17
Hi,

Did you try running fdisk as sudo?

Try mounting manually:

sudo mount -t ntfs /dev/sda1 /mount-point-somewhere

Then browse (cd) to relevant mount point and try to copy files.

You may also want to look into following subjects: auto-mounting NTFS drives in Ubuntu and ntfs-3g.

Dedoimedo


P.S. It is also possible that the ntfs drive was not unmounted properly by windows, so you might have to "force" it.

---

### Post by Junkieman on 2008-11-17
hi, do you know what filesystem the drive uses, i assume it would be the default ntfs for xp?

my first response would be to suggest using [Knoppix]("http://www.knopper.net/knoppix/index-en.html"), its a live cd that mounts all your drives read-only, and has ntfs support so you can copy the files off onto another drive/network. it's very handy to keep a knoppix cd lying around.

however if youre looking for a more immediate solution, i think you need to edit your /etc/fstab file so that it shows up as a fixed drive. im not quite sure but we can figure it out.

click *Applications -> Accessories -> Terminal* and enter:

```
sudo fdisk -l
```

paste the results here for us..

---

### Post by Craig-Vyvyan on 2008-11-17
Thanks for all the great replies.  Particularly the one on creating an admin user which will definitely solve my problem if it works.  

I just ran "sudo fdisk -l" and sure enough it shows up as /dev/sda2.  I feel like I am just missing the basic concept of how to navigate to it.  If it shows up in fdisk than it is mounted right?  So why doesn't it show up anywhere (except in the partition and Catfish where I tried a search but it came back with nothing)  It is listed in fdisk as HPFS/NTFS.  I am a little confused on how to navigate even through Terminal.  What would be the command? I attempted cd but probably got it wrong.

Thanks again for the responses.

---

### Post by Craig-Vyvyan on 2008-11-17
Basically I guess I am asking now what the mount point would be for the hard drive.

---

### Post by gychang on 2008-11-17
I installed the intreped in XP machine using wubi.  

Is there a way to "see" the files on the XP side?, I need .flac files...

gychang

---

### Post by Craig-Vyvyan on 2008-11-17
Got it.  My mistake was thinking that because the drive shows up in so many places, under fdisk and in the dev folder and all, that it was mounted.  Of course you guys said I had to mount it but I wasn't seeing it at all at that time.  Now, after doing some much needed reading I see that it was not auto-mounting.  I ran the ol'
sudo mount /dev/sda1 /mnt
and there it is in the mnt folder.  Of course I should have created a new folder under mnt and will umount and redo that now.

Done.  Now to move on to the very cool thing about creating a new admin user.

Thanks again.  Sorry about the newbie questions.  I've been meaning to get into Linux for 10 years but always ran into little things like this and gave up so I really appreciate the help.  It got me on my way and I learned a lot with your help and a lot of reading.

---

### Post by Junkieman on 2008-11-18
glad we could help!

yes to auto-mount any additional disks you need to add an entry into your /etc/fstab using the 'auto' option - but you wont need to do that if you only want to copy the files off... hope you got all your files :mrgreen:

---

### Post by cardinals_fan on 2008-11-18
> **Craig-Vyvyan said:**
> Thanks for all the great replies.  Particularly the one on creating an admin user which will definitely solve my problem if it works.  

While forum policy forbids explicitly explaining how to do it, I will give some opinions on this.  **In my unliable, unreliable opinion**: should you create a root password?  Yes.  Should you ever actually login as root (as opposed to typing "su" to enter a temporary root shell)?  **NO!**

---

