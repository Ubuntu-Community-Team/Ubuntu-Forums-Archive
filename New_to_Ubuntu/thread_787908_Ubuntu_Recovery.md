---
title: "Ubuntu Recovery"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-09
From a previous problem seemingly caused by an interruption to a package update
I am told that :

Gzip: /var/log/dmesg.0.gz: No space left on device
Mv: cannot stat `/var/log/ /dmesg.0.gz`: No such file or directory
root@bernard-desktop: ~# Bernard

Ubuntu 7.10 is the only OS I have on my computer so there should be no problem with space.

I can restart my computer and by pressing Esc get into the 3 options i.e.
Generic, recovery mode & memtest86+
Running in recovery mode gives me the above mentioned problem.

Is there any way I can recover & get back into Ubuntu 7.10??

Thanks


Bernard

---

### Post by Joeb454 on 2008-05-09
Ok if you're running from the Recovery Mode, can you try running ```
dpkg configure -a
```

---

### Post by bumanie on 2008-05-09
If you have a separate / and /home it is possible that / is getting full. It depends on how your system is set up and how much space / has allocated to it. If / and /home share the same partition, I have no answer at this stage.

---

### Post by bern1939 on 2008-05-09
In recovery mode and at root@bernard-desktop: ~# I ran dpkg configure -a and got:
Options marked * produce a lot of output - pipe it through `less' or `more'

??

Bernard

---

### Post by bern1939 on 2008-05-09
Ok got back in and looked at the Patitions.

/dev/sda1  ext3  /  size:43.70GiB     Used:43.70Gib

Where do I go to get rid of 'whatever' to free up the space??

Thanks


Bernard

---

### Post by bumanie on 2008-05-09
To increase the partition size you will have to use gparted live cd or live usb. You will not be able to use the ubuntu partition editor, because to change aprtitions with it the drive/partition must be unmounted. Get it [here]("http://gparted.sourceforge.net/download.php") It has a clear gui and has sliders etc. that you can use to increase your partition size with.

---

### Post by bern1939 on 2008-05-09
Thanks indeed....is there a way that I can delete unwanted programmes to retrieve some space?
Cannot get into Synaptic due to previous download problem.


Bernard

---

### Post by Joeb454 on 2008-05-09
```
sudo aptitude remove <packagename>
```

---

### Post by bumanie on 2008-05-09
As long as you can get into terminal, I guess so. As you partition is full, I'm not 100% sure. If it had a little space I'd be more confident. You would have to know what you want to get rid of though, because it won't be retrievable.

---

### Post by bern1939 on 2008-05-09
Thanks so much .....but when I try that in a terminal I am again told to manually run `dpkg --configure -a' to correct the problem.
When I do that as a superuser I get:
failed to write status record about `libacl1' to /var/lib/dpkg/status: no
space left on device.

Seem to be going around in circles ????

Bernard

---

### Post by bumanie on 2008-05-09
That was my concern that you had no space at all left, because to remove something there are processes that occur that require space to complete the removal. Do you have another hard drive either internal or external?

---

### Post by bern1939 on 2008-05-09
> **bumanie said:**
> That was my concern that you had no space at all left, because to remove something there are processes that occur that require space to complete the removal. Do you have another hard drive either internal or external?

I am afraid not......does that mean I have to re-install??
No other way of taking progs. installed via Synaptic off?

Bernard

---

