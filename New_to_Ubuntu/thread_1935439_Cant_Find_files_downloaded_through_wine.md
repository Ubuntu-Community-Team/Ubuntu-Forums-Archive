---
title: "Cant Find files downloaded through wine"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by Nu2ubun on 2012-03-04
i downloaded final fantasy VII from a website through wine and i can't seem to find the files. does anyone know where the program defaults to?

---

### Post by whatthefunk on 2012-03-04
So, you opened a web browser in wine to download the program?  Hmmm....Im guessing you checked the browsers default download location.  Wine puts a lot of stuff in ~/.wine so might want to check there.

---

### Post by grahammechanical on 2012-03-04
What do you mean "through wine."

Did you download this program using a web browser running under wine? Or did you download this program using a web browser in Ubuntu as normal and then install the program using wine and now wish to run the program?

You do not say which version of Ubuntu you are using. This makes a difference to directions we might give. I assume that you are using Ubuntu 11.10.

Open the dash and search for something called Browse C: Drive. That is a wine utility that looks like Windows Explorer. You can use it to look for files in the C: drive folder that wine has created in the wine folder.

The directory structure of the wine C: Drive folder follows the pattern of the Microsoft Windows folder structure.

Regards.

---

### Post by Mark Phelps on 2012-03-04
Anytime you're going to run something through Wine, you should first check the WineHQ website to see if it's worth the trouble.

Your game is shown on the pagelink below, and without the patches mentioned, it rates a Bronze -- the LOWEST rating an app/game can get if it installs at all!  With a game, this makes it all but useless.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=126]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=126")

---

