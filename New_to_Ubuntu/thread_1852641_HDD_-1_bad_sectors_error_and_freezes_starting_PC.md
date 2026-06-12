---
title: "HDD -1 bad sectors error and freezes starting PC"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Juliolp on 2011-09-30
Hi! The Smart Utility shows this error: i got -1 bad sectors. I don't understand: -1? Well, my PC is freezin while starting -sometimes it shows a violet display, sometimes a black display-, but always i got to reset the PC 3 o 4 times to run Ubuntu 11.04.

Maybe someone know if the -1 bad sectors is the problem and how to fix this? I really searched for anoher Bad Disk Sector error but not found no one with this '-1', i don't know what it means, how can i have -1 bad sectors, it should be a positive value, isn't? 

Thank you very much, community. ;)

[CENTER][[IMG]http://thumbnails53.imagebam.com/15178/aafc63151779657.jpg[/IMG]]("http://www.imagebam.com/image/aafc63151779657")
[/CENTER]
 [IMG]http://www.imagebam.com/image/aafc63151779657[/IMG]

---

### Post by cavh on 2011-09-30
Before getting into file system analysis, suggest you turn off the computer, open the case and reseat the memory stick(s) and the graphics card (remove them and reinsert them carefully). Over time you can get 'socket creep' due to thermal expansion and cooling. Then reboot and see if it happens again.

See 'socket creep' described here: [http://books.google.co.uk/books?id=waDmmqRgBmIC&pg=PA566&lpg=PA566&dq=computer+%22socket+creep%22&source=bl&ots=TTfyZgRCZ-&sig=aATDMUqdoHVuIPdwCosgZAGHvkg&hl=en&ei=VBSGTuqjIIa08QPP25FP&sa=X&oi=book_result&ct=result&resnum=4&ved=0CEcQ6AEwAw#v=onepage&q=computer%20%22socket%20creep%22&f=false]("http://books.google.co.uk/books?id=waDmmqRgBmIC&pg=PA566&lpg=PA566&dq=computer+%22socket+creep%22&source=bl&ots=TTfyZgRCZ-&sig=aATDMUqdoHVuIPdwCosgZAGHvkg&hl=en&ei=VBSGTuqjIIa08QPP25FP&sa=X&oi=book_result&ct=result&resnum=4&ved=0CEcQ6AEwAw#v=onepage&q=computer%20%22socket%20creep%22&f=false")

---

### Post by acrazyplayer on 2011-09-30
The smart data is sometimes the oppsite of what you think it should be. for example the -1 could be just that. there is everything okay minus 1 sector that is bad. 

your computer should know that the sector is bad and it wont try to write anything to it. however if something was written to it then it is probably lost. This could explain why Ubuntu is acting strange. 

Like was already said you should make sure everything is correclty in place but dont do anything your unsure of and dont push too hard on something. As always make sure everything is unplugged before you open your case.

---

### Post by cavh on 2011-09-30
Good point made by acrazyplayer - make sure you don't electrocute yourself ... and make sure you discharge any static you have in your body : [http://www.wikihow.com/Ground-Yourself-to-Avoid-Destroying-a-Computer-with-Electrostatic-Discharge]("http://www.wikihow.com/Ground-Yourself-to-Avoid-Destroying-a-Computer-with-Electrostatic-Discharge") and [http://www.pcworld.com/article/82184/avoid_static_damage_to_your_pc.html]("http://www.pcworld.com/article/82184/avoid_static_damage_to_your_pc.html")

---

### Post by Juliolp on 2011-10-01
Hey, guys, you all must be in the right direction! Well, if i remember, i cleaned the fan and then suddenly the PC started to hangs. Then i found that i must use a thermal paste again -yes, i could fry my motherboard LOL, but i never thougth-, so i cleaned the micro, the bottom of the fan, added the thermal paste and then my PC started, yes... first time Ubuntu started normally, next time started to freezes when i turn off my PC and try to started the next day. 

In the clean process i used an aspirator to remove dust and to do it i unplugged all from motherboard -SATA's, etc- and from the energy power to clean it... but RAM didn't. The Graphic Card is a chipset soldier on the motherboard (it's an old MSI PM8PM-V) so i can't unplug it. 

I read carfully the links about static damage and i will unplug/plug the RAM carefully, maybe the mistake is about those hangs when the micro doesn't have the fan and some affected the RAM. I hope this solve those hangs, thanks very much to all, without your help my way was to buy a new HDD... and probably i would have the same problem. ¡Thanks, thanks, thanks! :D

---

### Post by cavh on 2011-10-03
Cool, good luck! :)

---

