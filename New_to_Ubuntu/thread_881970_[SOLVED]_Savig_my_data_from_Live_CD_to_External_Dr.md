---
title: "[SOLVED] Savig my data from Live CD to External Drive for Reinstall"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by OZFive on 2008-08-06
Okay I have decided to backup my home folder to an external hard drive so that I might reinstall the OS.  I need to know what I need to do to my permissions so that I can do it from the Live Cd as the install Ubuntu is not working.

---

### Post by philinux on 2008-08-06
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

You'll have to adapt this slightly.

You could also move home to it's own partition the info is also on this site.

---

### Post by OZFive on 2008-08-06
[B]ubuntu@ubuntu:~$ rsync -av /media/disk/home/matthew /media/OneTouch4 Mini
building file list ... rsync: opendir "/media/disk/home/matthew/.bogofilter" failed: Permission denied (13)[/B]

I am running from the Live CD, does this method take that into account?

---

### Post by philinux on 2008-08-06
> **OZFive said:**
> [B]ubuntu@ubuntu:~$ rsync -av /media/disk/home/matthew /media/OneTouch4 Mini
building file list ... rsync: opendir "/media/disk/home/matthew/.bogofilter" failed: Permission denied (13)[/B]

I am running from the Live CD, does this method take that into account?
I would not suggest using sudo just yet.

How did you format the external and what permissions has it got?

---

### Post by OZFive on 2008-08-06
I did not format it I plugged it in and tried to drag it over.  I figured as I was not using it as a boot drive that it would not matter. It is a Maxtor OneTouch 4 Mini brand new out of the box for just this purpose.

---

### Post by philinux on 2008-08-06
> **OZFive said:**
> I did not format it I plugged it in and tried to drag it over.  I figured as I was not using it as a boot drive that it would not matter. It is a Maxtor OneTouch 4 Mini brand new out of the box for just this purpose.

If it's brand new you need to format it, ext3.

Also another solution
[http://ubuntuforums.org/showthread.php?t=810393](http://ubuntuforums.org/showthread.php?t=810393)

---

### Post by OZFive on 2008-08-06
I do not want to be a pest, but how do I need to go about doing that?

---

### Post by philinux on 2008-08-06
[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

---

### Post by OZFive on 2008-08-06
Okay I just got it reformatted and in ext3.  Gparted is pretty cool I must say.

So I tried the instructions fomr that page you suggested and got this....

[B]ubuntu@ubuntu:~$ cd /media/disk-1/home/matthew
ubuntu@ubuntu:/media/disk-1/home/matthew$ sudo cd -r -v * /media/disk-1
sudo: cd: command not found
ubuntu@ubuntu:/media/disk-1/home/matthew$ [/B]

What now?

---

### Post by OZFive on 2008-08-06
I tried your fist suggestion to and got this....

[B]ubuntu@ubuntu:~$ rsync -av /media/disk-1/home/matthew /media/disk
building file list ... rsync: opendir "/media/disk-1/home/matthew/.bogofilter" failed: Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(271) [receiver=2.6.9]
rsync: writefd_unbuffered failed to write 3048 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at io.c(454) [sender=2.6.9]
ubuntu@ubuntu:~$[/B]

---

### Post by philinux on 2008-08-06
> **OZFive said:**
> I tried your fist suggestion to and got this....

[B]ubuntu@ubuntu:~$ rsync -av /media/disk-1/home/matthew /media/disk
building file list ... rsync: opendir "/media/disk-1/home/matthew/.bogofilter" failed: Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(271) [receiver=2.6.9]
rsync: writefd_unbuffered failed to write 3048 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at io.c(454) [sender=2.6.9]
ubuntu@ubuntu:~$[/B]

disk-1 and disk - which is your home and which is the external ?

---

### Post by Blutack on 2008-08-06
Have you tried using
sudo cp -av /target /destination?
It copies and preserves all the permissions and users.

---

### Post by OZFive on 2008-08-06
> **philinux said:**
> disk-1 and disk - which is your home and which is the external ?

home is ....
/media/disk-1/home/matthew


destination is...
/media/disk

---

### Post by OZFive on 2008-08-06
> Originally Posted by **Blutack**
Have you tried using
sudo cp -av /target /destination?
It copies and preserves all the permissions and users.


Trying this now, not sure how it is going as it seems to have hung... I am wating...

---

### Post by philinux on 2008-08-06
> **OZFive said:**
> Trying this now, not sure how it is going as it seems to have hung... I am wating...

[http://ubuntuforums.org/showthread.php?t=445117](http://ubuntuforums.org/showthread.php?t=445117)

I'd avoid using sudo to copy you may have the same trouble copying stuff back. Better to fix the problem

I forgot there is also grsync which is the gui for rsync. Just makes things easier to do.

We may need to change the permission on your external. After the cp has finished.

[edit- did not see this]
Originally Posted by Blutack
Have you tried using
sudo cp -av /target /destination?
It copies and preserves all the permissions and users.

---

### Post by billgoldberg on 2008-08-06
Is there a reason you can't use nautilus on the live cd to copy the files?

I don't know if it's neccesary to start nautilus as root, if so, start it with gksudo nautilus.

ps: nautilus is the default file manager. Start it by going to "places -> home"

---

### Post by OZFive on 2008-08-06
I would be very intersted in that software for this.  Where may I find it, it is not in the usual repositories, not on getdeb.com and the softwre site seems to have a installer for all the major Linuxes but Ubuntu.

---

### Post by OZFive on 2008-08-06
> **billgoldberg said:**
> Is there a reason you can't use nautilus on the live cd to copy the files?

I don't know if it's neccesary to start nautilus as root, if so, start it with gksudo nautilus.

ps: nautilus is the default file manager. Start it by going to "places -> home"

not exactly sure what your telling me to do here but anythin easy would be GREAT!

p.s. Actually I am trying this and it seems to be working here.

---

### Post by Blutack on 2008-08-06
Oh...you are using a live cd?
Press Alt and F2.
Type
gksudo nautilus
into the resulting box.
Press File --> New Window
Try copying your stuff like that (go to your external HD in one, and your home folder in another).
This may mess your permissions up completely if you are using an ext3 drive.
You can change them back by selecting everything and right clicking, then setting your user as the owner once they are all copied.

---

### Post by OZFive on 2008-08-06
It is taking abot forever to get this done.  I am a bit inpatient and I have ALOT of music to save up.  So I was curious...  If I install 8.04 on the new excternal and boot up from that, can i then access the internal HD and use the DVD burner to burn my music to a DVD and do it that way?  No Live CD to use then?  Right?

---

### Post by philinux on 2008-08-06
cp is fast, using nautilus is very slow.

---

### Post by OZFive on 2008-08-06
Well I found grsync and this is what happened.....

and I would love to use the faster method but so far I am having no luck with any of the cp- commands I have tried

---

### Post by philinux on 2008-08-06
Right click on your ext drive and choose properties. Then click the permission tab. See what that says.

---

### Post by OZFive on 2008-08-06
Was already doing JUST that.

---

### Post by philinux on 2008-08-06
Open a terminal and use these

sudo chown -R yourusername /media/disk

then

sudo chmod 775 /media/disk

Just to check the ext is /media/disk

---

### Post by OZFive on 2008-08-06
Give me the instructions, I am your willing student.

---

### Post by OZFive on 2008-08-06
[attach]80493[/attach]

---

### Post by philinux on 2008-08-06
See previous post , edited.

---

### Post by OZFive on 2008-08-06
I tired that and I know my user name on my Internal Disk is user name matthew.   But on the external running of the live CD?

---

### Post by philinux on 2008-08-06
Try the chown again now. I've done this with a usb drive from the live cd and it worked. The live cd is just a tool.

---

### Post by OZFive on 2008-08-06
I tried it again but same thing with the matthew user name but I tried it with the "ubuntu" user name from the Live User Session and now it looks like grsync is working!

---

### Post by OZFive on 2008-08-14
Can you believe it literly took ONE WEEK to back up all my data?   ONE WEEK!

Okay now it is all backed up and I am ready to re-install to see if we can get this back up and running.  The installer is fine up untill 94% "Configuring Hardware".  I was wondering....

since all my data is backed up and safe on another drive and I am having this hang up here...  

Should I do something like the forbidden rm- thing to clear out all data on the disk to start over from scratch?

---

### Post by OZFive on 2008-08-20
Just wanted to get a {SOLVED} tag on this one.


I did lose some data over all but not much, I could see in the terminal when it was complaining of Input/Output errors but it seems no mission ciritical data was taken down.

I finally got around to getting to the store to get a new hard Drive and settled on a 120GB 7200rpm Fijuitsu from Frys Electronics for $99.  I had them install it as it is buried inside the machine and while I am pretty tech savvy I did not want to take the chance.  I also upgraded the ram to 2gb for $50.  Installed that myself.  The tech there Jeremy was great.  And was a Ubuntu user as well.

So thanks to all for the help and I am finaly back in the saddle!

---

