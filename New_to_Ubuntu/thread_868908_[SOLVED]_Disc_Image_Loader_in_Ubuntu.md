---
title: "[SOLVED] Disc Image Loader in Ubuntu"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by benditlikebecker13 on 2008-07-24
I was wondering if there was a simple way to mount ISO image files on a virtual drive.  I tried to search for my answer but it was difficult to come by.  I just want to be to mount any ISO file I get so that I can watch it or rip/edit it without having to burn a disc.

---

### Post by Potatoj316 on 2008-07-24
I think you can use the mount command to do that but I dont know how.  This is the way I usually mout iso

go to sourceforge.net and search for vcdmount
make and install vcdmount (you will need build-essential)
in a terminal you can now type sudo vcdmount -m ISONAME to mount
and sudo vcdmount -u to unmount
you will see a vcd on your desktop, this is your mounted iso

---

### Post by Paqman on 2008-07-24
Linux can do that by default, you don't need to install anything.

If you Google you should find a million articles telling you how to do it from the command line. There's also doubtless a few packages in the repos that have a GUI.

---

### Post by benditlikebecker13 on 2008-07-24
> **Paqman said:**
> Linux can do that by default, you don't need to install anything.

If you Google you should find a million articles telling you how to do it from the command line. There's also doubtless a few packages in the repos that have a GUI.

When I search "disc image loader software in ubunutu" I get a ton of articls on how to install Ubuntu from an image, but nothing on how to mount an image.  Is there some other phrase I should put into Google?  I also tried ISO image loader and still nothing.  

If it was in Google I would've found it, or I'm clicking the wrong links.

---

### Post by Paqman on 2008-07-24
> **benditlikebecker13 said:**
> Is there some other phrase I should put into Google?

I'd use "iso mount linux".

Take a look in Synaptic though. Something like gisomount might sort you out instead of faffing around with the command line.

---

### Post by hyper_ch on 2008-07-24
```

sudo mount -o loop -t iso9660 imgage.iso /path/to/mount/point

```

---

### Post by jimmywu013 on 2008-07-24
EDIT:  oops - didn't see hyper_ch's post.  sorry

> **benditlikebecker13 said:**
> I was wondering if there was a simple way to mount ISO image files on a virtual drive.  I tried to search for my answer but it was difficult to come by.  I just want to be to mount any ISO file I get so that I can watch it or rip/edit it without having to burn a disc.
```
sudo mount -o loop *filename*.iso /mount/point
```
should do it, where *filename.iso* is the path to the iso file you want to mount and /mount/point is the path to a (preferably empty) directory you want the iso to be mounted to

Once you do that, all the contents of the iso will be accessible from whatever you chose as /mount/point

HTH,
Jimmy

---

### Post by Potatoj316 on 2008-07-24
yup what hyper_ch and jimmywu013 said.  i thought mount could do it

---

### Post by benditlikebecker13 on 2008-07-24
> **Potatoj316 said:**
> yup what hyper_ch and jimmywu013 said.  i thought mount could do it

Thanks guys.  I did a search on gISOmount and got a list of similar programs, so I think I will try that first.

[http://packages.ubuntu.com/feisty/gnome/gisomount](http://packages.ubuntu.com/feisty/gnome/gisomount)

And if nothing there works like I want it to, maybe i'll work up the courage to us the CLI.

---

### Post by aeiah on 2008-07-24
although this isnt specifically what you asked for, a lot of media players in ubuntu will be able to play a dvd.iso without the need to mount it. im pretty sure mplayer and vlc do anyway. i find this more convenient for dvd images but obviously its impractical for anything else.

---

