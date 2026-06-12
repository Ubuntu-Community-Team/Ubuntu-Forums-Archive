---
title: "is it safe to use XP on Virtualbox without anti-virus?"
date: 2008-08-08
forum: Philippine Team
---

### Post by killer_d76 on 2008-08-08
..i've just installed Virtualbox on my Ubuntu and have XP Light running on it (wala lang, testing lang hehehe).. i haven't installed any anti-virus on it, now my question is.. is it safe for my laptop if ever Windows (running in Virtualbox) get infected with virus?, i was thinking that it won't affect or do any harm on my laptop since it is running on Virtual drive, but i need your opinion ;)

---

### Post by oldsoundguy on 2008-08-08
If you are going to take Windows ON LINE, ALL of the basic 5 protection programs should be installed with it in your virtual box.  Not to protect your computer per se, but to protect the operating system and to keep from spreading malware on line when you use it.

---

### Post by wersdaluv on 2008-08-08
Pag nag-XP ako sa vbox, hindi ako nagpupunta sa websites na maaring maka-virus. Bale, sa Ubuntu ako nagbbrowse tutal nasa Ubuntu rin naman ako eh. Dun na 'ko mag-internet.

---

### Post by killer_d76 on 2008-08-08
thanks for the input guys.. so.. if ever it (Windows) get infected with Virus (which it usually does :lolflag:) it will just be on the Windows OS that is running on the Virtualbox, not on the whole system or files that i have on my Ubuntu, right?

---

### Post by pendletone on 2008-08-09
Technically yes, coz most viruses out there are geared towards infecting Windows machines. So even if a virus made its way through your Ubuntu box, which probably wouldn't, it would just sit there idle.

Nag-install din ako ng virtualbox for testing purposes. So kung may gusto akong i-test na software (w/c I usually do), dun ko muna sya patatakbuhin sa virtual machine.  And if I didn't liked it (or if my XP VM got infected), I just simply revert to a previous VM snapshot at balik uli sya sa dati -- as if I hadn't installed it or got infected in the first place.

---

### Post by loell on 2008-08-09
> **killer_d76 said:**
> if ever it (Windows) get infected with Virus (which it usually does :lolflag:) it will just be on the Windows OS that is running on the Virtualbox, not on the whole system or files that i have on my Ubuntu, right?

there is some level of unlikelihood,but you'll never know,  when you  ](*,) ,

just be careful what  directories you're sharing to be accessed by XP through the virtual box.

---

### Post by king leoric on 2008-08-09
I agree with sir loell...in my case however, I run xp only for chikka and trillian messenger. Pidgin so far is not yet supporting webcam so I'm running messenger in xp.

And in the case of sharing folder, I don't share. I just enabling usb support so I could use my usb for transferring files.:guitar:

---

### Post by dynastywarrior on 2008-08-12
hi

try to do a "snapshot" of your existing good-running virtual machine so that if a virus gets into it you can easily revert back to your previous existing good configuration.

and if ever a virus gets into it, it will never affect your host system unless you've chosen a "host only" setup for networking during your installation....

---

### Post by wersdaluv on 2008-08-12
> **king leoric said:**
> I agree with sir loell...in my case however, I run xp only for chikka and trillian messenger. Pidgin so far is not yet supporting webcam so I'm running messenger in xp.

And in the case of sharing folder, I don't share. I just enabling usb support so I could use my usb for transferring files.:guitar:
This is offtopic but if you want to use webcam on Yahoo! Messenger, you can use Gyache Improved that loell packaged. You can also use Kopete.

---

### Post by king leoric on 2008-08-12
> **wersdaluv said:**
> This is offtopic but if you want to use webcam on Yahoo! Messenger, you can use Gyache Improved that loell packaged. You can also use Kopete.

well i've tried gyache but to be honest, I so dumb at di ko mapagana :lolflag:.....then I don't like running kde packages like kopete in my ubuntu box cause, wala lang....ayaw ko lang:):lolflag:

---

### Post by kaivar on 2008-09-19
@king leoric: napatakbo mo ang chikka sa winxp sa virtualbox? O_o missing dll daw sa akin everytime i open... :-S

---

### Post by Laibcoms on 2008-09-19
Actually, you should have an anti-virus, anti-spyware, and firewall as basic when running anything "Microsoft(R) Windows" even in a virtualbox under GNU/Linux.

1) Most viruses are targeted towards MS Windows, so they can still run even in a virtual Windows and spread via the internet.
2) If your virtual Windows can access anything outside of the virtual box, then the viruses can spread via the virtual windows to other files and even in the network.
3) YES, it may not do anything at all for non-Windows environment like Linux, BUT if the infected files are accessed via MS Windows, then the risk of that virus activating is high.

Off-topic.

Since we're in that topic, why don't you try to merge the desktop of Ubuntu and Windows?  Haven't tried it myself but there are instructions that works.  I know it is fun, coz I tried it the other way around ;)  Linux as Virtual merged with Windows desktop.

Oh btw, do NOT activate an unused OEM Windows License in a virtual box, you won't be able to use it anywhere except in that exact same virtual box.  A Full (ie non-OEM) Windows License however, can be "unregistered" so you can reuse the license code on a new machine or virtual box.

---

### Post by killer_d76 on 2008-09-19
thanks for info Laibcoms!.. very informative! :popcorn: .. :guitar:, when you say merge Linux with Window$.. did you mean use the "seamless" mode?.. i haven't tried it as well, i kinda like the small screen for the other OS that i use here.. i might get confused if i use the seamless mode! hehehe

---

