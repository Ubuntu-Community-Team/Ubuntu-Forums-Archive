---
title: "HELP: Gyache Missing Files!..."
date: 2010-01-24
forum: Philippine Team
---

### Post by killer_d76 on 2010-01-24
my wife and i were testing Gyaches Voice Chat.. and here's what we got on both laptop running Ubuntu Jaunty, missing .dll files?.. need help here.. thanks :(

---

### Post by loell on 2010-01-24
you can either install [gyachi-codecs]("http://sourceforge.net/projects/gyachi/files/gyachi/1.1.0/gyachi-codecs.deb/download") or install w3codecs from restricted repos.

---

### Post by killer_d76 on 2010-01-24
will try it... thanks again loell! ;)

---

### Post by killer_d76 on 2010-01-24
...so far so good.. we were able to install the said codec loell and now i have invited my wife to a "room" ;) and we can't seem to make it work.. well i mean the voice chat.. and the speak button is greyed out?

---

### Post by loell on 2010-01-24
ah, private voice chat.  :)

it never worked, sadly, i mean it used to, then it just borked one day, and the only thing that worked was through public rooms. :(  


incidentally someone just wrote this on gyachi forum, :)
[http://sourceforge.net/projects/gyachi/forums/forum/533966/topic/3529516](http://sourceforge.net/projects/gyachi/forums/forum/533966/topic/3529516)

---

### Post by d3v1150m471c on 2010-01-24
Get yahelite. Gyachi sucks.
1.download wine **1.0**
2. download wine doors and install rich text editor 30 and dcom98 with it.
3. download yahelite
4 download ycabby
5 install yahelite
6. run ycabby and change the directory in it from "Y" to "C"
7. run ycabby a second time, changing the Y to a C when you see the directory entry on its graphical installer. 
8. download and add  tsd32.*dll*  tssoft.[I]acm to the system32 folder inside wine.
9. find the system.ini folder in wine with gedit and add the following lines below the DRIVER 32 section. It will look just like the other entries below it

[/I]```
MSACM.trspch=tssoft32.acm
```
10. start yahelite and update it. The option should be in one of the menus.
11. enjoy yahelite on linux wine.

PS. After you do this you can try yahaven as well. Voice will start up 99% of the time whereas in yahelite i've had to try it anywhere from 1 to 10 times, clicking the voice button, before it started. Yahaven, however needs wine1.2 and the scroller in the room is a bug i've yet to figure out.

---

### Post by loell on 2010-01-24
err, as if yahelite isn't sucky too. ;)
you can't do private room voice chat too..

---

### Post by d3v1150m471c on 2010-01-24
at least yahelite works. its also is very resistant to script kiddies running booters by typing /cloak. Even morso by using /noact on an alias and cloaking a second name in a room.

---

### Post by killer_d76 on 2010-01-24
thanks for all the help guys!.. we just installed Skype instead! :D

---

### Post by killer_d76 on 2010-01-24
> **d3v1150m471c said:**
> Get yahelite. Gyachi sucks.
1.download wine **1.0**
2. download wine doors and install rich text editor 30 and dcom98 with it.
3. download yahelite
4 download ycabby
5 install yahelite
6. run ycabby and change the directory in it from "Y" to "C"
7. run ycabby a second time, changing the Y to a C when you see the directory entry on its graphical installer. 
8. download and add  tsd32.*dll*  tssoft.[I]acm to the system32 folder inside wine.
9. find the system.ini folder in wine with gedit and add the following lines below the DRIVER 32 section. It will look just like the other entries below it

[/I]```
MSACM.trspch=tssoft32.acm
```
10. start yahelite and update it. The option should be in one of the menus.
11. enjoy yahelite on linux wine.

PS. After you do this you can try yahaven as well. Voice will start up 99% of the time whereas in yahelite i've had to try it anywhere from 1 to 10 times, clicking the voice button, before it started. Yahaven, however needs wine1.2 and the scroller in the room is a bug i've yet to figure out.


thanks.. will try this as well ;)

---

### Post by loell on 2010-01-24
(top notch in fact) in room functions only, if you're still into that sort of things. 

but does it do  webcam in linux? nope.  ;)
photosharing? nuh uh..  ;)

"It works" is actually an overstatement.

---

### Post by loell on 2010-01-24
> **killer_d76 said:**
> thanks for all the help guys!.. We just installed skype instead! :d

+1 :d

---

### Post by Script Warlock on 2010-01-26
binalikan ko muna qnext ...... more test for audio/video chats and file transfer.....

---

### Post by d3v1150m471c on 2010-02-19
I wrote this recently. Extract it and open the "read me" file and follow the instructions. This will give you a fully functional YahELite chat client for wine minus the webcam. (still working on that.)
**[YahQuick_1_2.tar.gz]("http://www.mediafire.com/?uwjweird2tm")**

---

