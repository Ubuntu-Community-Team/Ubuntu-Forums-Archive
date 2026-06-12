---
title: "im completely confused"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by from-nibly on 2008-07-17
ok so im a beginner at linux but im pretty good with xp and vista and what not. im starting a business and i need to set up a php server so i can submit tickets for computers and customers so i can store all of their information.  and i wanted to use ubuntu to do that

i have previously installed ubuntu server addition but having no experience whatsoever a text based user interface is not going to bode well for me.  so i installed ubuntu desktop edition on my laptop.

ive downloaded what i thought were all the necessary tools to at the very least get started with creating the server.  however ive been flipping through countless tutorials and i cant seem to get connected to the internet. my wireless doesn't work and my ethernet doesn't work according to the network tools app neither of them exist and can't be configured.

i don't know why but i can't find the hardware information.  in the help window i click on connecting to the internet and one of the things it suggests is to see if my computer recognizes the hardware by going to hardware information but its not there.

can anybody help me?

ive got a Compaq presario c712nr

---

### Post by phidia on 2008-07-17
Put this in a terminal: lshw -C network
That should show your card. Also iwconfig will show the connections but if the card isn't enabled it won't show much.
I'm guessing with that notebook and because it wasn't detected automatically that you might have the atheros card but let's see from the output.

---

### Post by from-nibly on 2008-07-18
iwconfig gives me that lo = no wireless extensions and eth0 = no wireless extensions

the lshw command just tells me all the useless specs on my hardware (at least useless to me) both ethernet and wireless have drivers although i dont see it in network settings to configure it (although i dont know if it is supposed to be there)

my best guess is that the ethernet card and the wireless card is disabled the reason i say this is because my router doesnt detect it being plugged in (no light) and the card doesnt light up when its plugged in either

---

