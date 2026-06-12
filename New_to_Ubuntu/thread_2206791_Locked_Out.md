---
title: "Locked Out"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by john wagner on 2014-02-20
As stated, I find myself unable to boot up on my Linux Laptop.  I've been using ubuntu (gnome) starting with 6.1.  My current laptop has been loaded up to 7.10, for about a year or so (I dumped Windows for ubuntu 15 years ago).  I used it the previous night, shut her all down and went to sleep.  Woke up this morning and powered her up, got to the log on screen and it won't let me in.  It changed the password itself!

I've to the set up page, tried to reset everything, nada.  Used a live cd, nada, all my laptop wanted to do is load the kernal.  Am I screwed?  I have a 350 gig hard drive, and, er, I haven't backed it up recently (6 months or so...  Yeah, I know).  Is there any way to get logged on my laptop?  Any way to download the HD?  Would just yanking the drive and using it as an external drive work?
Replies
Ubuntu 7.10
HP Pavillion   dv5000  (yeah it's an old machine, on its 3rd HD, 2nd memory upgrade)
1.6GHz
2 gig Ram
350 gig HD

Please, any one who can help!!!


john

---

### Post by oldfred on 2014-02-20
7.10?
 Version  7.10 	Supported until 	18 April 2009 	

That has not been supported from a long time.
I would download 12.04.4 if system have video enough to support full Ubuntu, but you may do better with current versions of Xubuntu or Lubuntu.

I would first see if Disks or Disk Utility in Ubuntu show hard drive is ok.
Then try fsck from live DVD or flash drive if you can boot flash drives.


 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Are you sure you typed password correctly. It does not change on its own.

      
 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by coldcritter64 on 2014-02-20
A big +1 to oldfred's suggestion of an update to the release/lighter version etc. I started with that particular release ~ 6 years ago. It's been a very long time since it has been supported.

---

### Post by bc.haynes on 2014-02-20
Make sure the "CAPS LOCK" is not on when you try your password. That's happened to me.

---

### Post by Impavidus on 2014-02-20
You could try changing your password in recovery mode, if the problem is indeed your password.

But 7.10 has been unsupported for almost 5 years, which means you've used it for a long time without any (security) updates. You're running ancient versions of software, which isn't only insecure, but also lacks many modern features. The specs ([http://www.engadget.com/products/hp/pavilion/dv5000/specs/](http://www.engadget.com/products/hp/pavilion/dv5000/specs/)) of that machine seem quite decent, I think it should run a modern Xubuntu easely.

---

### Post by john wagner on 2014-02-20
Yes, I know it's an old OS.  But I'm stubborn.  I  was on Dapper for 5 years, then I reluctantly moved up...

Yes, I know passwords don't change themselves overnight, except mine has.  Went to sleep AFTER closing and logging off.  Woke up, turned on laptop and it accepts user name but not my password.  Will NOT let me past the logon.

Tried the f10 way.  Did everything I could possible do, nada.

Did a deep HD check, took 2 hours, HD fine.

Now I can use any of my Live CD's to reformatHD, but I'm trying to find out if their is a way to force the logon using a live cd or something else.

Thanks for everyone so far!

john

---

### Post by deadflowr on 2014-02-20
You can follow this to reset your password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Edit: Since I forgot this is dapper, you can also use a livecd to change passwords
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by john wagner on 2014-02-20
Tried using the reset links you guys provided.

I went to recovery mode, then arrow down to root shell prompt, select it then after the os finishes its scrolling, I typed :
mount -o rw, remount /

looked to see my ID was present (it was), then typed

passwd name

Nada.  It still refuses to admit I am the admin/sole user of my old laptop.

Any other ideas?

john

---

### Post by Derxst on 2014-02-20
When you are resetting your password, is it a simple password or a complex password?

---

### Post by mastablasta on 2014-02-21
since it is not supported means security holes as well as other bugs are left unpatched.

moving on - boot into live session of 12.04 (Mate is the old Gnome desktop), mount the disk, move the data to external drive (backup). replace the OS with the 12.04 (supported for another 2 years) then move the data back to internal disk. enjoy. instalation takes only 15-30 minutes (depends a bit on internet connection).

---

### Post by fdrake on 2014-02-21
> **john wagner said:**
> Tried using the reset links you guys provided.

I went to recovery mode, then arrow down to root shell prompt, select it then after the os finishes its scrolling, I typed :
mount -o rw, remount /

looked to see my ID was present (it was), then typed

passwd name

Nada.  It still refuses to admit I am the admin/sole user of my old laptop.

Any other ideas?

john
what error do you exacly get ?
past here theoutput of 
```
passwd -S username
```

---

### Post by mörgæs on 2014-02-21
> **john wagner said:**
> I dumped Windows for ubuntu 15 years ago

That's impressive, especially when you consider that the first Ubuntu was released october 2004.

---

