---
title: "How to get (install) N'KO, Manden language ?"
date: 2020-07-20
forum: New to Ubuntu
---

### Post by ourembaya on 2020-07-20
Hello,

I would to know how to install N'KO (nkoo, Manden language) on Ubuntu 20.04 ?


Best regards,
Moustapha Kourouma

---

### Post by ourembaya on 2020-07-21
I received the following message inbox, maybe it can help others :

                 Just Googling "N'ko Ubuntu" seems to suggest you need to  to install the "onak", "fonts-evertype-conakry" and  "libkf5pimcommonakodi5" packages. The last item probably means that KDE  (instead of gnome) has better support for it.
Hope this helps.

It is somewhat unfair for some of us to do your Googling for you though...  ( My comment :  The purpose isn't to make others googling, it's to help others by each others in the native forum)

            




The bellow link have the 3 elements :
[https://packages.ubuntu.com/onak](https://packages.ubuntu.com/onak)

---

### Post by Holger_Gehrke on 2020-07-21
Two of those packages are not in any shape or form related to language support. 'onak' is a keyserver for openPGP and 'libkf5pimcommonakonadi5' is part of the infrastructure for personal information management in KDE. The font package might be useful, at least the name 'conakry' came up in the searches I did. 

But support for a language is more than just having a font that displays the right characters. You also need a way to enter those characters. The page at [http://www.evertype.com/fonts/nko/](http://www.evertype.com/fonts/nko/) has a keyboard layout in kfml-format and instructions for Ubuntu 8.4 on how to install this. Of course those instructions are next to useless today. But the keyboard-layout you can download from there should work with kfml. kfml is available through a PPA and installation is described on [https://keyman.com/linux/](https://keyman.com/linux/) .

The third component of support for a language are translated message-files for programs, and that's were I completely struck out. There don't seem to be any.

Holger

---

### Post by ourembaya on 2020-07-26
Thank you,

With the instructions above (install the 3 packages) and KDE Connect on the Ubuntu ( Fedora also) and on my smartphone, i'm able to write N'KO in Ubuntu 20.04( Fedora 32 also). But, you need to install N'KO keyboard on your smartphone.

I will check your advise.

Best regards,
Moustapha Kourouma

---

