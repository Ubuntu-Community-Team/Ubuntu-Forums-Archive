---
title: "IC-PCR1000 Wideband Receiver"
date: 2007-04-28
forum: Programming Talk
---

### Post by ecarvalho on 2007-04-28
For over 10 years DXTuners held one of the biggest online Linux based radio / scanner network.
Basically, radios such as IC-PCR1000 Wideband Receiver connected to COM1 of a PC running LINUX could be controlled via their website using an embeded Java GUI.

Recently, the owner of DXTuners decided it was time to move on and shut down the website.
Thousands of subscribers have no longer a way to tune these receivers across the globe.
over 50 radios / nodes now are offline.

Why am I telling you all this?
I'm hoping someone with enough linux knowlege could come up with a GUI that can control a IC-PCR1000 Wideband Receiver thats connected to a PC (COM port 1) from the web.
I crying out for help! Is there a developer thats up to the challenge?

Heres the basic idea:

{ANTENNA}-->{RECEIVER}------>RS232 COM1{PC running Linux NOT Windows <---> Internet <---> {End User with GUI on Web Browser controls the radio from the internet}

The ideal GUI would have the various radio commands such as AM FM SSB.... knobs for volume, frequency dial, a small chat window so other users can share the same receiver and see someone else is there too, a start / stop audio stream button.... and a window where pre-set stations can be selected to listen to.

I have no money to pay for such work but I think having this running on Ubuntu can be great!
Maybe I'm day-dreaming here but I dont think it hurts to ask!

Let me know!
Ed

---

### Post by phossal on 2007-04-28
Strange. I had never heard of that site, but it seems to have been fairly well known and well regarded. Why did they kill the site? Wasn't it profitable? It doesn't have even one competitor?

If that's true, watch for budding pay sites with the same technology.

---

### Post by ecarvalho on 2007-05-02
I don't know if it was profitable or not. The owner is an IT guy and informed us all he was moving on with his personal life and no longer could keep up with admin the site. There were offers from other radio admins to take over but he decided it would be too complicated to run without him so scraped the site off.

The interface he used was his own design and it is copyrighted. I offered to buy the rights to use it but he ignored my email. 
I have my side of the server... the PC with fedora that controlled the radio and connected to the network. This PC had ssh running and open 8888 port but no web server running.
The program on the radio side is still there but I dont think we can even use it.
I have PCR1000 programs and Ubuntu has a GUI for the PCR-1000 radio called qpcr? not sure of the name. What Im looking for is a GUI that can be embeded on a webpage and control the radio.

---

### Post by phossal on 2007-05-02
Strange that the guy wouldn't want that hard work and contribution to live on - especially if he's "moving on". Maybe he's plotting a commercial path?

---

### Post by ecarvalho on 2007-05-03
Who knows...
I found on my archieves a screenshot of the site. Thats the GUI which controlled my radio. Each radio on the network had its own GUI.

[http://evpjournal.com:82/Dx/dxtuners.html](http://evpjournal.com:82/Dx/dxtuners.html)

I believe it was done using JAVA.

---

