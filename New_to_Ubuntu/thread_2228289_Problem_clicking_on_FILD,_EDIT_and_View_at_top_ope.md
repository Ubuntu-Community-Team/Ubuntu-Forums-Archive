---
title: "Problem clicking on FILD, EDIT and View at top open window?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by al_lafon on 2014-06-06
Hello i had problem clicking on FILE, EDIT and View or anything at top open window?
But not on all programs. I have to click over and over then it works off and on.
I tryed to find a fix but so far i can not find one anybody know whats going on here.
Posted small clip showing this problem>>> [http://youtu.be/pMx_fvpnbH4](http://youtu.be/pMx_fvpnbH4)

                                                       Thanks for any help Al Lafon

---

### Post by rahul4557 on 2014-06-07
I dont have a exact explaination on this one..
Perform an update
> sudo apt-get update
> sudo apt-get upgrade

after that try resetting the Unity and see if that works..
**To reset unity:**
install dconf-tools
> sudo apt-get install dconf-tools
reset compiz
> dconf reset -f /org/compiz/
Restart your Ubuntu..

Good Luck..

---

### Post by al_lafon on 2014-06-07
Well i did this did not seem to work But!! In system settings / appearance / changed from show in window bar 
to in menu bar and clicking problem has stoped . I can live with this! Wonder what little bug that is hope someone
finds a fix for it.

                                                                                                       Thanks A G Lafon

---

