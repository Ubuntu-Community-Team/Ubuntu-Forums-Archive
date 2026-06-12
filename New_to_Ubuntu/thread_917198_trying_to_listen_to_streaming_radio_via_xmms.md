---
title: "trying to listen to streaming radio via xmms"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by suzanneforums on 2008-09-11
Hello, 

I am trying to listen to streaming radio at [www.koop.org](www.koop.org).  Their instructions page suggested that linux users listen via xmms, so I downloaded xmms and--I don't know how to make it pick up the streaming radio.  I think the answer is probably really simple, but I am apparently the village simpleton, so it is beyond me.  Please help!

Thank you.

---

### Post by Pconfig on 2008-09-11
xmms is old and hasn't been updated for a while. Though it's still used alot. (rectification: xmms 2 is still active)

[http://streaming.koop.org:8508/listen.pls](http://streaming.koop.org:8508/listen.pls)

This is the url you need. You could paste it in firefox aswell. When i do so, firefox starts playing it ;)

As alternative you could use totem media player
movie ==> open location and paste the above url

---

### Post by BenAshton24 on 2008-09-11
Simple answer as you guessed, run the following command in terminal
> sudo apt-get install xmms2-plugin-pls
And that it basically, just click on the link the previous poster posted and open it in totem and your away :D
Hope this helps :D
Ben.

---

### Post by starcannon on 2008-09-11
audacious has pretty much replaced xmms for me. install it from synaptic, and grab all of its plugins while your there, and then open streams using that, it works great. I'm a long time xmms fan, and find audacious to actually work better (I was dubious when first told to try it but now prefer it).

GL and have fun

---

### Post by suzanneforums on 2008-09-11
Thanks for your help!  Playing it through Totem worked great.  I'll check out audacious.  Thank you everyone.

---

