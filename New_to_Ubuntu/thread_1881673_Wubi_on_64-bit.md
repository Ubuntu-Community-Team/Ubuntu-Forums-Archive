---
title: "Wubi on 64-bit"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by koymackoy on 2011-11-15
Hi everyone!

I have a laptop running Windows, below are the specs:


[LIST]
[*]OS: Windows 7 Home Premium 64-bit
[*]Processor: Intel Core i3 380M
[/LIST]
I've successfully downloaded Wubi. Will Ubuntu run smoothly on my laptop?

Thank you very much for your time. :D

---

### Post by bcbc on 2011-11-16
It depends - some graphic cards/wireless can require a little messing around. The best way is to create a CD or USB and boot from it and select "Try it" without installing. Then you can see if everything works before installing.

Or try searching for your computer here and see what rating it gets (that's with release 11.10): [http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any](http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any)

---

### Post by lolpenguin on 2011-11-16
If you can run Windows 7, you should be able to run Ubuntu (some hardware drivers may have to be installed). As always, burn a LiveCD and test it from there so you don't format a partition and replace your current OS with a non-working one.
BUT!!!!!!!!!!
With Wubi, you do not have to worry. Wubi simply creates a virtual hard driver with all of Ubuntu in it, and will not damage your Windows installation. If, however, Ubuntu does not work, uninstall "Ubuntu" from Programs and Features in the Windows 7 control panel.
To find out more about Wubi refer to _[Here]("http://ubuntuforums.org/showthread.php?t=1639198")_

---

### Post by Mark Phelps on 2011-11-16
A problem that more and more folks are running into, especially with the newest PCs, is the ones that support switcable graphics, that is, two graphics chips.  IF yours is one of those, the fact that it runs Win7 will have no bearing at all, because you'll have major problems getting video to work properly in Ubuntu.

As already said, best approach is to burn a DVD (Ubuntu is too big to fit on CDs now), boot from that, and see how well it works.

---

### Post by bcbc on 2011-11-16
> **Mark Phelps said:**
> A problem that more and more folks are running into, especially with the newest PCs, is the ones that support switcable graphics, that is, two graphics chips.  IF yours is one of those, the fact that it runs Win7 will have no bearing at all, because you'll have major problems getting video to work properly in Ubuntu.

As already said, best approach is to burn a DVD (Ubuntu is too big to fit on CDs now), boot from that, and see how well it works.
With dual video cards the important thing is not to install the driver for the on-demand gpu.

Regarding the ISO size, it's been reported that the ISO will be increased to 750MB for release 12.04, but the 11.10 ISO should still fit fine on a CD.

---

### Post by koymackoy on 2011-11-17
Thank you everyone!

Hi bcbc!

Regarding the link that you provide, [http://friendly.ubuntu.com/?desktops...popularity=any]("http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any") , under the core component section everything has a green check except for two items. First item is the ethernet card, for me this means that my laptop will **not run **Ubuntu smoothly when I connect to the internet using a wired network such as DSL/LAN, but will **work perfectly** fine if connected to a wireless network such as wi-fi. Does my understanding of the first item somehow correct or did I get it all wrong? 

The second item which I really don't have an idea is the **suspend/resume**. What does this means?

Once again thank you very much for all your help. I'm really excited towards Ubuntu and would like to understand/master how it operates. :p

---

### Post by bcbc on 2011-11-17
> **koymackoy said:**
> Thank you everyone!

Hi bcbc!

Regarding the link that you provide, [http://friendly.ubuntu.com/?desktops...popularity=any]("http://friendly.ubuntu.com/?desktops=on&laptops=on&stars=1&release=4&popularity=any") , under the core component section everything has a green check except for two items. First item is the ethernet card, for me this means that my laptop will **not run **Ubuntu smoothly when I connect to the internet using a wired network such as DSL/LAN, but will **work perfectly** fine if connected to a wireless network such as wi-fi. Does my understanding of the first item somehow correct or did I get it all wrong? 

The second item which I really don't have an idea is the **suspend/resume**. What does this means?

Once again thank you very much for all your help. I'm really excited towards Ubuntu and would like to understand/master how it operates. :p
You didn't actually say what computer you have... so I can't really comment on the Ubuntu friendly results. I think ubuntu friendly is useful, but it's pretty new so don't consider it the final answer - when I ran the test on my laptop (which only has a 1-star rating) I wasn't able to do all the tests and so it doesn't always reflect accurate information.  

But my laptop isn't totally compatible so I think the 1-star rating is pretty fair on the whole.

Having said that - not being able to Suspend/Resume would be a problem for me. I use it all the time (closing the lid, computer sleeps, opening wakes it up). 

So, do some follow up searches on your model with those search terms and see if it's really a problem or someone has got it working or post them here... i.e. computer brand/model/graphics card/wireless etc (or link to the actual ubuntu-friendly report)

---

### Post by koymackoy on 2011-11-18
Hi bcbc!

Thank you very much for that info/recommendation.;)

---

