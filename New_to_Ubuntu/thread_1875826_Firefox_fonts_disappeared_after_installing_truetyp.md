---
title: "Firefox fonts disappeared after installing truetype fonts"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by tschill on 2011-11-05
I encountered a problem with Firefox 7. After installing some Truetype fonts into /usr/share/fonts/truetype most, but not all websites didn't have any text in firefox. The text would still load (switching in firefox preferences>content>fonts&colours>advanced unticking "allow pages to show their own fonts..." would show the text in standard font) and using firefox with a shared profile in Windows would also show websites without any problem. 
The problem must therefore have been within Ubuntu but I didn't find any solution here in the forum. I found a solution on [SharmWeb]("http://www.promo.sharmweb.net/no-fonts-mozilla-firefox-ubuntu-text-disappeared") so I thought I post the link here in case anybody else is as desperate as I was (was ready to reinstall firefox from scratch, since reinstalling the main components with Synaptic Package Manager didn't help).

In case the above mentioned website goes offline, here's what they suggest:

[LIST]
[*]Open the terminal
[*][FONT=Courier New]cd /usr/share/fonts[/FONT]
[*][FONT=Courier New]sudo chmod -R 755 *[/FONT]
[*]Refresh the webpage in Firefox and everything should be turned normal.
[/LIST]

[ ]("http://www.promo.sharmweb.net/no-fonts-mozilla-firefox-ubuntu-text-disappeared")

---

