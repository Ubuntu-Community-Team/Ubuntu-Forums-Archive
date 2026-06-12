---
title: "How to make USB persistent?"
date: 2016-10-20
forum: New to Ubuntu
---

### Post by puppylover101 on 2016-10-20
I have to do this for a school project :)

I need to make the USB persistent so it's able to save all the files on it. This means that if I download applications on it and then reboot the PC/take out USB, those applications will be there. How do I do this, thanks! :)

---

### Post by C.S.Cameron on 2016-10-20
If you are running Ubuntu go to the hardware center and install mkusb, it has an option to make a USB with a persistent partition.
If you need <4GB persistence you can use UNetbootin, it can make a persistence file. It has Linux and Windows versions.

---

### Post by colmax on 2016-10-20
Hi P
So impressed someone of school age is into linux & doing live-installs :)
LinuxLive is another option for persistance
You could also search the forums for advice on this subject (top right of page)
Cheers & good luck

---

### Post by coffeecat on 2016-10-21
> **puppylover101 said:**
> I have to do this for a school project :)

Just a reminder of one of our forum rules in the [Posting Guidelines](https://ubuntuforums.org/showthread.php?t=2158945): 

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

I've jailed one post that included a step-by-step howto to achieve what the OP wants, and is obviously in breach of the spirit of our rules. I'll leave the suggestions for specific software that creates USB installs with persistence as I very much doubt that would satisfy the demands of the school project! :)

@puppylover101, good luck with your project and I hope you find material that helps you learn important stuff as well as simply achieving the end result of persistence in a USB installation.

---

### Post by bubbajack on 2016-10-21
Hi puppylover101,
If this really is something you should do as an assignment I advice  you to try stuff for yourself, eventually banging your head. In result you'll understand all this stuff much better.
Just a hint: you can actually INSTALL ubuntu (or any other distro) on a USB flash drive. With a 128gb USB3.0 drive you can have a  complete portable system (right now I'm running Ubuntu 16.04 off such a flash drive)

Have fun!

---

### Post by c.s.cameron.peng on 2016-10-21
Unless the op is in university I doubt the teacher would expect the students to design a persistent USB system from scratch.
The flash drive is probably for bringing lots of homework home.


Why the heck did my username change?

---

### Post by puppylover101 on 2016-10-22
yhea im not in university. I think i got it tho thanks..

---

### Post by kurt18947 on 2016-10-22
If your school is in the U.S. and knows there's more to computers than Microsoft & Apple, kudos to them!

---

### Post by sudodus on 2016-10-23
Welcome to the Ubuntu Forums, *puppylover101* :-)

> **C.S.Cameron said:**
> If you are running Ubuntu go to the hardware center and install mkusb, it has an option to make a USB with a persistent partition.
If you need <4GB persistence you can use UNetbootin, it can make a persistence file. It has Linux and Windows versions.

I don't know the Ubuntu hardware center. Do you mean the Ubuntu Software Center? Anyway, you cannot find mkusb there [yet]. You can find easily it if you search the internet for **mkusb** (with one of the major search engines).

> **c.s.cameron.peng said:**
> Unless the op is in university I doubt the teacher would expect the students to design a persistent USB system from scratch.
The flash drive is probably for bringing lots of homework home.


I agree.

> **puppylover101 said:**
> yhea im not in university. I think i got it tho thanks..

Please let us know how you are solving your problem!

> **kurt18947 said:**
> If your school is in the U.S. and knows there's more to computers than Microsoft & Apple, kudos to them!

I think this applies to most countries in the world ;-)

---

### Post by telcar on 2016-10-23
I'm a beginner as well but download this ( [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) )and an Ubuntu disk image .ISO from here ( [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) ). It does it all for you and anything you do on the os will save to the flash drive and be good to ge to boot from anywhere with all your files

---

### Post by C.S.Cameron on 2016-10-23
> **sudodus said:**
> Welcome to the Ubuntu Forums, *puppylover101* :-)

I don't know the Ubuntu hardware center. Do you mean the Ubuntu Software Center? Anyway, you cannot find mkusb there [yet]. You can find easily it if you search the internet for **mkusb** (with one of the major search engines).



You are correct about Ubuntu Hardware Center, (I guess Ubuntu Hardware Center is pronounced Amazon).
However if I search the Software Center, I do find **mkusb**.

Edit:
Oops, unfortunately I see it is not in Hardware Center until after it is installed.

---

### Post by sudodus on 2016-10-23
I know that English is seldom spelled like it is pronounced, but you beat me with this one :-D

---

### Post by rasmus91 on 2016-10-24
Rufus is also a good option for making a persistent live USB.

Generally Rufus is really good for flashing OS's unto USB's. Sadly it's only available from windows.

---

