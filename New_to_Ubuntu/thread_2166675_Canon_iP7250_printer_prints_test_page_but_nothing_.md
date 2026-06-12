---
title: "Canon iP7250 printer prints test page but nothing else"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by chris-burmajster on 2013-08-10
I wonder if anyone can help me please? I have a Canon Pixma iP7250 wireless printer and an Asus RT-N56U router. I installed the printer wirelessly with pukka Canon drivers thanks to someone on this forum and it always prints a test page successfully, but it won't print from any other program. The print queue box says "not connected?". It must be connected as it prints a test page, so what have I done wrong? I'm running 13.04.

Many thanks, as always.

Edit: I discovered the printer's IP address from the router and installed it via that. It now prints from LO as well as the test page but printing a photo from Image Viewer still brings up the "not connected" message. Why does it print from some programs and not others?

---

### Post by EBWQNHD on 2013-08-10
I guess if we just check the printer drivers are all installed fine;

you may have installed [COLOR=#008000]cnijfilter-ip7200series-3.80-1-deb.tar.gz
[/COLOR]
if you paste 

> [COLOR=#ff0000]dpkg -l | grep cnijfilter[/COLOR]

____________________________

Can I suggest you work through this

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

_____________________________________

I wonder what a command line print instruction would yield

for an MG3100, the command is 

> [COLOR=#ee82ee]lpr -P MG3100USB [filename] {-o option}[/COLOR]

I guess yours might be 

> lpr -P IP7250USB [filename] {-o option}  but you could check on the correct title

_____________________________________________________________--

Canon also offer the 

> cngpij -P MG3100USB Sample.png

this utilises cups: the cngpij command

so for you perhaps > cngpij -P IP7250USB Sample.png

---

