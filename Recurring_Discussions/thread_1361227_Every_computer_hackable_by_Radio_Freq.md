---
title: "Every computer hackable by Radio Freq?"
date: 2009-12-21
forum: Recurring Discussions
---

### Post by njiii on 2009-12-21
- a global conspiracy?   Maybe it's only Windows varients, but this guy claims to have found some strange things on his Windows PC:  Subversionhack Archive [https://tagmeme.com/subhack/](https://tagmeme.com/subhack/)  So, with modern blackboxed hardware components, are all of our PCs hackable via radio frequency / ham packet radio type of blackbox voodoo?  Dig deep, I've found no other site like this. Are Linux/BSD varieties vulnerable?

---

### Post by njiii on 2009-12-21
[http://www.invisiblethings.org/code.html](http://www.invisiblethings.org/code.html)

 [http://www.invisiblethings.org/papers.html](http://www.invisiblethings.org/papers.html) 

AND 

This talk explores three possible methods that a hardware Trojan can use to leak secret information to the outside world: thermal, optical and radio. 

    In the thermal Trojan demo, we use an infrared camera to show how electronic components or exposed connector pins can be used to transmit illicit information thermally. In the optical Trojan demo, we use an optical-to-audio converter to show how a power-on LED can be used to transmit illicit information using signal frequencies undetectable by human eyes. Finally, in the radio Trojan demo, we use a radio receiver to show how an external connector can be used to transmit illicit information using AM radio transmission. 

[http://www.cvorg.ece.udel.edu/defcon-16/](http://www.cvorg.ece.udel.edu/defcon-16/)

 [https://www.defcon.org/html/defcon-16/dc-16-speakers.html#Kiamilev](https://www.defcon.org/html/defcon-16/dc-16-speakers.html#Kiamilev) 

fools laugh and cry tinfoil, others read and learn and decide for themselves

---

### Post by sgosnell on 2009-12-21
It depends on what you mean by 'hackable', but anyone with the right equipment can sit in a van out on the street and pick up everything you do on your computer, even if you're not connected to the internet.  You can install a Faraday cage in your home and block the emissions, but that's about the only way.  Computers are very rf noisy.  The primary safety we have is that for most personal computers, it just isn't worth the effort, because there isn't that much useful data, but if someone really wants to find out what's on your computer, it can be done.

---

### Post by rookcifer on 2009-12-22
This is not news.  It has been [known]("http://www.builderau.com.au/news/soa/Microsoft-wireless-keyboard-hacked-from-50-metres/0,339028227,339284328,00.htm") for a long time that the RF from wireless keyboards can be picked up remotely.  However, as the guy above said, it would take someone sitting within a fairly close proximity to intercept it.

The problem is these signals are not encrypted.  I suspect this will change (if it already hasn't).

---

### Post by njiii on 2009-12-22
[http://bluepillproject.org/](http://bluepillproject.org/) 

[http://subversionhack.livejournal.com/1815.html](http://subversionhack.livejournal.com/1815.html) 

"I sincerely believe that Blue Pill technology will (very soon) allow for creating 100% undetectable malware, which is not based on obscurity of the concept. And I already stressed this in the description of my talk here ([http://syscan.org/program.html](http://syscan.org/program.html)) and here ([http://blackhat.com/html/bh-usa-06/bh-usa-06-speakers.html#Rutkowska](http://blackhat.com/html/bh-usa-06/bh-usa-06-speakers.html#Rutkowska)). The working prototype I have (and which I will be demonstrating at SyScan and Black Hat) implements the most important step towards creating such malware, namely it allows to move the underlying operating system, on the fly, into a secure virtual machine."  - [http://theinvisiblethings.blogspot.com/2006/07/blue-pill-hype.html](http://theinvisiblethings.blogspot.com/2006/07/blue-pill-hype.html) 

[http://rayer.ic.cz/romos/romose.htm](http://rayer.ic.cz/romos/romose.htm) 

"The ROMOS is a stand-alone x86 code allows you to load and run your own binary code or 3rd-party code. ROMOS rely on BIOS functions only so it can be executed directly without any operating system. The main purpose of ROMOS is to be placed in a ROM, from where it can load/run other software (e.g. bootmanager, HW diagnostics, special controlling software...) during POST (Power-On Self Test) while your PC is booting up. It can also load DOS-based operating systems (may be other OSes) such as FreeDOS  stored in ROM together with ROMOS. This mean that any floppy/harddisk/CD-ROM drive is not needed. It may be very useful in various embedded diskless systems. Or simply as reserve OS for rescue use. Other applications are on you."

---

### Post by 3rdalbum on 2009-12-22
> **njiii said:**
> - a global conspiracy?   Maybe it's only Windows varients, but this guy claims to have found some strange things on his Windows PC

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587)

[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)

The classic "I'm being hacked no matter what I do" threads.

Interacting with somebody's computer (or reading data) from a distance without using the Internet is possible, but highly impractical when you can sneak into that person's house and install a keylogger, or intercept their Internet access, or hit them over the head until they tell you their secrets.

---

### Post by CharlesA on 2009-12-22
Heard about this and the only thing I can think of is: "Oh noes my computer is telling my neighbor (with thermal gear) my secrets!"

Totally impractical, if someone really wanted to evesdrop on yer activities, there are far better ways to go about it.

---

### Post by __p1n__ on 2009-12-22
> **njiii said:**
> - a global conspiracy?   Maybe it's only Windows varients, but this guy claims to have found some strange things on his Windows PC:  Subversionhack Archive [https://tagmeme.com/subhack/](https://tagmeme.com/subhack/)  So, with modern blackboxed hardware components, are all of our PCs hackable via radio frequency / ham packet radio type of blackbox voodoo?  Dig deep, I've found no other site like this. Are Linux/BSD varieties vulnerable?


It's all true.  The government (all of them) is using ultra-radio computer controllers transmitting via dirt-modems through the earth and up through the ground wire on our computer power supplies to control our machines. ;)

In other news tinfoil tards tediously tout text-tags in lieu of actually knowing anything about what they're talking about.  I had a real laugh looking over the "findings" of the strings analysts on the site cited above.

---

### Post by rookcifer on 2009-12-22
Ah, blue pill.  Started by the inimitable  Joanna Rutkowska, as brainy as she is beautiful.  Ms. Rutkowska has a penchant for flashy headlines, much in the vein of security super-guru Steve Gibson. Unfortunately, neither usually turn out as illustrious as  originally sold.

---

### Post by bodhi.zazen on 2009-12-22
I moved this thread to Recurring discussions as it seems to be about general paranoia, tin foil hat kind of stuff, and sensationalism / general FUD rather then a support question.

[http://zapatopi.net/afdb/](http://zapatopi.net/afdb/)

---

### Post by jayze on 2009-12-22
How do you know its the "government?" (JOKING! JOKING!)....no feeding of paranoias here lol...personally I wouldnt know whats possible and what isnt but I guess having our washing hanging on the line is the price we pay for getting it dried!....so....:popcorn:

---

### Post by Exodist on 2009-12-22
I use no wireless devices and all my cables are EM shielded to prevent such stuff. Yes PC does need shielding, but I like my pretty plexi-glass window with all my UV bulbs making everything glow :lolflag:

---

### Post by JimInLakeland on 2009-12-22
Before continuing in this discussion, you must don your tin-foil hat!
[IMG]http://scienceblogs.com/startswithabang/upload/2009/04/weekend_diversion_do_tinfoil_h/tinfoil_hat_antenna.jpg[/IMG]

---

