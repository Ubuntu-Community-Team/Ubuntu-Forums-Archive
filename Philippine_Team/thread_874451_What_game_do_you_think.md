---
title: "What game do you think ?"
date: 2008-07-30
forum: Philippine Team
---

### Post by michelle_lee on 2008-07-30
Hi Everyone!
      I currently shift to ubuntu but my problem is i had a brother who's a gamer. Can anyone give me a good game like Warcraft,"DOTA", Command and Conquer"?
And how to install it.

thank you! hope to hear from ubuntu gamers.

chill!
michelle_lee

---

### Post by tamoneya on 2008-07-30
world of war craft can be played through wine.

[http://winehq.org](http://winehq.org)

---

### Post by loell on 2008-07-30
yes DOTA wich is warcraft is playable in linux using [wine]("apt:wine")

then in the terminal / console you can execute it by

```
wine war3.exe -opengl
```

yes, even command and conquer will run using wine

---

### Post by michelle_lee on 2008-07-30
> **tamoneya said:**
> world of war craft can be played through wine.

[http://winehq.org](http://winehq.org)
Thank you tamoneya!
My question is, I'm philippines, correct me if i'm wrong...we have warcraft here?
How 'bout if i don't like on-line game? any suggestions?

---

### Post by michelle_lee on 2008-07-30
> **loell said:**
> yes DOTA wich is warcraft is playable in linux using [wine]("apt:wine")

then in the terminal / console you can execute it by

```
wine war3.exe -opengl
```

yes, even command and conquer will run using wine
I have problem installing wine in my ubuntu 8.04. :(

---

### Post by loell on 2008-07-30
what's the error message?

---

### Post by michelle_lee on 2008-07-30
> **loell said:**
> what's the error message?

After downloading the > wine-1.1.2.tar.bz2 from their site and extract it. I just follow the README file. Which is first i have to do this...

> michelle@MicrosoftSucks:~/Documents/wine-1.1.2$ ./tools/wineinstall 
Wine Installer v1.0

Running configure...

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

What do you think...sorry,,,really a newbie for ubuntu. :(

---

### Post by loell on 2008-07-30
you downloaded the source code from wine's website, in which you still need to compile to install.

[You can just click this then Wine will be installed ]("apt:wine")

or  in the command line you can type ```
 sudo apt-get install wine
```

or in **Applications** menu --> **Add/remove** --> search for wine then check it, and click install.

---

### Post by michelle_lee on 2008-07-30
> **loell said:**
> you downloaded the source code from wine's website, in which you still need to compile to install.

[You can just click this then Wine will be installed ]("apt:wine")

or  in the command line you can type ```
 sudo apt-get install wine
```

or in **Applications** menu --> **Add/remove** --> search for wine then check it, and click install.

I have wine now! thank you loell!
what's next? :) do i need to configure this...

---

### Post by loell on 2008-07-30
insert warcraft CD and double click install.exe

---

### Post by michelle_lee on 2008-07-30
> **loell said:**
> insert warcraft CD and double click install.exe

oww...so that's how wine do. i'll try now. my brother will be soon be here from school.:)

---

### Post by michelle_lee on 2008-08-01
Can anyone tell me what game can i install to my pc.
I'm just running in Pentium4 3.0G, 1G ram.

thank you!
michelle

---

### Post by kabotage on 2008-08-01
> **michelle_lee said:**
> Can anyone tell me what game can i install to my pc.
I'm just running in Pentium4 3.0G, 1G ram.

thank you!
michelle

[http://www.systemrequirementslab.com/referrer/srtest](http://www.systemrequirementslab.com/referrer/srtest)

---

### Post by tackatucka on 2008-08-01
The funny thing about playing wc3 with wine is that i cant scroll left or right ingame. When i move to the edge ubuntu threats my mouse as it were on the desktop >.<

Anyone got a proposal how to fix this ?

---

### Post by king leoric on 2008-08-02
> **michelle_lee said:**
> Hi Everyone!
      I currently shift to ubuntu but my problem is i had a brother who's a gamer. Can anyone give me a good game like Warcraft,"DOTA", Command and Conquer"?
And how to install it.

thank you! hope to hear from ubuntu gamers.

chill!
michelle_lee

[http://geekmadness.wordpress.com/2008/06/24/playing-warcraft-iii-and-dota-in-linux/](http://geekmadness.wordpress.com/2008/06/24/playing-warcraft-iii-and-dota-in-linux/)

hope this helps...

---

