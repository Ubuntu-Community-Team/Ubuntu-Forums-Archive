---
title: "Is there any way to resize the dash?"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-26
Is there any workaround to change the size of the dash? 

I'm on a 23" monitor and it takes half the screen (please see screenshot). It makes no sense.

Thanks,
Effenberg

---

### Post by lucazade on 2011-09-26
p.s. hide the ip

---

### Post by effenberg0x0 on 2011-09-26
> **lucazade said:**
> p.s. hide the ip
Done, thanks :)

---

### Post by juancarlospaco on 2011-09-26
You must watch your own Screenshot, again, analyze that picture, you will find the solution right there

Its Shiny White, you can Maximize/Restore it from there...

---

### Post by effenberg0x0 on 2011-09-26
juancarlospaco => Yes, not being the idiot you expect me to be, I am aware of the maximize restore button, ie the $gsettings set com.canonical.Unity form-factor <Netbook|Desktop> method. 

However, as far as I understand, the dimensions of the dash have been hardcoded. But there's a video online since march showing a proposed dash that could have its dimensions changed as a normal window. It never made it to release.

So, what I am asking, is if anyone is aware of any workaround so far to change this.

Thanks,
Effenberg


**EDIT:** This video [http://www.youtube.com/watch?v=K0LoQFagNIM](http://www.youtube.com/watch?v=K0LoQFagNIM)
Look how the dash changes dimensions dynamically and how it has a "shiny white thing" in the lower-right corner to resize it.

---

### Post by mc4man on 2011-09-26
On this laptop (13", 1200X800) the dash was reduced considerably today with the new unity-4.18 upgrade,  More in line with unity-2d's size
(23" desktop is currently without a power supply so don't know if smaller size translates on larger displays

Edit: there is no way to resize other than the provided 2 settings in  com.canonical.Unity form-factor

---

### Post by effenberg0x0 on 2011-09-26
Hey mc4man,

Alternating between restored / maximized using Paco's white shiny thing or using...

gsettings set com.canonical.Unity form-factor Netbook
gsettings set com.canonical.Unity form-factor Desktop

... only gets me between maximized and almost half the screen on:
13" 1280x800
19" 1360x768
23" 1920x1080

I guess the proportion is the same, despite the monitor size. I'll connect the PC to a 40" TV later today and test. 
Its too big IMHO... I was hoping for some trick to play with this. I guess there's no easy way or something would have already come up.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-09-26
Just tested on a 40" LCD. The proportion is definitely always kept the same, regardless of display size - there's no maximum, minimum calculation of dimensions as it seems. 

The good thing is that people 100 meters away from the screen won't miss the huge firefox icon, in case they feel like browsing the Internet.

Regards,
Effenberg

---

### Post by chenzhiwei on 2011-09-27
> **effenberg0x0 said:**
> Is there any workaround to change the size of the dash? 

I'm on a 23" monitor and it takes half the screen (please see screenshot). It makes no sense.

Thanks,
Effenberg

top-left  :)

---

### Post by effenberg0x0 on 2011-09-27
> **chenzhiwei said:**
> top-left  :)

Sorry, didn't get it. Please add a couple more words :)

---

### Post by chenzhiwei on 2011-09-27
> **effenberg0x0 said:**
> Sorry, didn't get it. Please add a couple more words :)

top-left corner has the maximum and close button.

But I don't how to custom the dash size.

---

