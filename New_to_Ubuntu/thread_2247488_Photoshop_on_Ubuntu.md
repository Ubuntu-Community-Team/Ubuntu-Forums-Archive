---
title: "Photoshop on Ubuntu"
date: 2014-10-08
forum: New to Ubuntu
---

### Post by soufiane.android on 2014-10-08
how to install photoshop => ubuntu

---

### Post by mastablasta on 2014-10-08
see here: [https://appdb.winehq.org/appview.php?appId=17](https://appdb.winehq.org/appview.php?appId=17)

Anything below Gold rating is not really worth looking at.

---

### Post by Michael_McKenney on 2014-10-08
I run Adobe Photoshop on my Windows 7 workstation.  It needs a lot of resources to run properly.  I would never run it on Linux in an emulator.   I know for MAC their is Aperture, which many say is better than Photoshop.  [http://www.creativebloq.com/photoshop/alternatives-1131641](http://www.creativebloq.com/photoshop/alternatives-1131641)

---

### Post by mcduck on 2014-10-08
Wine is not an emulator, and the performance doesn't really necessarily suffer from running something through it (actually in some cases programs can even run better with Wine+Linux than natively, although that's quite rare). The actual disadvantage of Wine is that it's not perfect, some Windows system call's can't be directly translated to Linux ones, and it doesn't implement all windows features and services so not everyting works as intended (and often setting things up can require additional tweaks) and the experience might not be as smooth becuase of that.

Actually trying to *emulate* Windows would indeed be slow.

---

### Post by buzzingrobot on 2014-10-08
> **soufiane.android said:**
> how to install photoshop => ubuntu

Windows and OS X programs do not run directly on Linux, just as Linux programs do not run directly on those platforms.

As mentioned, a toolset called Wine allows some Windows programs to run on Linux, with varying degrees of success. It's a testament to Wine developers that they run at all.

Generally, it's better to consider your specific requirements and locate Linux programs that satify them, rather than trying to shoehorn Windows programs into Linux.

(Apple is curtailing work on Aperture and iPhoto; they plan to replace both with a single app next year.)

---

### Post by kodjaune on 2014-10-08
Why don't you try GIMP?

---

### Post by Impavidus on 2014-10-08
It seems some versions of photoshop work quite well on wine.

Gimp is a photoshop lookalike, running natively on Linux. According to the pros it's not as good as photoshop, but the average user won't notice. It's available from the repos an may be installed by default (on Xubuntu it is).

---

### Post by mcduck on 2014-10-08
As someone actually earning my living working with graphics, I'd say Gimp works perfectly fine for professional use. Assuming you know what you are doing, as it doesn't have as many easy&automatic tools for various tasks so you need to know your image editing to get the same results. If you do, It'll do everything Photoshop does...

---

### Post by BBQdave on 2014-10-08
> **soufiane.android said:**
> how to install photoshop => ubuntu

This is still in beta, but Google and Adobe are working together to bring Photoshop to Chrome. Personally, I use GIMP and Scribus... but I am amazed with Google Chrome on Ubuntu Unity - and use many applications through Chrome.

So for now, I would recommend exploring FOSS, such as GIMP, Scribus, Inkscape... and soon Photoshop will be available on Chrome :)

---

### Post by andrew.46 on 2014-10-08
I would second those who advise a look at Gimp, it is much more powerful than many would give it credit for. If you are set on Photoshop though have a look at running Windows as guest in a Virtual Machine with a shared folder or three. If your machine has sufficient resources this would be a good option...

---

### Post by Mike_Walsh on 2014-10-09
> **mcduck said:**
> Wine is not an emulator, and the performance doesn't really necessarily suffer from running something through it (actually in some cases programs can even run better with Wine+Linux than natively, although that's quite rare). The actual disadvantage of Wine is that it's not perfect, some Windows system call's can't be directly translated to Linux ones, and it doesn't implement all windows features and services so not everyting works as intended (and often setting things up can require additional tweaks) and the experience might not be as smooth becuase of that.

Actually trying to *emulate* Windows would indeed be slow.

I would agree with you on this.

Unlike you, I don't earn my living working with graphics, but I HAVE had a life-long interest in graphic design. I have, for many years, used a little-known, open-source graphics program called Photoscape. I used it for a long time in Windoze XP, from which I eventually migrated back in May.

I have to confess, I have Wine installed SOLELY for the purpose of running this one program, as I have not been able to find a suitable replacement for it in the repositories. The version I use (v. 3.6.5) is the prior one to the current release, v. 3.6.7. I run it in Wine 1.72; this combination has the coveted 'platinum' rating.....and to my absolute amazement, it appears to run **better **than it EVER did under XP; proof, indeed, of what you have stated as to the 'rare' combinations that do! \\:D/

Regards,

Mike.

---

