---
title: "945 Intel Graphics Help"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by SigmaSanti on 2008-04-30
I have a Intel mobile 945GM express graphics card on a Toshiba A105 satellite. Having just installed Hardy and being new to Ubuntu and Linux in general I downloaded several games from the repositories. I am having problems with the graphics card when running 3d games and effects. It blinks, runs slowly and acts poorly in general - even on the lowest settings. The games i am running are designed for systems half as powerful. I can't get it to stop, and have had trouble finding the correct drivers.
Help is very much appreciated and not required.

---

### Post by Tom--d on 2008-04-30
The graphics card works out of the box... I know this as I have it. 

I play games with it and it seems fine to me :) 

What games you playing?

---

### Post by SigmaSanti on 2008-04-30
A few would be nexuiz, and warzone 2100. If you don't have any problems thats great, because I have had trouble with it even on windows. It got worse on linux though.

---

### Post by dangerpl on 2008-04-30
I have the same problem with some of the games and I have the same card, Toshiba A105.

---

### Post by SigmaSanti on 2008-04-30
I brought this up because I saw several other (much older posts) with the same questions. I guess I sort of renewed it.

---

### Post by scorp123 on 2008-04-30
> **SigmaSanti said:**
> I have a Intel mobile 945GM express graphics card on a Toshiba A105 satellite. Having just installed Hardy and being new to Ubuntu and Linux in general I downloaded several games from the repositories. I am having problems with the graphics card when running 3d games and effects. It blinks, runs slowly and acts poorly in general Intel cards are not really up to the job for 3D shooters. Especially if you're running 3D effects on your desktop. Different than graphics card with dedicated memory (e.g. Nvidia) most Intel cards in most laptops have to use shared memory from the system's main RAM ... and that's bound to be slower than having dedicated RAM. So the performance will always be rather poor.

If you want a laptop with decent gaming performance (especially for 3D shooters) you'd have to buy one with a Nvidia 8600M or 8800M chip.

---

### Post by SigmaSanti on 2008-04-30
> **scorp123 said:**
> Intel cards are not really up to the job for 3D shooters. Especially if you're running 3D effects on your desktop. Different than graphics card with dedicated memory (e.g. Nvidia) most Intel cards in most laptops have to use shared memory from the system's main RAM ... and that's bound to be slower than having dedicated RAM. So the performance will always be rather poor.

If you want a laptop with decent gaming performance (especially for 3D shooters) you'd have to buy one with a Nvidia 8600M or 8800M chip.

So the problem is just that its an intel graphics card? and AVI or Nvidia will solve the problem? Thanks, I was hoping that it might be an outdated driver or something, but if its the physical components then i'll just buy a real graphics card next time.

---

### Post by st33med on 2008-04-30
> **SigmaSanti said:**
> So the problem is just that its an intel graphics card? and AVI or Nvidia will solve the problem? Thanks, I was hoping that it might be an outdated driver or something, but if its the physical components then i'll just buy a real graphics card next time.

Also, you can't replace the integrated card with another graphics card. In order to get rid of the curse of the integrated card, you need another motherboard...

Kinda unfortunate, though...

---

### Post by scorp123 on 2008-04-30
> **SigmaSanti said:**
>  So the problem is just that its an intel graphics card?  Take a look here:
[http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html](http://www.notebookcheck.net/Mobile-Graphics-Cards-Benchmark-List.844.0.html)

See who's top on that list? Nvidia. Now scroll to the bottom ... You will find the "Intel X3100" on rank #83, the "Intel GMA 950" on rank #97 (of 111 total) and the "Intel GMA 900" on rank #99 (pretty much towards the very end of that list).

Also compare the numbers: e.g. Intel's 3DMark scores in comparison to the Nvidia cards higher up on the list. In simple terms: You want gaming performance on your laptop? ==> you want your laptop to have at least a Nvidia 8600 chip, or even better: 8800. Don't bother with the 6xxx lines and the 7xxx product lines: they are outdated. There are still some laptops which have those chips. Don't buy those. Never ever. I am saying this because only the newest 8xxx chips are DirectX 10-compatible hardware-wise, the 6xxx and the 7xxx product lines are not! So if you're seriously into gaming you at least want to make sure that the hardware you spend money on can do DirectX 10 (and all later versions) and that you get all the graphics effects, right? There is no point in spending money on outdated hardware, IMHO ... even though I'd have to admit that some of those 6xxx and 7xxx chips are damn fast and high up in the list .... But again: They're old ... 

Besides: In just a few months the first laptops with Nvidia's new 9xxx line of graphics chips should be shipping, which means that you will get more graphical firepower for the same money and that currently existing models with the older 8600 and 8800 chips should become cheaper.

> **SigmaSanti said:**
>  ATI or Nvidia will solve the problem?  It is my understanding that ATI chips are rather troublesome on Linux. e.g. different models of their "Radeon" product line need different drivers. And ATI drivers are said to be badly programmed, the quality of their Linux drivers is quite lacking. Just take a look here in the support forums. Nvidia seems to be less troublesome. So as Linux user you should go for a Nvidia chipset. Even though their driver is closed-source you have to give Nvidia the credit that the one single driver they produce for Linux (and which works for all card models!) is of equal quality as the one for Windows (so they don't regard Linux as being a "2nd class" OS as ATI does) and thus Nvidia cards should deliver top performance regardless if you use Linux or not. I personally like having a choice and therefore all my desktop graphics cards have always been Nvidia's ... and so far I have always been happy with this choice.

> **SigmaSanti said:**
>  Thanks, I was hoping that it might be an outdated driver or something Intel's drivers are open-sourced so given that you can safely assume that with each new release of Linux (e.g. Ubuntu 8.04) you will automatically also receive the newest of the newest Intel graphics drivers. Different than ATI or Nvidia, Intel has opened the technical specs of their graphics chips so the development of new graphics drivers for Linux doesn't depend on them.

> **SigmaSanti said:**
>  but if its the physical components then i'll just buy a real graphics card next time.  There is one reason why those Intel graphics chips are so popular in laptops: They are cheap. And they don't consume nearly as much electric power as those top-notch chips from Nvidia. So for the purposes of a laptop where battery life is important those Intel chips aren't such a bad idea. But for gaming they suck badly and it is obvious that Intel's engineers didn't have gamers in mind when they designed their chips. Hence those many oddities you see, because Intel chips are lacking many features hardware-wise, especially if you compare it side-by-side with Nvidia's top-of-the-list products.

---

### Post by SigmaSanti on 2008-05-01
Thanks, that clears a lot of things up. However when running some games such as warzone 2100 I did not have the previous problems. I have problems with the 3d graphics in windows, but not the same ones. Anyhow, thank you very much.

---

