---
title: "My dream system.  Can it be done?"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-03-29
I have 11.10 running from an 8 Gb USB flash.

Started using it yesterday on a Win 7 fast desktop.

My wife is using a Pentium 4 XP 3.2 Ghz SP2 that for some reason cannot update to SP3.  (Access denied message when almost installed).

Both machines have bogged down over time and that is why am attempting Ubuntu.

AAMOF My wife's machine was getting blue screens until I cleaned the registry, and it still runs slow albeit no blue screens.

What I would like to do is to use Ubuntu for the majority of tasks and also use XP or Win7 for some applications.

In addition, when running Windows applications, I do not want to be connected to the internet for security reasons.

My dream system would have simultaneous dual boot and I could toggle between Windows and Ubuntu.

I would also like the ability to transfer files between Windows disk space and Ubuntu disk space.

Is this doable?

Edit:  When I saw the cup and green coffee beans, I wanted to add that I roast my own green coffee beans! lol

---

### Post by lykwydchykyn on 2012-03-29
When you say "simultaneous dual boot", are you asking if you can have both systems booted at the same time, and just switch instantly between them?  I'm pretty sure that's impossible.  You have to choose the OS at boot-time, or virtualize one of them (the latter of which is probably beyond the P4 computer's capabilities).

Everything else you describe is possible.

---

### Post by NikTh on 2012-03-29
Hello and welcome to Ubuntu forums. 
Of course your "dream system" is doable . You can do either dual boot with ubuntu and win7 or you can install only ubuntu (and delete win7) and then install Virtualbox(package) and run win7 from Virtual machine. 

For the first option read here --> [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 
or 
see this video --> [http://www.youtube.com/watch?v=dMTL_-XJjyU](http://www.youtube.com/watch?v=dMTL_-XJjyU) 

For the second option (virtualbox) see this video --> [http://www.youtube.com/watch?v=ZaHbmbrqjvQ](http://www.youtube.com/watch?v=ZaHbmbrqjvQ) 

I suggest before you proceed with any of 2 options  , IF you have any problem with installation or something that you don't understand post here your question. Again.. Before proceed .
:p

---

### Post by MG&amp;TL on 2012-03-29
Okay, you can do all of those things except toggle between the two.

Before we start, I do suggest you use Lubuntu or Xubuntu for your Pentium IV-I have one myself and it runs much faster and smoother. Both Lu- and Xu-buntu are the same as Ubuntu "under the hood", but they have lighter desktop environments and default programs.

To have both Windows and *buntu on your machine, follow [this guide]("http://www.psychocats.net/ubuntu/installing") -it has pictures! :)

You will then be able to choose between Windows and Ubuntu when you boot.

To transfer files between them, Ubuntu can natively support the Windows filesystem, FAT & NTFS, whereas if you want to access Ubuntu from Windows, I suggest you either boot into Ubuntu and copy things across, or use either [linux reader]("http://www.diskinternals.com/linux-reader/") or [explore2fs]("http://www.chrysocome.net/explore2fs")

PS: Yeah, the beans are a laugh. Not sure we've ever had an actual bean-roaster on here before though.

---

### Post by sudodus on 2012-03-29
Welcome to the Ubuntu Forums :-)

> **Boyntonstu said:**
> ...
In addition, when running Windows applications, I do not want to be connected to the internet for security reasons.

My dream system would have simultaneous dual boot and I could toggle between Windows and Ubuntu.

What do you mean by toggle? Normally dual boot means that you boot either of the systems, and you have to reboot to run the other one.

But you can run a virtual machine and run the other system inside that. Then you can have both systems running simultaneously. But the virtual machine slows things down, so that would work better on your fast desktop.

I run VirtualBox and have Windows XP in it for Windows specific things. I also test various linux versions in other instances of VirtualBox.
> 
I would also like the ability to transfer files between Windows disk space and Ubuntu disk space.

Is this doable?

This is easy. Ubuntu can read NTFS, so you can have a common ***data*** partition that you can read and write from Windows and Ubuntu.
> 
Edit:  When I saw the cup and green coffee beans, I wanted to add that I roast my own green coffee beans! lol

---

### Post by QIII on 2012-03-29
As above, many of us do exactly what you want by virtualizing other OSes.

Simply put, however:  I doubt your hardware is suitable.

But, hey, give it a try.  Maybe we'll all learn something valuable.

---

### Post by Boyntonstu on 2012-03-29
> **MG&TL said:**
> Okay, you can do all of those things except toggle between the two.

Before we start, I do suggest you use Lubuntu or Xubuntu for your Pentium IV-I have one myself and it runs much faster and smoother. Both Lu- and Xu-buntu are the same as Ubuntu "under the hood", but they have lighter desktop environments and default programs.

To have both Windows and *buntu on your machine, follow [this guide]("http://www.psychocats.net/ubuntu/installing") -it has pictures! :)

You will then be able to choose between Windows and Ubuntu when you boot.

To transfer files between them, Ubuntu can natively support the Windows filesystem, FAT & NTFS, whereas if you want to access Ubuntu from Windows, I suggest you either boot into Ubuntu and copy things across, or use either [linux reader]("http://www.diskinternals.com/linux-reader/") or [explore2fs]("http://www.chrysocome.net/explore2fs")

PS: Yeah, the beans are a laugh. Not sure we've ever had an actual bean-roaster on here before though.

Thanks, 

I am on a nice journey.

And for being 73 years old quite proud of getting 11.10 up and running in one day. ;>)

I am sure that I will be back with more questions.

Many thanks.

For laughs:
  Homemade Trike and Coffee Roaster on TV 

  [http://www.youtube.com/watch?v=0yBLJg0efmk](http://www.youtube.com/watch?v=0yBLJg0efmk)

and:Homemade $100 elevator video:*
 *
[http://www.youtube.com/watch?v=-fKyZ9v_65o](http://www.youtube.com/watch?v=-fKyZ9v_65o)

---

### Post by QIII on 2012-03-29
Dual booting will work fine.  You lose th "toggle" dream, but that might be a small trade.

---

### Post by nutrapi on 2012-03-29
of course.
for a first time dual boot user - sometimes it's easiest just to have a separate hard drive though and use the bios to choose OS on boot.

---

### Post by QIII on 2012-03-29
I would submit that in such a hardware arrangement it is substantially easier to install each system independently on one disk while the other is disconnected, reconnect both drives, set the BIOS to boot from the Linux drive first, update GRUB and simply use the GRUB menu to choose.

The MBR of each OS is preserved by installing that way.  If the Linux OS poops out.  You can simply disconnect it and Windows will be quite happy to boot without complaint.

But, again, that is with two physical drives and the opposite one disconnected while installing an OS on the other.

---

### Post by Atomic-Fanboy on 2012-03-29
"PS: Yeah, the beans are a laugh. Not sure we've ever had an actual bean-roaster on here before though!" -I have 5 cups!

Boyntonstu - Have you thought of giving WUBI a brief trial? 

WUBI is "Windows- based Ubuntu Installer". 
It can either be run from a standard install CD, run from a .iso image (But you will need disk imaging software too, I think), or use Wubi to download the image as a torrent file. Then, Wubi should install straight away. You can use Wubi to create a virtual partition of up to 30 Gigabytes. It performs slightly worse than a direct install, though. However, you can use "Wubi Move" to turn it into a proper install on an actual partition, or uninstall Wubi. You will not be making any changes to Windows while using Wubi.

"What I would like to do is to use Ubuntu for the majority of tasks and also use XP or Win7 for some applications." - 'Wine' (WINE is not an emulator) can allow you to use some Windows based programs. You may want to research first and see if it is compatible with the software you use.

---

### Post by Paddy Landau on 2012-03-29
> **lykwydchykyn said:**
> When you say "simultaneous dual boot", are you asking if you can have both systems booted at the same time, and just switch instantly between them?  I'm pretty sure that's impossible.
It **is** possible. You use a hypervisor, which allows two systems to run at the same time (you need a modern 64-bit computer with virtualisation hardware and plenty of RAM; I suggest 8Gb to run both Windows 7 and Ubuntu). This allows you to swap instantly between the two systems without rebooting.

I believe that the supported hypervisor for Ubuntu is KVM, but there are others such as Xen. (I understand KVM can also be used as a supervisor in the same way as Virtual Box is used.)

Be aware that using a hypervisor requires advanced knowledge, so if you want to go that route, first learn all about dual-booting and get used to using both Ubuntu and Windows (swapping between them requires a reboot). Also learn how to use a virtual machine so that you can understand the concepts of running two systems at the same time.

Dual-booting is by far the easiest method; using a virtual machine (if you have enough RAM) is also easy, and if you use Virtual Box you can use Seamless mode.

Finally, you can use [WUBI]("http://www.ubuntu.com/download/ubuntu/windows-installer") -- **but** it is not as stable and tends to fail on major upgrades, so don't use WUBI unless you just want to experiment.

---

### Post by Mark Phelps on 2012-03-29
Don't know how familiar you are with Virtualization, so I aplogize in advance if I'm telling you something you already know -- but complete reinstallation of Windows is going to be necessary, whether you use a Virtual solution or a separate drive.  Either way, you will need actual Installation media to do that.  

IF you have that, and you're up to the task, then have at it!

---

### Post by Atomic-Fanboy on 2012-03-29
Paddy - yes, I know Wubi isn't amazingly stable. However it should be usable enough for a brief trial before committing to a full install. 12.04 LTS is only a couple of weeks away, anyways.

---

### Post by d4m1r on 2012-03-29
> **Boyntonstu said:**
> 

And for being 73 years old quite proud of getting 11.10 up and running in one day. ;>)


Wow, that is impressive :shock:

---

### Post by SeijiSensei on 2012-03-29
I'm going to suggest an alternative that you can ignore.

Buy another machine.  These days you can get a decent desktop computer and monitor for a few hundred bucks like [this one]("http://configure.us.dell.com/dellstore/config.aspx?oc=sdcm101&c=us&l=en&s=soho&cs=ussoho1&model_id=vostro-260&").

I'm 62, by the way, and not especially profligate.  I've gotten a lot of mileage out of the computer hardware I have, but at some point the time comes to bite the bullet and buy a new machine.  Besides, any modern machine will support a lot more of the options being discussed here, particularly virtualization.  If the virtualization approach has appeal, I'd spring for the memory upgrade to 4 GB.

You don't need to discard the machine you have now, either. Put Ubuntu on it and turn it into a file/media server.

---

