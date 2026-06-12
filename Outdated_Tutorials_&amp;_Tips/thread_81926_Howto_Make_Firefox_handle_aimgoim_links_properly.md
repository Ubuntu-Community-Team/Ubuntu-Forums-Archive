---
title: "Howto: Make Firefox handle aim:goim links properly"
date: 2005-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ming0 on 2005-10-25
Now you can make Firefox and Gaim handle the little IM links properly ( i.e. href=Aim:goim?screenname=whateversclever).

1.) open Gaim's buddy list and open: tools > preferences

2.) on left pane, click "plugins". in main pane, find "remote control" and make sure it is enabled

3.) in a new firefox tab (ctrl + t) in the address bar, type about:config
 
4.) right click and choose "new" > "string"

5.) in the first box add the following value```
network.protocol-handler.external.xmpp
``` 6.) in the second box add the following value```
true
``` 7.) right click again and make another "string"

8.) in the first box add the following value```

network.protocol-handler.app.xmpp
``` 9.) in the second box add the following value```
/usr/bin/gaim
``` 10.) test it out here: [Send a message to ming0]("aim:goim?screenname=thegoodstufsgone&message=Hi+there,+I+am+an+uberdork.")

11.) when the "external protocol" box pops up, check the "remember this choice" box and click "launch application"

12.) yippe! it worked! (IM me if it didn't)
[]("http://www.cusser.net/extensions/disabletarget/")

---

### Post by majikstreet on 2005-10-25
It worked! W00t!

I only have one correction: when you right click, you need to select "New" then "String".

:)

**I installed the extension, and AIM link still open in a new tab**

---

### Post by ming0 on 2005-10-26
[quote=majikstreet]**I installed the extension, and AIM link still open in a new tab**[/quote] you know, now that I reset, I'm getting an extra tab too :(

Edit: I figured it out--first I was clicking on my extra link and then I tried the one on my profile <---- That one doesn't spawn an extra window...

BTW, thanks for the correction ;)

---

### Post by Technoviking on 2005-10-26
Does Gaim have to be running?

Mike

---

### Post by NeoChaosX on 2005-10-26
Just  tested it - yeah, Gaim has to be running and logged on.

Still, this is useful.

---

### Post by majikstreet on 2005-10-26
[QUOTE=ming0]you know, now that I reset, I'm getting an extra tab too :(

Edit: I figured it out--first I was clicking on my extra link and then I tried the one on my profile <---- That one doesn't spawn an extra window...

BTW, thanks for the correction ;)[/QUOTE]
No problem.... But, I wish it didn't open a new tab....

---

