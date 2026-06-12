---
title: "Cannot open apps in Launcher"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by sillystring on 2012-02-07
Really new to this. Installed 11.10 64 bit. Trying to learn how to install and open apps. If I click on the icons in launcher, some open but some don't. 

Firefox, for example, was pre-installed.  I click, right click... nothing. The menu says it's installed but I can't make it open. Libre Office apps were pre-installed and they do open by clicking. 

I downloaded Calibre and GNUCash, the menu shows they are installed but I cannot open them either.Then I downloaded GIMP and it does open from launcher when I click on it. 

Menu says they are all installed so why do some open and some won't???

Thanks for the help!

---

### Post by joetait on 2012-02-07
Can you open them from the dash?

Also, have you tried removing them from the launcher and then replacing them? Might be worth a shot.

---

### Post by Frogs Hair on 2012-02-07
You can try the following command in the terminal also .```
unity --reset-icons
```

---

### Post by sillystring on 2012-02-07
No, they won't open from Dash or from Launcher.  I tried Frogs Hair's suggestion and that took the icons for the apps I had installed out of Launcher and reset them back to how they were when first installed.  Found them in Dash and did drop and drag back into Launcher.  

The problem is still the same... the same ones that opened before still do.  The same ones that would not open still won't.

---

### Post by Mark Phelps on 2012-02-08
Open a terminal and try running each app by entering the program name in the terminal.  If it's unable to launch properly, you should see some error messages in the terminal window.

---

### Post by Frogs Hair on 2012-02-08
>  I tried Frogs Hair's suggestion and that took the icons for the apps I had installed out of Launcher and reset them back to how they were when first installed. Found them in Dash and did drop and drag back into Launcher.

Sorry , I should have written that the command resets the launcher icons to default .

---

### Post by sillystring on 2012-02-08
Mark Phelp's suggestion makes sense and may shed some light on the problem.

Sorry for such an elementary question, but, even after searching, can't seem to figure out the correct command to use to open an app in the terminal.  I have attempted a few different things but no success. 

What exactly should I type to open, for example, the app "Calibre" from the terminal?

---

