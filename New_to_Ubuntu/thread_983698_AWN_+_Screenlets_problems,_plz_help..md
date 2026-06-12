---
title: "AWN + Screenlets problems, plz help."
date: 2008-11-15
forum: New to Ubuntu
---

### Post by gackt on 2008-11-15
Ok first of all I'm completely new to ubuntu (just got it yesterday) and i will be using this ub for now on.

The first error is AWN: it did not auto start upon booting, i have add it to the preference > session. But the record in auto startup simply disappeared after booting. Is there any other methods to get this done?

The second error is screenlets: this is the error message: Automatic creation failed. Please manually create the directory:
/home/hendrisalim/.config/autostart/ - reason: the folder is already exist, but its not there! And when i try to create it manually the system respond by saying that the folder is already exist. i already showed the hidden folder in that directory but i couldn't found it. What is the problems?

Thank you very much.

---

### Post by stoogiebuncho on 2008-11-16
What did you add to the startup sessions for awn?  The command should be 

```
avant-window-navigator
```

I'd try that once more if I were you.  If that doesn't work, you can close down all the programs that are running EXCEPT the programs you want to start at startup.  Then, go to System > Preferences > Sessions and go to the "Session Options" tab.  You can click "Remember Currently Running Applications" and whatever programs are running will start when you start your computer the next time.

As for screenlets, I'm afraid I can't help you there.:confused:  I'm assuming you looked for hidden folders as well? (Ctrl + H in Nautilus).

---

### Post by gackt on 2008-11-16
Because i dont want to do it everytime i boot the computeer, well my english is that well so i understand that you got confuse, sorry and thanks.

---

### Post by Peter09 on 2008-11-16
Hi gackt,
I think we are a bit confused with your Awn problem ... If you run awn from your sessions menu

System->Preferences->Sessions

It will run automatically every time you boot. Is that what you want?

---

### Post by gackt on 2008-11-16
hi pete

Yes i've already do that, i added the avant-windows-navigator in session. But if i turn off my laptop and turn it on again then the avn record in the session is disappears (like using deep freez), no matter how many i add it to session it will delete it self upon booting.

Thanks

---

### Post by stoogiebuncho on 2008-11-16
Did you try this?:  

1) Go to System > Preferences > Sessions

2) Go to Session Options

3) Click "Remember Currently Running Applications"

Every program that is running when you press the button will start up every time you start your computer after that.

Does that make sense?

---

