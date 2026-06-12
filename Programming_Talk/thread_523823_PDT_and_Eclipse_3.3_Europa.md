---
title: "PDT and Eclipse 3.3 Europa"
date: 2007-08-12
forum: Programming Talk
---

### Post by petbse on 2007-08-12
My spec
Athlon XP 2200+ Thoroughbred
512MB DDR 400 RAM
Nvidia GeForce FX 5200
Feisty Fawn (ubuntu with kde installed - i use kde and sometimes gnome depends on mood)
kernel version: linux-generic-2.6.20.16.28.1
I followed instruction to get eclipse running and it runs fine.
command java -version gives this:
Quote:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
when i start eclipse from console it also finds java-6-sun as compatible jre
I had problems before with gcj so i setup suns java. My problem: I had to update to eclipse-3.3 Europa because of PDT plugin via eclipse update manager (i need to build cake-php site). PDT plugin needed WST version 2.0 that i found only in europa's discovery site and not on calisto's (i was not able to find any other eclipse discovery sites). I fear that all my troubles result from this upgrade. But I dont have any choice because PHPeclipse-1.18 runs only on eclipse 3.1 and I wasn't able to find any PDT version that would work on eclipse 3.2.
The problem is i can't save files in pdt i can see them in my project(its located in my /home/petbse/projects) so its not an permissions issue i think. Eclipse looks like saving file it doesn't show any errors but when i look to file in nano or krusaders edit I dont see the changes. I am not sure if this is a java IO issue or Eclipse 3.3 not working in Feisty. Its weir but I was doing weird thing all day today I installed all needed plugins in sudo eclipse and via update manager. From following eclipse update sites:
[http://download.eclipse.org/tools/pdt/updates/](http://download.eclipse.org/tools/pdt/updates/)
[http://download.eclipse.org/releases/europa/](http://download.eclipse.org/releases/europa/)
and calisto but now after installs from europa is no longer in my list, so I dont remeber its url.
I was using phpeclipse for a while on windows but I am no more than firstime lucky noob with it
Any help is appreciated

---

### Post by petbse on 2007-08-12
Its working. As always it was a between chair and screen problem. In my own stupidy i was having two folders with the same name and content on different paths one eclipses workspace and the other used in cake and available to apache. So the changes are saved ok. Thank you for not having to help :)

---

