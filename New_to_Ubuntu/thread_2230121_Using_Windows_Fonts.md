---
title: "Using Windows Fonts"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by david228 on 2014-06-17
The curse of the newbie! (Knowing so little).

I was looking through the list of supplied fonts with LibreOffice and while I don't like to be negative, they didn't seem to be overly exciting or numerous.

Can Windows Fonts be easily imported?

I did see a posting ([http://ubuntuforums.org/showthread.php?t=208396&highlight=Windows+Fonts](http://ubuntuforums.org/showthread.php?t=208396&highlight=Windows+Fonts)) but I didn't understand it. (Yet).


Thank you.

---

### Post by 3rdalbum on 2014-06-17
> **david228 said:**
> The curse of the newbie! (Knowing so little).

I was looking through the list of supplied fonts with LibreOffice and while I don't like to be negative, they didn't seem to be overly exciting or numerous.

Can Windows Fonts be easily imported?

I did see a posting ([http://ubuntuforums.org/showthread.php?t=208396&highlight=Windows+Fonts](http://ubuntuforums.org/showthread.php?t=208396&highlight=Windows+Fonts)) but I didn't understand it. (Yet).


Thank you.

Please be very clear on this: **[SIZE=4]DO NOT[/SIZE]** follow ANY tutorial that is more than a year old. Instructions written for Ubuntu in 2006 will **[SIZE=4]NOT[/SIZE]** be relevant. If you try and follow them, you're likely to break your system. Eight years is a Linux eternity, your instructions from 2006 were valid back in the time of the dinosaurs!

To answer your question, if you have any fonts you want to install, simply double-click them and click the Install Font button.

Sorry for the "shouting", I just wanted to make sure you read this. The last thing I want is for you to end off with an unusable Ubuntu, it would make me feel bad.

---

### Post by david228 on 2014-06-17
Thanks **3rdalbum**. Shouting is happily accepted if it stops a stuff-up from happening. Being new does leave one a bit vulnerable at times. I have just downloaded The Linux Command Line (William E Shotts), & Ubuntu An Absolute Beginners Guide to hopefully get me going in the right direction - however, off the point.

So what you are saying is that I copy the specific fonts from Win and place them on the Ubuntu computer, then when I double click the specific filename it will be recognised as a font and offer me the install option? Is there a specific directory I should copy them to?

---

### Post by Bucky Ball on 2014-06-17
You want ttf-mscorefonts-installer. You should be able to find it in the Software Centre or in a terminal, try 'sudo apt-get install ttf-mscorefonts-installer'.

---

### Post by Drakkenn on 2014-06-17
A really simple way to install all the microsoft fonts: (From the cli) sudo apt-get install wine. sudo apt-get install winetricks. Once that is done, launch the gui front end from the menu, go to install, find the fonts and install whatever ones you want. Hope that helps.

---

### Post by 3rdalbum on 2014-06-17
> **david228 said:**
> Thanks **3rdalbum**. Shouting is happily accepted if it stops a stuff-up from happening. Being new does leave one a bit vulnerable at times. I have just downloaded The Linux Command Line (William E Shotts), & Ubuntu An Absolute Beginners Guide to hopefully get me going in the right direction - however, off the point.

So what you are saying is that I copy the specific fonts from Win and place them on the Ubuntu computer, then when I double click the specific filename it will be recognised as a font and offer me the install option? Is there a specific directory I should copy them to?

Correct. There is no specific place you need to put them. The 'install' button will copy the font to where it needs to go.

---

### Post by Bucky Ball on 2014-06-17
> **Drakkenn said:**
> A really simple way to install all the microsoft fonts: (From the cli) sudo apt-get install wine. sudo apt-get install winetricks. Once that is done, launch the gui front end from the menu, go to install, find the fonts and install whatever ones you want. Hope that helps.

This is to be absolutely avoided. It is NOT a simple way at all and installs a whole lot of bloat you don't need to install something which can be installed VERY easily by installing the mscorefonts installer. 

Wine: Don't go there, at least not for this. It will install a heap of stuff and it is very difficult (if not impossible) to get rid of once installed.

---

