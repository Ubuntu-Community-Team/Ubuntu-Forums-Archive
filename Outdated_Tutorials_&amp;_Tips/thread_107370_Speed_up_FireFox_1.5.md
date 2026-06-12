---
title: "Speed up FireFox 1.5"
date: 2005-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Sp@z on 2005-12-22
Here is a lil tip for Firefox. I tried the extension to speed up firefox and was sorely dissapointed. this will make you blink and shake your head and say Hot diggity damn! 

1. Type about:config into teh address bar and hit return.

2. Alter teh entries as follows (by double clicking each entry):

Set network.http.max-connections to 48

Set network.http.max-connections-per-server to 24

Set network.http.max-persistent-connections-per-proxy to 12

Set network.http.max-persistent-connections-per-server to 6

Set network.http.pipelining to true

Set network.http.proxy.pipelining to true

Set network.http.pipelining.maxrequests to 8.

Any more and you may get banned from teh site visited, as it may be viewed as DOS attack. Try a higher value say upto 32 but be prepared to lower teh value if sites fail to load.

3. Lastly right-click anywhere and select New-> Integer.

Name it nglayout.initialpaint.delay and set its value to 0.
This value is teh amount of time teh browser waits before it acts on information it recieves.

Pages should load 2-3 times faster.
	
_________________

---

### Post by ubuntu_demon on 2005-12-23
thnx for the howto :)

You could also try the extension fasterfox :
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

### Post by majikstreet on 2005-12-23
[QUOTE=ubuntu_demon]thnx for the howto :)

You could also try the extension fasterfox :
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)[/QUOTE]
yeah..
I actually ran into one site that wouldn't let me do something because I used that extension - related to prefetching.. it's [http://dnsstuff.com/](http://dnsstuff.com/)

> 
FORBIDDEN: Pre-fetching abuses our website.

If you are using the FireFox extension 'FasterFox', it is very poor and will block you from websites that it abuses. Please uninstall it (and perhaps add a comment to the FasterFox page. If you are not running it, you are running some sort of poor extension that pre-fetches pages that it shouldn't (ones without a 'link' marker). Once you have done this, you can re-load this page. Note that if you do not remove the rogue program, you will continue to see this message occasionally.

If everyone did this, it could easily quadruple the load on our server, and increase the total amount of wasted bandwidth on the Internet by 10 times or more. While we should be able to handle at least 10 times our current load, other websites aren't so lucky, and the operators may have to pay extra money as a result -- and perhaps shut down their websites. FasterFox abuses the Internet, there is no question about that.

NOTE: There *are* a few other rarely used programs besides FireFox that do this (there appears to be a rogue web proxy that does this too).


---

### Post by ubuntu_demon on 2005-12-23
You don't have to enable prefetching in fasterfox. Fasterfox also optimizes the network settings.

---

### Post by benplaut on 2005-12-23
[QUOTE=majikstreet]yeah..
I actually ran into one site that wouldn't let me do something because I used that extension - related to prefetching.. it's [http://dnsstuff.com/](http://dnsstuff.com/)[/QUOTE]

up in the corner of the page, 

Your IP: --------------
ASN: 10838 [OCEANIC-INTERNET-RR]
Near: [COLOR="Red"]**Herndon, Virginia**[/COLOR]
United States


ROFL!!!

---

### Post by majikstreet on 2005-12-23
[QUOTE=benplaut]up in the corner of the page, 

Your IP: --------------
ASN: 10838 [OCEANIC-INTERNET-RR]
Near: [COLOR="Red"]**Herndon, Virginia**[/COLOR]
United States


ROFL!!![/QUOTE]
LMAO :)

mr. hawaii..

---

### Post by Brando569 on 2005-12-23
fasterfox did all that for me, and i had the values set higher with it so i let them the only thing i had to add in was ng.paint.delay and i havent had a problem with faster fox yet

---

### Post by Syphin on 2005-12-23
fasterfox did it all for me as well, accept

network.http.max-persistent-connections-per-proxy
network.http.max-persistent-connections-per-server

were set to 18 and 8..  nglayout was already made also.. :) Thanks though, i used to do all this manualy ><  all these extensions and addons are making me lazy.. :P

---

### Post by dage on 2006-01-01
Thanks a lot for this best tuto :), my firefox 1.5 is 4 or 5 time faster :d, thanks a lot and happy new year :)

---

### Post by Lord Illidan on 2006-01-01
Hot diggity damn! This does feel faster. Thanks for the howto!

---

### Post by dage on 2006-02-06
if you want to change it for all users, mod this file: /opt/firefox/greprefs/all.js with your text editor ;)

---

### Post by bikeboy on 2006-02-06
Guys you do realise that the initial paint delay option doesn't actually speed anything up. It might give that impression to some but all its really doing is showing you what's going on eariler. If the delay was set longer FF would still be doing the rendering but you wouldn't realise until it popped up.

Some ppl talk about IE being faster but what it's actually doing is showing you the page eariler.

---

### Post by fuscia on 2006-02-17
changing the value in both *network.http.proxy.version* and *network.http.version* from 1.1 to 1.0, speeds things up. can't say i have any idea why. the advice was given to me by someone who knows what he's talking about (if that's any comfort to you).

---

### Post by bdb51 on 2006-03-06
you could use the tweak network extention. It's better than fasterfox

---

### Post by Christopher on 2006-03-17
[QUOTE=bdb51]you could use the tweak network extention. It's better than fasterfox[/QUOTE]

Is it compatible with Firefox v1.5.0.1 ?

---

### Post by ironchef on 2006-03-17
[QUOTE=ubuntu_demon]thnx for the howto :)

You could also try the extension fasterfox :
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)[/QUOTE]

This works great, except mplayer-plugin keeps crashing for me.

---

### Post by Klejs on 2006-03-20
Thanks for that m8!

---

