---
title: "React OS:Here comes the Windows Nemesis!"
date: 2007-08-21
forum: Other OS Talk
---

### Post by Dark Star on 2007-08-21
[IMG]http://www.imgx.org/pfiles/972/images.jpeg[/IMG]ReactOS is a free and open-sourced operating system based on the Windows architecture, providing support for existing applications and drivers, and an alternative to the current dominant consumer operating system.

 ReactOS 0.3.1 Mainly, the work focused on rewriting certain parts of the ReactOS Core (kernel, HAL, bootloader, etc). It’s very hard to sum up the huge [[COLOR=#800080]Changelog[/COLOR]]("http://www.reactos.org/wiki/index.php/ChangeLog-0.3.1") in an outline, but briefly:
 
 [LIST]
[*]Freeldr was improved
[*]HAL’s key areas have been significantly improved (irql-related, bus support, kd-functions)
[*]The Kernel experienced a massive rewrite of incompatible parts (and is still in the process of improvement)
[*]Run-time library (Rtl) got a lot of improvements and bugfixes
[*]Bugs were fixed in kernel-mode drivers and a better USB driver was added
[*]Registry-support has been greatly improved thanks to addition of “cmlib”, a library shared by the boot loader and the kernel to handle binary registry hives; it even supports binary registry hives created by Windows
[*]More fixes in the Win32 subsystem and user-mode DLLs
[*]Boot video driver (and a splash screen) was added[/LIST] Read through the changelog, and you will see the amount of changes in this release!
However, there are a few things worth mentioning. First of all, please don’t forget this is an alpha-stage operating system, which means it is not suitable to replace your main OS (due to stability and compatibility concerns). And second, this release is aimed to be run mostly in virtualizers / emulators (like QEmu, VMWare, Parallels, etc): because of the big amount of changes, our development team was not able to test/fix all problems which arise when running ReactOS on real hardware.
 [CENTER][[IMG]http://forums.erodov.com/imagehosting/thum_59464342f9d3f65.jpg[/IMG]]("http://forums.erodov.com/vbimghost.php?do=displayimg&imgid=320")[/CENTER]

 [LEFT][COLOR=#ff0000]**Note:**[/COLOR] This project is still in Alpha state .. But has shown massive improvements which is a good point.[/LEFT]
 [B]Download: [React OS]("http://www.reactos.org/en/download.html")
More Screen Shots: [Click Here]("http://www.reactos.org/en/screenshots.html")[/B]
****
Source : [http://tuxenclave.wordpress.com/2007/07/17/react-oshere-comes-the-windows-nemesis/](http://tuxenclave.wordpress.com/2007/07/17/react-oshere-comes-the-windows-nemesis/)

---

### Post by LaRoza on 2007-08-21
Just Downloaded :D

---

### Post by jrusso2 on 2007-08-21
By the time ReactOS is finished Windows will be a totally different thing.

---

### Post by igknighted on 2007-08-21
> **jrusso2 said:**
> By the time ReactOS is finished Windows will be a totally different thing.

True, but then again think of the scale of the project they are undertaking... reimplementing the entire windows OS is no easy task.

---

### Post by Dark Star on 2007-08-21
> **LaRoza said:**
> Just Downloaded :D
Do post your views with screen shot .. or a short review would do gr8 :)

---

### Post by LaRoza on 2007-08-21
> **Dark Star said:**
> Do post your views with screen shot .. or a short review would do gr8 :)

Will do soon (tomorrow), in school now.

---

### Post by FuturePilot on 2007-08-21
This project is still alive? The last time I check it was nearly dead. Anyway, maybe I'll give it a try.

---

### Post by kellemes on 2007-08-21
> **jrusso2 said:**
> By the time ReactOS is finished Windows will be a totally different thing.

Good point..
I don't see ReactOS as a serious alternative for Windows or GNU/Linux for that matter.
It seems to be aiming for "the next best thing". Not good enough for me..

---

### Post by tico on 2007-08-21
I thinks this project is more than 10 years old!! And it's still in alpha stage?! Is this really useful? When it will be a stable OS?

---

### Post by angryfirelord on 2007-08-21
[http://www.reactos.org/en/about_roadmap.html]("http://www.reactos.org/en/about_roadmap.html")

---

### Post by smiggs on 2007-08-21
> **jrusso2 said:**
> By the time ReactOS is finished Windows will be a totally different thing.

That doesn't matter, ReactOS will excellent for using a Windows compatible OS on older hardware especially as Microsoft often like to discontinue their support for older versions of their hardware. Like it or not Windows has been a crucial part of the IT world for the better part of two decades so people do need compatibility and often WINE is not the best option.

Eventually of course React OS may move away for just shadowing the functionality of Windows and become it's own OS just as Linux has moved on from simply being a UNIX clone.

---

### Post by init1 on 2007-08-21
There are many threads like this. Reactos is very unstable and does not run on my machine. The live CD hangs, and the installer does not recognize my HD.

---

### Post by LaRoza on 2007-08-21
> **init1 said:**
>  The live CD hangs, and the installer does not recognize my HD.

First time I used it, it did too, try it in a VM, I used VirtualBox.

---

### Post by happysmileman on 2007-08-21
> **igknighted said:**
> True, but then again think of the scale of the project they are undertaking... reimplementing the entire windows OS is no easy task.

Yeah... First they have to completely forget how to program :P

---

### Post by init1 on 2007-08-21
> **LaRoza said:**
> First time I used it, it did too, try it in a VM, I used VirtualBox.
I ran it in Qemu. I got a BSOD. But I downloaded the newer version, which works on my computer. So I guess I spoke too soon. I am downloading the installer now.

---

### Post by aysiu on 2007-08-21
ReactOS isn't usable.

---

### Post by cookies on 2007-08-21
> **tico said:**
> I thinks this project is more than 10 years old!! And it's still in alpha stage?! Is this really useful? When it will be a stable OS?

Wine is still in beta, after all. 

ReactOS, hrrm, I really wanna see what happens with this.

---

### Post by Dark Star on 2007-08-21
> **angryfirelord said:**
> [http://www.reactos.org/en/about_roadmap.html]("http://www.reactos.org/en/about_roadmap.html")
Awesome so Beta ver. in 08 :D Awesome liiink :D

---

### Post by LaRoza on 2007-08-22
ReactOS:

* No hard drive detected (Sata), couldn't install
* In VirtualBox, hung on blue.sys, live cd worked.

---

### Post by init1 on 2007-08-22
> **LaRoza said:**
> ReactOS:

* No hard drive detected (Sata), couldn't install
* In VirtualBox, hung on blue.sys, live cd worked.
Same here. I have Sata, so that probably why the installer never works.

---

### Post by Fonon on 2007-08-22
From the look of the one screenshot I saw, it appears your copying Windows GUI.  Now, I don't know much about stuff like copyright infingement or anything, and I only saw one screenshot, though I will see some more.  However, it appears like Microsoft can sue you pretty easily once it goes public.

---

### Post by smartboyathome on 2007-08-22
> **jrusso2 said:**
> By the time ReactOS is finished Windows will be a totally different thing.

Even IF it is different, it will probably be GUI and Graphical Interface tweaks (ie: XP, Vista). If this still holds true, then it will be VERY easy to update ReactOS - it may even turn into something like Linux did (developed indipendantly) as well as keeping its own development going.

---

### Post by LaRoza on 2007-08-23
> **Fonon said:**
>  However, it appears like Microsoft can sue you pretty easily once it goes public.

Yes, buy why would they care? Use it, it is not competing with Vista, in the normal sense.

---

### Post by Rhapsody on 2007-08-23
> **Fonon said:**
> From the look of the one screenshot I saw, it appears your copying Windows GUI.  Now, I don't know much about stuff like copyright infingement or anything, and I only saw one screenshot, though I will see some more.  However, it appears like Microsoft can sue you pretty easily once it goes public.
The ReactOS team seem fairly conscious about legal problems (the main reason behind slow development of late has been the [code audit](http://www.reactos.org/wiki/index.php/Audit), which now stands at 99.4% completion) so I doubt they'd let themselves be caught out by the most visible (pun fully intended) part of their project. They've probably made it as close to Windows as possible without infringing on any of Microsoft's copyrights.

Additionally, a stock Kubuntu install currently contains the "Redmond" window decorations and "MS Windows 9x" style. Canonical seem to have gotten away with the same stunt fairly easily it seems.

---

### Post by sdowney717 on 2007-08-25
what about the nebulous 'intellectual patent infringement' being pushed by Balmer?


if Linux qualifies, then how much more will an OS that looks like windows looks. And aims to operate like windows operates.

---

### Post by Rhapsody on 2007-08-25
> **sdowney717 said:**
> what about the nebulous 'intellectual patent infringement' being pushed by Balmer?

if Linux qualifies, then how much more will an OS that looks like windows looks. And aims to operate like windows operates.
I think the fact that they've tried to say Linux qualifies has hurt their argument. If a completely different operating system infringes on 200+ patents, how the hell are you supposed to *avoid* infringing on their patents? Once someone has basically patented the entire field of operating systems, the situation has gotten out of hand.

Additionally, Microsoft has stated that they have no intention of suing anyone (because most of the patents would be thrown out and various other companies would then start suing Microsoft for the various patents Windows infringes on) so why worry? It's all idle threats.

---

### Post by jrusso2 on 2007-08-25
The main thing I can see as being practical use for ReactOS once it gets to the point of being able to run most windows applications and become stable is that you would be able to run it in a virtual machine on Linux without having to buy a copy of windows.

That way you could run a couple of windows apps you really need to use without having to buy a copy of windows.

Too bad its not at this point yet and with only a couple of devs working on it I don't know how long it will take to get to this point.

---

### Post by toupeiro on 2007-08-25
I struggle to find the point of ReactOS in any realm outside of "can it be done".  The truth of the matter is, If you running linux, but still have a dependency on windows apps, you are going to run them in wine, or you are going to run windows.  If you are not running them in wine, its probably because they act buggy and you need 100% stability, or you are a business and you need a vendor supported environment, again, which reactOS cannot give you.  If I want an alternative to Windows, I'm not going to choose an OS that strives to be like windows.  I want a paradigm shift.

---

### Post by aysiu on 2007-08-25
If ReactOS worked, then it would be great. Right now it's just a curiosity item. They're not kidding when they say it's Alpha.

---

### Post by Rupertronco on 2007-08-25
It's neat. That's about all it has to offer. If you are dependant on a windows only application, and can't get it to run properly on wine, dual boot windows. There is nothing advantageous to having this operating system, it seems to me it's stuck at "well, that's kinda cool".

---

### Post by sdowney717 on 2007-08-25
I have tried it in virtualbox and it just hangs during the install. I see the have some virtual images you can try but none for virtualbox. 

I suppose their ultimate goal would be to make an OS that can run all windows apps, natively. If they get to that point, then perhaps they could even sell it at a significant cost advantage to MS windows.

---

### Post by angryfirelord on 2007-08-25
Failed to install in virtualbox. Oh well, considering the size of the iso is only 20~MB, I think there's still plenty of work to be done.

---

