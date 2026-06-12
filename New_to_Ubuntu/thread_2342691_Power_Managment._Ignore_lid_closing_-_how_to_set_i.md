---
title: "Power Managment. Ignore lid closing - how to set it?"
date: 2016-11-09
forum: New to Ubuntu
---

### Post by rompacz on 2016-11-09
Hi community,

Pre conditions: 
-Lubuntu 16.04
-Notebook Lenovo 
-External display plugged and working.

Action:
-Close the lid 

Result:
-External display switches off or goes to standby or etc.

Expected result:
-None. External display should still work.

How to change settings to achieve above? 
In power manager there is no possibility to choose something like 'no action' on lid closing.
I modified the file /etc/systemd/logind.conf and have now the line:
HandleLidSwitch=ignore      (without the # at the beginning)

The problem still exists. 
How the hell change this dummy setting?

Thanks in advance.

---

### Post by Bucky Ball on 2016-11-09
Welcome. Have you felt how hot the front of the laptop gets when the computer has been on for awhile? Where your hand goes when typing? It will be hotter when you close the screen, especially under heavy load. I'd be a bit worried about damaging the laptop screen which is why I've never done it as I had a setup where that would have been good previously.

What I did was install arandr and switch the laptop screen off. arandr is in the repositories (Synaptics, Software Centre). Good luck finding what you're looking for.

---

### Post by rompacz on 2016-11-09
Thank you for the reply, Bucky Ball.

Don't worry about my hardware, it is easy to turn off the laptop display while using external display. It could be done in display settings.  
I'm typing with external keyboard and I use external mouse. 
Plenty of people in my company work in such way from years. The only difference between me and them is they use other distro...

Is it anything more I can try?

---

### Post by Bucky Ball on 2016-11-09
I have no other suggestions.

> **rompacz said:**
> I'm typing with external keyboard and I use external mouse.

Yep, exactly the way I was using my laptop.

Good luck finding a fix.

---

### Post by mastablasta on 2016-11-10
> **Bucky Ball said:**
> Welcome. Have you felt how hot the front of the laptop gets when the computer has been on for awhile? Where your hand goes when typing? It will be hotter when you close the screen, especially under heavy load. I'd be a bit worried about damaging the laptop screen which is why I've never done it as I had a setup where that would have been good previously.
.
slightly off topic - second time i heard something like this. 

but it is strange to me that such option is (at least in my case)
1. officially supported by manufacturer
2. when they installed it that is how they set it up for me (at work). 
3. dock has a button to be able to turn on the laptop with screen closed.

I use dock and external mouse, monitor, keyboard. perhaps i need to go out in the field more to actually ,move the laptop. :-)

i have to say i did notice some darker letters on laptop's keyboard, though the screen is definitelly off in my case.

i really can't get used to working on 2 uneven screens. i think maybe i do not know how to set it all up propperly for dual screen.

> **rompacz said:**
> 
 Action:
 -Close the lid 

 Result:
 -External display switches off or goes to standby or etc.
.

in my case this happens on Windows 10 Fujitsu laptop. The workarround is so strane
1. using intel driver tool and setup a cloned screen
2. reboot
3. sign into OS and select only external monitor to be on. if i close the lid it will do as in your case.
4. reboot - while OS is rebooting, i quickly close the laptop lid.
5. now it should work.

else repeat from 1.

i have to repeat the excercise each time after i plug the laptop to projector at conference room (so at least once a week). Windows screen/desktop tools just get overwritten somehow or are not taken into account. it's like my command doens't reach the card. it's there but it's not registering. sicne i have to do this relatively often - i wish they gave me an SSD rather than 5400 rpm.

while it doesn't have to do that much with Lubuntu, my point is that perhaps official driver tools are needed for the desired setup.

---

### Post by Bucky Ball on 2016-11-10
> **mastablasta said:**
> slightly off topic - second time i heard something like this. 

Better to be off-topic for a post than have a user irreparably damage their machine. ;) My laptop gets real hot there and I wouldn't want to close a lid on it. A friend wrecked their laptop screen through the heat from their machine with the lid closed.

No doubt for many it is fine. Worth mentioning. Carry on. :)

---

### Post by mastablasta on 2016-11-11
it just means there is something to it. 

 but strangely enough - nothing in the official manufacturer's manuals regarding this. i always read the manual first before using the device.

 in any case it is company's laptop. so if it "burns" they will replace it. though i would lose all data on clients since there is 0 backup done (on a Windows PC with seeminly no additional antivirus and default firewall :o).

---

