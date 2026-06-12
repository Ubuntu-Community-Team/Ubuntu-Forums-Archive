---
title: "WOW (Burning crusade) installed on Laptop"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by grrrbob on 2008-05-27
Hi. Feel free to ask me questions because i am new to linux and therefore likely to omit important information (so apologies over onto the problem.

i have installed the new version of ubuntu onto my lenovo thinkpad laptop using the free cd from ubuntu website(impressive btw). There seemed to be no problems. I can connect to internet ok both wireless and with wire. I then attempted to install WOW. checked forums and installed Wine using package manager on ubuntu (different than what i am used to..but got round this). then i installed wow using wine. then i used cd to again install burning crusade expansion. The watched intro...still looked good. then logged in and had to install patch. 

however, since installing the patch i cannot seem to start WOW from either the icon on desktop or through wine. 

Any ideas or should i uninstall then install again first?


BTW i used the blizzard repair program and it failed at the end with an error message which read...(sadly from top of my head) failed to initialize. you do not have permission to ....

any help appreciated

---

### Post by Astarroth on 2008-05-27
Here is how I installed WOW on my machine. I opened Wine so that I was in it's version of the C:\ directory then copied my Wow folder from my windows machine to it (C:\ program files\...). Copied it to the same place in Wines directory. All I had to do then was edit the WFT.config file to add the opengl settings.(Sorry but I don't remember the settings but, I found it by searching for WOW on unbuntu in the forums.) I was off and running without any problems.

---

### Post by grrrbob on 2008-05-27
sadly i dont have windows partition. 

i installed over windows vista. it was using 60% of my memory when idle compared to 20-30% memory used by ubuntu when idle.

BTW i have already added the opengl settings to config file.

---

### Post by T-Virus on 2008-05-27
I've seen that Cadega have specific setting for WoW which might make installation easier. That's in case if you'll want to try Cadega instead of Wine.

---

### Post by grrrbob on 2008-05-27
will try that tonight and report back tomorrow.

unless anyone recommends anything else?

---

### Post by T-Virus on 2008-05-28
> **grrrbob said:**
> will try that tonight and report back tomorrow.

unless anyone recommends anything else?

How did that go?

---

### Post by nefrin on 2008-05-28
Cedega is also a subscription service (5$ a month, but it's still a fee) to use, plus your sub to WoW. 

I have heard of a lot of people that use WINE to run WoW and it works fine, do a little googling, read some forum threads and stick with WINE (unless you really want to pay the extra $$$).

Generally I find that when I come across a game installation problem taking those steps gets me a solution within a day or two. I'll try to contact some of my buddies that run WoW under WINE and see how they set it up.

---

### Post by T-Virus on 2008-05-29
Ah, so it's pay to use.. Not a gamer myself. Btw, I actually heard somewhere that if you compile it yourself, it's free, and you only pay for .deb, .rpm. Is that true?

---

### Post by hyper_ch on 2008-05-29
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

follow this guide and it will run perfectly. In that guide I opted for the actuall "installation" of wow for this approach
> 
Alternative 1 (Copy from Windows):

You can also just install WoW in Windows and then copy the entire World of Warcraft folder over from your Windows installation. 


runs perfectly fine with teamspeak et al.

---

### Post by grrrbob on 2008-05-29
not been able to attempt cadega yet. although if there is a fee involved i dont think i will bother.

i dont have internet access at home at the moment. so will probably uninstall and try again this weekend. will post results.

although last night when i experimented with ways of opening wow. i opened the wow.exe program in wine folder and the wine scren came up and the game started but then crashed. i had to unplug the battery.

@Hyper...yeah thats the thread i used to install wow. will try again though as i may have missed a small step.

---

### Post by hyper_ch on 2008-05-29
don't you have access to a win machine anywhere? There you could just install wow and then copy it over to your laptop...

---

