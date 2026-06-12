---
title: "[SOLVED] Audio Player with Equaliser"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by electroblaze1989 on 2008-06-01
Does an audio player with equaliser exist?? if so where can i get it? and also how do i install it? please assist...

---

### Post by shifty_powers on 2008-06-01
amarok?

(it's under tools iirc).

just look for it in synaptic.

---

### Post by electroblaze1989 on 2008-06-01
i cant seem to find it...could you please link me?

---

### Post by atomkarinca on 2008-06-01
Try Audacious, you can import Winamp presets, too. Open up a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get install audacious
```

---

### Post by electroblaze1989 on 2008-06-01
well i've found it by googling for it...but it doesn't seem to have Ubuntu in the list of compatible OS's provided on that page...it has Debian though..should i go for that or shud i use the one meant for kUbuntu?

---

### Post by shifty_powers on 2008-06-01
have a look in the screenshot.

also yo can try

```
sudo apt-get install amarok
```

in a terminal

---

### Post by shifty_powers on 2008-06-01
heh, yes it is a kubuntu app, and it will run fine on ubuntu. it will download some kde libs.

you can also try exaile. it is a gnome version if that suits you better...

---

### Post by electroblaze1989 on 2008-06-01
well i'm done with audacious...thank you very much guys...

---

### Post by Joeb454 on 2008-06-01
Glad you found one that suited your needs, I was just about to suggest amarok too :p

Can you please mark your thread as solved? It's in thread tools at the top of this page :)

---

### Post by shifty_powers on 2008-06-01
np's. glad we could help :D

---

### Post by electroblaze1989 on 2008-06-01
where can i find more multimedia applications for Ubuntu?? I don't have anything specific in mind..just hunting around...i also need themes...

---

### Post by shifty_powers on 2008-06-01
have you looked in the add/reomve section of applications?

also checkt out gnomelook. (google it ;))

---

### Post by Joeb454 on 2008-06-01
I'd check Add/Remove as well :)

It's under the Applications Menu at the top left of the screen :)

---

### Post by shifty_powers on 2008-06-01
gotta love this forum. helped out loads when i started out wiht ubuntu :D

---

### Post by atomkarinca on 2008-06-01
> **electroblaze1989 said:**
> where can i find more multimedia applications for Ubuntu?? I don't have anything specific in mind..just hunting around...i also need themes...

Also don't miss [Ubuntu Studio]("http://ubuntustudio.org/home").

---

### Post by electroblaze1989 on 2008-06-01
i seem to be having a problem with my Add/Remove Programs...it freezes when i try to add anything at all...i can't even install CompizFusion and it was one thing i was really looking forward to...is there an alternate way?? can i do something with the terminal??

---

### Post by shifty_powers on 2008-06-01
what version of ubuntu do you have for a start?

and was it a clean install or an upgrade?

---

### Post by electroblaze1989 on 2008-06-01
it is the latest one..8.04 64bit version..if u mean upgrade over another version of Ubuntu...then no...it was a clean install using Wubi over WIndows XP...

---

### Post by shifty_powers on 2008-06-01
any particular the 64-bit?

and try and install something from the command line.
go applications>accessories>terminal

then

```
sudo apt-get install vlc
```

(vlc is a very good media player :D)

---

### Post by electroblaze1989 on 2008-06-01
Its an AMD Turion 64 Single Core ancient monster..lol...yes i have installed everything using the terminal only uptil now..i have even upgraded all my software with it..it wud be very nice of you if you could explain how to use the terminal to get software...i have to post for every little software otherwise...really sorry...

---

### Post by shifty_powers on 2008-06-01
well the normal way is using apt. synaptic is actually a gui frontend for apt.

so

```
sudo apt-get install *package name*
```

is the standard code. sudo is super user do, to give you admin privileges, apt-get is a version apt to install will, install is self-explanatory. of course you need to know the package name ;)

also, have you tried

```
sudo dpkg --configure -a
```

and then the add/reomve?

---

### Post by electroblaze1989 on 2008-06-01
yes i have tried that... it still doesn't work..is tere some super-library containing all the pakage names? how will i know???

---

### Post by shifty_powers on 2008-06-01
heh, not afaik.

you could always have a look at

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Joeb454 on 2008-06-01
If your intent on learning the terminal (which is a good thing in my books ;)) then you may want to run ```
apt-cache search <package>
``` to find applications relating to that package. You can also use keywords if I remember correctly :)

Sometimes you may want to pipe it through less, so it's easier to read ```
apt-cache search <package> | less
``` To get out of reading if you use the above - just hit 'q'

---

### Post by electroblaze1989 on 2008-06-01
no too many softwares there though..but i'll keep checking...thanks a ton mate..

---

### Post by Joeb454 on 2008-06-01
The medibuntu repo may be something you want to look at - as well as Ubuntu Studio :)

---

### Post by electroblaze1989 on 2008-06-01
i am also not able to download the Flash plugin for Firefox...it just freezes after i click on install plugin.. what should i do?
is there a terminal command line for this as well???

---

### Post by Joeb454 on 2008-06-01
You can try ```
sudo apt-get install flashplugin-nonfree
```

---

