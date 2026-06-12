---
title: "VLC Refuses to play DVD"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Old-un on 2012-07-01
Have been trying to play a DVD video using VLC media Player but for some reason unknown to myself VLC refuses to play the DVD.

I am running Ubuntu 12.04 which is fully updated

Thanks

---

### Post by insane_alien on 2012-07-01
have you installed libdvdcss? this is required to decrypt DVD's and doesn't come installed by default.

---

### Post by kellemes on 2012-07-01
Any feedback from vlc?

---

### Post by sudodus on 2012-07-01
Is it one particular DVD disk, or DVDs in general?

Have you done what is suggested in for example this link?
[[COLOR="Red"]_https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/_[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/")

---

### Post by Old-un on 2012-07-01
When i try to play the dvd in VLC media player the title of the film on the dvd flashes up on the screen but that's it?

I did try to install 'libdvdcss' via a terminal using: sudo apt-get install libdvdcss but got back an error message stating:

Error: Package 'libdvdcss' has no installation candidate?

---

### Post by howefield on 2012-07-01
Believe it is libdvdcss2.

Can be downloaded form medibuntu.org

---

### Post by Old-un on 2012-07-01
Have added the medibuntu repository to Ubuntu so where do i go from here? Have tried to find libdvdcss2 from the software center but no luck so far?

---

### Post by howefield on 2012-07-01
```
sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

If no joy, you can always download the deb package from the medibuntu site and double click to install.

---

### Post by Old-un on 2012-07-01
That worked perfect howefield. Many thanks

---

