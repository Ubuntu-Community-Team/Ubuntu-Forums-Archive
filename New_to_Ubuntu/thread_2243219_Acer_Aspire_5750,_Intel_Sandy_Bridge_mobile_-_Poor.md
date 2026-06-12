---
title: "Acer Aspire 5750, Intel Sandy Bridge mobile - Poor Performance"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by Ritchiejoe8 on 2014-09-07
I have recently installed ubuntu 14.04.1 LTS and it is running quite slowly...... even slower than my windows installation. So I wanted to ask if my laptop is perhaps a little dated and I need a newer machine or whether there are some tweaks I can perform.

If my machine is dated I would appreciate it if you could point out a newer laptop I should be considering...... no macs ;)

[http://i1050.photobucket.com/albums/s408/Rjoe8/Computerspec_zpsbabab745.png](http://i1050.photobucket.com/albums/s408/Rjoe8/Computerspec_zpsbabab745.png)

Thanks In advance

---

### Post by ne0h on 2014-09-07
Two things can happen.

a) Your graphics card driver is not installed properly. Install the driver.
b) Unity is too much for your configuration. I would suggest you to install GNome.

---

### Post by bullethead on 2014-09-07
open the terminal and run these commands, I recommend being "friendly to it" saying yes to everything

--to update the software availability (ubuntu is constantly being made available new software)

sudo apt-get update

--then to get gnome---

sudo apt-get install gnome-shell ubuntu-gnome-desktop

--then all you do is log out of the desktop, log back in and I think there should be an option to use gnome at the login if that works correctly---

---

### Post by Ritchiejoe8 on 2014-09-07
I'm pretty new to linux could explain how I check if the driver is installed on linux, is gnome another version of ubuntu?

---

### Post by Ritchiejoe8 on 2014-09-07
Thanks I will give that a go now Bullet

Do you think my machine is a little dated or fine?

---

### Post by bullethead on 2014-09-07
> **Ritchiejoe8 said:**
> Thanks I will give that a go now Bullet

Do you think my machine is a little dated or fine?

i think it is fine for gnome, which I recommend you have a go at it.

Unity desktop is very graphics intensive for that laptop you have.  Don't get something else before you see how it turns out.  Also Linux is going to be a little bit not as snappy as windows, you have to live with that to get the security and stability.  It is a serious system, not something for everyone ;)  

have fun!

---

### Post by Ritchiejoe8 on 2014-09-07
I saw a footprint when I rebooted so I am guessing gnome is working. Thanks again

---

### Post by mörgæs on 2014-09-07
Ne0h, please don't begin talking about graphics drivers before you know which GPU we're dealing with. 

Richie, please post the complete hardware description.

---

### Post by Ritchiejoe8 on 2014-09-07
is that not what I posted in the screenshot? If not is there a command in terminal which will detail the information you requested. I am new to ubuntu so I am grateful for your patience with me

---

### Post by EuclideanCoffee on 2014-09-07
Gnome itself is a full-featured desktop.

XFCE might be a better alternative.

[http://xubuntu.org/](http://xubuntu.org/)

Try it out on a Live CD. If you like it, overwrite your Ubuntu partition with it.

Xubuntu is just Ubuntu with the XFCE Desktop Environment.

---

### Post by Vladlenin5000 on 2014-09-07
> **Ritchiejoe8 said:**
> is that not what I posted in the screenshot? If not is there a command in terminal which will detail the information you requested. I am new to ubuntu so I am grateful for your patience with me


The screenshot shows almost everything that's relevant for your reported problem but the information about the graphics is still missing although most certainly is just an integrated Intel. The command below show give the required information.

```
[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 vga[/FONT][/COLOR]
```

---

### Post by coffeecat on 2014-09-07
> **Ritchiejoe8 said:**
> is that not what I posted in the screenshot? If not is there a command in terminal which will detail the information you requested. I am new to ubuntu so I am grateful for your patience with me

No - the graphics wasn&#8217;t detailed in your screenshot. This terminal command in Ubuntu will tell us which GPU you have and also which driver it is using:

```
sudo lshw -c video
```

You will be prompted for your password, but you won't see it echoed to the screen when you type it in. Don't worry - it is going in. Just type it in and press ENTER. You can copy the output by highlighting it with the mouse -> right-click -> copy and then paste it into your post.

A comment and a question:

Posters are recommending you try a desktop environment other than Unity before we have determined what graphics card and driver you have. That is somewhat premature. I run Ubuntu with Unity on a laptop with much more modest hardware than you have and its performance is quite satisfactory. Let's see if the graphics card and driver might be the problem before complicating matters with talk of other desktop environments.

The question - I'm curious. Your screenshot appears to be from Windows 7 but with Ubuntu-like theming. Is that correct?

**EDIT**: I didn't see Vladlenin5000's post as I posted. Vladlenin5000's command will do just as well for the information we need and doesn't require sudo authentication.

---

### Post by Ritchiejoe8 on 2014-09-07
I ran both commands just incase

This is what Vladlenin's command gave me *"**00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)******	Subsystem: Acer Incorporated [ALI] Device [1025:0504]***
[I]**	Kernel driver in use: i915"**
[/I]

This is what CoffeeCat's command gave me ***" *-display               ***
***       description: VGA compatible controller***
***       product: 2nd Generation Core Processor Family Integrated Graphics Controller***
***       vendor: Intel Corporation***
***       physical id: 2***
***       bus info: pci@0000:00:02.0***
***       version: 09***
***       width: 64 bits***
***       clock: 33MHz***
***       capabilities: msi pm vga_controller bus_master cap_list rom***
***       configuration: driver=i915 latency=0***
[B][I]       resources: irq:47 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64)"
[/I]
[/B]Yes Coffee that is a windows 7 installation with a ubuntu theme. I have always been a windows user but I am an avid android user and I am wanting to make a Linux distribution my primary OS and maybe keep windows for certain applications that you cannot use on linux.

Again if after reading the above graphic driver information you think that my Laptop is a little dated or not powerful enough I would greatly appreciate it if someone could recommend me some new hardware which will no doubt come preloaded with windows 8 :-x

Again thank you for your patience

---

### Post by Vladlenin5000 on 2014-09-07
No, your laptop definitely isn't dated and it should be able to handle smoothly not one but two concurrent Unity sessions (if that were possible...). As a rule, if it runs Windows 7 smoothly then it should run the latest Ubuntu with Unity as good as Windows or better.
Whatever is causing the slowdown isn't related with insufficient hardware specs but it can be related with hardware problems, namely old and/or "unhealthy" HDDs.
You should also keep in mind that during the first boot after installation there are lots of processes running in the background finishing things that weren't finished in the installation process, namely updates. You should test again after fully updating your newly installed system and reboot. If the symptom persists then it's worth looking into it and perform some hardware tests if needed.

---

### Post by Ritchiejoe8 on 2014-09-07
I thought perhaps I maybe messed up with the installation but I followed a youtube walk-through on my laptop during the install. Is it possible to carry out the tests using the ubuntu partition? I may carry out the tests then if needed nuke my hard-drive and start over.

Can I ask which version of ubuntu or other linux based OS you are using?

---

### Post by Vladlenin5000 on 2014-09-07
Have you noticed any error messages during the installation or anything out of the ordinary?

---

### Post by Ritchiejoe8 on 2014-09-07
> **Vladlenin5000 said:**
> Have you noticed any error messages during the installation or anything out of the ordinary?

No not that I noticed, I gave it 2gb of swap and followed the tutorial every step of the way. [https://www.youtube.com/watch?v=xlTgaWs9BD0](https://www.youtube.com/watch?v=xlTgaWs9BD0)

I don't expect you to watch the video. the only thing I did which I'm guessing you don't usually do is install it without putting grub on the MBR and used EasyBCD to add an entry to the bootup. which is what was advised in the above link

---

### Post by Vladlenin5000 on 2014-09-07
> **Ritchiejoe8 said:**
>  the only thing I did which I'm guessing you don't usually do is install it without putting grub on the MBR and used EasyBCD to add an entry to the bootup. which is what was advised in the above link


Bad bad bad advice... However, I think that *per se* shouldn't impact anything else provided it boots (and it does). Perhaps someone else more knowledgeable than me can contribute to this discussion...

---

### Post by grahammechanical on 2014-09-07
I have an Intel Core2 Duo 2.40Ghz and 1 GB RAM (physical memory). And it runs Ubuntu and I do not notice any slowness. I think that it is snappy. You have a much more powerful CPU than me and 6 times the RAM. So, there is nothing old and insufficient about your machine.

Please open the power/cog menu and select About this Computer. A dialog will open on the Overview page. What does it say about Graphics? While you are at it what does it say about the Processor and the Memory?

Also open the Dash (the Ubuntu icon at the top of the launcher on the left and search for System Monitor. That should show you CPU activity and memory usage. Anything strange about it?

Another thing that you can try is to run this command in the terminal

```
top
```

The top utility will show you every process that is runing and how much CPU and memory is being used by each process. Is anything using more and more of the CPU or memory?

Regards.

P.S. If you want proof that you graphic adapter can run Unity then run this command

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Ritchiejoe8 on 2014-09-07
> **Vladlenin5000 said:**
> Bad bad bad advice... However, I think that *per se* shouldn't impact anything else provided it boots (and it does). Perhaps someone else more knowledgeable than me can contribute to this discussion...

Interesting I would also like someone to clear that up for us :) if it is a poor method I will re-install.


> **grahammechanical said:**
> I have an Intel Core2 Duo 2.40Ghz and 1 GB RAM (physical memory). And it runs Ubuntu and I do not notice any slowness. I think that it is snappy. You have a much more powerful CPU than me and 6 times the RAM. So, there is nothing old and insufficient about your machine.

Please open the power/cog menu and select About this Computer. A dialog will open on the Overview page. What does it say about Graphics? While you are at it what does it say about the Processor and the Memory?

[B]Graphics: intel sandybridge mobile
Processor intel® Core™ i5-2410M CPU @ 2.30GHz × 4 
Memory: 5.7gb[/B]

Also open the Dash (the Ubuntu icon at the top of the launcher on the left and search for System Monitor. That should show you CPU activity and memory usage. Anything strange about it?

Another thing that you can try is to run this command in the terminal

```
top
```

The top utility will show you every process that is runing and how much CPU and memory is being used by each process. Is anything using more and more of the CPU or memory?

**Not that I can see, this whole problem doesn't make sense going by what everyone has said :(**

Regards.

P.S. If you want proof that you graphic adapter can run Unity then run this command

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Ritchiejoe8 on 2014-09-07
So my Ubuntu has just totally crashed and I had to hold down the power key to turn it off. Does anyone have any advice on where I should go from here?

---

### Post by Ritchiejoe8 on 2014-09-07
I think the best thing for me to do would be to Fix any hard drive issues that I can (recommendations on the best way to do this are welcome), then Nuke my harddrive and try a clean install from there agreed?

Would you do a dual boot or just a linux OS?


I apologise for the twenty one questions today, hopefully by sticking around I will learn things and eventually have some valuable input of my own on the forum :)

---

### Post by sandyd on 2014-09-07
I know someone with this laptop.

Ubuntu 14.04 works perfectly on it (With Unity, Ubuntu 14.04)

Side note:
I am not very sure if this applies in your situation since this particular laptop has had a battery and RAM replacement, but within 1-2? years of use, the (Toshiba) HDD had an odd habit of randomly spinning down, and crashing the computer in both Windows/Linux. It was eventually replaced with a SSD, which rendered the computer usable again.

---

### Post by mörgæs on 2014-09-08
> **Ritchiejoe8 said:**
> 
Would you do a dual boot or just a linux OS?


As long as there might be a hard disk problem to investigate I would keep Windows, but reinstalling Ubuntu is a fine exercise if you are new. 

You cold use the occasion and try another desktop environment (like Xubuntu) as has been suggested. Not because of hardware limitations just to see which one you like more.

---

### Post by Ritchiejoe8 on 2014-09-09
I deleted my Ubuntu partition, scan hard disk for errors using hirens boot CD and repaired them. I have done a clean install and everything appears to be working as it should be, thankyou to everybody who offered advice. Now to find some good equivalents to windows software :)

---

### Post by JeQhdMD on 2014-09-09
Glad you got it going . . I've have an Acer Timeline 4830T-6841 with exact same specs but 640 GiB hdd.   With 6 gigs of ram, Ubuntu Unity works perfect - - it's stable and fast.   So, your disk hardware issues may have been the culprit.   Just be sure you're running the 64 bit version instead of the 32 bit version so all of your ram will be utilized.

---

