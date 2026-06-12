---
title: "Ubuntu 18.10 won;t boot after NVIDIA driver installation."
date: 2019-01-03
forum: New to Ubuntu
---

### Post by alexrivus on 2019-01-03
I've installed the recommended 390 driver (and also tried the same with 340, and 410) and got this when trying to boot:

[ATTACH=CONFIG]282088[/ATTACH]



So my Ubuntu doesn't boot, I managed to delete the driver and it works with open source one, but how can I get the Nvidia driver, why is it damaging my system if it's "recommended" and also I've seen A LOT of issues like mine on forums(like from 14.04 to nowadays) so is Ubuntu team even working on fixing it?


My specs:

CPU Phenom II 4x 955

GPU GeForce GTX 650

8 Gigs of RAM

Ubuntu 18.10 64-bit

---

### Post by QIII on 2019-01-03
Hello!

Hopefully someone will be along to help you shortly.  But just to dispel what appears to be a misconception you harbor:  Canonical does not write the NVIDIA Linux driver(s).  NVIDIA does.  Driver failure is on NVIDIA and there is nothing at all Canonical, or any other purveyor of Linux distributions, can do.

If you would, please don't post such large images.  Even in these days of immensely fast internet, some of our users are on slow connections or have data limits.  Please use the attachment facility (the paperclip button in the tool bars above the text entry box) to insert an expandable thumbnail and let other users decide if they want to view the image full sized.

Cheers!

---

### Post by alexrivus on 2019-01-03
Hello! Thanks for info about nvidia, and sorry for posting that big of a picture :)

---

### Post by Autodave on 2019-01-03
As QIII said, hopefully someone will ba able to help you.  What card to you have in your machine?

I have 4 machines running 4 different Nvidia cards: one very old card, 2 that are a few years old, and one rather new one.  I have never had a problem with any of them.  Did you do a clean install of 18.10 or did you upgrade from an older release?

---

### Post by alexrivus on 2019-01-03
I totally forgot to specify it. GeForce GTX 650

---

### Post by NM5TF on 2019-01-04
please post the output of...

```
inxi -G
```

.please use code tags for your response to make it more readable...


tommy

---

### Post by oldrocker99 on 2019-01-05
How did you install the driver? From the PPA, or the download from nVidia's site? To enable the PPA:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-graphics-drivers-415
```

This will install the latest nVidia drivers.

---

### Post by alexrivus on 2019-01-05
It got me the same result :(

---

### Post by alexrivus on 2019-01-05
Not quite sure what do you mean.

---

### Post by NM5TF on 2019-01-06
> **alexrivus said:**
> Not quite sure what do you mean.

and we are not quite sure who you are responding to...

---

### Post by oldrocker99 on 2019-01-06
> **alexrivus said:**
> It got me the same result :(

*What* got you the same result? When you use pronouns without definite antecedents, it's difficult to know what you mean.

---

### Post by alexrivus on 2019-01-07
> **NM5TF said:**
> please post the output of...

```
inxi -G
```

.please use code tags for your response to make it more readable...


tommy

I'm not sure how to do that. Could you help me with it?

---

### Post by alexrivus on 2019-01-07
> **oldrocker99 said:**
> *What* got you the same result? When you use pronouns without definite antecedents, it's difficult to know what you mean.


The installation of the 415 through terminal got me the same result.
[COLOR=#000000]
Code:[/COLOR]
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-graphics-drivers-415

---

### Post by NM5TF on 2019-01-07
> **alexrivus said:**
> I'm not sure how to do that. Could you help me with it?

of course we can help....

open a terminal and type

```
inxi -G
``` 

post your results using [COLOR="#FF0000"]code tags[/COLOR] to make the result more readable....use the [COLOR="#FF0000"]adv reply button[/COLOR]...
select the [COLOR="#FF0000"]#[/COLOR] character to open code tags and [COLOR="#FF0000"]paste your results between the # characters.[/COLOR]...

welcome to the world of Linux...

tommy

---

### Post by alexrivus on 2019-01-10
Sorry for taking so long, I've been away from home. Here's the "[COLOR=#000000][FONT=&quot]inxi -G" result.
[/FONT][/COLOR]
```
Graphics:
Device-1: NVIDIA GK107 [GeForce GTX 650] driver: nouveau v: kernel 
Display: x11 server: X.Org 1.20.1 driver: nouveau 
resolution: 1600x900~60Hz 
OpenGL: renderer: NVE7 v: 4.3 Mesa 18.2.2
```

---

### Post by NM5TF on 2019-01-10
> **alexrivus said:**
> Sorry for taking so long, I've been away from home. Here's the "[COLOR=#000000][FONT=&quot]inxi -G" result.
[/FONT][/COLOR]
```
Graphics:
Device-1: NVIDIA GK107 [GeForce GTX 650] driver: nouveau v: kernel 
Display: x11 server: X.Org 1.20.1 driver: nouveau 
resolution: 1600x900~60Hz 
OpenGL: renderer: NVE7 v: 4.3 Mesa 18.2.2
```

the very 1st thing I notice is that the OS is using the open source NOUVEAU driver rather than the
nvidia driver that you think was installed.....you might want to try re-installing the correct nvidia
390 driver....

there is/was a bug reported about this very problem...the bug is now closed for some reason.....
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053)

I found this searching through the bug report....I have not tried this myself, but numerous people
report it "fixed" the problem......try it and see if it will work for you.....

```
Please try, in the /etc/gdm3/custom.conf, uncomment WaylandEnable=false and Nvidia driver will work with gdm3.
```

let us  know if it works...

tommy

---

### Post by alexrivus on 2019-01-10
Ok.Didn't help. I don't have the time for this stuff, and if Ubuntu ever becomes an OS where everything is easy as it is on Windows, I will check it out again. Thank you for your help and your time.

---

### Post by oldrocker99 on 2019-01-11
That's a shame. You were on the way to solving your problem. Good luck with Windows.

---

### Post by alexrivus on 2019-01-18
Hello again. I've put my drive into another PC with GTX660, I7 3770 and reinstall Nvidia drivers and got the same results :(

---

### Post by alexrivus on 2019-01-18
May it be caused my GNOME? Should I try another "Flavor" of Ubuntu?

---

