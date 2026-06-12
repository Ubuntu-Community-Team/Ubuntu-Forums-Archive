---
title: "Can't detect wifi on Ubuntu 10.04 LTS"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by caliber38 on 2012-02-07
Hello there.

I'll go straight to the point.

For some reason, my network manager on 10.04 LTS can't detect my wifi. That's why I'm typing this from my Mac OS (Intel). 

Was there possibly a part of the installation that I forgot?

Can someone please guide me step by step to resolve this.

---

### Post by RedSingularity on 2012-02-07
You probably did not forget anything.  Its a matter of loading the correct modules.  Did you take note if the WiFi worked when using the Live CD?

---

### Post by Bucky Ball on 2012-02-07
Plug in with a cable and get updates then check 'Additional Drivers' (maybe hardware drivers in 10.04).

You could also post the output of:

```
lspci
```... from the terminal so we can determine your wireless card and help further. It is the line that starts with 'Network Controller'. ;)

---

### Post by 3rdalbum on 2012-02-07
Ubuntu 10.04 is pretty ancient. Have you tried 11.10 which is the latest Ubuntu? It has more up-to-date hardware support.

---

### Post by Linux Dutchman on 2012-02-07
> **3rdalbum said:**
> Ubuntu 10.04 is pretty ancient. 
 
Why??? It's totally not ancient! It's still the latest LTS version which will be kept up-to-date till 2013. All the other (non) LTS versions are ancient after 1 year (end-of-life). 
 
When 12.04 will be launched officially, then you can say that 10.04 is a bit outdated, but still not ancient.
 
DOS 3.3 is ancient, Windows 3.11 is ancient..... But Ubuntu 10.04 isn't.
 
 
 
@topic starter:
Try installing Wicd. Wicd is a much better network manager then the standard Gnome network manager. Use synaptic to remove the Gnome network manager and installing Wicd. Be smart and install Wicd first before removing the Gnome network manager!
 
Wicd provide you with a bit more info about Wifi network than the Gnome network manager. I'm using it and i'm really happy with it!
 
 
Then what you can do is searching this forum for a solution. There are many topics related to your problem. Search for it and read them. It might be very usefull to you!

---

### Post by caliber38 on 2012-02-07
> **Linux Dutchman said:**
> 
 
 
 
@topic starter:
Try installing Wicd. Wicd is a much better network manager then the standard Gnome network manager. Use synaptic to remove the Gnome network manager and installing Wicd. Be smart and install Wicd first before removing the Gnome network manager!
 
Wicd provide you with a bit more info about Wifi network than the Gnome network manager. I'm using it and i'm really happy with it!
 
 
Then what you can do is searching this forum for a solution. There are many topics related to your problem. Search for it and read them. It might be very usefull to you!

Thanks!

---

### Post by 3rdalbum on 2012-02-07
> **Linux Dutchman said:**
> Why??? It's totally not ancient! It's still the latest LTS version which will be kept up-to-date till 2013. All the other (non) LTS versions are ancient after 1 year (end-of-life). 

It's not actually kept up-to-date. It is merely given security fixes. There is no additional hardware support added after release day. If the OP's wireless card was released after March 2010 it probably won't be working on anything less than 10.10.

Ubuntu 10.04 is ancient for Ubuntu and I don't see any reason for new users to start with an old distro. Especially with 10.04's age - normally Ubuntu releases are totally obsolete after 18 months, but the LTS releases are essentially kept on life support for twice as long.

> @topic starter:
Try installing Wicd. Wicd is a much better network manager then the standard Gnome network manager. Use synaptic to remove the Gnome network manager and installing Wicd. Be smart and install Wicd first before removing the Gnome network manager!

Check that Wicd actually works before removing Network Manager. In fact, DON'T remove Network Manager. Wicd only deals with wireless and can't help you with wired or mobile broadband connections; whereas Network Manager can.

Personally, I've never come across a wireless card that Wicd could manage and Network Manager couldn't. Underneath, they all use the same kernel wireless support.

I'd be more interested in seeing if you can use the Additional Drivers program (System > Administration > Additional Drivers, in 10.04) to get the driver downloaded, or as I mentioned before if it is supported out-of-the-box on a later version of Ubuntu.

---

### Post by resander on 2012-02-07
I have been on Ubuntu 10.04 since it was released and installed on several computers without wifi problems. I have used Belkin, Netgear and Virgin media's Super-Hub routers. The last install was for a netbook on Ubuntu 10.04.03 LTS. 

Are you using Ubuntu 10.04.03 LTS? If not, do.

Just in case...
 
Does wifi work with the LIVE CD or with Windows? Have you checked the router settings? Does your physical router work on other PCs or operating systems? 

Search Ubuntu forums and google on <your router name&model> AND Ubuntu.

If all these make no difference, get latest Ubuntu 11.10 Live CD and try.

---

### Post by adrien214 on 2012-02-07
Is anybody trying to actually help the OP here?

resander, open a terminal and type in the following command:

```
sudo rfkill list all
```

this will output a list of all the radio device on your machine and their statuses. Past the output here in the forum (select the text with the mouse cursor in the terminal>right click>copy).

Do the same for the following command:

```
lspci | grep -i net
```

---

### Post by Bucky Ball on 2012-02-07
> **3rdalbum said:**
> Ubuntu 10.04 is pretty ancient. 

It is the current long-term support release fully supported until April 2013, server until 2015, and the OP might be using it for a very good reason (production machine). It is stable and reliable (as LTS releases are intended). ;)

---

### Post by wildmanne39 on 2012-02-07
Hi, if you have tried additional drivers, then please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

