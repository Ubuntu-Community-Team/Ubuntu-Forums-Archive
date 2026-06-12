---
title: "Scanner issue on cannon mp280"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by Kanahau on 2013-01-19
I have managed to get the printer part of this basic printer/scanner but cant seem to coax any life into the scanner side of this machine? I tried looking but found no real leads as to how to solve this one?? Any clues or pokes in the right direction welcome, but baby step numbered instructions work best for me............

---

### Post by Daveth on 2013-01-19
this might aid you

[http://askubuntu.com/questions/182604/canon-mp280-all-in-one-prints-but-scanner-not-recognized](http://askubuntu.com/questions/182604/canon-mp280-all-in-one-prints-but-scanner-not-recognized)

---

### Post by ld114 on 2013-01-20
I used to have a Canon all-in-one printer and had much difficulty getting it to work. 

I found this information:

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

and a ppa at:

[https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

Unfortunately I don't see your model in the list, but you could contact the guy.

[I should say in the end I got a cheap wireless HP all-in-one and have never looked back.]

---

### Post by pdc on 2013-01-20
Hi Kanahau;

Canon make a programme to run the scanner on your MP280 ....the programme is called [COLOR="SeaGreen"]SCANGEARMP[/COLOR] ............ScanGear for MP printers ..

if you go here........the Canon Asia website

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html)

and download this file [COLOR="SeaGreen"]scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR]

it comes down as a compressed .tar.gz file

When you click to download it, your system will offer you to open it with archive manager or save it ..if you SAVE IT..


...it should by default save it to your Downloads directory and if I offer you some commands to run the install script that Canon supply:

if you [COLOR="Magenta"]open a terminal[/COLOR] (Accessories-Terminal) and [COLOR="Magenta"]copy and paste these commands[/COLOR] into it

.....*use the MENU ...EDIT at the top line of the terminal to paste as the shortcut CONTROL V does not work in the terminal ..(it is SHIFT CONTROL V)*

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]tar -zxvf scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd scangearmp-mp280series-1.60-1-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

.........that should install the scangear programme

to run it copy and paste this command into the terminal

> [COLOR="Red"]scangearmp[/COLOR]

and the programme should open .......if you now create a launcher 

.......to launch the programme each time you want to use it .......

...... so from here

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

copy and paste these commands

> [COLOR="Red"]sudo apt-get install gnome-panel[/COLOR]

......enter your sudo password when asked..this installs a launcher utility

> [COLOR="Red"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

....this opens a dialogue box like the one I enclose as a thumbnail 

for [COLOR="Blue"]NAME[/COLOR]: I suggest [COLOR="Blue"]scangearmp[/COLOR]

and [COLOR="Red"]COMMAND[/COLOR]: [COLOR="Red"]scangearmp[/COLOR]

---

### Post by cogier on 2013-01-20
Canon do a driver for Linux here [http://software.canon-europe.com/products/0010883.asp]("http://software.canon-europe.com/products/0010883.asp")

---

### Post by greg_ory on 2013-01-20
I would consider Linux supported hardware for the future, I know it's not helpful yet but might be a big help for the future and hopefully big names rethink their strategy to provide hardware devices for Windows/Mac only.

-Greg

---

### Post by archery on 2013-01-20
> **greg_ory said:**
> I would consider Linux supported hardware for the future, I know it's not helpful yet but might be a big help for the future and hopefully big names rethink their strategy to provide hardware devices for Windows/Mac only.

-Greg

Canon provide pretty good linux support in my experience. pdc has provided an excellent walk-through but for complete newcomers the process can be made even simpler using the deb packages and a few mouse clicks.

---

### Post by pdc on 2013-01-20
to [COLOR="SeaGreen"]Cogier[/COLOR]: > Canon do a driver for Linux here..thanks very much for this; a very useful pointer: I think it's the same file: each country that Canon sells in now have good websites for driver support; 

to [COLOR="SeaGreen"]greg_ory[/COLOR]: > *I would consider Linux supported hardware for the future* ....if you go here 

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

and use Control F to find the MP280 you will see the sane-pixma backend provides good support: xsane should find the scanner for Kanahau but a) one could troubleshoot or b) scangearmp does well: 

when you say [COLOR="SeaGreen"]greg_ory[/COLOR] >  *hopefully big names rethink their strategy to provide hardware devices for Windows/Mac only*. that's a very important point you make: it a very serious issue: however I note that Canon, Brother and Epson; to name 3: all provide linux drivers for their products; as they provide drivers for mac/windows: ...so to me .....that's sort of a very similar arrangement ...........what is it you believe when you say "hopefully big names rethink their strategy to provide hardware devices for Windows/Mac only" ............because

for Canon: go here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

for Brother go here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

and for Epson go here: [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

to [COLOR="SeaGreen"]jjmorgs1[/COLOR]: thanks very much> *the process can be made even simpler using the deb packages and a few mouse clicks*. 
...with the ./install.sh script that Canon provide in the package, as you will know it identifies if the user has 32bit or 64bit; and if deb or rpm; .......... to run it though, you seem to need to run it in terminal so I hope by giving newcomers a series of copy and paste commands, that most folks can manage that

..... you say .............> *the process can be made even simpler using the deb packages and a few mouse clicks*....to be honest, I would hope these days that most folks could manage copy and paste: I understand it is how most Masters Degrees are written :) ;)

---

### Post by archery on 2013-01-20
> ...to be honest, I would hope these days that most folks could manage copy and paste: I understand it is how most Masters Degrees are written  

Agreed. I was emphasising the point that Canon's support was pretty good with .deb packages and a potential 'click' based approach to installing (all be it through a process of elimination re 32 bit/64 bit packages). On the Masters point, that wouldn't surprise me.

---

### Post by Kanahau on 2013-01-22
Thanks all, especially pdc. I managed the copy and paste technique and the scanner works a treat, thank you. I am so inspired with confidence and the soundness of your advice I feel ready now to go for my Masters.......... :-)

---

### Post by pdc on 2013-01-22
great! Enjoy! :D

........oh by the way, you can now mark the thread as SOLVED: the forum administrators like it ........ I think it is in thread tools top right ..

---

### Post by resander on 2013-01-22
> **ld114 said:**
> 
[I should say in the end I got a cheap wireless HP all-in-one and have never looked back.]

l114:
My HP Deskjet 1470 is showing signs of age. Need another HP.
What is the model number of the HP wireless all-in-one?

Ken

---

### Post by pdc on 2013-01-22
a forum administrator is likely to tell you this question is WAY off the thread.......which was about a Canon printer ........

........ you should start a new thread or try google 

[http://lmgtfy.com/?q=wireless+HP+printer](http://lmgtfy.com/?q=wireless+HP+printer) :D

---

