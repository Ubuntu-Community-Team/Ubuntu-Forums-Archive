---
title: "File permissions...any permissions - for XUBUNTU"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-25
Hi,
 Maybe this was somewhere in these forums, but I couldn't find it and I'm tired of looking...

I'm trying edit the /etc/modprobe.d/alsa-base file to get my sound going. If I were in regular Ubuntu, I would do this:

```
sudo gedit /etc/modprobe.d/alsa-base
```

And that would bring up the file and I could edit it as root. But this does not work in Xubuntu for whatever reason. And Xubuntu works from Xfce, not Nautilus. So 'sudo nautilus' is a not an option. 

I tried 'sudo Xfce' but that didn't fly.

So....How can I get file permissions in Xubuntu??

I appreciate any help and apologize ahead of time for the upcoming Postscript Rant.

Many Thanks, 
Frank B.

PS THESE FACTS SHOULD BE EASIER TO FIND !! MAYBE IN THE FAQ?  ](*,)

---

### Post by icheyne on 2008-07-25
sudo mousepad /etc/modprobe.d/alsa-base
or
sudo nano /etc/modprobe.d/alsa-base

I would use nano if you can - [http://www.google.co.uk/search?q=nano+tutorial](http://www.google.co.uk/search?q=nano+tutorial)

---

### Post by koji042 on 2008-07-25
The file manager for Xfce is called Thunar and is the equivalent of Nautilus, so you could just type "sudo thunar" in the Terminal and work from there. Also, gedit doesn't come installed with Xubuntu since it uses GNOME libraries, so that would explain why "sudo gedit ..." doesn't work. 

Hope that helps. :)

---

### Post by Brightbelt on 2008-07-25
Many Thanks to both of you.:) It's amazing how much searching I did and I found nothing even similar to your suggestions. 
 
(Hence my rant. Oh, well.) 
Many Thanks, Frank B.

---

