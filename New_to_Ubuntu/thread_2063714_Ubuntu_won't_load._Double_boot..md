---
title: "Ubuntu won't load. Double boot."
date: 2012-09-27
forum: New to Ubuntu
---

### Post by Fails101 on 2012-09-27
I double booted my computer by (Loaded Windows 7 and then Ubuntu) and got everything set up and working, and I used EasyBCD to get to the screen where I can select which to load.

It was all set up and worked, and I've booted Ubuntu multiple times, so I know it worked.

Recently, however, I tried to boot it up again and after selecting Ubuntu it says:

Try (hd0, 0): NTFS5: No ang1
Try (hd0, 1): NTFS5: No ang1
Try (hd0, 2): Extended:
Try (hd0, 3): invalid or null
Try (hd0, 4): EXT2: No ang1
Try (hd0, 5): Extended:
Try (hd0, 5): EXT2: No ang1
Try (hd0, 6): Extended:
Try (hd0, 6): EXT2:

and it won't boot.

Does anyone know why? :(
Thanks for any help.

---

### Post by daslinkard on 2012-09-27
I found this from another forum

> Use the Live CD(DVD) to reinstall Grub2. In terminal type "sudo  grub-install /dev/sda".(without quotes). then enter password when  prompted. that will get you back where you started.

In your Ubuntu install "Grub Customizer". Grub customizer can edit the  Grub menu you see at boot. Simply uncheck the items you don't want to  appear. You can also rename the options, for example you can change  "Vista Loader" to Windows 7.

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

Instructions to set Windows as default can be found at the Ubuntu forums.

---

### Post by Fails101 on 2012-09-27
I don't use Grub2 (Is it like EasyBCD?), and if I can't load Ubuntu how  would I get to terminal? (Sorry if these are silly questions....)
Thanks for the help. :)

> **daslinkard said:**
> I found this from another forum

---

### Post by daslinkard on 2012-09-27
> **Fails101 said:**
> I don't use Grub2 (Is it like EasyBCD?), and if I can't load Ubuntu how  would I get to terminal? (Sorry if these are silly questions....)
Thanks for the help. :)

First off, do not apologize for what you deem as silly questions.  Anyone who is good at anything was a noob at some point in time.

Here is a detailed [link]("https://sites.google.com/site/easylinuxtipsproject/grub") about the GRUB and how you can fix it.  Check it out, see where you can get and know 2 things....

1.) Always post questions back here on the forum

2.) Google is King!  

Good luck!

---

### Post by Fails101 on 2012-09-27
> **daslinkard said:**
> First off, do not apologize for what you deem as silly questions.  Anyone who is good at anything was a noob at some point in time.

Here is a detailed [link]("https://sites.google.com/site/easylinuxtipsproject/grub") about the GRUB and how you can fix it.  Check it out, see where you can get and know 2 things....

1.) Always post questions back here on the forum

2.) Google is King!  

Good luck!

Thanks so much!!! :D You're a life saver. :) I need it for school....

And thanks, I will. :) I'm so glad this community is so nice. :)

---

### Post by daslinkard on 2012-09-27
> **Fails101 said:**
> Thanks so much!!!  You're a life saver.  I need it for school....

And thanks, I will.  I'm so glad this community is so nice. 

Only a life saver once we get this back up and running!;)  Let us know how you progress with this!

---

### Post by Fails101 on 2012-09-27
> **daslinkard said:**
> Only a life saver once we get this back up and running!;)  Let us know how you progress with this!

I will! I'm about to try; hopefully I'll be back saying I succeeded soon!

---

### Post by daslinkard on 2012-09-27
> **Fails101 said:**
> I will! I'm about to try; hopefully I'll be back saying I succeeded soon!

No worries, I'll be checking throughout the night to see your progress.  Good luck!

---

### Post by Fails101 on 2012-09-27
> **daslinkard said:**
> No worries, I'll be checking throughout the night to see your progress.  Good luck!

Thanks! :)

I followed the instructions on downloading Grub and restarting it, but then I get stuck. It says I should see Ubuntu (if not my windows as well) and instead I get a page with the heading "GNU GRUBB   version 1.99-21ubuntu3" and it says "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions", and then it has "grub> " like it's a terminal (only in bash). It doesn't have the menu where I could select ubuntu and load it....

I've been googling what I could have done wrong, but I'm not finding a solution. Do you know? :(

---

### Post by Fails101 on 2012-09-27
> **Fails101 said:**
> Thanks! :)

I followed the instructions on downloading Grub and restarting it, but then I get stuck. It says I should see Ubuntu (if not my windows as well) and instead I get a page with the heading "GNU GRUBB   version 1.99-21ubuntu3" and it says "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions", and then it has "grub> " like it's a terminal (only in bash). It doesn't have the menu where I could select ubuntu and load it....

I've been googling what I could have done wrong, but I'm not finding a solution. Do you know? :(


EDIT! I found the solution!! :D :D /gives everyone cookies

It was here:
[http://askubuntu.com/questions/140785/gnu-grub-version-1-99-21ubuntu3-does-not-work](http://askubuntu.com/questions/140785/gnu-grub-version-1-99-21ubuntu3-does-not-work)

Except because I was/am using a newer version of GRUB2 instead of 
sudo grub-install --root-directory=/home/ubuntu/temp /dev/sda
use
sudo grub-install --boot-directory=/home/ubuntu/temp /dev/sda
which I found out from
[http://ubuntuforums.org/showthread.php?t=1972331](http://ubuntuforums.org/showthread.php?t=1972331)

(I love google :D)

---

### Post by daslinkard on 2012-09-27
Has this solved the issue at hand for you?

---

### Post by Fails101 on 2012-09-27
> **daslinkard said:**
> Has this solved the issue at hand for you?

Yep! Thank you so much for your help!! :D

---

