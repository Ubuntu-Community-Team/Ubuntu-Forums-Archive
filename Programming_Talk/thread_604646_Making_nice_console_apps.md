---
title: "Making nice console apps"
date: 2007-11-06
forum: Programming Talk
---

### Post by gushy on 2007-11-06
Guys,

I need to build a new application to monitor some system process, this app will be designed run on very old hardware so as such needs to be console based as I don't want to use xorg.

I need to be able to display text in varying sizes and colours, in positions on the screen that I define.  I also need to be able to display graphs in one section of the screen to show performance (like the line graphs in the resources tab of System Monitor).

Can anyone tell me what I should be using?  I thought ncurses might do the trick, but looking into it I can't find any examples of something similar.

Thanks,

---

### Post by CptPicard on 2007-11-06
No, ncurses won't cut it as it's text based and you need graphics...  how about [SVGAlib]("http://www.svgalib.org/")?

---

### Post by gushy on 2007-11-06
I did think ncurses was text base, but I wasn't sure if that was it's limit.

SVGAlib looks like it'll do the trick, no need for X, looks like it's fast (speed of loading and running is a major factor here).

Thanks.  I'll look into it further!

---

