---
title: "How to Uninstall ies4linux"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-05-15
I think that I have it installed twice and its not really working in ether. How do I find and uninstall it?

---

### Post by philinux on 2008-05-15
Apps>Wine>Uninstall Wine apps

---

### Post by niceguy123 on 2008-05-15
> **philinux said:**
> Apps>Wine>Uninstall Wine apps

I don't know why that didn't help me. (I didn't understand where I'm am supposed to follow that trail).

---

### Post by philinux on 2008-05-15
The menu's in the top panel

Applications>Wine>Uninstall Wine Applications

---

### Post by niceguy123 on 2008-05-16
> **philinux said:**
> The menu's in the top panel

Applications>Wine>Uninstall Wine Applications

That's what i thought you meant. But, I don't see Wine under applications in the menu bar. I have wine installed. How do I add it to the applications menu bar?

Thanks

---

### Post by angry_johnnie on 2008-05-16
According the the IEs4Linux website, there isn't an easy, point and click, uninstall feature.  You'll have to remove those directories yourself.

Take a look [here]("http://www.tatanka.com.br/ies4linux/page/Uninstall").

---

### Post by niceguy123 on 2008-05-16
> **angry_johnnie said:**
> According the the IEs4Linux website, there isn't an easy, point and click, uninstall feature.  You'll have to remove those directories yourself.

Take a look [here]("http://www.tatanka.com.br/ies4linux/page/Uninstall").

> Usually you have to remove:

    * ~/.ies4linux folder
    * Executables at ~/bin
    * Desktop shortcuts 

Where do I find     * ~/.ies4linux folder  ?

---

### Post by shifty_powers on 2008-05-16
that will be in your home folder.

go >places>Home Folder and press control H

---

### Post by philinux on 2008-05-16
Just checked the wine menu and the uninstall app is called uninstaller.

So you could run that from the terminal.

uninstaller

---

### Post by niceguy123 on 2008-05-16
> **philinux said:**
> Just checked the wine menu and the uninstall app is called uninstaller.

So you could run that from the terminal.

uninstaller


How come I don't have a Wine menu? How do I make one?

---

### Post by eko291 on 2008-05-16
If you installed wine via synaptec, it should be on your menu.  If you manually installed via a download file, it may not have added itself.

FYI, I had to remove the directories manually to get rid of ies4linux.

---

### Post by philinux on 2008-05-16
> **niceguy123 said:**
> How come I don't have a Wine menu? How do I make one?

I installed wine from synaptic.

---

### Post by niceguy123 on 2008-05-16
I installed both wine and ies4linux in terminal. How can I add them to the menu?

---

### Post by philinux on 2008-05-16
Do you mean you did apt-get install wine. This should have set up the menu. If you did it by downloading from winehq not sure. 

You could try looking through System>Prefs>Main Menu
see if it got put in accessories or other.

---

### Post by niceguy123 on 2008-05-16
> **philinux said:**
> 
You could try looking through System>Prefs>Main Menu
see if it got put in accessories or other.

Thanks that worked.

---

