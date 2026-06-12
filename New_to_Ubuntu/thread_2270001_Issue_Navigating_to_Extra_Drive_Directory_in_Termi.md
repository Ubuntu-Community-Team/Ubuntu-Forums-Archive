---
title: "Issue Navigating to Extra Drive Directory in Terminal"
date: 2015-03-19
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-03-19
Hello, while I'm fairly capable in admin'ing my Linux PC's, I am not a regular user of the Terminal.   I have done the basics on it though.

So, it's been a bit frustrating the last couple days when I am not able to successfully navigate to a specific location on my Laptop.

Input is basically like this:   *cd /media/greg1* (ok to this point) then the next location is a second or extra hdd on the laptop.   The files manager (nautilus) shows the drive labeled as "Extra Drive 1".  

I am getting "no such file or directory" errors at that point.    Could the spaces for the drive label be an issue?   The whole input string that I've tried (with several variations) is similar to:

"*cd /media/greg1/Extra Drive 1/Tech/Treeline*" with the TreeLine folder containing an install script that has to be opened in a Terminal  '*python install.py*'

Is there an alternate identifier to add to the command line input?  I think I could install another file manager (like pcmanfm) and then "open terminal from here" . . . but I would prefer to learn how to navigate in the terminal the standard way.

Thanks for any tips.

GG

---

### Post by Vladlenin5000 on 2015-03-19
Indeed, spaces are the problem. The good news is you should be able to access it anyway and auto-completion is your friend:
Assuming you're already at /media/greg1 then just type cd followed by the first 2-3 characters ("Ext" in your case and yes, it is case sensitive) then TAB. Voilá! It shows you how you should have typed those spaces but you don't have to, thanks to the auto-completion.

---

### Post by Geoffrey_Arndt on 2015-03-19
Thanks Vladin!  That did it . . . now just need to install a later version of python & am done.

GG

---

