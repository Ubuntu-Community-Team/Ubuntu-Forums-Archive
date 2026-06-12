---
title: "Unlock CDROM -&gt; Eject with cd-rom button"
date: 2006-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Gandalf on 2006-01-10
Hello,

This HOWTO is just for trick to make the cd eject by pressing the eject button on the cd drive which has been included into dapper, but this is how to do it on breezy

Open Terminal and type
```

sudo sysctl dev.cdrom.lock=0

```

now your cd can be ejected by simply clicking on the eject button but if you restart it will no longer be available, to make it permenant, then type
```

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

```

Now it will be permenant

**P.S:** Taken from [Ubuntu Bugzilla](http://bugzilla.ubuntu.com/show_bug.cgi?id=11480)

Hope that help

---

### Post by Gandalf on 2006-01-11
finally it has been approved :D

---

### Post by beerorkid on 2006-01-11
that is fancy.  That was one of the little things that made me scratch my head.
Thanks

---

### Post by Gandalf on 2006-01-11
Yeah and the solution was obviously easy :)

---

### Post by Iandefor on 2006-01-11
Awesome! Glad to hear it's being fixed in Dapper. In the meanwhile, thanks for this little workaround!

---

### Post by benplaut on 2006-01-12
that's the coolest thing i've seen in a really, really long time!

now if only it was possible to just pull out a jumpdrive, without unmounting

*grundle grundle*

---

### Post by manicka on 2006-01-12
I have added this How-To to the Ubuntu Document Storage Facility

---

### Post by Gandalf on 2006-01-12
Thank you manicka for informing us, i was going to write it now :D

---

### Post by Bloot on 2006-01-12
It doesn't work with my second dvd+-rw. I tried cdrom1, dvd1, cdrw instead but no luck. :?

---

### Post by frodon on 2006-01-12
Thanks Gandalf, i always forgot the first command.

Really useful !!!!!! :KS

---

### Post by Gandalf on 2006-01-12
[QUOTE=Bloot]It doesn't work with my second dvd+-rw. I tried cdrom1, dvd1, cdrw instead but no luck. :?[/QUOTE]
Checking man sysctl, I've found that sysctl modify parameters under /proc/sys, so actually
```

sudo sysctl dev.cdrom.lock=0

```
is equivalent to
```

sudo sh -c 'echo "0" > /proc/sys/dev/cdrom/lock'

```

anyway back to your problem please give me the output of the command
```

ls -l /proc/sys/dev

```

---

### Post by Bloot on 2006-01-12
[QUOTE=Gandalf]anyway back to your problem please give me the output of the command
```

ls -l /proc/sys/dev

```[/QUOTE]

Here it is

```
ls -l /proc/sys/dev
total 0
dr-xr-xr-x  2 root root 0 2006-01-13 00:08 cdrom
dr-xr-xr-x  2 root root 0 2006-01-13 00:08 hpet
dr-xr-xr-x  4 root root 0 2006-01-13 00:08 parport
dr-xr-xr-x  2 root root 0 2006-01-13 00:08 raid
dr-xr-xr-x  2 root root 0 2006-01-13 00:08 rtc
dr-xr-xr-x  2 root root 0 2006-01-13 00:08 scsi

```

Many thanks. ;)

---

### Post by Gandalf on 2006-01-12
hmmm, am a bit confused coz check /proc/sys/dev/cdrom/info u will find the info  of ur both cdrom drived so i think the lock file is shared with both drives, it should unlock them both :S but am not sure, anyway i dont see any other cdrom drive :S

---

### Post by Bloot on 2006-01-12
[QUOTE=Gandalf]hmmm, am a bit confused coz check /proc/sys/dev/cdrom/info u will find the info  of ur both cdrom drived so i think the lock file is shared with both drives, it should unlock them both :S but am not sure, anyway i dont see any other cdrom drive :S[/QUOTE]
Nevermind, I've survived to this for months, I'll survive 'till dapper. ;)

Thanks for your interest!.

---

### Post by Gandalf on 2006-01-12
oh ok :D
you're welcome anyway :)

---

### Post by quonsar on 2006-01-13
i guess i'm confused at what you're talking about here? i just made a launcher like so and put it on my panel:

[IMG]http://2trak.com/Launcher-Properties.png[/IMG]

---

### Post by benplaut on 2006-01-13
[QUOTE=quonsar]i guess i'm confused at what you're talking about here? i just made a launcher like so and put it on my panel:[/QUOTE]

now you can just press the button on the CD drive and it will eject, like it's supposed to! :eek:

---

### Post by quonsar on 2006-01-13
*slaps forehead*  :oops:

---

### Post by xcap on 2006-02-12
[QUOTE=Bloot]It doesn't work with my second dvd+-rw. I tried cdrom1, dvd1, cdrw instead but no luck. :?[/QUOTE]

Oh my, I had the same problem, how can I solve it, no one knows?

---

### Post by christooss on 2006-02-12
My CdRom doesn't open. This is my ls -l /proc/sys/dev

dr-xr-xr-x 2 root root 0 2006-02-12 23:03 cdrom
dr-xr-xr-x 2 root root 0 2006-02-12 23:03 hpet
dr-xr-xr-x 4 root root 0 2006-02-12 23:03 parport
dr-xr-xr-x 2 root root 0 2006-02-12 23:03 raid
dr-xr-xr-x 2 root root 0 2006-02-12 23:03 rtc

Im using Dapper

---

### Post by Gandalf on 2006-02-12
Dapper already have this option, but not using sysctl, using another thing... check the bug link posted at the first post

---

### Post by christooss on 2006-02-13
Hm I have done this but now it doesn't mount CD-ROM any more. How can I undo this. So I can follow instructions from Bugreport

---

### Post by Gandalf on 2006-02-13
edit /etc/sysctl.conf and remove the last line which is dev.cdrom.lock=0 if am not mistaken

---

### Post by rado_london on 2006-02-13
Thanks it worked as a charm on HP Pavilion DV4145ea laptop:D:D:d

---

### Post by mstlyevil on 2006-02-21
I can say for a fact it worked in Dapper also. I did it before I read through the whole thread but hey it worked.

---

### Post by detyabozhye on 2006-02-28
Thx! Works great here.

---

### Post by daredevil on 2006-03-01
REally handy thnk u very much

---

