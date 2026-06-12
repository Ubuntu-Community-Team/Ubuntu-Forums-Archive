---
title: "Newbie who could use some help troubleshooting Firefox and Amazon player"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by wizrddreams on 2015-04-15
Hello. I am a new user of Ubuntu 14.04 and Mint 17.1. I really enjoy the operating systems, especially Mint! 
However, I have an Amazon account that my girlfriend and I have purchased a lot of content on, and we enjoy watching stuff using the Amazon Player. 
A few months back when I started on the Ubuntu 14.04, I came across in various forums, a solution to get the Amazon Player to work by installing the HAL ppa. 
This worked great for quite some time! Until last weekend.

When I started using another computer with Mint, I used the same procedure and it worked, aside from a slightly glitch-y screen. 
So me being agitated I needed to get rid of glitch-iness. 
So I updated the flash-plugin, did some searching around and came across Pipelight. ([http://pipelight.net/cms/about.html](http://pipelight.net/cms/about.html))
I thought, oh great! This will probably fix it, let me install without really thinking about it (stupid and a mistake). 
Once I installed Pipelight following the standard procedure, the Amazon player no longer worked. 
To the best of my abilities I tried to get rid of pipelight, using purge apt-get remove. 

The strange thing is that Amazon Player through Firefox no longer works on my 14.04 computer, nor a Windows computer with Firefox. 
The only way the mess I made on the Mint Firefox could be correlated to the other computers not working is if these changes transmit through my Firefox account. 
Which can not be?

Anyways, I am at a point now where I need to either completely un-install my current Firefox on both computers, and re-install HAL to see if it works. 
In which case, I will need help learning how to do so, so that there are no traces of Firefox or it's current settings in the OS. 
Or, perhaps the Firefox and Amazon Player are just incompatible at present. 

Thanks, ahead. And I'm looking forward to any responses.

---

### Post by wizrddreams on 2015-04-15
Well turns out that there was a very simple fix. 
Instead of completely reinstalling Firefox, I just deleted all the contents of the hidden /.mozilla folder in the home directory. 
Did the trick. Don't ask me why. :-P

---

### Post by RogerStenning on 2015-05-11
+1 - that trick worked for me as well - many thanks :D

---

