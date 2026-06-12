---
title: "aMSN"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hmarkg on 2008-05-08
Hi all, I"m new to ubuntu and starting to like it... I have problems installing skins and plugin in aMSN i didnt follow the instruction to installing but I still install it... HELP please...

---

### Post by Achtung on 2008-05-08
Well, is it installed, and does it work?

To install plugins or skins on a working install of aMsn, just download the plugin/skin, unpack it and put the folder containing all the files in either /home/<user>/.amsn/plugins or /home/<user>/.amsn/skins ... You can then select them in the correct dialog in aMsn's "Account" menu.

---

### Post by skymera on 2008-05-08
Just a quick note - When i changed the theme i experienced major slowdown and high CPU usage.

---

### Post by Joeb454 on 2008-05-08
> **skymera said:**
> Just a quick note - When i changed the theme i experienced major slowdown and high CPU usage.

It could have been the theme that caused this. However I don't use aMSN much, and the default theme is ok for me, so I can't be sure.

---

### Post by hmarkg on 2008-05-08
> **hmarkg said:**
> Hi all, I"m new to ubuntu and starting to like it... I have problems installing skins and plugin in aMSN i didnt follow the instruction to installing but I still install it... HELP please...

Sorry sorry... i meant i DID follow the instruction... Just like what you state there... i follow the same way but error message telling me that Error moving file: Permission denied
How to solve..??

---

### Post by Joeb454 on 2008-05-08
You're getting permission denied in your /home/<username> directory? (aka ~/)

---

### Post by skymera on 2008-05-08
When i followed a guide i had to move files to somewhere like /usr/share/amsn/blahblah

If so open the terminal and

[cd /location/of/theme
sudo mv <theme> /location/of/amsn/theme/folder[/code]

If you understand what i mean

---

### Post by hmarkg on 2008-05-08
> **Joeb454 said:**
> You're getting permission denied in your /home/<username> directory? (aka ~/)

Erm not sure totally new but the directory of my file is /usr/shared/amsn/skins

---

### Post by hmarkg on 2008-05-08
> **skymera said:**
> When i followed a guide i had to move files to somewhere like /usr/share/amsn/blahblah

If so open the terminal and

[cd /location/of/theme
sudo mv <theme> /location/of/amsn/theme/folder[/code]

If you understand what i mean

Sorry but i do not understand I am new

---

### Post by Joeb454 on 2008-05-08
The directory you are trying to write to requires administrative privileges, this is why you are getting the error :)

Try moving the files to /home/<yourUsername>/.amsn/skins/

If you want to do this from the Graphical Interface, you need to open "Home" and then press Ctrl + H - as .amsn is a hidden folder :)

If you want to do it in a terminal, that path would translate to ```
~/.amsn/skins/
```

---

### Post by hmarkg on 2008-05-08
> **Joeb454 said:**
> The directory you are trying to write to requires administrative privileges, this is why you are getting the error :)

Try moving the files to /home/<yourUsername>/.amsn/skins/

If you want to do this from the Graphical Interface, you need to open "Home" and then press Ctrl + H - as .amsn is a hidden folder :)

If you want to do it in a terminal, that path would translate to ```
~/.amsn/skins/
```

Wow problem solve.. So simple yet i duno... I Am still learning day by day

---

### Post by Joeb454 on 2008-05-08
I'd recommend learning some simple terminal commands :) I thought I probably should one day. Changed my whole opinion of the terminal :)

And just so you know ```
~/
``` is the same as ```
/home/joe/
``` Obviously it would be different for you - but my username is joe :)

---

### Post by hmarkg on 2008-05-08
> **Joeb454 said:**
> I'd recommend learning some simple terminal commands :) I thought I probably should one day. Changed my whole opinion of the terminal :)

And just so you know ```
~/
``` is the same as ```
/home/joe/
``` Obviously it would be different for you - but my username is joe :)

OK maybe i'll get a book or something

---

### Post by Joeb454 on 2008-05-08
I was considering getting a book when I first started too :) I think this is what LaRoza did also (though I may be mistaken).

I never did get a book, I just broke it and tried to fix it :lolflag:

---

