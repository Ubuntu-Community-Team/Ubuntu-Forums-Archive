---
title: "[SOLVED] Flash problems in Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by shadow-of-sin on 2008-05-01
I have a weird problem with Flash in Hardy. I am able to play Youtube and Veoh videos fine. However when i go to sites with embedded Veoh videos, they don't appear. I get the same problem for crunchyroll.com. (I can get them to work by looking in the page source for the direct url to the player though)

Flash worked perfectly fine for me in Gutsy. Also, no, I don't have either Gnash nor swfdec installed. I get the same problems with both the flashplayer from the repos as the one from the adobe site.

---

### Post by shadow-of-sin on 2008-05-01
Ok, after some troubleshooting, it seems that this problem lies in Firefox 3 as all flash sites work using Epiphany. I would submit a bug report but I don't know exactly what the problem is.

What I've found out so far:

[LIST]
[*]Youtube works (it uses SWFObject)
[*]Sites that use the  <embed src""> tag work
[*]Sites that use the <object type="application/x-shockwave-flash" data=""> tag don't work
[*]Crunchyroll which uses UFO ([http://www.bobbyvandersluis.com/ufo/](http://www.bobbyvandersluis.com/ufo/)) doesn't work
[/LIST]

Anyone have any ideas as to what's wrong?

EDIT: Tudou.com also uses SWFObject but it doesn't work. Tudou.com uses the swfobject.embedswf method to display the flash while Youtube does this:
[HTML]var fo=new SWFObject(swfUrl,"movie_player","480",height,v,"#FFFFFF");
fo.write(player_div);
[/HTML]
So I think the problem lies there.

EDIT2: It seems that Tudou uses SWFObject 2 while Youtube uses 1.5, this could be the problem.
Another EDIT: Ok, I'm stumped, I tried the SWFObject 2 samples from the site, and they work, so I'm not sure why sites like tudou don't work...

---

### Post by Das Uberdog on 2008-05-07
I am also experiencing this issue.

---

### Post by shirokurokun on 2008-05-07
Hmm... Flash Player problems?
Are you using Ubuntu hardy?
Are you using Firefox 3 beta 5 bundled with hardy?
Did you install adobe flash player 9(if you didn't, that's probably the problem)?

this only applies if lines 2 and 3 are true:
I had this problem first when using firefox 3 beta bundled with ubuntu hardy. I can't install adobe flash player 9 using the debian or rpm packages converted by alien -k. If that is true for you then do this:

follow the link [COLOR="Blue"]_here_[/COLOR]
-download the tar.gz package
-open it with archive manager
-drag install_flash_player_9_linux folder out to desktop or 
 wherever you want
-open install_flash_player_9_linux folder with file manager
-rightclick on empty space to open menu and select open terminal here
-type on terminal sudo ./flashplayer-installer
-press enter
-quit your mozilla browser and press enter
-if the installer is asks for directory put /usr/lib/firefox-3.0b5
 (this installs flash for all users)
-check your flash player plugin by viewing some vids on [www.crunchyroll.com](www.crunchyroll.com)

It should work for Xubuntu hardy, I don't know for others.

---

### Post by svenofix on 2008-05-07
> **shirokurokun said:**
> Hmm... Flash Player problems?
Are you using Ubuntu hardy?
Are you using Firefox 3 beta 5 bundled with hardy?
Did you install adobe flash player 9(if you didn't, that's probably the problem)?

this only applies if lines 2 and 3 are true:
I had this problem first when using firefox 3 beta bundled with ubuntu hardy. I can't install adobe flash player 9 using the debian or rpm packages converted by alien -k. If that is true for you then do this:

follow the link [COLOR="Blue"]_here_[/COLOR]
-download the tar.gz package
-open it with archive manager
-drag install_flash_player_9_linux folder out to desktop or 
 wherever you want
-open install_flash_player_9_linux folder with file manager
-rightclick on empty space to open menu and select open terminal here
-type on terminal sudo ./flashplayer-installer
-press enter
-quit your mozilla browser and press enter
-if the installer is asks for directory put /usr/lib/firefox-3.0b5
 (this installs flash for all users)
-check your flash player plugin by viewing some vids on [www.crunchyroll.com](www.crunchyroll.com)

It should work for Xubuntu hardy, I don't know for others.


I seem to be having more or less the same problems as everyone else,
although flash games screw up for me.

Btw shirokurokun, your link doesn't work for me.

---

### Post by shirokurokun on 2008-05-08
sorry, here it is
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
you should be able to download the tar.gz package now

---

### Post by shadow-of-sin on 2008-05-17
It turned out the problem was with one of the extensions I used: Adblock. I disabled it and everything works fine now

---

