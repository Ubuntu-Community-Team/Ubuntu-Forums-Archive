---
title: "No working internet"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by M3TAL1QU1D on 2008-06-23
Hi,

I am new here and I am also new (and a total n00b) to linux as well. I had recently triplebooted my laptop with vista/xp/ubuntu 8.04 (Hardy Heron). I was able to install it and boot it up sucessfully without any problems. Right now i am trying to to all the software updates by installing the packages from the repositories, but i am finding this hard to do seeing i have no internet connection.](*,)](*,)](*,) I am using a dv2615nr hp pavillion laptop. 

My question is what is it i need to do to get the internet working, preferebly the wireless, so that i can continue setting up ubuntu?

Let me know if any info is needed

Thanks in advance:)

---

### Post by secondstage on 2008-06-23
Have you tried to go to System > Administration > Network, and configure it frok there? To do anyhting you need to Unlock it, by clicking unlock ,and typing your password. Also, type 
```
iwconfig
```
into terminal (Applications > Accessories > Terminal), and press enter. Then post the ouput of that command. 
And do 
```
lshw -C network
```
Hope this helps.

---

### Post by M3TAL1QU1D on 2008-06-23
I've tried going to sys -> admin -> network and there was only two options, one for wired internet and the other for dial-up.

I went into terminal and did what you said and this came up,

> dylan@dylan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dylan@dylan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:16:d3:f1:da:5b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
dylan@dylan-laptop:~$ 


No luck with the wireless though

I am not to sure what all that is above or what a super user is. Thats me being a newbie for ya.

---

### Post by secondstage on 2008-06-24
Try [this how-to]("http://ubuntuforums.org/showthread.php?t=769990"). It is for your wireless card.

[COLOR="Red"]WARNING: IMPROPER USE OF THE SUPERUSER MAY RESULT IN DAMAGE TO YOUR COMPUTER![/COLOR]Now that that has been established, the Super-user(su) is a user that has access to your whole system. You can become the su by going into terminal, and typing su. Then typing in your password (and enter, you should do this at the end of a command, it tells the computer "do this"). Like I siad before don't use it unless you knwo what your doing. The sudo command is used alot in Linux when installing programs and what not. You can understand sudo as super-user-do. 

iwconfig shows your network and what is allowing you to connect to the network. lshw lists capabilities, and -C filters the capabilities to the CLASS. The CLASS in this situation is network. If you ahevany other questions I'll try my best to answer them!

--secondstage

---

### Post by M3TAL1QU1D on 2008-06-24
Thanks for the info! Much appreciated! 

From what im reading in other peoples posts on the guide you sent me, it gives me much hope that will be the solution. Unfortunatly, i cannot do the guide right now since i am nowhere near a wireless connection. I am actually trying to set up an EV-DO card as well. I would use the built in wi-fi at school, and the EV-DO at home. 

I Have found a sprint setup guide for the card (its a 595u sierra wireless btw) and i feel i am close to gettin it running. But the problem i am runing into with that is i need to get ahold of kppp or gnome-ppp (i think thats what it is). I was able to find one thru windows but when i try to install the package i get an error like "dependancy is not satisfiable kdelibs4c2a". What does that mean? My guess it is some sort of file i need maybe???

Thanks for any help!

---

### Post by secondstage on 2008-06-24
Yeah you guessed it, you need to install something else to install the first one. Almost all of the packages are at [this site]("http://packages.ubuntu.com/hardy/"), where you can organize them by type. Or just go to [this other site]("http://packages.ubuntu.com/hardy/allpackages") to list all of the packages they have in alphebetical order. This may take alot of time to load. Just look around there. Finally [here]("http://packages.ubuntu.com/hardy/kdelibs4c2a") is the link for the package you need. 

You may get lost in a ocean of dependancies, so if you feel like you are going nowhere, make sure to keep track of your progress, so that you don't get more lost, and forget a package. I am speeking from personal memory, I had to spend alot of time, to install one application. Don't worry too much though.

Once again, any questions I will try my best to help!

--secondstage

---

### Post by M3TAL1QU1D on 2008-06-24
Thanks alot (again!)!:)

Well, it turns out i do need more than just that, and i have a feeling i will need do get alot more of those files to satisfy the depenencies.

I have a feeling this will take awhile...

---

### Post by secondstage on 2008-06-24
Keeping a log will really help you if you are starting late in the day, or don't have enough time to finish. Start with the original package, and indent one time for every dependency more that you need to install. You might find that you run off the page. Make sure to write down the name of the package next, so that you're confused at what to do next, later on.

---

### Post by M3TAL1QU1D on 2008-06-24
Argggggg.....

I seemed to have ran into a snag. I am trying to install the libopenexr2c2a just to have it give me a message that it wont install. I guess i need that to meet a dependency for 
kdelibs4a2c. Is there anything i need to do special to get this to work, or find another one possibly? I feel i am close to solving this freakin thing to just run into a stubborn program!!! AAAHHH!!!!

---

### Post by secondstage on 2008-06-25
I did a google of the package, and it looks to me like there isn't a Hardy version. I did some more googling, and found that package on another site. This new package is in testing but I should work. I have not tested this, so what I am saying now is from other posts. If you go to [this site]("https://edge.launchpad.net/~secretlondon/+archive"), you will find two lines of code called apt sources.list entries. You neeed to open a terminal, and type...
```
sudo gedit /etc/apt/sources.list
```
This will open up a window with words in it. Scroll all the way to the bottom, and copy-paste those two lines in it. Click save, and exit. Next, type...
```
sudo apt-get update
```
This will install the two lines that you pasted into the file.The package should be install now. Finally, continue to satisfy the dependancies.

P.S. Take a breather. Installing while mad isn't as fun as installing when happy.

--secondstage

---

### Post by M3TAL1QU1D on 2008-06-25
Thank you for the above methoid, but it did not work because i dont have the internet. that is what i am trying to accomplish by installing all these apps to get my sierra wireless 595u card working. but thanks for the help yet again. 

i got a message when i tried intsalling the libopenexr2c2a, it said it was having a conflict with libopenexr2ldbl. i am wondering if there is a way to get past this, or maybe a different version might work???

---

### Post by secondstage on 2008-06-25
Option 1: Have some with internet connection post what you need(me if you want)

Option 2: Get a new wireless card that is known to work with Ubuntu Hardy

I think that your problem is the number one problem for Linux users. It's that there isn't much support for products that are a common for Windows users.

---

### Post by M3TAL1QU1D on 2008-06-25
Well, i guess ill have to try the next thing besides kppp, i think gnome ppp or something. Ill see how that goes now that i have a bit more direction.

Thanks for the help tho!

---

