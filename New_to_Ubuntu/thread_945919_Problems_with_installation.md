---
title: "Problems with installation"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by swampdude on 2008-10-12
Hi, i newish to ubuntu. I used to have ubuntu before, then used windows, and now windows is boring me i want ubuntu back. The problem im having is when i go to install ubuntu the loading bar works, but after that i get a bouncing message saying input not supported. 

Well i bought a new computer since i last had ubuntu. I know its not the monitor or ubuntu as they both worked on my last computer(i think).

So it is either my graphics card or my data transfer switch. 

My graphics card in a Nvidia 6 series 256mb.
Ram:2 gb
cpu: amd athalon 3700+(i think)

I think it would work once i got the drivers installed but i cant even install ubuntu lol.

If anyone has any idea i thank you now.

---

### Post by dhtseany on 2008-10-12
What is the make and model of the new computer?

Peace
Sean

---

### Post by swampdude on 2008-10-12
It doesnt have one its custom built

---

### Post by swampdude on 2008-10-12
my graphics card shud be able to go to 640x480 resolution which is the minimum requirements. 

Also whats a 64-bit pc?

---

### Post by linux4life88 on 2008-10-12
> **swampdude said:**
> my graphics card shud be able to go to 640x480 resolution which is the minimum requirements. 

Also whats a 64-bit pc?

If it is a newer pc then it is most likely 64 bit. Check this out:

[http://en.wikipedia.org/wiki/64_bit](http://en.wikipedia.org/wiki/64_bit)

---

### Post by jemate18 on 2008-10-12
> **swampdude said:**
> Hi, i newish to ubuntu. I used to have ubuntu before, then used windows, and now windows is boring me i want ubuntu back. The problem im having is when i go to install ubuntu the loading bar works, but after that i get a bouncing message saying input not supported. 

Well i bought a new computer since i last had ubuntu. I know its not the monitor or ubuntu as they both worked on my last computer(i think).

So it is either my graphics card or my data transfer switch. 

My graphics card in a Nvidia 6 series 256mb.
Ram:2 gb
cpu: amd athalon 3700+(i think)

I think it would work once i got the drivers installed but i cant even install ubuntu lol.

If anyone has any idea i thank you now.

Did you tried other LiveCD or installer?

---

### Post by bodhi.zazen on 2008-10-12
Try booting the cd in safe graphics mode

It that fails try installing with the alternate CD.

Post install you will need to install the nvidia drivers. You can either go open source 

```
sudo apt-get install nvidia-glx-new nvidia-settings
```

or the nvidia drivers. If you go the second route take a look at envy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by swampdude on 2008-10-13
fixed pressed F4 when it asked me to install or check bad memory etc, and then hit the graphics option thing and worked.

---

