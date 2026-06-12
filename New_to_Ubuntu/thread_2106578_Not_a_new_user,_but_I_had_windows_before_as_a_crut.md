---
title: "Not a new user, but I had windows before as a crutch"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by AIvClW7W on 2013-01-19
No more crutches here, I am windows free!

For a research position I have in school, I have been using Ubuntu for terminal.  I have gotten used to and kind of more affectionate to  this OS over windows.  I have a brand new laptop with windows 8 and for what ever reason, the antivirus that came installed was never turned on.  Lots of viruses later have crippled the system completely.  Long story short, I wiped everything and reinstalled Ubuntu as the only OS.  

Because of my major, I have access to a wide variety of free programs.  I dont really need windows, but some things on this computer need it.  I am new to this open source thing, just found a "pandora" last night, so unless there are programs out there I can use to control my hardware, windows it is.  I have already found virtualbox to run windows with, but I think it wants the actual program.  

Now for the hard part.  Or at least what seems to be hard with a quick google search.  I have to download a front program to download another front to download the actual windows OS.  BUT, this first front is a .pkg which I apparently cant run.  That is where I need help.  

Admittedly, I need a lot more help, in a lot more ways, than just running virtualbox, but lets start here.

Any help is appreciated,
Russell

---

### Post by howefield on 2013-01-19
Uhm,  what exactly,  is the question ?

---

### Post by AIvClW7W on 2013-01-19
Right.  Sorry about that.

Are there any programs I can use to run the pre-existing hardware on my laptop?  If not, I want to run windows via virtualbox instead of with a dual install.  The files I have access to to install windows are in .pkg format.  How does one run a .pkg?

To summarize:
- Software to run my hardware/windows programs (camera, vga port, Rosetta stone...)
or
- How does one run .pkg?

---

### Post by Frogs Hair on 2013-01-19
I interpreted the post as meaning you are looking for programs like the ones at the links. Both are in the software enter but Crossover is not free and offers a trial.

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by grahammechanical on 2013-01-19
I am confused. It seems to me that you want to install Microsoft Windows into virtual box running in Ubuntu. But you need to run a .pkg file which is an Apple package format, according to this

[http://en.wikipedia.org/wiki/.pkg]("http://en.wikipedia.org/wiki/.pkg")

How does running an Apple file in Ubuntu get you to a working Windows OS in Ubuntu? Please explain.

[http://stackoverflow.com/questions/11093123/run-pkg-files-in-linux]("http://stackoverflow.com/questions/11093123/run-pkg-files-in-linux")

Regards.

---

### Post by AIvClW7W on 2013-01-19
Crossover might be what I am looking for.  I have tried to connect to my tv via vga cable, but unbuntu doesnt support that.  Are there ways around that?  

The .pkg thing confused me as well.  I did find that it was a mac file, but for what ever reason, it is what I need to download my program.  As I said before, the .pkg file is for a front program that will allow me to download the real program.  It is set up this way to be more secure.  

Before I got rid of windows, I was able to download everything properly, so I know it can be run on windows.

---

### Post by lisati on 2013-01-19
Let's see if I understand you properly. You have found a version of software that you used to use in Windows, and you want to use it with Ubuntu. The trouble is that it comes as a .pkg file, which seems to be intended for a machine running an OS made by Apple. Is this a correct assessment of your situation?

---

### Post by AIvClW7W on 2013-01-19
I wanted to dual boot or run windowsOS in virtualbox.  

I have to download the OS so I can install it.   It is free this way through my major.

Because it is a secure download, I have to download a front program first.  This will allow me to download the file I actually need.

I can download the front program, but I cannot install it because it is a .pkg.  

If the links provided a few responses ago, Wine or Crossover, prove to be of use, I wont need to run the .pkg file.  Until then, I am looking for a way to install said .pkg program.

---

### Post by lisati on 2013-01-19
I'm wondering if the download page sees that you're not using Windows, and assumes that you're using a Mac. I've had that happen to me from time to time.

---

### Post by GordThompson on 2013-01-19
I *think *this "front" program may be a Mac application intended for Mac users to download the Windows installer so they can set it up under Boot Camp, or Parallels, or whatever. If that's the case then you'll need to contact your IT department and see if you can get the Windows installer some other way.

---

### Post by mcduck on 2013-01-19
> **lisati said:**
> I'm wondering if the download page sees that you're not using Windows, and assumes that you're using a Mac. I've had that happen to me from time to time.

In that case using something like the [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")-extension for Firefox might work.

...on the other hand, if the download is just for a program sued for donwloading other stuff, something like Wine would still be required to run that. So it would probably just be easier to to the downloading on some other machine instead if that's possible.

---

### Post by GordThompson on 2013-01-19
> **mcduck said:**
> if the download is just for a program sued for donwloading other stuff, something like Wine would still be required to run that.
...unless the "front" program is specifically for downloading the Windows installer, in which case there would be no need for a Windows version of such a program, would there? ;)

---

### Post by AIvClW7W on 2013-01-19
Do any of you use virtualbox or crossover/wine?  Is it even worth all this bother?  There is a free trial of crossover available on their site so I am going to try that before I keep trying to work with virtualbox.

I had the the realization of what mcduck said while I was typing that last message.  I could try the download on someone elses computer.

---

### Post by archery on 2013-01-19
I use an Lubuntu 12.10 x64 host to run Windows 7 as a guest OS in Virtualbox.

I assume the laptop is relatively new and has a CPU with virtualisation support and at least 4 GB RAM?

If so, don't bother with Crossover or Wine, use Virtualbox. My system has an ULV core i7 with 8GB of RAM, prev 4 GB, with 1.5 GB allocated to Windows 7 and it runs fine. I mostly use it for Office but have used more intensive programs and they run fine as well.

I'm not sure what the front program is that is required to download the Windows OS but you'll have a hard time getting it to run natively on Ubuntu/any distro. I suggest you get hold of an OEM copy of Windows 7 and use that in Vbox.  Alternatively use a friends computer to download this 'front' program, I assume it'll then download an iso, then transfer it to your laptop and boot from it in Vbox.

I don't have time to check but Windows 8 may run in Virtualbox, if your laptop came with an install DVD you may be able to boot from this.

Also, if you are serious about using a virtual machine and your hardware is a lack lustre, consider a lightweight Ubuntu distro (I recommend Lubuntu). No bells and whistles but does everything I require (browser, vlc and a terminal!). That way if you're spending a reasonable time in your Virtual machine as I do with Office 2010, you'll see a speed benefit in both.

---

### Post by AIvClW7W on 2013-01-19
My computer shouldnt have any problems from the hardware side.  Its a Lenovo W530, I got it so I wouldnt have to buy a new computer for quite a long time.  I got crossover to install and I now have all of Microsoft Office installed.  Seems to run fine.  I have 8gb of ram currently, but I plan on upgrading it in the future.  I am also looking into replacing my HDD with an SSD.  I am currently trying to work out all the bugs before I go crazy with all the new toys.

---

### Post by CharlesA on 2013-01-19
> **GordThompson said:**
> ...unless the "front" program is specifically for downloading the Windows installer, in which case there would be no need for a Windows version of such a program, would there? ;)

This is likely the case, I have had to use a "secure downloader" to download the Office setup program I got from my school. It only offered Windows and Mac versions, from what I remember.

Best thing to do is contact the school's IT guys and see if they have any other options.

---

### Post by Paqman on 2013-01-19
> **rtfaber said:**
> I wanted to dual boot or run windowsOS in virtualbox.  

I have to download the OS so I can install it.   It is free this way through my major.


What version of Windows are you trying to install? You can get a free ISO image of Windows directly from Microsoft, all you need is a valid licence key to activate it.

---

### Post by archery on 2013-01-19
Glad that you have a solution that works, I tried Wine but some functions weren't supported for Office 2003, this was a while ago. Also it seemed a bit ugly. 

With the hardware you've got, I'm sure you'll find Virtualbox a better solution in the long term. You can install it now and try another linux distro as a virtual os. When you've got a bootable copy of Windows it should be relatively straight forward.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by brusegadi on 2013-01-19
I dont know if I am understanding correctly, but you mentioned the utilization of a vritual machine running a windows guest.  My impression was that you wanted to use the virtual box to utilize hardware not supported in ubuntu?  

If this is the case, then it will not work.  The virtual machine does not support most hardware directly, but through the host OS (Ubuntu in your case.)  For example, if your video card is not supported in ubuntu (host OS), it will not work in the guest OS either.  Thanks!

---

### Post by AIvClW7W on 2013-01-19
Brusegadi, you would be right.  I want to use virtualbox so I can run some of my unsupported hardware.  So far this seems to be my graphics card, havent come across anything else I cant use yet.  How would I go about fixing this problem if this is the case?

Crossover let me install and run microsoft office so far, I havent tried rosetta stone yet.  So far so good I guess.

---

### Post by archery on 2013-01-19
OK, looking through your posts I can see you mentioned your vga out wasn't working. The laptop model you refer to has an Nvidia Graphics card. As a starting point I'd make sure your familiar with your distros display settings and how to adjust them. I use Lubuntu, here they're in Preferences - Monitor settings.

If your satisfied that its not working then you may need additional drivers, Nvidia is relatively well supported on linux. Check how to enable proprietary drivers. In Lubuntu, if there are any available, they're in Preferences - Software Sources.

I'm sure others will be able to provide more assistance, normally a quick google search does the trick (and time familiarising yourself with the new setup).

---

### Post by Paqman on 2013-01-19
> **rtfaber said:**
> Brusegadi, you would be right.  I want to use virtualbox so I can run some of my unsupported hardware.  So far this seems to be my graphics card

You can't do that with virtualisation. The guest OS (Windows) uses the hardware supplied to it by the host OS (Linux). So if it isn't working in the host it won't work in the guest.

You need to get your graphics card working in Linux. Have you installed the drivers? If so which one?

---

### Post by AIvClW7W on 2013-01-19
I havent installed anything yet.  I didnt know I had to until it was mentioned.  Trying to do that now.

---

### Post by brusegadi on 2013-01-19
> **Paqman said:**
> You can't do that with virtualisation. The guest OS (Windows) uses the hardware supplied to it by the host OS (Linux). So if it isn't working in the host it won't work in the guest.

You need to get your graphics card working in Linux. Have you installed the drivers? If so which one?

Just for the record, my post also clarified this point. :(

---

### Post by AIvClW7W on 2013-01-19
Haha I have been looking for a way to check my drivers since you said something.  Still havent figured out how.

---

### Post by howefield on 2013-01-20
Hit the Dash by pressing the Super (Windows) key or clicking on the topmost icon in the lacuncher and start typing Software Sources, after a few letters the icon for it should appear, load it up and go to the end tab "Additional Drivers" you might find an available driver in there for your graphics card.

Haven't read through all the posts in the thread, did you mention which card you had ?

---

### Post by AIvClW7W on 2013-01-20
[FONT=Comic Sans MS]I found the additional tabs driver, but no driver.  Would it be a driver problem that wont let me use my VGA port?  Havent tried HDMI since I dont have that cable.

My card is an NVIDIA Quadro K2000M.
[/FONT]

---

### Post by archery on 2013-01-20
> **rtfaber said:**
> [FONT=Comic Sans MS]I found the additional tabs driver, but no driver.  Would it be a driver problem that wont let me use my VGA port?  Havent tried HDMI since I dont have that cable.

My card is an NVIDIA Quadro K2000M.
[/FONT]

Your laptop uses Nvidia Optimus hardware: 

[http://www.nvidia.com/object/optimus_technology.html]("http://www.nvidia.com/object/optimus_technology.html")

The setup is not as straightforward as it otherwise might have been. Have a read of this thread:

[http://ubuntuforums.org/showthread.php?t=2007485]("http://ubuntuforums.org/showthread.php?t=2007485")

It sounds like you need install the Bumblebee driver set:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Or, alternatively, select the Nvidia card as the sole graphics card in your BIOS.

---

### Post by AIvClW7W on 2013-01-20
I tried changing my graphics card settings in BIOS to discrete, but that lead to some very slow loading and more errors than wanted.  Switched back.  I tried to download the driver straight from NVIDIA and that just froze firefox.  Going to try the bumblebee solution now.

---

