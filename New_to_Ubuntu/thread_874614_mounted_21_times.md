---
title: "mounted 21 times ??"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by todaymueller on 2008-07-30
Ok I have a couple of basic questions , every so often [ presumably every 21st time , although I have not counted ] I get a screen pop up when booting that says 'dev sda 1 has been mounted 21 times without being checked' , it then force checks whatever it is . This takes a few minutes and then I have to reboot . Where upon everything is fine for a few days . What's this all about and is there a solution ? 
Also if I upgraded to 8.04 LTS would I be correct in thinking I would not have to up grade again until the next LTS release ?
On the good news front I managed to install adobe flash player successfully all on my own :guitar: I'm learnin !

ps. how do I get rid of the comedy number font? :)

---

### Post by jimv on 2008-07-30
You don't have to upgrade to a new release.  In fact, in the Software Sources control panel, you can disable new release notifications.  It's under the Updates tab in the Releases section.

---

### Post by sdennie on 2008-07-30
That's a lot of unrelated questions but, usually the machine will check a disk around every 25-30 mounts (generally 30 reboots).  I don't recommend tweaking this setting as it's there for a good reason (to keep your disks in good order).  I'm not sure how you are seeing this every few days unless you reboot the machine many times a day.

If you are using 8.04, you will have support for 3 years whereas a regular release only has support for 18 months.

---

### Post by gvartser on 2008-07-30
Ubuntu forces drives to be checked once for every 30 times the filesystem is mounted. This means that on an average, once every 30 times you bootup your computer, the filesystem integrity is checked. This is very reasonable for a desktop, which is seldom rebooted. However, for a laptop, this means pain, since you may be planning on making a presentation, and Ubuntu may start a filesystem check just when you hook up your laptop to the projector and bootup

If you want to you can always change the fs check period from its default.

example: (Change the FS Check to check each 100 boot)
# sudo tune2fs -c 100

As always, you can read
# man tune2fs
for more detailed information and examples.

Best regards,
/G

---

### Post by iaculallad on 2008-07-30
> **todaymueller said:**
> Ok I have a couple of basic questions , every so often [ presumably every 21st time , although I have not counted ] I get a screen pop up when booting that says 'dev sda 1 has been mounted 21 times without being checked' , it then force checks whatever it is . This takes a few minutes and then I have to reboot . Where upon everything is fine for a few days . What's this all about and is there a solution ? 


Actually, that message/action is a good for your Ubuntu filesystem. It's a way of self-preservation, it autochecks on every 30'th startup. Try reading this [link]("http://ubuntuforums.org/showthread.php?t=300477") to get more information regarding this subject.

---

### Post by adult swim on 2008-07-30
edit: too slow!

---

### Post by ModelM on 2008-07-30
I don't understand why you would need to reboot after a filesystem check. The file system check (fsck) should run, complete, the boot process continue (although it may look different) and leave you at the usual login screen.

If the machine hangs during the fsck, there may be problems elsewhere.

---

### Post by sdennie on 2008-07-30
> **gvartser said:**
> Ubuntu forces drives to be checked once for every 30 times the filesystem is mounted. This means that on an average, once every 30 times you bootup your computer, the filesystem integrity is checked. This is very reasonable for a desktop, which is seldom rebooted. However, for a laptop, this means pain, since you may be planning on making a presentation, and Ubuntu may start a filesystem check just when you hook up your laptop to the projector and bootup

If you want to you can always change the fs check period from its default.

example: (Change the FS Check to check each 100 boot)
# sudo tune2fs -c 100

As always, you can read
# man tune2fs
for more detailed information and examples.

Best regards,
/G

Actually for a well supported laptop, you could just always suspend the machine instead of shutting it down (mine has never been completely off) to avoid that scenario.  That, or, rather than changing the limit with tune2fs, you can temporarily reset the mount count with -C to insure you won't open the machine and have it fsck the disks.  However if you do this often enough it will eventually decide to check the disks because after a certain number of days, it ignores the mount count.

---

### Post by gvartser on 2008-07-30
> **vor said:**
> Actually for a well supported laptop, you could just always suspend the machine instead of shutting it down (mine has never been completely off) to avoid that scenario.  That, or, rather than changing the limit with tune2fs, you can temporarily reset the mount count with -C to insure you won't open the machine and have it fsck the disks.  However if you do this often enough it will eventually decide to check the disks because after a certain number of days, it ignores the mount count.

True, but you can also reset the FS check for D W & M aswell:

To have the filesystem check run periodically, say once a week, use
$sudo tune2fs -i 1w
changing the &#8220;w&#8221; to &#8220;d&#8221; or &#8220;m&#8221; will have the check run once daily and once monthly - you get the idea.

Also im agreeing to that it is an good idea to have your fs checked. The only thing i mentioned was how to change the time frame if you find it to be a pain. ;)

Best regz,
/g

---

### Post by vanadium on 2008-07-30
Suspending a laptop unfortunately does not always work with Ubuntu. For me, fortunately, it works since Hardy, but other people are less lucky.

Anyway, for my laptop, I disabled the mount count setting and have the time set to one month. It is the balance between convenience/security that I choose. You are free to choose your settings. However, it is very unwise to disable checking alltogether.

This is the command I needed. The device name (/dev/sda1) is specific for your configuration.

```

sudo tune2fs -c 0 -i 1m /dev/sda1

```

---

### Post by todaymueller on 2008-07-30
I have managed to change the font to serif from Vermana 2000 . This is my fault for thinking vermana would be similar to verdana . It isn't its horrid .
 As regarding the file system check I will have to make better notes of what is said . But I have a feeling it ends 'fail' in red .

---

