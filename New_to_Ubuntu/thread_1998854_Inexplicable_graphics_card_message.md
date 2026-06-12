---
title: "Inexplicable graphics card message"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by Gela on 2012-06-07
While on your website, I was trying to get to Absolute Beginners Talk and at one stage received the following message which I am completely unable to understand or do anything about. It stated: "Ubuntu is running in low graphics mode.  Your screen card and input device settings could not be detected. You will need to configure them yourself. " As I am spending hours trying to understand the fundamental geography of Ubuntu I am at a loss as to whether this is an important message or whether it can safely be ignored. Can anyone help me please?

---

### Post by mastablasta on 2012-06-07
you should probably  install graphics card drivers. but before you do that what graphics card do you have?

---

### Post by Gela on 2012-06-08
> **mastablasta said:**
> you should probably  install graphics card drivers. but before you do that what graphics card do you have?

I have looked in System Settings\System Info\Graphics and receive "Driver unknown" and "Experience Standard".  In Hardware Drivers I receive "No proprietary drivers in  use on this system".  How do I install a graphics card driver that *would* be  recognized please? and when they ask me asked where to put it, where do I put it?
 I have a netbook (Aspire) with 991.5 MiB memory and an Intel Atom CPNU 550@1.20GHz x 4 with a 32 type OS and a 30.7GB disc.  I am very grateful for your help.

---

### Post by Gela on 2012-06-08
> **mastablasta said:**
> you should probably  install graphics card drivers. but before you do that what graphics card do you have?

I have looked in System Settings\System Info\Graphics and receive "Driver unknown" and "Experience Standard".  In Hardware Drivers I receive "No proprietary drivers in  use on this system".  How do I install a graphics card driver that *would* be  recognized please? and when they ask me where to put it, where do I put it?
 I have a netbook (Aspire) with 991.5 MiB memory and an Intel Atom CPNU 550@1.20GHz x 4 with a 32 type OS and a 30.7GB disc.  I am very grateful for your help.

---

### Post by Mark Phelps on 2012-06-08
Unfortunately, System Info is unreliable.  To find out what video card you have, open a terminal, enter "lspci", and look for the line containing "VGA".  Post that info back here.

The Additional Drivers option only applies to AMD and NVidia video cards.  If you don't have one of those, you won't see any drivers offered.

If you are already seeing a desktop, you already have video drivers installed.  The results of the command above will let us know if there are any other drivers.

---

### Post by snowpine on 2012-06-08
Your netbook has Intel graphics, which are supported out-of-the-box in Ubuntu (no additional drivers required). 

The message indicates that you have low-end integrated graphics (rather than a dedicated graphics card like on a gaming desktop) therefore some of Ubuntu's sparkly "eye candy" features will be disabled.

If you are otherwise satisfied with Ubuntu's performance then you can safely ignore the message.

Which version of Ubuntu did you install, by the way?

---

### Post by Gela on 2012-06-09
> **Mark Phelps said:**
> Unfortunately, System Info is unreliable.  To find out what video card you have, open a terminal, enter "lspci", and look for the line containing "VGA".  Post that info back here.

The Additional Drivers option only applies to AMD and NVidia video cards.  If you don't have one of those, you won't see any drivers offered.

If you are already seeing a desktop, you already have video drivers installed.  The results of the command above will let us know if there are any other drivers.

I am_*reall*y_ an "Absolute Beginner" - How do you "open a terminal" please.

---

### Post by Gela on 2012-06-09
> **snowpine said:**
> Your netbook has Intel graphics, which are supported out-of-the-box in Ubuntu (no additional drivers required). 

The message indicates that you have low-end integrated graphics (rather than a dedicated graphics card like on a gaming desktop) therefore some of Ubuntu's sparkly "eye candy" features will be disabled.

If you are otherwise satisfied with Ubuntu's performance then you can safely ignore the message.

Which version of Ubuntu did you install, by the way?


I upgraded to version 11.10 when a message turned up telling me to upgrade. It took hours!

---

### Post by Mark Phelps on 2012-06-09
> **Gela said:**
> I am_*reall*y_ an "Absolute Beginner" - How do you "open a terminal" please.

You click on the Dash icon (on the top left) and when it opens, you enter "term" -- and select the Terminal app.

---

### Post by Gela on 2012-06-11
> **Mark Phelps said:**
> Unfortunately, System Info is unreliable.  To find out what video card you have, open a terminal, enter "lspci", and look for the line containing "VGA".  Post that info back here.

The Additional Drivers option only applies to AMD and NVidia video cards.  If you don't have one of those, you won't see any drivers offered.

If you are already seeing a desktop, you already have video drivers installed.  The results of the command above will let us know if there are any other drivers.

Thank you so much for all the help you are giving me. 
I followed your instructions and there was no line with VGA in it.
There was a long list of various "Controllers"
I have copied to clipboard and pasted below if this is of any use - but it is in a different format towhat I am writing so I am not sure you can read it. Sorry to be such a nuisance

---

### Post by mastablasta on 2012-06-11
when making an answer you can wrap the text in code tags (use the # icon available in "Go Advanced" not quick reply). then it is all displayed like on your terminal screen. so you just highlight all text, right click and copy it and then paste it to the forums.
 
though it's one of the intel HD chips (not really a card). they are crappy on Atoms, but not that crappy. they should be recognised and configured by ubuntu since Intel offers drivers for linux. it might be that a configuration is wrong or that system missconfigured it as it tried to do it automaticly. having exact chip model (availbale via lspci command or lswh command) would help people to check if anyone else had an issue with it and if they found a solution.

---

### Post by Gela on 2012-06-13
> **mastablasta said:**
> when making an answer you can wrap the text in code tags (use the # icon available in "Go Advanced" not quick reply). then it is all displayed like on your terminal screen. so you just highlight all text, right click and copy it and then paste it to the forums.

Thanks again for your help. I have tried the advice regarding quoting in replies. I could only get the whole answer and not  just the  highlighted part to appear, so deleted the unwanted bit and hope it has come out correctly. I am learning all the time but at 84 last birthday I am probably a little slow on the uptake, for which I apologize. . I still  could not copy the information in the *_lspc _*instruction - perhaps it is not possible?  I can see now that it did not appear in my reply to you although it did appear on the screen I sent off,   but in a completely different font.  I didn't quite understand your information about the graphics drivers - but I gather there is little I can do now, so thank you once again

---

