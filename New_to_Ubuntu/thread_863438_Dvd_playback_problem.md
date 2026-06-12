---
title: "Dvd playback problem"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by arkark07 on 2008-07-18
I apolygise if this is a simple solution in one of the posts, but I looked and was a bit overwhelmed.

I followed the instructions to install libdvdcss2

[http://ubuntuforums.org/showthread.php?t=855953&highlight=libdvdcss2](http://ubuntuforums.org/showthread.php?t=855953&highlight=libdvdcss2)

and now my dvd's do play etc they play in like negative that is all the colours are like blue or orange.
Same on both gxine and Totem.

Any ideas?

Thanks

---

### Post by bumanie on 2008-07-18
Go to the [medibuntu site]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions there. It was down a day or two ago but it's up and running again. Make sure to add the repository before going further.

---

### Post by joshsmith on 2008-07-18
you could try running
gstreamer-properties
in the terminal

then go onto video tab, and in default output, try changing the plugin. click ok and try playing the dvd again

---

### Post by LowSky on 2008-07-18
use the info on this page. Make sure to use the correct code for your version

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

assuming your using 8.04 32bit processor version follow these instuctions, enter each into a terminal window
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
```
sudo apt-get install w32codecs
```

---

### Post by ayenack on 2008-07-18
Try this. This should install all you need plus lots of other useful stuff. It's not open source though.

1, Open Add/remove (Applications>Add/Remove.)
2, At top of window click on all available applications in the drop down menu.
3, Type ubuntu restricted extras in search.
4, Click on ubuntu restricted extras.
5, Apply Changes.

Tha should do it.

---

### Post by t0p on 2008-07-18
> **ayenack said:**
> Try this. This should install all you need plus lots of other useful stuff. It's not open source though.

1, Open Add/remove (Applications>Add/Remove.)
2, At top of window click on all available applications in the drop down menu.
3, Type ubuntu restricted extras in search.
4, Click on ubuntu restricted extras.
5, Apply Changes.

Tha should do it.

Hi ayenack, I thought I'd best point out that ubuntu-restricted-extras doesn't include libdvdcss2, which is what people need to watch encrypted dvd.  It's necessary to get libdvdcss2 from the medibuntu repo.

---

### Post by sneeks on 2008-07-18
as above ,you will have to install the packages via synaptic package manager,i also installed the extra g streamer plugins from the repo's.

---

### Post by SunnyRabbiera on 2008-07-18
Unless its a video card issue...

---

### Post by nikgare on 2008-07-19
If you are using Totem, you can just change the hue/saturation settings to get the correct looking picture

---

