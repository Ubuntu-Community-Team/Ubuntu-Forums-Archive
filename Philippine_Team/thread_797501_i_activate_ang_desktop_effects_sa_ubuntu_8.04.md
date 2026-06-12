---
title: "i activate ang desktop effects sa ubuntu 8.04"
date: 2008-05-17
forum: Philippine Team
---

### Post by eryllex on 2008-05-17
hi guys... bumili aq ng new laptop,my last one was a neo and had prob with its graphic cards kya hnd q ma activate ang desktop effects. now my new one is a acer  AMD turion with NVIDIA graphics.

---

### Post by pendletone on 2008-05-17
Go to System-->Preferences-->Appearance then click on the Visual Effects tab. If it is currently set to None, tick Normal or Extra (requires faster graphics card, though).

And there you go! :)

---

### Post by eryllex on 2008-05-17
i,ve tried it alredy,but still i cannot even choose any other option than with no effects

---

### Post by pendletone on 2008-05-17
do you happen to know what nvidia chipset you're using? if not type this in the terminal:

```
lspci
```

then paste the results here.

---

### Post by yssida on 2008-05-18
Are nvidia drivers closed source? If so, it most likely isn't included with Ubuntu by default. You have to manually install it.

---

### Post by loell on 2008-05-18
also, what do you see when you go to **Systems**-->**Administration**-->**Hardware Drivers** ?

it  should look something  like this
[ATTACH]70542[/ATTACH]

---

### Post by pendletone on 2008-05-18
Just to add to what sir loell said, if you see there **Nvidia accelerated graphics driver**, you can enable it by ticking the checkbox under the Enabled column. It will download the driver for your Nvidia card and prompt you to restart your computer. That's what I did when I wanted to enable desktop effects on my system.

If you later decide that you want to disable it, you can safely uncheck it anytime. :)

---

