---
title: "[SOLVED] Gah help me get rid or tuxpaint"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-20
i got tuxpaint. ever since i got it my comp has been super laggy. I treid to uninstall it the regular way but that only uninstalls the launcher! I searced for all files containing tuxpaint and delete them, but the owner was root so i couldnt

Then when i gksudo nautilus and then searched for tuxpaint---MY COMPUTER FREEZES

HOW CAN I GET THIS STUPID THING OFF MY COMPUTER???

---

### Post by HellNoire on 2008-09-20
TuxPaint is normally not installed under Ubuntu, but assuming it installed anyway.

Go to System-> Adminstration -> Synaptic Package Manager, put in your password, then once it's up, click down to Tuxpaint and remove it like that. I am assuming you're the 'head' so to say of your computer, and not a limited user?

---

### Post by hyperhopper on 2008-09-20
i am the head, and i installed it manually using about 6 .deb files


yes it too that many to get it to work 

*WAH-WAH*

---

### Post by HellNoire on 2008-09-20
I've had to use at max three to install something. Did you try what I suggested? You might need to look past the first Tuxpaint to find more that would be hiding because of how many debs it's using.

---

### Post by hyperhopper on 2008-09-20
i did and all it removed was the tuxpaint in applications>education

---

### Post by RequinB4 on 2008-09-20
This may or may not help, but
```
dpkg --get-selections | grep tuxpaint
```

will output all of the installed packages with the name tuxpaint inside it somewhere.  All you should have to do is to sudo apt-get remove all of those...

---

### Post by hyperhopper on 2008-09-20
manually?

is there a way i can apt-get romove all of thos ein one command?

---

### Post by RequinB4 on 2008-09-20
> **hyperhopper said:**
> manually?

is there a way i can apt-get romove all of thos ein one command?

hmm... I would ALSO like to know how to find words in a single line in stdout but I have no idea.  The problem is the "install" at the end...

Some tips to speed it up, combine at your will:

When typing sudo apt-get remove, you can press <TAB> to autocomplete a package name.  For instance sudo apt-get remove tuxp<TAB> will autocomplete tuxpaint.

Second, you can put multiple package names on the same command eg
```
sudo apt-get remove tuxpaint tuxpaint2 tuxpaintevil
```

Finally you can make that output go to a file where you can use the control+f find feature of gedit or whatever to copy and paste (for this short of a list it'll probably be more work to manually delete the extra stuff and read the file line by line via shell script):
```
dpkg --get-selections | grep tuxpaint > listofpackagestoremove
gedit listofpackagestoremove &
```

Edit:  dpkg does have a feature for doing all of this automatically but the function is exact match only eg you'd be back to where you started in synaptic.  Guess this is why debs aren't that great ;P

---

### Post by hyperhopper on 2008-09-20
one last thing, now everything says deinstall, but doesnt that mean they are somewhere on my system?

is there any way i can COMPLETELY wipe these off?

btw thanks for helping me get 75 mb back :mrgreen:

---

### Post by RequinB4 on 2008-09-20
> **hyperhopper said:**
> one last thing, now everything says deinstall, but doesnt that mean they are somewhere on my system?

is there any way i can COMPLETELY wipe these off?

btw thanks for helping me get 75 mb back :mrgreen:

yw.  if your problem is fixed, please mark this thread as solved :)

instead of using sudo apt-get remove, use sudo apt-get purge

---

### Post by Sef on 2008-09-20
>  instead of using sudo apt-get remove, use sudo apt-get purge

purge will get rid of the configuration files as well.

---

### Post by hyperhopper on 2008-09-20
thank you!

I am completely finished!

---

