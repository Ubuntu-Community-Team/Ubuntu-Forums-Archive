---
title: "Screen deformed"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-10-12
Bs'd

I have a laptop, and I installed ubuntu on it.  But the picture I get, is distorted.  
My screen of the laptop is not square, but much wider then it is high.  So now, if I see a square chess board, it is not square, but much wider than it is high.  

How can I solve that?

Thanks in advance.

Carni

---

### Post by Bobbino on 2008-10-12
It sounds like to me you need to modify your screen resolution.. If you go the System > Prefereces > Screen Resolution you should be able to do it in there. If you're have a widescreen screen, you'll want something like a 1280x800 resolution (or similar depending on the dimensions of your screen.)

---

### Post by Carnivorum on 2008-10-12
Bs'd

When I go to screen resolutions, i can only chose from 2 options, 800 x 600, and 640 x 480 

Is there anything I can do about that?


Carni

---

### Post by Bobbino on 2008-10-12
I'm guessing you'll need to install the driver for your GFX card to get additional resolutions. I needed to do that for my PC before i could set the resolution for my widescreen monitor.

Sadly.. My knowledge is going to start to wane here... But do you have a standard type onboard GFX with you laptop? Or is it something fancy like a Nvidia card etc?

---

### Post by Gutt on 2008-10-12
Did you install your graphics card's drivers ? If you haven't then do so, that usually fixes the resolution problem.

---

### Post by Carnivorum on 2008-10-12
Bs'd

I didn't install any drivers for my screen.  But I don't have the slightest idea what screen I have.  How can i find out?

Carni

---

### Post by Gutt on 2008-10-12
> **Carnivorum said:**
> Bs'd

I didn't install any drivers for my screen.  But I don't have the slightest idea what screen I have.  How can i find out?

Carni

Don't look for drivers for your screen but for your graphics card. Do you know what model you have ? ATI, Nvidia, Intel ?

---

### Post by patrickballeux on 2008-10-12
What is your laptop brand?  

Enter that command "lspci" so we can find out what is your graphic card on that laptop...

Then, we will know what driver to use and fix your resolution problem.

---

### Post by Carnivorum on 2008-10-12
Bs'd

I have a Fujitsu Siemens.  And where do I enter that command Ispci?

---

### Post by scratman on 2008-10-12
Go to Applications >Accessories > Terminal

then type lspci, press <enter> and post the result

---

### Post by Carnivorum on 2008-10-12
Bs'd

This is my card:  VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by Carnivorum on 2008-10-12
Bs'd

Where can i find the drivers for that card?

Carni

---

### Post by Carnivorum on 2008-11-01
Bs'd

Is there a way to change the screen resolution in the terminal?

Which command do use for that?

Carni

---

### Post by Carnivorum on 2008-11-02
Bs'd

I changed my screen resolution, and everything became a lot bigger, and therefore I can't click on the button anymore to make the resolution normal, the button is out of my screen. 

So I must change it in the terminal.  

Help would be greatly appreciated. 


Carni

---

