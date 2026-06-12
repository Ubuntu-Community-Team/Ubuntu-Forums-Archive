---
title: "Just started using Ubuntu :)"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Huw_Dawson on 2008-06-04
I'm loving it already. It's noticeably faster and more stable than XP, and thanks to it being able to be installed inside Windows, I didn't have any messy trouble with having to defrag my computer several times! Wine just seals the deal for me, thanks to it being able to run mIRC and Ventrilo, both of which I find vital. Five gold stars from me. :KS:KS:KS:KS:KS

 Anyway, I've got a couple of issues at the moment (one big, one little):

 a) Is there any way to stop the computer beeping at me when I press backspace when it isn't tied to a command like deleting text?

 b) When I boot into Ubuntu without touching anything, it gets to the loading screen, but then it says "dropping down to shell!" and puts me into a text application called BusyBox (that looks like a DOS-application, even though I'm aware the coding is utterly different). I've had to press ESC on that countdown and go down to the third option (That has a 16 at the end - I'm not a coder but I'm guessing it just means a slightly earlier version) and now it's working fine - it just refuses to boot properly without going into the options.

 The second one is the more major, obviously. Could somebody help me with some solutions? :p

 - Huw

---

### Post by mevets on 2008-06-04
To solve problem a I believe this will work. System > Preferences > Sound > System Beep > Uncheck Enable System Beep

---

### Post by tompickles on 2008-06-04
problem number two sounds like youve got recovery mode as the default boot......im not sure how you would go about changing the boot order as you installed using Wubi (installed it into windows). Basically, the other option is normal boot, which is correct. the 16 is just the kernel release number - nothing to worry about really.

google on how to change order of your windows boot loader........ 

hope that kinda maybe possibly helps?!

---

### Post by tompickles on 2008-06-04
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)   might help you there

---

### Post by bryncoles on 2008-06-04
assuming tompickles is right, the easiest way to change the default OS for you would be with start up manager, available in the repos. 

click system->administration->synaptic package manager. click settings->repositories and make sure universe and multiverse are selected. close, reload, ok. search for startup manager, mark for installation, apply. 

then you can easily set your default boot mode!

---

### Post by tompickles on 2008-06-04
NB  he mentions installing using Wubi - and therefore [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) as the picture shows the boot manager is the windows one - so, you would need to edit in from windows => i may be completely wrong, but i beleive this is what you have to do, and i beleive that boot.ini is the file that needs changing. the link in my second post walks you through (eventually) how to set hte default OS.

Huq_Dawson - can you try when you boot up your pc, when the menu happens, press down on the arrow keys - but before pressing enter just remember what your options are.... just so we can have an idea of what is being defaulted etc....

thanks :) and i hope someone will correct any errors...

---

### Post by SlappyPappy on 2008-06-04
Greetings Huw. 

Wine is good for some things Windows but not all. Check out VirtualBox if you get a chance. I have some Windows programs that I just can't do without. I'm running Windows2000 in VB and it works great. In fact I'd say it's more stable now in VB than outside of it!

Good luck friend and enjoy.   :)

---

### Post by tompickles on 2008-06-04
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623)

sorry - beating around the bush a bit - was jsut guessing - try this perhaps first, its a lot easier and sounds like your initial problem...

---

