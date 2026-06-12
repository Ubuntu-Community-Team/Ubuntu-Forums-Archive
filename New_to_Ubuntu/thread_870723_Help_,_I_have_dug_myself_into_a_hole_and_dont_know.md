---
title: "Help , I have dug myself into a hole and dont know how to get out ."
date: 2008-07-26
forum: New to Ubuntu
---

### Post by todaymueller on 2008-07-26
:confused: Hi everyone , 
                        this is my first post here [ although i have a feeling there will be more ] . 
I have recently installed gutsy gibbon on my PC and everything was hunky dory , until I started messing around trying to get the graphics card to work . I looked on the forum to see if anybody else had had any problems with the Radeon X300SE and it would appear that it was a problem card . In fact I could not see that anybody had come up with a satisfactory answer to this . But I carried on fiddling and downloading drivers and trying them out on various settings to see if I could get it to go . But with no joy . Then I managed to install a driver that does not work and now I can not see anything other than white/blue noise . I have tried re-booting , but no luck . I tried plugging my monitor into the port on the motherboard so it would run off the integrated graphics . It just told me to plug it back into the graphics card . I even tried removing the card altogether , that did not work either . As I do not play games on my PC and do not need a fancy graphics card I would think the best solution , for now , would be to run off of the integrated graphics . I have a Dell Dimension 5150 running a Pentium D 2-66 GHZ .  So what do I have to do to get it to start up with the monitor working off the motherboard ?
 As is probably obvious to anybody reading this I am  a computing dunce so any answers will have to be easily understood !!

---

### Post by Elfy on 2008-07-26
If you want to go back to the integrated graphics - remove the Radeon card. When you reboot - use the recovery option, when you get to the root prompt, use this command

```
dpkg-reconfigure xserver-xorg
```

It shopuld ask you some questions - answer as best you can, mostly default I think.

---

### Post by eightmillion on 2008-07-26
You might try "sudo dpkg-reconfigure -phigh xserver-xorg". Make sure you select the appropriate graphics card when prompted. It might be a good idea to use the "lspci" command before you reconfigure xorg and find the line with your integrated graphics card. For example, mine is "**00:02.0** VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)". The bolded numbers are the BusID. You may want to write that down. If you come across questions that you don't know the answers to, go with the defaults. Good luck. Hope that helps.

---

### Post by Elfy on 2008-07-26
> It might be a good idea to use the "lspci" commandGood idea - if the output for the graphics goes past the screen and you can't see it try

```
lspci |grep VGA[/code
```

but do it after you have removed the other card

---

### Post by todaymueller on 2008-07-26
Thanks for the replies , 
                         I tried 'dpkp-reconfigure xserver-xorg' and answered all the questions as best as I could . All appeared to go well until I got 'xserver-xorg postinst warning ; back up in /etc/x11/xorg.conf. 200080726222115'
then 'root[at]john-desktop.accent hash 
Ok first problem what do I type in now and why has my keyboard gone peculiar ?  When I type 'at' 'accent' and 'hash' i get " \ and |  
My hole has now got a little deeper !

---

### Post by Elfy on 2008-07-27
Firstly - is the screen ok now - assuming it is you can chnage keyboard layouts in System Preferences Keyboard.

---

### Post by quinnten83 on 2008-07-27
yeah the reconfigure command is not just for graphics, but also for keyboard layout. You probably just chose the wrong one. It can easily be reconfigured so don't worry about it for now.

---

### Post by todaymueller on 2008-07-27
Waahay\\:D/ I am up and running !The machine is now using the on board graphics and its looking good . Still have not worked out how to re-configure my keyboard yet . I have tried choosing the make [ logitec ] from the list of manufacturers but that has not made any difference . I will have another bash at it this evening when I have more time , Thanks again to you all for spending the time to sort me out . 
But I have now got my head out of the hole and am now in daylight smelling the roses .

---

