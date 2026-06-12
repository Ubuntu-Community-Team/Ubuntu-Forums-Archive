---
title: "Intel 82852/82855GM/GME Problems"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by bipolaric on 2012-10-15
Hi everyone, I have just installed Ubuntu 10.10 on an old laptop, as I don't like unity and maverick looks pretty good to me.  But when I go into System/Preferences/Appearance/Visual Effects, it will not enable the extra (for wobbly windows), which I quite like.  So I want to enable this graphics chip with a better driver, but I don't know how.

I have added the ppa:glasen/intel-driver into my 'other software sources' at the required APT prompt, but I don't know what to do next.  Is there anyone out there who can help me out ?
It's an Intel 82852/82855GM/GME Onboard Graphics, if that helps.

Thanks - Mark

---

### Post by squakie on 2012-10-16
Something may have changed since the last I looked at it, but the 85x series normally hasn't supported things like the eye candy effects.  You may want to do a search in this forum with the following in the search string:
 
intel 855GM compiz
 
and see what turns up.  I might be remembering incorrectly, but I think GLX either doesn't work at all or at a very minimal state with the 85x series.
 
You can also try the following in a net search:
 
ubuntu intel 855 compiz
 
and see what you get from that as well.

---

### Post by newb85 on 2012-10-16
This is a little off-topic, but are you aware that you can get the same classic Gnome experience in 12.04 through fallback?  See these instructions.  (They're written for 11.10, but work the same for 12.04.)  [http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/]("http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/")

Running 10.10 is not a good idea, as it is no longer supported (since April 2012).  10.04 will be supported through April 2013.
12.04 will be supported through April 2017.

---

### Post by bipolaric on 2012-11-09
Thanks newb85, Sorry for the late reply, I have been ill.
Will Ubuntu 12.04 allow me to use this graphics chip ?
tbh, I only want wobbly windows and a bit of ubuntu tweak (transparency)

Thanks - Mark

---

### Post by mörgæs on 2012-11-09
Best is to begin with a fresh install of X/Lubuntu 12.04 or 12.10 and after that follow the instructions in

[http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)

---

