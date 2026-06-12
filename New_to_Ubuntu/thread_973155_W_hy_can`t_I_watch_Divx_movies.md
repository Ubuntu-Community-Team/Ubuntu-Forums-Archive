---
title: "W hy can`t I watch Divx movies?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by germanix on 2008-11-06
I run Ubuntu 8.04. I have the VLC player installed that I understand also play Divx. Whenever I want to watch a movie streamer over the internet, it wont run. Any ideas what I need to do to be able to watch Divx movies?

---

### Post by jpoRS on 2008-11-06
Hey Germanix,

I am not sure if this will help, but go to System>Administration>Software Sources.  On the first tab (Ubuntu Software) do you have "Software restricted by copyright or legal issues" selected?

Viel gluck,
jim

---

### Post by desperado665 on 2008-11-06
You could also install Ubuntu Tweak from here: [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

Then use it to install Ubuntu restricted extras. It should install the gstreamer codecs you seem to be missing.

---

### Post by LowSky on 2008-11-06
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by germanix on 2008-11-06
> go to System>Administration>Software Sources. On the first tab (Ubuntu Software) do you have "Software restricted by copyright or legal issues" selected?
Yes this is selected

> You could also install Ubuntu Tweak from here: [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
I have done this

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
This was already installed but not activated. I have now activated it.

I have done all of the above and thank you all for your tips. Unfortunately it still wont work. I only get an error message as follows:

Error. "You do not have a decoder installed to handle this file"
Any other ideas?

---

### Post by Crandom on 2008-11-06
Open a Terminal (Applications > Accesories > Terminal) and type this command:
```
sudo apt-get install ubuntu-restricted-extras
```
and press enter. Enter your password when it says (it won't appear to be typing anything, but it is). Press y if it asks you any questions.

---

### Post by germanix on 2008-11-06
I have the Ubuntu restricted extras already installed but thank you for your help.

---

### Post by billgoldberg on 2008-11-06
See the "codecs in ubuntu" link in my signature.

Click it and follow the guide.

You'll be set.

---

### Post by germanix on 2008-11-06
See the "codecs in ubuntu" link in my signature.

Click it and follow the guide.> 

I followed your advice. All is installed but no luck. Still get the same error message
Error. "You do not have a decoder installed to handle this file, you may need to install the correct codecs"
Thank you for your help

---

### Post by philinux on 2008-11-06
Can you post a link to a movie that doesn't play. We can try it and see if it plays at all.

---

### Post by LowSky on 2008-11-06
have you tried restarting the ocmputer after installing the codecs?

---

### Post by germanix on 2008-11-06
[http://movielab.tv/](http://movielab.tv/)
On this site all of the flash movies I can play, but none of the Divx movies

---

### Post by philinux on 2008-11-06
I get this and it does not play. No codec error message though, plus if i right click and choose open in movie player I get a codec error.

---

### Post by germanix on 2008-11-06
have you tried restarting the ocmputer after installing the codecs?> 

Yes I have, but it made no difference.

---

### Post by germanix on 2008-11-06
have you tried restarting the computer after installing the codecs?> 

Yes I have, but it made no difference.

---

### Post by germanix on 2008-11-06
> I get this and it does not play. No codec error message though, plus if i right click and choose open in movie player I get a codec error.

Well it looks like it is not playable then. The error message comes later. If you click on the triangle it opens a grey square and when you click on that, after a while the error message appears.
I have the same problem on other sites with divx movies.

---

### Post by philinux on 2008-11-06
There is this I found.
[http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)

Also some guy has package it in a deb file. It wont install here it says.

---

### Post by igknighted on 2008-11-06
Divx codec installed fine for me in Jaunty, still no luck in getting it to play.  I don't have any codecs installed on this setup though aside from that one, so I'll install the rest and see if it works.

FWIW, I've never gotten divx to play on linux, but would love to see it work if possible.

---

### Post by Viranh on 2008-11-06
I am able to watch DivX movies from the site you listed. I use mplayer and the mplayer package for firefox. I also have all gstreamer codecs from add/remove programs installed. Mplayer and mplayer for firefox were also installed from add/remove programs. As a side note, I'm using Intrepid and mplayer embedded in firefox is working much better for me now, although I still occasionally have to refresh a page to get something to load properly.

---

### Post by billgoldberg on 2008-11-06
> **philinux said:**
> I get this and it does not play. No codec error message though, plus if i right click and choose open in movie player I get a codec error.

It most likely means the video is removed or something.

Download a divx file from another source and see if it's working.

If you can play any divx movie using totem, then you can also stream it.

---

### Post by philinux on 2008-11-06
Tried a few at the site the OP posted all the same no dice.

---

### Post by philinux on 2008-11-07
Ok I got this to work using previous posters advice.

Remove totem-mozilla
Install mozilla-mplayer

---

