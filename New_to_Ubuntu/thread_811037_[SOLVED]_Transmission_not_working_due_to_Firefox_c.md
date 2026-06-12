---
title: "[SOLVED] Transmission not working due to Firefox can't find a magnet"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-28
I'm trying to download 

Apology, Crito, and Phaedo of Socrates

at Gutenberg.org ([http://www.gutenberg.org/etext/13726](http://www.gutenberg.org/etext/13726))

when I click the P2P links, I get an error message that Firefox can't find a magnet. Can someone tell me how to set Firefox to work with Transmission in P2P mode. I can't find a how-to on this. The FF Edit/Preferences doesn't show Transmission under applications. Somebody give me a clue!

---

### Post by kwacka on 2008-05-28
[http://kb.mozillazine.org/Register_protocol#Linux_and_Mac](http://kb.mozillazine.org/Register_protocol#Linux_and_Mac)
suggests:

* Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true

---

### Post by quelx on 2008-05-28
Good books,

Try this

You need Azureus as Transmission doesn't handle magnet links

at the terminal ```
sudo apt-get install azureus
``` if you havn't already done so.

Open FireFox > type **about:config** > promise to be careful

Right click the **Preference Name** bar > Click New > String
**network.protocol-handler.app.magnet** and Value **/usr/bin/azureus**

Right click the **Preference Name** bar > Click New > Boolean
**network.protocol-handler.external.magnet** and Value **true**

It may pop up and ask you which application to use, just point it at /usr/bin/azureus again.

EDIT: I tried to download using the P2P on guterberg's site and got ```
No data contained in 'magnet:?
```
> 
"If the link is dead, you’ll get a message “ERROR : No data contained in…”. This is comparable to downloading a .torrent file with no seeds/leechers. Click “cancel” and try to find another viable source (i.e. the corresponding .torrent file is an option)." so apparently the links are dead, you may need to find a different magnet source to verify.

---

### Post by spiralciric on 2013-03-05
I have posted the solution on my website. Its for Windows, but exactly  the same principle goes for Linux, just change the path. This goes for  all the clients. Visit: [Resolving Firefox Magnet Bug]("http://www.leeenux-linux.com/blog/resolving-bugs/")

---

