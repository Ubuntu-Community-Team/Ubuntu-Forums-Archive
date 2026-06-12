---
title: "Sound card not supported?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by elcomputo on 2008-09-07
I had been having problems getting my sound to work. Although all the tests (but one) gave me a tone, I got no sound for VOIP or video downloads. I ran a scan for installed equipment, and for audio card, it indicated I had an Intel product. But I knew I have a Sigmatel 92xx card.

It looks as though the problem is ubuntu does not support this card. Or that Sigmatel doesn't support ubuntu. I have a question in to Sigmatel to find out whether they do. I suspect they don't. Which leads me to my question:

It's prohibitively expensive for me to drop my PC out of a five-story window and buy a Mac, something I should have done 10 years ago. It would be cheaper to buy another sound card to replace the Sigmatel.

But what kind of card should I get if I want to run sound in Ubuntu?

---

### Post by Xiong Chiamiov on 2008-09-08
Hmm, I don't see your card listed in [the ALSA matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main").

I haven't had *too* much in the way of problems with [my creative card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102002").  Mostly it's just been me, forgetting to modprobe the right thing into the kernel or somesuch.

---

### Post by talsemgeest on 2008-09-08
By all means your sound should be working. Don't go buying anything until you have made sure it is a hardware problem.

It sounds to me like it is just a configuration problem. Try changing some of the sound-related settings around in the menu, but since you get the test tones, I think it is more of a problem with the programs you are using. Go into the settings of the program and change some of the sound settings in there, which should do the trick.

But even if you do end up having to get a new card, you can probably get one for around $20, and if you don't know how to install a card, you can always get a usb sound device.

---

