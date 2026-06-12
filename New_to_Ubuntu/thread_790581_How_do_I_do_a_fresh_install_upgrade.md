---
title: "How do I do a fresh install upgrade"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by medphys on 2008-05-11
Hi all;

I would like to do a fresh install upgrade form 7.10 to 8.04.  I have downloaded and burnt a CD for 8.04.  How do I use the CD and do a fresh install of the software while preserving my home partition.

I do not like to do an upgrade over the internet.  I am new to Ubuntu and would like to knowwhat is the best way to upgrade?

Thanks

---

### Post by 0ni on 2008-05-11
Just copy the content's of /home/ to your memory stick. Then take note of any programs you have installed.

There is a command that will auto do this for you but I can't remember it off of the top of my head.

---

### Post by jamyskis on 2008-05-11
> **medphys said:**
> Hi all;

I would like to do a fresh install upgrade form 7.10 to 8.04.  I have downloaded and burnt a CD for 8.04.  How do I use the CD and do a fresh install of the software while preserving my home partition.

I do not like to do an upgrade over the internet.  I am new to Ubuntu and would like to knowwhat is the best way to upgrade?

Thanks

Whatever you do, I would recommend keeping a backup of your home partition when doing a reinstall, as there is no guarantee that it can be preserved.

However, if you insist, you can quite happily use the LiveCD and nautilus to wipe everything off your drive with the exception of the home directory. Then install but **do not **format the drive in question.

---

### Post by jamyskis on 2008-05-11
> **0ni said:**
> Just copy the content's of /home/ to your memory stick. Then take note of any programs you have installed.

There is a command that will auto do this for you but I can't remember it off of the top of my head.

mkdir /media/memstick/homebackup
cp -R /home/username /media/memstick/homebackup/

Replace memstick with the name of your memstick mount point and username with your username.

---

### Post by nynoah on 2008-05-11
This is one of the things that bothers me about Ubuntu.  It is hard to do what you are trying to do.  The best thing to do is buy an external hard drive that is the same size as your hard drive and back up all the files you want to keep.  Doing a fresh install is really the best thing.  So you are doing right.  What I always do is back up my home directory and copy and paste all the files I wanted to keep back into my fresh install.  Its the safest way to go.

---

### Post by indiana_crook on 2008-05-11
> **medphys said:**
> Hi all;

I would like to do a fresh install upgrade form 7.10 to 8.04.  I have downloaded and burnt a CD for 8.04.  How do I use the CD and do a fresh install of the software while preserving my home partition.

I do not like to do an upgrade over the internet.  I am new to Ubuntu and would like to knowwhat is the best way to upgrade?

Thanks

I agree, back up all your files on CD/DVD or flash drive.  I ahd to do the same because something went wrong with my ubuntu upgrade via internet.  Also, if you attempt to keep your home partition by selecting only a percentage of your hard drive for hardy heron's partition, you'll actually end up dual booting gutsy and hardy.  I highly recommend that you backup your filesystem and do a complete install using your entire disk.  Hope this helps.

---

### Post by zvacet on 2008-05-11
Do you have enough space to make separate home partition? If you do make ir following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.Ans as **jamyskis** said **do not format** that partition during install.Just give in mountpoint /home and nothing else.

@ **indiana_crook**


> Also, if you attempt to keep your home partition by selecting only a percentage of your hard drive for hardy heron's partition, you'll actually end up dual booting gutsy and hardy.

This is not truth.

---

### Post by Frak on 2008-05-11
> **indiana_crook said:**
> Also, if you attempt to keep your home partition by selecting only a percentage of your hard drive for hardy heron's partition, you'll actually end up dual booting gutsy and hardy.

?

That is the most random logic ever. Grub is stored on the MBR and it points to the / (or /boot if you have one) to find the menu.lst. Therefore, anything in your / (or /boot) partition that has a menu.lst is used. And if ANYTHING SPECTACULARLY RANDOM OCCURS to cause a dual boot of hardy and gutsy (such as installing gutsy on a / and hardy on a / and asking them both to use the same ~/) then there may be an issue. NOTHING points to the /home partition, with the exception of fsck. Therefore, it will NOT have a dual boot list unless XP or Gutsy happens to already be installed and you just decide to keep it on there.

To the Original Poster
Like everybody else said, burn your home to disc or copy to external HDD/Flash drive, thumbdrive etc. Then copy it back to replace the one you have after the install and run
```
sudo chown -R $USER ~/
```
to return the ownership of the home directory back to you.

---

