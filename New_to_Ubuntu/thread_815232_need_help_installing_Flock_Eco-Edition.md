---
title: "need help installing Flock Eco-Edition"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by T2manner on 2008-06-01
the bad thing is that it doesn't come in a deb file.
it comes in tar.gz and i'm not good with installing those
i found a guide to installing Flock [tar.gz] but it doesn't work with this Eco Edition
plz help

---

### Post by Daveth on 2008-06-01
you probably should post the errors you get when you try to install it- it ought to be fairly straightforward but may be running into a number of problems, so we need to work out which one(s).

---

### Post by T2manner on 2008-06-01
i don't know how to install it..

---

### Post by y-lee on 2008-06-01
It is usually something like: [How to Install Source Files in Ubuntu]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html")

I haven't looked at the package you are trying to install and sometimes dependencies are a bit tough to track down.

---

### Post by y-lee on 2008-06-01
Actually I was wrong I think as this is not a source file package.

I just downloaded the file flock_afcC72FB3ACF09E-1.2.1.en-US.linux-i686.tar.gz which is I believe the file you are trying to install and no installation is needed. you just have to extract the folder flock somewhere and run the file flock, the bins are included. And btw it is pretty cool I just run it :)

---

### Post by T2manner on 2008-06-01
okay cool, but how do i make a thing for it in my main menu?
i tried to install it, but nothing would work
every command i put in to install i got this :```
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by Joeb454 on 2008-06-02
Where did you save and extract the file?

---

### Post by y-lee on 2008-06-02
> **T2manner said:**
> okay cool, but how do i make a thing for it in my main menu?
i tried to install it, but nothing would work
every command i put in to install i got this :```
make: *** No targets specified and no makefile found.  Stop.

```

No installation is needed for the file I downloaded. All you have to do is extract either the folder flock or the hidden folder that contains the folder flock somewhere on your hard drive. You can do this by double clicking the tar.gz file and clicking extract. After you have  did that you find the file called simply flock and click it to run flock. When you click it you will get a message "Do you want to run "flock", or display its contents?" choose run. 

To add a menu item Right click your menu and choose edit menu (or run Alacarte Menu Editor under  Accesseries) Click Internet in the Alacarte window and then in Alacartes menu choose file and then new entry. A Entry Editor window should pop up now fill in the entries. Name of course Flock, Comments whatever you want, For command either type in the path to the file flock in your flock folder or click browse and select it that way. [NOTE if your path to the file flock contains a folder with a space in its name, you must put quotes around the whole path here] Now I suppose you wish an icon so click the icon button, a window will pop up click browse and go to your flock directory and the folder icons contained within it. Click open.

Now you should be back to your Entry editor browse window choose the mozicon128.png icon and click ok. now in the entry editor window which you should return to be sure run in terminal is unchecked and click ok.

Now you should a menu item for flock under Internet :)

---

### Post by durand on 2008-06-02
Yeah, its not a source tarball. If only it came as a deb file...

The eco edition is pretty cool though mozilla is so slow compared to opera's renderer otherwise I would love to use this.

---

### Post by T2manner on 2008-06-02
> No installation is needed for the file I downloaded. All you have to do is extract either the folder flock or the hidden folder that contains the folder flock somewhere on your hard drive. You can do this by double clicking the tar.gz file and clicking extract. After you have did that you find the file called simply flock and click it to run flock. When you click it you will get a message "Do you want to run "flock", or display its contents?" choose run.

To add a menu item Right click your menu and choose edit menu (or run Alacarte Menu Editor under Accesseries) Click Internet in the Alacarte window and then in Alacartes menu choose file and then new entry. A Entry Editor window should pop up now fill in the entries. Name of course Flock, Comments whatever you want, For command either type in the path to the file flock in your flock folder or click browse and select it that way. [NOTE if your path to the file flock contains a folder with a space in its name, you must put quotes around the whole path here] Now I suppose you wish an icon so click the icon button, a window will pop up click browse and go to your flock directory and the folder icons contained within it. Click open.

Now you should be back to your Entry editor browse window choose the mozicon128.png icon and click ok. now in the entry editor window which you should return to be sure run in terminal is unchecked and click ok.

Now you should a menu item for flock under Internet 

okay thanks.
i got it working :]
but when i go to browser for an icon and i go to the Flock directory and then to the icons folder, nothing shows up :\


> Yeah, its not a source tarball. If only it came as a deb file...

The eco edition is pretty cool though mozilla is so slow compared to opera's renderer otherwise I would love to use this.

well.. it's pretty fast for me.
i tried opera, and i didn't like the way it loaded pages.

---

### Post by y-lee on 2008-06-02
> but when i go to browser for an icon and i go to the Flock directory and then to the icons folder, nothing shows up :\

At this step simply click open and it goes back to a window where you can pick the icon. :)

---

### Post by T2manner on 2008-06-02
yay
thanks :]

---

