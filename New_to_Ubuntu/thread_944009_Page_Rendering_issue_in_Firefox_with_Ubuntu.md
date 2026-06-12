---
title: "Page Rendering issue in Firefox with Ubuntu"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Orographic on 2008-10-10
Hi all,

Have been enjoying my install of Hardy Heron, presently have it as a dual boot on my older system with XP so as to work on my website in various browsers etc.

There is one slight problem though. At the top left hand side, 'Warnings - Quick Link' and 'Local Weather Guide' on my websites main page now render on two lines instead of one. In Linux Mint they render as one line, just like in FireFox 3 and IE via Windows XP.

[http://www.blackheathweather.com/](http://www.blackheathweather.com/)

And on my wife's page, the link 'Special Occasion Music' also pushes onto the next line.

[http://www.marionmusic.net/](http://www.marionmusic.net/) 

I've tried to change it in fonts in Ubuntu but it still persists. Anyone know why this happens in Ubuntu 8.04 but not Linux Mint? My Eee PC also renders the above mentioned menus as two lines via its default Xandros OS.

I'm no web design pro but my pages do pass the W3C standards in CSS and html.

---

### Post by sokopok on 2008-10-10
Every system will render fonts slightly different. Don't count on things looking the same everywhere. Design your pages so they don't break. different users will definitely see your page rendered slighty different. If you really need this kind of pixel-accurate layout use images instead of text (or even better: [the swap trick]("http://stopdesign.com/articles/replace_text/"))

---

### Post by mkokotovich on 2008-10-10
In Ibex beta those web pages look like you described they should, so it may have something to do with the current build of Firefox or some other relevant application that is on your machine.  I would make sure you are up to date (sudo apt-get update && sudo apt-get upgrade) or just wait until Ibex is released.

---

### Post by Orographic on 2008-10-10
Thanks for the replies. I do appreciate it. I'm a moderator on a large meteoroligical forum myself and value the time and effort put into posts etc.

I noticed that Ubuntu (Hardy Heron) on my newest machine also rendered the links mentioned above, onto two lines, so it seems something is a little different with Ubuntu. That's cool, I really like Ubuntu as it has so much support and collaboration associated with it. I'm up to date with Hardy Heron as well.

I do work fairly hard to make sure my site doesn't break and have tested it in Safari, IE 6 and 7, Firefox 2 and 3 via XP and Ubuntu and Mint in Linux. So far Hardy Heron is the only one that renders a touch differently and also a non-updated version of Xandros on my Eee PC 701. 

Will look into it more. :)

---

