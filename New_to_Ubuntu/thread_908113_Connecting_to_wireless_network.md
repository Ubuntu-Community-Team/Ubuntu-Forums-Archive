---
title: "Connecting to wireless network"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by scrutineer on 2008-09-02
I've installed Ubuntu 8.04 LTS on my HP desktop on a second partition. I have a wireless PCI card that I use to connect to the internet via a modem when running in windows. Do I have to manually activate the PCI card in Ubuntu in order to connect to the wireless network and make use of it's resources ?:rolleyes:

---

### Post by skrållarn on 2008-09-02
check out [http://wiki.ubuntu.com/LaptopTestingTeam](http://wiki.ubuntu.com/LaptopTestingTeam) and see if your laptop have been tested with ubuntu. many models are tested and if it doesnt work right away you will often find step-by-step sollutions on how to make it work

---

### Post by porchrat on 2008-09-02
you'll probably need a driver for it if one isn't installed already.

If one is installed it will be under "System --> Administration --> Hardware Drivers"

to see what PCI card you're running, and see whether or not it has drivers installed (and in case you need to go and find drivers) type this in the terminal:

```
sudo lshw -C network
```

Then you at least paste the ouput of that here on the forum so we can have a look.

---

### Post by porchrat on 2008-09-02
> **skrållarn said:**
> check out [http://wiki.ubuntu.com/LaptopTestingTeam](http://wiki.ubuntu.com/LaptopTestingTeam) and see if your laptop have been tested with ubuntu.

I think it is a desktop PC using a wireless PCI card actually

---

### Post by Dougie187 on 2008-09-02
Do you know what kind of wireless card you have in your desktop?

Also, I am not sure what
> I have a wireless PCI card that I use to connect to the internet via a modem when running in windows.
means. So I can't help with that part. But a lot of wireless cards work out of the box in ubuntu, so depending on which type you have we could help you out. If it doesn't work out of the box though, you will probably have to install ndiswrapper and then download the windows drivers for it, and set it up that way.

---

### Post by barbedsaber on 2008-09-02
> **porchrat said:**
> I think it is a desktop PC using a wireless PCI card actually

You should know if its a  desktop PC! :) :lolflag

---

### Post by porchrat on 2008-09-02
> **barbedsaber said:**
> You should know if its a  desktop PC! :) :lolflag

Dude...it isn't my thread...someone else made the mistake and I was correcting him...keep up

---

### Post by skrållarn on 2008-09-02
> **porchrat said:**
> I think it is a desktop PC using a wireless PCI card actually

i think you´re right...:-#

[QUOTE=scrutineer]I've installed Ubuntu 8.04 LTS on my HP desktop[/QUOTE]

---

### Post by skrållarn on 2008-09-02
> **barbedsaber said:**
> You should know if its a  desktop PC! :) :lolflag

Dont you know that laptops also has a PCI bus?
the mini-PCI.

---

### Post by porchrat on 2008-09-02
wow I didn't know that...thought all you got were PCMCIA cards.  We don't get those around here, or at least if we do I have never seen them.  They are quite interesting, thank you for pointing those out to me.

Anyway we are sort of getting off topic, this poor fellow is asking for help and we're going off on a tangent about laptop cards lol.

As I said before check your "Hardware Drivers" menu under "System --> Administration" to see if there is a driver there, alternatively type:

```
sudo lshw -C network
```

into the terminal and paste the ouput here so we have a better idea of what is going on.

---

### Post by scrutineer on 2008-09-02
Well thanx for the reply & jacking, made me feel right @ home:wink: I'm still getting used to the Ubuntu environment, so excuse if i run my mouth in an otherwise direction. anyway

To clear out some confusion, I have an HP desktop worksation, the PCI card is as Intellinet Wireless Super G PCI Card(108 Mbps Wireless networking for desktop PC) I'l type the sudo in the terminal to make sure then paste the output.

---

### Post by Dougie187 on 2008-09-02
Just so you know, the command that has been offered in this thread does not require the use of sudo.

It is not a good practice to "liberally" use the sudo command, so you want to make sure what you are using it for *NEEDS* it. 

Seeing as it is using administrative privileges, this can get you in a lot of trouble using certain commands, so if you are going to use sudo a lot make sure you know what you're doing. Also, there are stickies all over the place talking about using commands carefully.

---

### Post by porchrat on 2008-09-03
> **Dougie187 said:**
> Just so you know, the command that has been offered in this thread does not require the use of sudo.

It is not a good practice to "liberally" use the sudo command, so you want to make sure what you are using it for *NEEDS* it. 

Seeing as it is using administrative privileges, this can get you in a lot of trouble using certain commands, so if you are going to use sudo a lot make sure you know what you're doing. Also, there are stickies all over the place talking about using commands carefully.

Whenever I run "lshw" it says you should run it with administrator permissions.  ALthough I've never seen it give a different result without sudo I still use sudo to make sure.

When the OS talks...porchrat listens

---

### Post by Dougie187 on 2008-09-04
> **porchrat said:**
> Whenever I run "lshw" it says you should run it with administrator permissions.  ALthough I've never seen it give a different result without sudo I still use sudo to make sure.

When the OS talks...porchrat listens

I think its because there are certain classes that you could call lshw with that need to have sudo to read the information. But network is not one of those as far as i know. So when you do a ```
lshw -C network
``` you don't need to have sudo in front of that. I'm just giving this advice because if people are more cautious to use sudo they will get in less trouble, for instance if someone tells him to type ```
sudo rm -rf /
``` that would screw up his whole system, but if he knows to be weary of using sudo, then he could ask about it and find out it will screw him over before he does it.

---

