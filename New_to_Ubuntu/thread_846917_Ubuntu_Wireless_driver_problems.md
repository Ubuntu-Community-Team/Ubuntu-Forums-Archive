---
title: "Ubuntu Wireless driver problems"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by anabi on 2008-07-02
Hi,

I am new to Ubuntu and have spent the last few days trying to find a way to install a driver for my intel wireless card. I have read through documentation and still do not understand.

I found a linux version of the driver which gives me a file and says I have to copy it into [COLOR="Red"]/lib/firmware[/COLOR] folder. I tried this but filesystem is owned by [COLOR="Red"]'root'[/COLOR]. I found topic on forum with something about [COLOR="Red"]chmod[/COLOR]. But I still do not understand how to acess the filesystem files through my terminal. I can only acces things on my [COLOR="Red"]Desktop[/COLOR].

I also found other documentation which suggests [COLOR="Red"]NDIS[/COLOR] to install windows drivers:

> 
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.

   1.

      Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2.

      Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).
   3.

      Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).
   4.

      Select Install new driver.
   5.

      Choose the location of your Windows .inf file and click Install.
   6.

      Click OK.



I tried this, but after i install the [COLOR="Red"]ndis-utility[/COLOR], I cannot fint the [COLOR="Red"]'Windows Wireless Drivers'[/COLOR] option under [COLOR="Red"]System -> Administration[/COLOR]

I would greatly appreciate it if anyone could help me with this problem, or perhaps suggest a better way to install my wireless driver in Ubuntu.

Thank you

---

### Post by nothingspecial on 2008-07-02
Nautilus gives you root permissions over folders.

```
gksudo nautilus
```

navigate to /lib/firmware and you will be able to copy the file(s).

---

### Post by cariboo on 2008-07-02
You didn't install ndisgtk, you only installed the utlitities package you have to install:

ndisgtk
ndiswrapper-common

Also.

Once you've installed those to files, it is pretty simple. Make sure you have the .inf file as that is what is needed to install the windows drivers.

Jim

---

### Post by tashmooclam on 2008-07-02
I believe Intel wireless drivers are included in Ubuntu already. I can't remember what steps I did to enable my Intel wireless card, but it was very simple and I downloaded nothing.

---

### Post by tashmooclam on 2008-07-02
I'm not able to help, but just a comment. There is no need to use windows drivers and a wrapper to make it work in Linux if your card is Intel. The Intel wireless card drivers for Linux are in Ubuntu. But, I can't remember well what I did about this so many months ago. This is probably why Dell has Intel wireless cards on their ubuntu laptops.

---

### Post by anabi on 2008-07-02
> **cariboo907 said:**
> You didn't install ndisgtk, you only installed the utlitities package you have to install:

ndisgtk
ndiswrapper-common

Also.

Once you've installed those to files, it is pretty simple. Make sure you have the .inf file as that is what is needed to install the windows drivers.

Jim

Thanks for the replies.

But I could not find ndisgtk on the list in the Synaptic Package Manager. Do I have to download that file separetely?

---

### Post by anabi on 2008-07-02
> **tashmooclam said:**
> I'm not able to help, but just a comment. There is no need to use windows drivers and a wrapper to make it work in Linux if your card is Intel. The Intel wireless card drivers for Linux are in Ubuntu. But, I can't remember well what I did about this so many months ago. This is probably why Dell has Intel wireless cards on their ubuntu laptops.

Thanks for that tip, I will try to find information on this. If you do happen to remember please let me know.
Thank you

---

### Post by nothingspecial on 2008-07-02
Make sure you have all the repositories checked.
System >Administration >Software Sources then put a tick next to Universe and Multiverse.
When you close the window it will ask you if you want to reload. Do this. Then```


sudo apt-get install ndisgtk ndiswrapper-common
```

---

### Post by anabi on 2008-07-02
nothingspecial,

I did as you explained, went to System>Administration>Software Properties. But when I tick Universe and Multiverse, it tries to connect to the internet to download, as my wireless card driver isnt installed, i have no internet connection on Ubuntu. 

Also when i type 
```


sudo apt-get install ndisgtk ndiswrapper-common
```[/QUOTE]

into the terminal i get the following error:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndisgtk

Any suggestions? Thank you

---

### Post by nothingspecial on 2008-07-02
Can you get a wired connection to the internet. Things will be a lot easier if you can. That`s why you`re getting the errors.

---

