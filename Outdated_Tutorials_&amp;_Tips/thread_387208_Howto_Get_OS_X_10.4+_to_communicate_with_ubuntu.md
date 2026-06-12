---
title: "Howto: Get OS X 10.4+ to communicate with ubuntu"
date: 2007-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Draddy on 2007-03-18
This is not a formal tutorial, just an FYI how to combination of other tutorials. 


I spent the last 7 hours of my life reading every single tutorial on this disscussion board. 

I reinstalled ubuntu, installed samba, and about 15 other options trying to set up my PC to be accessable to my Apple computers as a data server.

and hole-lee crap that was the most unproductive, conter-intuitive afternoon i have EVER spent working on computers... I can NOT get much less figureoutable than that. my heart started beating at 2x when it first worked... I was so surprised and happy.. that is how frustrated I was all afternoon. 

So this tutorial is for all the normal people in the world, who are not super nerds, what want to use their PC as a server.


Now out of all the tutorials, this one was the easiest to understand, and most accurate in what he said would happen. 

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

as you can see he is discussing how to connect it to a windows network.

follow those steps exactly.. I found that the less i changed the better... everytime I changed something it ended up not working in the end. So only change what you have to (host name, etc.) (oh and BTW: one thing, while editing the config file, the only thing I didn't catch right away, is the last to fill in things, at the very bottom (the force-whatevers) make sure they are BOTH your login names (which should be the same for both computers... for me they both were david.)

after you get that working, make sure to go to networking and set the linux computer to a static IP address. On my network, I went into my linksys wireless router (192.168.1.1) and set up 192.168.1.106 as one of the 3 possible static IPs. You obviously do not have to dissable DHCP. 

I also set the WINS ip to 192.168.1.106 right below it.


Then go into networking, double click on your eithernet card, and type all of that in, IP = 192.168.1.106, whatever the second one is called = 255.255.255.0, and the gateway 192.168.1.1 .

now go to your apple.... while in finder go up to the "go" menu, click on networks, and the names you picked should be in there.

as you can see in the picture, its a simple click of the mouse. follow the thing over and then click connect. Make sure to authinticate yourself (I believe it also has the option of authinticating  under a different name.) and connect.. it should connect and show up on the left like you see, (the myfiles link)

good luck! 

I understand this is not a normal tutorial... but I know 1 BILLION percent that I would have not been as frustrated, and would have finished 6 and a half hours ago if someone had created this thread for me.

[img]http://www.draddy.org/mbp/Picture 3.jpg[/IMG]

---

