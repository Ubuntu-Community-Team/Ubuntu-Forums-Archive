---
title: "Dual Monitor Setup"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Morpheun on 2008-08-31
Hey,
     I recently bought one of these [http://www.newegg.com/Product/Product.aspx?Item=N82E16889107041](http://www.newegg.com/Product/Product.aspx?Item=N82E16889107041) to replace an old TV. Since it also has a VGA port I tried hooking it up to my computer as a second monitor but I can't get it to work in Ubuntu. I tried using it as a second monitor on my windows boot out of curiosity and it worked decently. However when I try to set it up with "Screen and Graphics Settings" it doesn't work properly giving me this error: 

[IMG]http://i38.tinypic.com/2a9e9hl.jpg[/IMG] 

I have a "Intel Corporation Mobile GM965/GL960 Integrated Graph[ics card]" as reported by lspci. I'm not adverse to using command line to configure it properly however I'd prefer not to use Xinerama if possible because of several limitations using it with a laptop. Btw, the monitor has been plugged in since boot (I've tried plugging it in after booting up too) but has been displaying an "OUT OF RANGE" message.

Thanks in advance for any help

---

### Post by _Atreides_ on 2008-08-31
I'm no expert but i think you need to use something like xinerama since you have an intel card. I mean I have an nvidia one so I can use twinview but your going to need one of those programs.

---

### Post by Morpheun on 2008-08-31
So I've been looking around, should it be possible to do this with xrandr?

---

### Post by Morpheun on 2008-09-01
So I tried with xrandr and can't get it working in there either. I'm using the vesa drivers if that helps.

---

