---
title: "USB kit for beginners?"
date: 2008-08-24
forum: Programming Talk
---

### Post by raccoonone on 2008-08-24
I'd like to learn how to interface with USB devices, and how to build them. Is there a good kit for beginners, where I could start out building something really simple (like an LED that I could control from a Python or C/C++ program)? Eventually I'd like to move on to some robotics, but I've got a lot to learn first. I've read a little about the USB spec, and tried getting input from my mouse with libhid, but all I managed to do was find out things like the vendor and product ID.

---

### Post by jinksys on 2008-08-24
> **raccoonone said:**
> I'd like to learn how to interface with USB devices, and how to build them. Is there a good kit for beginners, where I could start out building something really simple (like an LED that I could control from a Python or C/C++ program)? Eventually I'd like to move on to some robotics, but I've got a lot to learn first. I've read a little about the USB spec, and tried getting input from my mouse with libhid, but all I managed to do was find out things like the vendor and product ID.

What is your electronics background?

---

### Post by raccoonone on 2008-08-25
> **jinksys said:**
> What is your electronics background?

I've soldered, and assembled a few circuits from kits (strobe lights and the like). I wouldn't know how to design anything complex from scratch, but I'm an electrical enginnering and computer science major and will be taking my introductory class in circuit design this fall. So I should know more soon. I've also taken electricity and magnetism in physics, so I'm familiar with the theory.

---

### Post by jinksys on 2008-08-25
If what you want to do is essentially learning how to interface with USB devices, you could buy a USB LCD module like this:

[[img]https://www.crystalfontz.com/phpthumb/phpThumb.php?id=644&w=430[/img]](https://www.crystalfontz.com/products/632usb/index.html)

It comes with sample code, but you could always write your own interface.

---

### Post by raccoonone on 2008-08-25
> **jinksys said:**
> If what you want to do is essentially learning how to interface with USB devices, you could buy a USB LCD module like this:

[[img]https://www.crystalfontz.com/phpthumb/phpThumb.php?id=644&w=430[/img]](https://www.crystalfontz.com/products/632usb/index.html)

It comes with sample code, but you could always write your own interface.

Thanks, that looks pretty nice. I was kind of hoping for a kit that had LEDs, light sensor, maybe a temp sensor--several things that I could hook up to the controller. But maybe an LCD screen like that is a better place to start?

---

### Post by jinksys on 2008-08-25
[Spark Fun](http://www.sparkfun.com/commerce/categories.php) is also a good place to look.  They have USB development platforms.

---

### Post by raccoonone on 2008-08-25
> **jinksys said:**
> [Spark Fun](http://www.sparkfun.com/commerce/categories.php) is also a good place to look.  They have USB development platforms.

Thanks, they have [a tutorial series for beginners]("http://www.sparkfun.com/commerce/tutorial_info.php?tutorials_id=57") that looks nice. It uses the ATmega168, is that a good microcontroller for beginners? I don't think it has a USB interface, but maybe it would be a good place to start. Is there a different kit that uses USB that you would recommend instead (or for after the ATmega168)?

---

### Post by jinksys on 2008-08-26
> **raccoonone said:**
> Thanks, they have [a tutorial series for beginners]("http://www.sparkfun.com/commerce/tutorial_info.php?tutorials_id=57") that looks nice. It uses the ATmega168, is that a good microcontroller for beginners? I don't think it has a USB interface, but maybe it would be a good place to start. Is there a different kit that uses USB that you would recommend instead (or for after the ATmega168)?

I wouldn't know, sorry.  The only CPU that I've worked with at a low level is the x86 architecture.

---

### Post by raccoonone on 2008-08-26
> **jinksys said:**
> I wouldn't know, sorry.  The only CPU that I've worked with at a low level is the x86 architecture.

Thanks anyway. I looked into it more, and it seems that there is a USB interface, that at least allows you to program it. I think I'll get one to play with. It looks pretty simple, and they're cheap too.

---

