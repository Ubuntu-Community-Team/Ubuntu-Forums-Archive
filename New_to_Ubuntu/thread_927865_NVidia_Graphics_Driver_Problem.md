---
title: "NVidia Graphics Driver Problem"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Bulker on 2008-09-23
Hello!

I am new to Linux, but am getting used to it remarkably well. There is only one problem.

After having installed Ubuntu, it did not take long before I noticed that I could not change my screen resolution to anything higher than 800x600. Neither did it take long for me to realize that the problem most probably had to do with the graphics card.

When I choose to use the driver which Ubuntu suggests, I get a black screen upon rebooting. I have also tried using EnvyNG, where the auto-detect function gets me nowhere - returning a message that my card is not supported. Manually selecting 173.14.12, using EnvyNG, does bring my resolution up to normal (1440x900), but also causes bugs, such as text and images that cut into each other in horizontal lines when scrolling down in an internet browser. (Cannot take screenshot as screen refreshes when I press print screen, sorry!)

I have a NVidia Geforce 9400M graphics card. To me it seems, from reading information on the internet, that there is no stable release for my card - am I correct in this assumption?

What would be the best thing to do in this situation?

Grateful for all help!

---

### Post by SpenceMakesSense on 2008-09-23
try changing the moniter size in this program run this command
```
gksu displayconfig-gtk
```

---

### Post by Tatty on 2008-09-23
Did you try to install the 96.x driver via Envy?  I found in hardy that the 173.x driver did not work for me but 96.x did.

As your card is newer i wouldnt hold out much hope for backwards compatibility like that, but its worth a go.

---

### Post by Bulker on 2008-09-23
I cannot choose any higher resolution than 800x600 from that window. What is interesting, though, is that my screen model is registered as "Plug 'n' Play". How am I supposed to know what model screen I have for a Acer Aspire 7530G laptop?

I will try the other driver now.

*Edit: It did not work. I was forced to use low-graphics settings to start the OS.*

---

