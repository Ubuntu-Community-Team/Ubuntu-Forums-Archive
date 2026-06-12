---
title: "Hacking a ds? please?"
date: 2009-05-09
forum: Programming Talk
---

### Post by Squigy Dunkens on 2009-05-09
Has anyone at all hacked a DS? I found out a while ago that people do [homebrew on the nintendo DS]("http://en.wikipedia.org/wiki/Ds_homebrew") all the time! It seems that it is mostly a windows thing though. I've been searching so long, and EVERY SINGLE tutorial I follow has something wrong with it! Everything is either windows only, or outdated, or just doesn't work for me. Yet, all the sites i go to have joyful comments like "Awesome, it worked! Thanks for the tutorial!" and others similar. So has anyone gotten anything to work on their DS? I really want to get [dslinux]("http://dslinux.org/faq.htm") to work (And, ***of course***, everything on that site is down except the index page and the faq page.) So if anyone could lead me to something that worked for them that would be great. If possible, I don't want to get any extra hardware, but if I have to, I want it to be easily obtainable.

---

### Post by slavik on 2009-05-09
I doubt you'll find someone here who knows about it ...

---

### Post by Squigy Dunkens on 2009-05-09
I do too, but I'm tired of searching, and if no one knows here, I guess thats too bad.

---

### Post by Npl on 2009-05-09
I dunno about dslinux, but I know people who run homebrew apps on a DS. Quite simple, get a cartridge that allows homebrew to run, like this one: [http://www.m3adapter.com/index.htm]("http://www.m3adapter.com/index.htm") and copy your homebrew stuff there.

And I hope you dont mistake developing **for** NDS as developing **on** NDS.

---

### Post by Squigy Dunkens on 2009-05-09
Ok, I might use the itouch (Its the cheapest.) Do you know if thats good? also, What if i dont have an sd slot on my computer? can i do it without through download play? alot of tutorials i saw used download play to connect to their computer.

---

### Post by issih on 2009-05-09
I've got a supercard lite in my ds.

What is it that you want to know?

Most DS homebrew is simply a case of dropping the nds file onto the flash memory of your device and running it. for simple programs that is really all there is to it.

Historically the different flash memory hardware solutions all had different drivers, so you needed to find a version of the program compiled for your hardware, more recently a dynamically linked library has been developed (dldi) so that programs can be patched to work with your card, for this there is a linux gui.

[http://sourceforge.net/projects/dldigui/](http://sourceforge.net/projects/dldigui/)

The only remaining thing is something like supercard's own software for backing up original nds roms (I'm not going anywhere near the more nefarious uses of that software), the only solution there is to run it under wine.

Be aware that the DS is not that powerful, and all the video players I've used are pretty limited. dslinux is cool, but again limited. an ipod touch is certainly capable of a great deal more, but I had fun with it all.

Hope that helps

---

### Post by Squigy Dunkens on 2009-05-09
Ok. I still want to know if i can do it wireless though. thanx. :)

---

### Post by issih on 2009-05-09
huh? do what wirelessly?

If you are referring to wifime as a method of bypassing the nds encryption, I'm pretty sure it does not work with anything but a very early DS running early firmware.

You basically need to have a slot1 nopass cartridge, and a separate slot2 flashcard device (which is what I have) or one of the newer flashcards that have the flash storage and the nopass in one slot1 device.

Once you have either of those it is a simple job of loading the nds files onto the appropriate flash memory.

I admit I haven't really been keeping pace with the scene for a couple of years now, so I could be wrong, but I think that is the current state of play.

---

### Post by Squigy Dunkens on 2009-05-09
Oh. well do i need an sd card slot on my computer? cause i dont have one. and has anyone heard of "Datel Games 'N Music"? It looks pretty good, and it also looks like it comes with some sort of usb like thing. does that mean i don't need an sd card slot on my computer?

---

