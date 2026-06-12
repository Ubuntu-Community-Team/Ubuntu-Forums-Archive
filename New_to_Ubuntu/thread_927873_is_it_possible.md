---
title: "is it possible"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by 0lzi on 2008-09-23
is it possible to boot windows vista on hard drive 1 and run linux inside windows from hard drive 2 ?

i have vista 64 ultimate on hard drive 1 
and ubuntu on hard drive 2 
and i hate having to restart pc to switch between windows n linux so i was wondering if i acn run my linux distro in windows from a real hard drive not a virtual or an iso and install to virtuall hdd 

thanks for teh help

---

### Post by Paqman on 2008-09-23
> **0lzi said:**
> 
and i hate having to restart pc to switch between windows n linux 

Then your only option is to use a virtual machine. It doesn't matter which physical drive the VM files are located on.

There are some major drawbacks to using a VM. They can't do 3D graphics acceleration, so whichever OS your run in the VM won't have desktop effects. Also, you take a big performance hit.

If you dislike rebooting more than you like desktop effects and speed, then a VM is probably your best option. Otherwise dual booting is the way to go.

---

### Post by 0lzi on 2008-09-23
so thers no program to make linux boot inside windows at full speed with full gfx etc ?

---

### Post by NullHead on 2008-09-23
No. 

The best you can get is using virtualbox with seamless mode enabled.

---

### Post by hyper_ch on 2008-09-23
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by Tatty on 2008-09-23
> **0lzi said:**
> so thers no program to make linux boot inside windows at full speed with full gfx etc ?

No because linux, like windows. is an operating system, so it is designed to run at that level.  To get it to run within windows you need to "trick" it into thinking it is running just above the hardware layer.

For example, normally if you gave ubuntu some input, the flow of processing would go like this:

Your input -> ubuntu computation -> kernel -> hardware

However, if you want to run it within windows it would have to do this:

Your input -> ubuntu computation -> kernel -> virtual machine -> windows computation -> windows kernel -> hardware.

As you can imagine, that adds massively more computation to every task, and so will run slower.

And the reason you will not be able to get your 3D graphics drivers working is because they will need direct access to your graphics cards, however as you can see, they will not get it as all their calls will need to go via windows.

---

### Post by 0lzi on 2008-09-23
would it run at reasonable speed if u had a decent computer tho? graphics wise atm is not a big thing, if i want pretty graphics for linux i will have to restart pc n boot linux but its jus atm to learn linux.

what programs would u recomend to load my linux of my 2nd hard drive to run in windows, cos i want to be able to save work to linux on the hard drive not a virtual one liek ms virtual pc does

---

### Post by Paqman on 2008-09-23
> **0lzi said:**
> would it run at reasonable speed if u had a decent computer tho?


Depends what you call "reasonable". IMHO no OS will run well on current hardware if you have Vista as the host.

> 
what programs would u recomend to load my linux of my 2nd hard drive to run in windows

VMWare Server.

---

### Post by 0lzi on 2008-09-23
so how wud i set up vmserver to run linux of a physical seperate hdd?

---

### Post by 0lzi on 2008-09-23
and by resonable i mean

q6600 @ 3ghz
GTX 280- oc
4gb ram

---

### Post by Paqman on 2008-09-23
> **0lzi said:**
> so how wud i set up vmserver to run linux of a physical seperate hdd?

It doesn't matter which drive it's on, it's just running as an application in Windows. Just download & install the VMWare server package (you'll need to register). Once it's installed, run it in Windows, and create a new Virtual Machine. Make sure the VM has access to all the hardware it needs (sound, USB, optical drive, etc) Then just start up that VM with the Ubuntu CD in the drive and install Ubuntu into it.

For your hardware i'd give each OS one core, with Vista taking 3GB of RAM and Ubuntu 1GB. So each OS will run as if it was on hardware of about that spec.

---

