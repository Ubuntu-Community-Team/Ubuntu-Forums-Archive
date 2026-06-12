---
title: "Dial-up connectivity"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by DiscipleRayne on 2008-10-21
I'm new to linux, and ubuntu. I currently use a dial up connection, but I cannot get it to work on ubuntu. I use a HDAUDIO Soft Data Fax modem with SmartCP, and I installed the driver from [www.linuxant.com](www.linuxant.com), I'm not sure how to check if it worked however. How can I check to see if the driver is working correctly? By the way, I set up the network modem connecting perfectly, but i'm not sure how to check and see why it's not doing anything, I can't even tell if it's even trying to connect.

Any help is appreciated.

---

### Post by sazan on 2008-10-21
see this...might help...........[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by DiscipleRayne on 2008-10-21
> **sazan said:**
> see this...might help...........[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Lol, I saw that coming. My modem aparently just isnt compatible with ubuntu even though scanModem says it is.

---

### Post by kahlil88 on 2008-10-21
Modems can really be a pain with Linux, unless you get a hardware modem like I did.

---

### Post by DiscipleRayne on 2008-10-21
Looks like I'll be doing the same.

---

### Post by ardvark71 on 2008-10-21
> **kahlil88 said:**
> Modems can really be a pain with Linux, unless you get a hardware modem like I did.

I agree fullheartedly. :)

The trick is to making sure that the modem is a true hardware modem and from my experience, the only ones these days that are available (in this catagory) are external modems like this one...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104135](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104135)

Best Regards...

---

### Post by dstin1 on 2008-10-21
Post your scan modem results and you may get some help.

---

### Post by kahlil88 on 2008-10-21
Mine is a US Robotics [3CP-2977]("http://www.google.com/products?q=3cp2977") PCI hardware modem. Bought it on eBay a few years ago for about $20.

---

### Post by ardvark71 on 2008-10-21
> **kahlil88 said:**
> Mine is a US Robotics [3CP-2977]("http://www.google.com/products?q=3cp2977") PCI hardware modem. Bought it on eBay a few years ago for about $20.

Hi...

Yes, I had forgotten about these. :)

How well does yours work? I bought one (either the same model or one just like it) a year or two ago and had problems setting the IRQ. It automatically defaulted to COM 4, which I guess is a virtual port whereas Linux requires a real port such as COM 1 or COM 2.

Along with that, there was no driver included with it and I couldn't find the exact driver it needed, despite my searches.

Best Regards...

---

### Post by Irihapeti on 2008-10-21
If scanmodem says that your modem has a Conexant chipset, then it may be worth your while posting to the mailing list at [www.linuxant.com](www.linuxant.com) and asking for help.

Possibly you got the wrong driver. There are HSF drivers and HCF drivers (and no, I don't know much about the differences).

For testing if a modem really is doing anything or not, I like to use Cutecom. (It's in the repositories, and if you can't get a connection, you can download it from [http://packages.ubuntu.com](http://packages.ubuntu.com) . It does have quite a few dependencies, though.) You can type the actual AT commands to the modem and see what kind of response you get. 

I've had no luck with Network Manager with my dialup modem, by the way. Gnome-PPP is my dialup manager of choice.

---

### Post by lemuriaX on 2008-10-21
You might look into getting an external serial or USB dial-up modem, like the USB one described here:

[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)  

or similar.

---

### Post by kahlil88 on 2008-10-22
> **ardvark71 said:**
> Hi...

Yes, I had forgotten about these. :)

How well does yours work? I bought one (either the same model or one just like it) a year or two ago and had problems setting the IRQ. It automatically defaulted to COM 4, which I guess is a virtual port whereas Linux requires a real port such as COM 1 or COM 2.

Along with that, there was no driver included with it and I couldn't find the exact driver it needed, despite my searches
It works great - the Linux driver (RPM) is available on the manufacturer's website, but I only needed it for older versions of SuSE and Fedora. Should work out of the box with Ubuntu. :)

---

### Post by ardvark71 on 2008-10-22
> **kahlil88 said:**
> It works great - the Linux driver (RPM) is available on the manufacturer's website, but I only needed it for older versions of SuSE and Fedora. Should work out of the box with Ubuntu. :)

Hi...

Ok, thanks, I might give another one a try if and when I build another Ubuntu/Kubuntu system. :KS

Best Regards...

---

### Post by DiscipleRayne on 2008-10-23
> **Irihapeti said:**
> If scanmodem says that your modem has a Conexant chipset, then it may be worth your while posting to the mailing list at [www.linuxant.com](www.linuxant.com) and asking for help.

Possibly you got the wrong driver. There are HSF drivers and HCF drivers (and no, I don't know much about the differences).

For testing if a modem really is doing anything or not, I like to use Cutecom. (It's in the repositories, and if you can't get a connection, you can download it from [http://packages.ubuntu.com](http://packages.ubuntu.com) . It does have quite a few dependencies, though.) You can type the actual AT commands to the modem and see what kind of response you get. 

I've had no luck with Network Manager with my dialup modem, by the way. Gnome-PPP is my dialup manager of choice.

Thanks for all of the help guys, I'm sorry I didn't reply sooner. Thats the thing, I don't know if the driver worked or not, I don't even know if I needed the driver, I just know that when I use the connection manager, nothing happens I don't really understand the connection manager and I can't use Gnome-PPP because I don't have a connection on ubuntu to download what I need to compile it, and I can't find an already compiled version.

---

### Post by cek on 2008-10-23
This USB modem works flawlessly -- just setup the modem to use /dev/ttyACM0


[http://www.amazon.com/56K-USB-Modem-Windows-Linux/dp/B0013FDLM0/ref=sr_1_2?ie=UTF8&s=electronics&qid=1224775700&sr=8-2](http://www.amazon.com/56K-USB-Modem-Windows-Linux/dp/B0013FDLM0/ref=sr_1_2?ie=UTF8&s=electronics&qid=1224775700&sr=8-2)

---

### Post by Radioman991 on 2008-10-23
FWIW

Set up an old Dell Optiplex for my father-in-law.  Managed to get the slot Dell modem to work...but it would stop working at random.  Finally went to Staples and bought a serial external modem.  Issue now gone.  To cut your stress level down, I would recommend an external modem...YMMV.

PK

---

### Post by Irihapeti on 2008-10-23
You can download Gnome-PPP from [http://packages.ubuntu.com/hardy/net/gnome-ppp](http://packages.ubuntu.com/hardy/net/gnome-ppp) .

---

