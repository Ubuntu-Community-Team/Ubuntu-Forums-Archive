---
title: "Gnomebaker with multisession burning"
date: 2005-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by depp on 2005-11-21
I don't want install some kde stuff just for k3b, so i was expecting somehow Gnomebaker to work with multisession burning. There are few threads in the forum, i checked some hints in Gnomebaker's site. Finally, i got it work.
What i did was:
1, add "ro" to your /dev/hdc in /etc/fstab
2, sudo umount /dev/hdc
After that, you can "import session" in Gnomebaker smoothly.

---

### Post by bored2k on 2005-11-22
Well bye bye **kdelibs** :D. 

That was almost too easy to believe &#172;_&#172; .

For those wondering how to add the "ro", use my fstab line as an example:

```
/dev/hdb        /media/cdrom0   udf,iso9660 **ro**,user,noauto     0       0
```


Note: depp, you might want to reformulate your post. Not everyone uses **hdc** and you might want to add the correct way to add ro.

**Thanks depp**, that was so easy I'm ashamed of myself for not figuring it out.

---

### Post by kittcankitt on 2005-11-22
How would one apply this to an external drive...ie: my external dvd burner that gets mounted at /dev/scd0?  

and not to jack a thread but would someone be able to explain to me why I get permission errors trying to use k3b (and "input/output errors:not nescesarily serious) then hangs for minutes before occasionally actually writing to the disk?  For that matter, the more I think about it, gnomebaker gives me permission errors about not being able to access /dev/sg0 and tries 20 times before failing.  The gnomebaker issue is mostly when trying to write to a cd and NOT when writing to a dvd.

My writer is not in my fstab as it's external.  Would adding an entry solve some of these problems?  It seems to me the last time I tried to add it, all I got were errors about the device not being present.  I think it had to do with the proper modules not being loaded at the right time/sequence.

Any ideas about either issues?  I would really like to be able to able to write a multisession disk. (ok, they are cheap enough but some days I end up wasting over 3/4 of a disk for no other reason than that, kind of a pain)

I would appreciate any info.  I've searched for usb permissions, external drives, and plenty of other things but nothing really seemed to match up with my problem with the permissions in k3b.  AND if I try to start k3bsetup2 (actually that doesn't start anything) but k3bsetup just gives me a blank window with "help, ok, and apply" at the bottom.  Starting k3b sudo still gives me the input/output error and the whole operation fails most of the time.

---

### Post by kaamos on 2005-11-23
To check what your device is:
```
ls -la /dev/ | grep cdrom
```
.. or if you have a dvd-burner
```
ls -la /dev/ | grep dvd
```

See where the symlink points to and you're good to go. For example for me the output is:> lrwxrwxrwx   1 root root           3 2005-11-23 09:12 cdrom -> hdc

---

### Post by depp on 2005-11-23
thanks bored2k kaamos, your additional infos make things better!

---

### Post by ored on 2005-11-30
this is just avesome! I've tried to make it works for a long time and now it just works! Thanks a lot!

---

### Post by tanari on 2005-12-16
what is **ro** and why is it helps? Just interesting :)

---

### Post by ember on 2005-12-16
I always thought 'ro' was 'readonly', so I'm interested, too

---

### Post by nocturn on 2005-12-16
[QUOTE=ember]I always thought 'ro' was 'readonly', so I'm interested, too[/QUOTE]

It is read only...

[quote=mount man page]
-r     Mount the file system read-only. A synonym is -o ro.
[/quote]

---

### Post by ember on 2005-12-16
So I still wonder why it helps with multisession reading.

---

### Post by cutOff on 2005-12-16
Unmount it before? Do I have to do that each time? hmm...

---

### Post by tanari on 2005-12-16
Does Nautilus support multisession CD/DVD?

---

### Post by depp on 2005-12-16
I don't really know either, what "ro" does.
And it doesn't work, unless i umount CDROM before i read previous session.
Maybe we shall throw these two questions to the Gnomebaker developers. :rolleyes:
But anyway, i like this lightweighted burning program, it looks better than k3b too.

---

### Post by tassoman on 2006-10-29
I'm trying to get it working, but while I'm writing the 2nd session on CD it fails with this error log:

```
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
Rock Ridge signatures found
mkisofs: No such file or directory. Invalid node - /media/cdrom1/NVIDIA-Linux-x86-1.0-9625-pkg1.run

```

---

### Post by drmartens on 2006-11-11
Yeah, same here. It was working in dapper. I have some CD with my backups. I was making a backup each month, so I have already a few backups there. After I upgraded to edgy, multisession stopped working and I have errors like people in this thread. I think I'll file a bug in gnome maybe

---

### Post by drmartens on 2006-11-15
I reported the problem to developers. For now, I installed k3b and with some problems I finnaly managed to burn my CD ;-)

---

### Post by Turin Turambar on 2006-11-15
Yeah, I get the same error.... Why can't Gnome have a clean & simple CD/DVD burner program?

I find GnomeBaker buggy! In every release they fix loads of stuff, yet I almost always experience some bugs... minor or major.

---

### Post by Turin Turambar on 2006-11-16
I just want to say that NeroLinux is great! It uses GTK 1.2 though, but with some skins (industrial + ubuntu skin) it looks almost like a genuine Ubuntu program (gtk2).

It does all the things that you'd expect from a cd burner to do:
uses all hardware advantages, there's a verify option and multisession is working as it should.

So, until Gnomebaker fixes the long list of bugs (and adds the "verify" feature), I'll stick to NeroLinux.

---

### Post by dpm on 2006-11-17
> **Turin Turambar said:**
> So, until Gnomebaker fixes the long list of bugs (and adds the "verify" feature), I'll stick to NeroLinux.

I couldn't have put it better myself. Why on earth such a basic feature as "verify" is still missing in GnomeBaker is beyond me. Up till now k3b is the only kde app I've got on my system, since GnomeBaker is just not working reliably enough.

---

### Post by dpm on 2006-11-17
Sorry for sort of hijacking the thread, but I was getting pissed off by this and just reported a bug on Launchpad and upstream:

[https://launchpad.net/products/gnomebaker/+bug/72217](https://launchpad.net/products/gnomebaker/+bug/72217)

Going back to the original subject. Could anyone with knowledge of what the **ro** option does and why exactly it is needed fill in a bug report on Launchpad or SF?

Cheers

---

### Post by mistypotato on 2007-01-04
> **depp said:**
> I don't want install some kde stuff just for k3b, so i was expecting somehow Gnomebaker to work with multisession burning. There are few threads in the forum, i checked some hints in Gnomebaker's site. Finally, i got it work.
What i did was:
1, add "ro" to your /dev/hdc in /etc/fstab
2, sudo umount /dev/hdc
After that, you can "import session" in Gnomebaker smoothly.

Well Sum Beeach!

Worked for me too!

For those wondering what's going on....especially newbies (like me)....
This is actually VERY VERY easy.

I didn't know what the heck they were talking about until I went and actually LOOKED at the file called fstab.

It's located in /etc/ and you might have to scroll WAY down to the bottom.

Once I added **ro**...my CD burning magically started working!

Now I'm using k3b with no problems at all.   I'm lovin it!!

Thanks DEPP (and bored2k) !!!!

---

### Post by nnovillo on 2007-01-27
> **bored2k said:**
> Well bye bye **kdelibs** :D. 

That was almost too easy to believe ¬_¬ .

For those wondering how to add the "ro", use my fstab line as an example:

```
/dev/hdb        /media/cdrom0   udf,iso9660 **ro**,user,noauto     0       0
```


Note: depp, you might want to reformulate your post. Not everyone uses **hdc** and you might want to add the correct way to add ro.

**Thanks depp**, that was so easy I'm ashamed of myself for not figuring it out.

Hi there,
Thank you four your help. I managed to add ro to the fstab file, but when I do
sudo umount /dev/hdb

I get
umount: /dev/hdb: not mounted

Another question is if after adding ro, Can I import previously recorded sessions, or does it only work from now on?

These are my outputs for ls -la /dev/ | grep dvd and -la /dev/ | grep cd

lrwxrwxrwx  1 root root           3 2007-01-27 10:55 dvd -> hdb
lrwxrwxrwx  1 root root           3 2007-01-27 10:55 dvdrw -> hdb

lrwxrwxrwx  1 root root           3 2007-01-27 10:55 cdrom -> hdb
brw-rw----  1 root cdrom     3,  64 2007-01-27 07:55 hdb


Thanks!
Nike.

---

### Post by ored on 2007-12-02
I've installed **[COLOR="Red"]brasero[/COLOR]** on ubuntu gutsy and it worked fine for me.
I hope it helps.

---

