---
title: "HOWTO: Install GnoCHM (CHM Viewer) on Ubuntu 5.04"
date: 2005-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by vibranze on 2005-05-28
1. Download the debian packages from [http://www.linuxfans.org/nuke/modules.php?name=Site_Downloads&op=geninfo&did=3342](http://www.linuxfans.org/nuke/modules.php?name=Site_Downloads&op=geninfo&did=3342)
2. Do a tar jxcpf gnochm.tar.bz2
3. Do a dpkg -i *.deb
4. Enjoy the CHM Viewer under Applications - Accessories

Hope this howto is useful to all you guys. :) 

Regards,
Vibranze

---

### Post by peluchio on 2005-06-02
Thanks, I was breaking my head over that  one since tuesday. 
 :)

---

### Post by bored2k on 2005-06-02
[QUOTE=peluchio]Thanks, I was breaking my head over that  one since tuesday. 
 :)[/QUOTE]
 What's wrong with sudo apt-get install xchm ? This is really not the "Ubuntu" way to do it, as you are using Debian's own, wich might or might not work.

---

### Post by sn0n on 2005-08-22
revive.. and .. thank you..

---

### Post by sn0n on 2005-08-22
sry for the double post, but, it appears that this package dont actually work.. i believe its a proglem with 

gnome-python2-gtkhtml2

running a sample browser script

rob@sn0nsb0x:~$ python /usr/share/doc/python2.4-gnome2-extras/examples/gtkhtml2/simple-browser.py

i get many errors, and it wont work.. 

/me shrugs

was worth the try anyways.. back to xchm  :-(

---

### Post by Belutz on 2005-08-25
I've been looking for this :)
for me gnochm is much more better than xchm.
maybe gnochm must be included in the next release of ubuntu :D

---

### Post by aledie on 2005-08-29
[QUOTE=sn0n]sry for the double post, but, it appears that this package dont actually work.. i believe its a proglem with 
.....
was worth the try anyways.. back to xchm  :-([/QUOTE]

Try it again, after installation of the two .deb contained in the tarball you need to open synaptic. 
You will get a message "2 broken packages". You do following:

1. Edit-->Fix broken packages
2. You get a message "successfully fixed dependency problems"
3. Click "Apply" - synaptic will install libgtkhtml2-0 and its dependant packages for you

Now gnochm will work for you :) . It is definitely better than xchm, i use it for months.

---

### Post by makushimu on 2005-10-06
thanks so much for the info!

---

### Post by grizzly on 2005-11-08
I am getting this on tar jxcpf gnochm.tar.bz2
```
tar: You may not specify more than one `-Acdtrux' option
```

Any ideas?

---

