---
title: "HP Webcam help 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by twang103 on 2008-04-29
I just upgraded to hardy 8.04 from 7.10. Now my webcam in my HP Pavilion dv6000 will not work. 
It worked fine in 7.10, but if i start cheese in 8.04, no image is shown, just coloured boxes. I tried ekiga aswell but it wouldnt recognise it. 
Also the blue light next to the built in camera used to only be on when the camera was being used in 7.10, now it is constantly on...

I have read that the drivers should be generic for 8.04, but it just doesnt work.

Please help,

---

### Post by tliotis on 2008-04-29
try to go to the support site of hp and download drivers for your laptop , or reinstall them.one friend had the same problem with toshiba and he reinstall and working good
hope to help you! :)

---

### Post by twang103 on 2008-04-30
They only offer support and drivers for windows versions

---

### Post by immukesh on 2008-04-30
First Post.. hopefully not breaking any forum rules..

My HP dv 9207 webcam doesnt work either. Any suggestions how to fix that?

using ubuntu 8.4.. cheese and stuff doesnt work. Blue light doesn't ever switch on in ubuntu..

---

### Post by immukesh on 2008-04-30
[http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation)

Followed the instructions on there , installed the driver after compiling from source.and the cam did work with kopete and not cheese.. Will see and try to make it work later.. 

Again this works for HP9207 

it claims to work with HP 1000 series and sony vaio as well..

All the best!

let me know if anyone has any tips on cheese and ekiga..

---

### Post by hermes0710 on 2008-04-30
Can you post the output of lsusb?

```
sudo lsusb
```

I have an hp (see my signature) and i installed the correct drivers from mediati and it worked (I had them compiled).

---

### Post by twang103 on 2008-04-30
Thanks for the help everyone, I found out the problem. As I said, the blue light was always on, so i figured the drivers were ok. 
However, I found a bunch of photos of me in the tmp directory, apparently, when I upgraded to 8.04, the program 'motion' was installed, and it was automatically set to start when the computer starts.
This program took a photo of me every time it detected movement, which is why I could not use cheese or any other program (cos webcam was in use).

After uninstalling 'motion' everything works!!! and I also have a collection of photos of myself trying to fix this problem as a memento...

---

### Post by hermes0710 on 2008-04-30
> I also have a collection of photos of myself trying to fix this problem as a memento...

:lolflag:

---

