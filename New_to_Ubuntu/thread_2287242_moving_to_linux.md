---
title: "moving to linux"
date: 2015-07-17
forum: New to Ubuntu
---

### Post by mcaulay_brown on 2015-07-17
so I am a current windows user and I hate windows a lot so I was thinking about moving over to a Linux based os for my computer I have heard lots about Ubuntu but the problem is that I have also read that some windows software is not compatible for Linux based operating systems I like to use photo and video editing software on my computers is it possible to get these types of software on a Linux based machine

---

### Post by Bucky Ball on 2015-07-17
Welcome. Windows apps are not for Linux at all. You can run some using Wine. Look up apps [here]("https://appdb.winehq.org/"). If you are wanting to use mostly Win apps, stick with Win. 

If you want to do photo editing, Gimp is probably where you want to look. There are others. There's a ton of stuff for video editing, but depends what you want to do. You are not going to find anything like the pro-level Avid editing software, for instance. 

Have a research for Linux alternatives. Perhaps try, for instance:

'photoshop alternative linux'

Replace 'photoshop' with the app you want an alternative for. Or,

'alternative application linux'

Your other options are to use Windows as a virtual machine with Ubuntu as the host, or vice versa, or dual-boot Win and Ubuntu (each OS on its own partition).

Also, you might like to have a quick look at [this]("http://linux.oneandoneis2.org/LNW.htm"). Good luck. :)

---

### Post by kerry_s on 2015-07-17
what photo/video editor ?

suggest you also give specs, type of pc. there are many ubuntu variants for many machines based on specs.

for example i use a weak netbook(hp-mini 210-1010nr) 2x atom 1.6ghz, 2gb ram(maxed) so i run the lighter variances, currently running xubuntu 15.04, but i can also do ubuntu-mate & lubuntu very well, standard ubuntu(unity) & ubuntu-gnome do run, but are slow enough i don't want to use.

---

### Post by steve_mc on 2015-07-18
If your currently running windows 8, i would suggest checking the settings in the UEFI of your pc to make sure that secure boot can be disabled, before spending much
time researching software. I removed windows 8 from my pc about 3 weeks ago and now i only run ubuntu 15.04. Love it!!

---

### Post by leunam12 on 2015-07-18
I use Photoshop CS2 all the time in WINE.

---

### Post by Lars Noodén on 2015-07-18
If you want to manage collections of photos there is Digikam or Shotwell, or Fotoxx.  

Darktable or RawTherapee are for raw image processing.  

Krita is supposed to be pretty good for general photo editing, I've read that it has passed Gimp.  Both are different from Photoshop but met my needs better.  However, it's now been ages since I've done that kind of editing myself.

---

### Post by grahammechanical on 2015-07-18
We have a family of Linux distributions based on Ubuntu. One of these family members is called Ubuntu Studio. It brings together lots of applications that specialise in Audio, Video and Graphic work. I am not suggesting that you install Ubuntu Studio but a look through the list of applications that come with Ubuntu Studio by default will give you an idea of the great variety of Linux applications that are available in this area. Each of these can be installed in any member of the Ubuntu family of Linux distribtutions.

 [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)/

[https://ubuntustudio.org/tour/](https://ubuntustudio.org/tour/)

Take the tour and you will get an idea of the kinds of applications and their quaility that are available in LInux for those doing audio, video and graphic work.

Regards.

P.S. If you are really serious about moving to Linux, then I recommend, as others have down, either installing Ubuntu in a Virtual Machine or dual booting and then test to see if you can get Ubuntu setup exactly the way you want and can convert all your present files and documents to be edited in Linux applications.

---

### Post by Bucky Ball on 2015-07-18
Or you can install ubuntustudio-graphics and/or ubuntustudio-photography in Ubuntu from the Software Centre and you will have the graphics/photography apps from Ubuntu Studio in Ubuntu. If you don't do audio there is tons in UStudio you definitely don't need.

I would recommend a lighter flavour than Ubuntu, though, for doing audio/visual stuff. Perhaps Xubuntu or a minimal install with xfce4 and ubuntustudio-graphics and ubuntustudio-photography. 

Ubuntu Studio uses the xfce4 desktop envrionment, incidentally, rather than the Unity one used in regular Ubuntu (Xubuntu uses xfce4 also).

---

### Post by buzzingrobot on 2015-07-18
> **mcaulay_brown said:**
> ...I have also read that some windows software is not compatible for Linux based operating systems...

Software created for a specific operating system won't run on other operating systems. Windows software won't run on Linux or OS X or iOS or Android.  Or Linux software on Windows, etc.  

Various alternatives are available in Linux for Windows applications.  While they often provide similar capabilities and features, they typically are not simple clones of Windows products, so there is a learning curve.  

You're smart to research the availability of Linux software that you need/like before making the switch.

---

### Post by Bucky Ball on 2015-07-18
> **buzzingrobot said:**
> 

You're smart to research the availability of Linux software that you need/like before making the switch.

+1. Better than diving in head first and then whining about Ubuntu not being a free drop in replacement for Windows so it's rubbish. Why can't I run Internet Explorer???? That attitude doesn't go down great with a community of people successfully using Ubuntu as their main OS. :-k :)

---

### Post by stalkingwolf on 2015-07-18
I woukld suggest a stop at distro watch.  there are many distributions available that are based on or forks of debian.  all of which use synaptic package manager, the major software downloader and repository.
I prefer it to software center, others prefer SC that is a situation that is common across Linux os's.
There is no right or wrong one just different ones.  what works for me may not be right for someone else.  That is the major foundation of linux . choice.

---

### Post by sports fan Matt on 2015-07-18
I would agree with everything Stalkingwolf has said.  Linux is not a replacement for Windows as others have stated but in my case, I was tired of Windows 7 BSOD's back in 2007 and started just as you did.  Nearly eight years later I still have basic questions I sometimes ask and that's what I enjoy, the willingness to help others and rreceive help in return.

But I digress, this OS is not for everyone.  I second a look at distrowatch.  [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by mystics on 2015-07-18
You could always try running Ubuntu as a virtual machine. From there, you have two major options:

1.  Do some research and test out alternatives that are on Linux. Some have already mentioned alternatives in this thread, and the Internet has a vast amount of information in this regard. If you're pleased with any of these, great. If not, then...

2. Look into the compatibility of different Windows programs through Wine. There's already a [database]("http://appdb.winehq.org")  of various programs and how well they work, but it would also be best  to try them out in the virtual machine. If you want to bypass some of  the difficulties of Wine, there's other software like PlayOnLinux that  helps make things easier on new users.

Basically, this will both help ease the transition to Ubuntu, or whatever other Linux distro you choose, while also making sure it is right for you.

---

### Post by Mark Phelps on 2015-07-19
My own experience using Wine is that it was, essentially, a big waste of time.  If you check the WineHQ compatibility database, you'll find that over half of the Windows apps listed run poorly or not at all, and the "big two" of Windows apps (Internet Explorer 11, and MS Office 2013) do not run at all in Wine.

If you seriously need to continue to use Windows apps on a daily basis, then a dual-boot is recommended.  If you don't want that, you could consider using Windows in a VM, but understand, you'll have to reinstall it from scratch, along with all your Windows apps, to use it.

---

### Post by Buntu Bunny on 2015-07-19
FWIW I like Gimp Image Editor and OpenShot Video Editor. Windows users will likely say they don't stack up, but they do a good job, I think.

---

### Post by MGrowl on 2015-07-20
@mcaulay_brown. Are you related to Esteban_brown by any chance? Most programs don't run on Ubuntu, but some can using WINE. If you do a lot of photoediting with photoshop and feel comfortable using it, I suggest you dual-boot and only use windows for that program/application. If your intent is to use the same programs in linux as you do windows, better research if they are supported. Otherwise, tough luck. 

GIMP is good, although you'll have to relearn the basics all over again coming from photoshop. @Mcaulay_brown.

---

### Post by mastablasta on 2015-07-21
> **mcaulay_brown said:**
> so I am a current windows user and I hate windows a lot 

"*fear leads to anger. anger leads to hate. **hate leads to suffering.***"

seriously opensource Linux tools usually have windows version so you can try them out without installing the OS. you can do plenty on them but they might not be as intuitive and automated as some windows only tools. for example have a look at a few videos on your tube from Blender project. it's amazing what can be done with that tool. but it is also quite difficult to use and needs some time invested into it. if you are a pro you could try to jump into some of these opensource tools see how you like them. for example Inkspace for me was easy to use, but I only use beginner stuff. and having it translated well into my language made me easy to understand what functions do just by looking at "mouseover" explanation.

---

