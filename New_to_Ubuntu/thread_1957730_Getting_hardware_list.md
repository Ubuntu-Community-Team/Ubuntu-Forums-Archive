---
title: "Getting hardware list"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by MonkWy on 2012-04-13
I am waiting for Ubuntu 12.04 LTS. I am brand new to Ubuntu, I have a HP Vectra VLi8 SF Desktop. Am currently running RedHat Linux 9. I want to see if I can and how to upgrade to the current stable release of Ubuntu on the above-mentioned machine. I suppose before that I need to list the hardware here from that machine? How would I go about getting the list of hardware on my PC? Is there a comand I can type and where/how would I do that? It currently isn't connected to the internet, however, I have future plans to do so, wirelessly if possible. Can anybody offer advice or point me in the direction of places to look please? Thanks.:biggrin:

---

### Post by drpjkurian on 2012-04-13
You can get all the hardware specs from bios set up screen

---

### Post by ronaldbrijo on 2012-04-13
Welcome to Ubuntu

I dont think it is really an issue to have a list of the hardware in your PC as Ubuntu will install without a hassle on any pc (ive tried it on many). 

Hope you like Ubuntu as much as we all do.

I also used other distros and have found Ubuntu to be the easiest to install and run everyday.

---

### Post by DeezyFaReal on 2012-04-13
> **MonkWy said:**
> I am waiting for Ubuntu 12.04:biggrin:

What do you mean you are waiting for it. Are you downloading it? And as far as getting help with finding out what hardware you are running, you can search for specs on your computer by running a search for the computer's model like- Compaq Presario CQ60.

---

### Post by drpjkurian on 2012-04-13
> **DeezyFaReal said:**
> What do you mean you are waiting for it..

Ubuntu precise pangolin (12.04)is still in beta release. It will be released on 28 april 2012

---

### Post by MonkWy on 2012-04-13
Okay all the info is helpful, I will start chasing things down. Thanks everyone. If I remember correctly 12.04 LTS is supposed to be released this month? I have been trying to keep an eye out at [http://www.distrowatch.org](http://www.distrowatch.org)
or is there a different site I should be watching like [http://www.ubuntu.com](http://www.ubuntu.com)?
Please keep in mind I am not very computer litterate, I just know basics with Windows 7. Thank you guys all the same for the replies, I am greatful.

---

### Post by MonkWy on 2012-04-13
I have Ubuntu 10.04.4 LTS Lucid Lynx and 11.10 Oneiric Ocelot on DVD RW. From [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
Also I just seen that Ubuntu 12.04 LST is in Final Beta. So I suppose I can go download it to disk.

---

### Post by raja.genupula on 2012-04-13
yeah we will appreciate your action if you wont care about any bugs and ready for test .

---

### Post by mastablasta on 2012-04-13
you can use command lshw in terminal to list all hardware. 
 
you can use a live cd/usb and use this command if ti's not available in Red Hat :-D
 
Also if you use live session (boot from USB/CD and select "try it") you will see there is always a programme that will give all hardware information in Graphical interface (if oyu dont' liek ocmmand line).
 
release for 12.04 is scheduled for 26th April. : [https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)
 
besides Ubuntu, you might also have a look at it's offspring: Kubuntu (using KDE) and the lighter ones: Xubutnu and Lubuntu.
 
Depending on your hardware you should select the appropriate one.

---

### Post by MonkWy on 2012-04-13
Thanks as I have more time I will look into what you suggested. My ultimate goal is to switch from Windows 7 to just using Ubuntu on my ASUS CM1630. the HP Vecta was only $3 at a garage sale so I thought it wouldn't be much of a lose learning about Ubuntu on it if something went wrong. Thanks again.

---

### Post by raja.genupula on 2012-04-13
> **MonkWy said:**
> Thanks as I have more time I will look into what you suggested. My ultimate goal is to switch from Windows 7 to just using Ubuntu on my ASUS CM1630. the HP Vecta was only $3 at a garage sale so I thought it wouldn't be much of a lose learning about Ubuntu on it if something went wrong. Thanks again.

Ok check that is 12.04 running fine in all cases in your Lappy/System by using its LIVE CD/USB . here cases means MOUSE/KeyBoard/wifi/sound etc .


if it fines then you can go .

---

### Post by MonkWy on 2012-04-13
Thanks, I have alot to learn. I am taking a class this fall at the college where I live, Introduction to Linux. The Instructor says we will be working with Ubuntu 12.04 LTS. Am excited about it. Is late here and am tired, good night everyone. Thanks.

---

### Post by lht2685 on 2012-04-13
> **MonkWy said:**
> Thanks, I have alot to learn. I am taking a class this fall at the college where I live, Introduction to Linux. The Instructor says we will be working with Ubuntu 12.04 LTS. Am excited about it. Is late here and am tired, good night everyone. Thanks.
 
Just try the current version of ubuntu, its actualy rather good :guitar:
 
Or for a try out on your current Windows box, download VMware player (free) and install by pointing to the .iso file of ubuntu. This gives you a virtual mashine inside your normal PC/laptop. Minimum space required is 20Gb, but perhaps give it 30 or 40 if you have the space.

---

### Post by MonkWy on 2012-04-13
I have thought about using Oracle VM VirtualBox. Is the VMware player better? I have 200 GB free on windows machine so no issues there. The HP Vectra VLi8 SF has a 40 GB IDE HDD and 256 MB RAM. Also a Pentium III 550Mhtz CPU. Still looking into the rest of the hardware. Is there anything you guys need to know specific about the HP computer? i e any other hardware info?

---

### Post by raja.genupula on 2012-04-14
> **MonkWy said:**
> I have thought about using Oracle VM VirtualBox. Is the VMware player better? I have 200 GB free on windows machine so no issues there. The HP Vectra VLi8 SF has a 40 GB IDE HDD and 256 MB RAM. Also a Pentium III 550Mhtz CPU. Still looking into the rest of the hardware. Is there anything you guys need to know specific about the HP computer? i e any other hardware info?


No we need more RAM to run .

---

### Post by jerome1232 on 2012-04-14
With those specs you will want to run lubuntu, it uses lxde as it's desktop environment and is meant for low ram environments.

You won't get as much sparkle it'll be snappy. Xubuntu has a bit more sparkle but 256 is pretty low ram, I'd go with Lubuntu.

---

### Post by mastablasta on 2012-04-14
your options with that small amount of ram and weak porcessor are limited. 

Lubuntu is a good choice.
Bodhi linux (based on Ubuntu LTS) is even lighter
--
Both use interface that is still not very mature.

Another option is Chrunchbang linux based on Debian stable or Debian stable (perhaps with LXDE) itself. for some reason it needs much less ram. And it will run on RaspberyPi.

if you can increase your ram, you may be able to run Xubuntujust dont' expect much with such a CPU.

other non Ubuntu very good light Linux options include Slitaz and Puppy Linux. They both work on very old maschines with latest software...

addition: VritualBox works great: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

It is also a good way to run a liveCD (live session) so you can quickly try many systems and see how they look like before installing them.

---

### Post by jerome1232 on 2012-04-14
> **mastablasta said:**
> 

addition: VritualBox works great: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

It is also a good way to run a liveCD (live session) so you can quickly try many systems and see how they look like before installing them.

Not with 256 MB of ram on the host it doesn't :P

---

### Post by MonkWy on 2012-04-15
Most likely I will, some day, set up the HP as a firewall with IPCop v2.0.2  Prolly be a good job for it right?

---

### Post by mastablasta on 2012-04-15
> **jerome1232 said:**
> Not with 256 MB of ram on the host it doesn't :P

he has much more powerfull windows computer and was thinking of using VM. that newer maschine can be used with virtualbox as it is more than enough to satisfy the requirements.

---

### Post by mastablasta on 2012-04-15
> **MonkWy said:**
> Most likely I will, some day, set up the HP as a firewall with IPCop v2.0.2  Prolly be a good job for it right?

yes, but why. as an experiemnt sure. but otherwise it will use a lot of power just for a firewall.

you can probably also use it as server i think. though depedns really what kind of server. maybe data storage or webserver. could also run some older multiplayer games (maybe enemy territory server and such but not too many new ones i guess.

---

### Post by MonkWy on 2012-04-24
Thanks everyone, for all the advice and helpful information. I have a new question regarding anti-virus and firewalls. Should I post it here under a new title or in another area/category in this forum?

---

