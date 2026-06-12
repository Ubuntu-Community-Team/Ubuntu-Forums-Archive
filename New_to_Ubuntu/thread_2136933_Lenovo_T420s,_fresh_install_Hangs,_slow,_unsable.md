---
title: "Lenovo T420s, fresh install: Hangs, slow, unsable"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by Magick93 on 2013-04-19
HI all

I got locked out of my windows os due to a faulty bit locker drive encryption, so I installed the latest LTS ubuntu.

My computer is a Lenovo T420s. I installed the 64bit version of ubuntu.

When I try to use gmail in either firefox or chrome the whole computer hangs. Other web pages also effect the whole system in a similar way. 

In general, its running like a pig - basically its unsable. 

What can I do? Besides buying a windows license?

---

### Post by mastablasta on 2013-04-19
What are computer specs? Did you install any proprietary drivers?

BTW pigs are not really slow animals... ;-)

---

### Post by lisati on 2013-04-19
Just to clarify, which Ubuntu version have you installed? The reason I ask is that if someone finds this thread in a year or two, the "latest" version will be different to the one you're asking about.

---

### Post by sudodus on 2013-04-19
Maybe the specs can vary within that model name, but what I could see from an internet link, it should have enough horsepower (cpu, ram, graphics) to work well with Ubuntu. Please check with top or the system monitor, which programs or processes, that keep the processor busy and fill the memory!

---

### Post by Magick93 on 2013-04-19
the ubuntu version is 12.04 LTS.

Im not totally sure of the specs of the laptop - but its fairly new. It could run windows 7 without any problems - until MS released a dodgy update.

ubuntu throwing up error report dialog boxes about every 10min. 
the browser hangs.
sometimes I forced to do a hard reset.

Its really seems buggy and unstable - and all I am doing is using a browser, yet it seems to lock up the whole OS.

---

### Post by Derxst on 2013-04-19
Boot into Memtest+ and check out your memory. I have 12.04 LTS running on several T420s and they fly!

---

### Post by jimafternoon on 2013-04-19
That sounds like the gpu hang 'apport error'  that lots of people have been having. 

I'm on a Lenovo Ideapad u400 and had all the same issues., in my case it was due to switchable graphics I think. I had to upgrade to 13.04 to solve the problems.

---

### Post by dave2001 on 2013-04-19
Good point Jimafternoon. I have a T500 Thinkpad with switchable graphics running 12.04. In order to get good functionality turn off switchable graphics in the bios config menu by choosing either integrated or discrete gpu. Then 12.04 will run fine (assuming that was the only problem).

---

