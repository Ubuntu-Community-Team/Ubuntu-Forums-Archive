---
title: "[SOLVED] Going crazy trying to print in A4"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-09-03
I live in Europe & only use A4 paper.

I would have thought that might have been common...

I would have expected to be able to choose that as a default printing option somewhere in 1 click, or maybe 2 clicks as I have 2 printers.

So far, I have not found this magic click...
Everything in Ubuntu, or at least in OOo seems to default to Letter.

In System > Admin > Printing > Printer options, I set both my printers  to A4.
That seems to stick OK.
But OOo still defaults to Letter.

In OpenOffice.org-Writer I followed this tutorial to set my default Template to one with A4 printer settings (for one printer).
> 
[Tutorial] Creating a new default template

Postby Lazy-legs on Wed Dec 26, 2007 10:36 pm
If you want every new document to have user-defined settings, you must create a new template and set it as default.

   1. Create a new document, add or modify styles, and change other settings as you desire.
   2. From the File menu, choose Templates -> Save.
   3. Give the template a name.
   4. Select a category in the Categories list (for example, My Templates).
   5. Click OK to save the template.
   6. Choose File -> Templates -> Organize.
   7. In the Categories list, double-click on the My Templates folder.
   8. Right-click on the template you want to use and choose Set as Default Template from the menu.
   9. Click the Close button.

and this managed to bring up A4 every time I call up that printer, but when I try to set the second printer to A4 then the first one drops back to Letter & vice-versa... :confused:

I saw somewhere that one way to "fool" OOo into doing what you want (why is OOo so obscure???) was to pretend you live somewhere else!
> 
Re: [Solved] How to set default paper size to A4?

Postby Caracalla on Sun Jun 22, 2008 10:30 pm
hah! i found the setting that does this without changing the template (and does a bunch of other things besides). It is the lacele setting. To be found under tools->options->Language Settings->Languages. All you need to do is set the locale setting to a country weher A4 is the standard (which is most of the world) and you're set. Just be careful to keep an eye on the other things it changes.

So I "moved" to UK like that, but it did not seem to change my printer settings.

Recap: In OOo with 2 printers, whenever I set one printer to A4, the other printer shifts to Letter...

Any suggestions?

---

### Post by LowSky on 2008-09-03
this link should help
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=6948](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=6948)

if not just set the bounderies to fit A4 paper.

I really don't know why North America uses a different size paper than the RoW

---

### Post by 2CV67 on 2008-09-03
Thanks, but in fact that was the link I found, used & quoted in my first post. ;)

I still can't understand why, as soon as I open Printer settings in OOo & set one printer to A4, the other printer resets to Letter.
I can carry on doing that indefinitely!

Anybody else have similar problems?

Or solutions?

Thanks!

---

### Post by 2CV67 on 2008-09-03
Found a good clue in this old thread (in fact most reported problems have been from Americans complaining that they wanted Letter & got A4...)
[http://ubuntuforums.org/showthread.php?t=399754](http://ubuntuforums.org/showthread.php?t=399754)

I went to etc/papersize  & saw it said "letter" so I changed it to "a4" and now everything SEEMS to be OK as I want it - both printers defaulted to A4 size.
Have not checked all possible combinations yet, but it looks good...

Why on earth did I need to go through all that?

Should not System > Admin > Printing overwrite any preset files???

---

### Post by philinux on 2008-09-03
Thats weird I just checked my /etc/papersource and it says a4.

I set it in printing as normal.

---

### Post by 2CV67 on 2008-09-03
You mean you can change the content of "etc/papersize" by actions in System > Admin > Printing?

I don't think I can.

---

