---
title: "ubuntu server 12.04 installation"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-05-17
Have installed ubuntu server 12.04 on a laptop and now i'm trying to connect to it...

I'm a bit confused about how the server broadcasts to other computers.
I take it it doesn't use its built in wireless card. Nor does it use the router which recieves the internet from the phone line and broadcasts it through the house? it is currently connected to this router through an eithernet cable to the internet..

If i plug in an old router into the laptop which is configured to broadcast from an ethernet cables in place of the current one- is that the best way for the server to broadcast...

Does 12.04 need access to the internet? if so perhaps i could set up the wireless card to receive internet

this is a command line installation...

sorry my lack of understand on this, and thanks for any replys

---

### Post by rgreener25 on 2012-05-17
ahh its okay we were all like you at one point, right on the computer with ubuntu server computer type ```
ifconfig
``` and note the ip address for eth0 now go to another linux computer and open a terminal window and type ```
ssh -l <username for server pc> <ip for eth0 on server pc>
```.

Thats to access a remote terminal to access the files open the file browser on a linux computer press CTRL L and type ssh://<username for server pc>@<eth0 address for server pc>

---

### Post by bikefreakvinnie on 2012-05-19
V excited about this folks! Its finally working and i've made contact from a windows machine!! I just gotta tweek and up the security a bit etc!!

At the moment i'm trying to set up access to an external hard drive plugged into my server laptop.

could anyone tell me the correct way to do this?





i've mounted it fine at: /media/external but i dont know how to make a path to this from my windows machine

my current share folder is at: \\my ip\share

i thought it'd be something like: ../../media/external 
as this is the relative path from /home/me where share is located - or perhaps its possibe to mount the external in my /home/me folder....

---

