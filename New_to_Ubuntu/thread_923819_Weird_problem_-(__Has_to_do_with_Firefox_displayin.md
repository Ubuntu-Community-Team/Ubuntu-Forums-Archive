---
title: "Weird problem :-(  Has to do with Firefox displaying the wrong fonts"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by sum janus on 2008-09-18
Hey,
I'm having a really weird problem with my Firefox.  I'm on Ubuntu 8.04 LTS with Firefox 3.0.1.

What's going on is that for [one specific forum software](http://www.anelectron.com/board/index.php?), all of the fonts are displaying in COURIER (or courier new, I can't tell the difference).  This stinks!  The only exceptions to that problem is data run through forms... i.e., when I fill information into a form field that displays right.

Now, I ask this *here* as opposed to on a Firefox forum because, for some reason, I don't get this problem anywhere else.  I've checked in Firefox 2, Firefox 3, IE 6, and IE 7 on computers running Windows XP.  They display the forum just fine.  Which makes me think there's some back-end plugin running for Firefox that was developed by Ubuntu.

Just some random tidbits:
[LIST]
[*]I've viewed the CSS, and it's not SUPPOSED to be showing up in courier
[*]I'm running the theme "Nautilus 1.8.38"
[*]The only extensions I have are: FireFTP, Adblock Plus, RefControl, web developer toolbar, and of course, the Ubuntu modifications
[/LIST]

Any help you could give me would be WONDERFUL!  Thanks so much!

-Eric

[hr]

EDIT:
A-ha!  I've figured it out!  I'm almost glad that I got to this before all you friendly people replied... because this is a rewarding feeling!  Here's a block of the CSS:
```

body{background-color: #FFF;
color: #000;
font-family: Verdana, Tahoma, Arial, Trebuchet MS, Sans-Serif, Georgia, Courier, Times New Roman, Serif;
font-size: 11px;
margin:0px 15px 0px 15px;
padding: 0px;
}

```

All of the fonts listed there *except* Courier, sans-serif, and serif are *Windows* fonts, and exclusively for Windows!  Even though Sans-Serif is listed before Courier, it's called (at least on Ubuntu) **sans-serif** WITHOUT the capitalization!

Hurray!  Since I will (possibly) be joining the development team for that software.... I might be able to help them out by fixing that ;)

Even though you guys didn't really do anything (although somebody may have replied while I'm editing this), Ubuntu Forums just gave me a place to think out loud!  Hurray!

---

