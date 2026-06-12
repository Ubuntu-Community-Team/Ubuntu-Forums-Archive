---
title: "DSL uses 100% CPU"
date: 2007-08-04
forum: Other OS Talk
---

### Post by dptxp on 2007-08-04
DSL 3.4 uses (shows) 100% CPU on my laptop even in idle state, 0% on my desktop in idle state.

What can be the reason ? I have used boot option- ' dsl toram'

It is quite impressive with just 35 MB loaded to RAM.
But I could not see my partitions. How do I see them and mount them ?

---

### Post by kerry_s on 2007-08-04
your asking the wrong people, you need to ask on the DSL forum were you can get help from robert. robert can point you to how to find the problem since he is 1 of the main builders. i know he's busy working on the next version, but he always takes the time to scout the forums.
[http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

how come you went for 3.4 instead of the new 4.0a2, i heard the new setup is pretty interesting. i wish i had a working cd burner. :(
[http://distrowatch.com/?newsid=04384](http://distrowatch.com/?newsid=04384)

---

### Post by dptxp on 2007-08-04
> **kerry_s said:**
> your asking the wrong people, you need to ask on the DSL forum were you can get help from robert. robert can point you to how to find the problem since he is 1 of the main builders. i know he's busy working on the next version, but he always takes the time to scout the forums.
[http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

how come you went for 3.4 instead of the new 4.0a2, i heard the new setup is pretty interesting. i wish i had a working cd burner. :(
[http://distrowatch.com/?newsid=04384](http://distrowatch.com/?newsid=04384)

Thanks. I have posted there. I posted here because I am very familiar with the forums here and this is for OTHER OS TALK. Most of us using Ubuntu are Linux lovers and try other Linux distros.

BTW K3B burned my iso at about 27X speed in automode, InfraRecorder in Windows burns at about 20X.

---

### Post by kerry_s on 2007-08-04
> **dptxp said:**
> Thanks. I have posted there. I posted here because I am very familiar with the forums here and this is for OTHER OS TALK. Most of us using Ubuntu are Linux lovers and try other Linux distros.

BTW K3B burned my iso at about 27X speed in automode, InfraRecorder in Windows burns at about 20X.

as long as you posted there, true alot of us use other os's, i haven't used DSL in a while though, so i wouldn't even know where to start, much less remember how it all works. :)

you should not burn iso's at high speed, it's recommended they be burned at 4x for the best results. burning at higher speeds can cause all sorts of errors and many,many bad burns.

have you run top, to see if anything jumps out at ya.
for mounting, don't they still have that mount tool in the corner?

---

### Post by jacob01 on 2007-08-04
go into the terminal and type    top      to find out what is running and taking up so much of your resources

---

### Post by init1 on 2007-08-04
And type "fdisk -l" to see your partitions. It is possible that DSL does not recognize them.

---

### Post by cobrn1 on 2007-08-05
Not sure for DSL, but in DSL-N in the bottom right hand corner there is a little box with a button for the partition and a button to mount/unmount. But i guess that's a bit obvious so maybe not in DSL...

have you tries using the mount command?

Also, I too get a 100% CPU usage - I'm not sure what to think, but it doesn't worry me too much... the ram usage is incredible - 20Mb!

---

### Post by kerry_s on 2007-08-05
never mind, was still sleepy, i keep mistaking percentage for ram. :)

---

### Post by dptxp on 2007-08-06
> **cobrn1 said:**
> Not sure for DSL, but in DSL-N in the bottom right hand corner there is a little box with a button for the partition and a button to mount/unmount. But i guess that's a bit obvious so maybe not in DSL...

have you tries using the mount command?

Also, I too get a 100% CPU usage - I'm not sure what to think, but it doesn't worry me too much... the ram usage is incredible - 20Mb!

Thanks

I tried the mount button, but it was for FDD, maybe I missed out something. Shall try after a few hours.
No I did not try the mount command, shall it be-
mount /dev/hda1 
and so on ? maybe a sudo to precede it.
The Ram usage is impressive, but the fonts are bad, they are like XP, but worse.

---

### Post by init1 on 2007-08-06
> **dptxp said:**
> Thanks

I tried the mount button, but it was for FDD, maybe I missed out something. Shall try after a few hours.
No I did not try the mount command, shall it be-
mount /dev/hda1 
and so on ? maybe a sudo to precede it.
The Ram usage is impressive, but the fonts are bad, they are like XP, but worse.
fdisk -l will give you valid partitions. The code is:
```

mount /dev/thedevice thedirectory

```
thedevice=hda, sda, maybe something else
thedirectroy=some folder. Try /mnt or make you own folder for this. The contents of this folder will not be seen until you umount it.
For me it is:
```

mount /dev/sda4 a

``` 
to get my fdos partition mounted. And
```

mount /dev/sdb1 a

```
to get my USB drive mounted.

---

### Post by cobrn1 on 2007-08-06
click on the botton that says FFD or what ever. It'll change to something else like hda, or cdrom. Just keep clicking until you get the partition or device you want to mount.

---

