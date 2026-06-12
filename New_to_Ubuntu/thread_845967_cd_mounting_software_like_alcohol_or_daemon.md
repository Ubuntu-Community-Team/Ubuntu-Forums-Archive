---
title: "cd mounting software like alcohol or daemon"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by ettercap on 2008-07-01
i  need a cd/dvd mounting software like alcohol or daemon  tools for ubuntu 
are there any available softwares........
i heard about acetone iso ...sounds like it will only mount iso files...is this true ?

will the mount command work for files like

.nrg
.mdf etc........

please help
thanks

---

### Post by hyper_ch on 2008-07-01
it's not needed.. you can mount iso images just like that

```

sudo mkdir /media/iso
sudo mount -o loop -t iso9660 iamge.iso /media/iso

```

.nrg should work also... no clue about .mdf

---

### Post by Mornedhel on 2008-07-01
mount will probably work only for .iso files. This :

sudo mount -t iso9660 path/to/your/file.iso /media/cdrom -o loop

will mount the image, and

sudo umount /media/cdrom

will unmount it.

Several utilities seem to convert .nrg and others to .iso ('iat' claims to be able to do this, never tried it though), and if you feel like using FUSE, then their ISO module should also be able to mount .bin, .img, .nrg etc. files.

---

### Post by atomkarinca on 2008-07-01
Check out [AcetoneISO2]("http://www.acetoneiso.netsons.org/").

---

### Post by eotakos on 2008-07-01
actually i have a question here - at the community documentation site, if you search for "mount iso" (... and you get here [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso))

at some point is reads [HTML]Alcohol 120% image (.mdf) files can either be converted to iso using mdf2iso or mounted directly using mount. [/HTML]

but the example underneath mounts an .iso image. I tried to do something like that with a .mdf file and nothing happened. Any ideas?

if it's wrong, we should post somewhere for the documentation editors to correct it

---

### Post by cariboo on 2008-07-01
It's not wrong, you're supposed to convert the image to an iso. You could try to mount your .mdf using the following command:

```
sudo mount -o loop <name>.mdf /mnt
```

The mounted image will not show up on your desktop so you will have to nvaigate to /mnt either in a terminal or your favourite file manager.

Jim

---

### Post by bulletxt on 2008-07-01
AcetoneISO2 mount most common images (iso,mdf,nrg,bin,img) and you can also convert them to iso.

---

### Post by eotakos on 2008-07-03
> cariboo907 wrote:
It's not wrong, you're supposed to convert the image to an iso. You could try to mount your .mdf using the following command:

i tried that but it asks me to specify file system type. i guess this is because the cd-image is made of a cd with data AND audio. (and actually this is why i'm trying to mount .mdf image - if i convert it to .iso i loose the audio part of the cd and it becomes only data)


and something else:
> bulletxt wrote:	
AcetoneISO2 mount most common images (iso,mdf,nrg,bin,img) and you can also convert them to iso. 

does it work for .cue too? 

I'm interested in somehow mounting the cd and maintaining it's property to be both audio and data is it possible?

in order not to leave any questionmarks i'll explain myself. i love warcraft II the game :-)  and  while playing the game you listen to the audio-cd tracks. if the cd is mounted like data-only the audio you listen is simple midi sounds

there you go! i've said it! :-)

---

### Post by bulletxt on 2008-07-03
the only way to do that is to use cdemu 1.1 . but it's not very easy to make it work. I suggest to try AcetoneISO2 and see what happens, if it doesn't do the job try cdemu.

---

### Post by eotakos on 2008-07-03
thanks for the reply

---

