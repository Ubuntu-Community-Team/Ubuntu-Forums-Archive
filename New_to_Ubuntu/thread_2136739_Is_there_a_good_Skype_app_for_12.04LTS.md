---
title: "Is there a good Skype app for 12.04LTS?"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-18
I can't find anything that looks like a Skype app in the software center for 12.;04LTS. It's not a huge problem but, it would be nice to have if one is available somewhere.

---

### Post by plucky on 2013-04-18
> **alhefner said:**
> I can't find anything that looks like a Skype app in the software center for 12.;04LTS. It's not a huge problem but, it would be nice to have if one is available somewhere.

If you enable the **partner** repository in **Software Sources** you should be able to install **Skype**

Good Luck

---

### Post by fantab on 2013-04-18
Enable **Partner Sources**, as plucky said and also enable **Independent Sources. **(These Sources will enable you install applications that are not available through Ubuntu repositories. These applications are mostly 'closed source', for instance Skype, Adobe reader, etc..., there are other licence restrictions why Ubuntu does not give these apps through its main repos... )

Then you have to run:

```
sudo apt-get update
sudo apt-get install skype
```

From the TERMINAL [Ctrl+Alt+T]

---

### Post by alhefner on 2013-04-18
> **plucky said:**
> If you enable the **partner** repository in **Software Sources** you should be able to install **Skype**

Good Luck

OK, how do I do that? I looked in the "Software Center" and didn't find anything there to enable. Is it something I need to access through the web browser or is it a system setting of some kind I need to set through the terminal, or what?

I'm still trying to learn how to navigate Ubuntu and Linux in geneal.

---

### Post by uzumakifahim on 2013-04-18
You can also download skype from their official website. You can [click here]("http://www.skype.com/en/download-skype/skype-for-computer/") and select Ubuntu 12.04 (multiarch) from the "Choose your distribution" dropdown menu.

---

### Post by Kopkins on 2013-04-18
It should be in settings. System Settings > Software & Sources, in the first tab you shoud have a series of checkboxes.

Good luck

Kopkins

---

### Post by kostkon on 2013-04-18
> **alhefner said:**
> OK, how do I do that? I looked in the "Software Center" and didn't find anything there to enable. Is it something I need to access through the web browser or is it a system setting of some kind I need to set through the terminal, or what?

I'm still trying to learn how to navigate Ubuntu and Linux in geneal.
In the software centre, select Edit &#8594; Software Sources from the menu.

Also, if you'd like to integrate it better in Ubuntu, then check [Skype Wrapper]("http://www.omgubuntu.co.uk/2012/09/skype-wrapper-for-ubuntu-gets-updated").

---

### Post by alhefner on 2013-04-19
> **Kopkins said:**
> It should be in settings. System Settings > Software & Sources, in the first tab you shoud have a series of checkboxes.

Good luck

Kopkins

Got no "Software & Sources" in the software center at all. No menu either. Hmmm... what to do, what to do. Seems very limiting.

---

### Post by 3rdalbum on 2013-04-19
Software Sources is in the Edit menu of Ubuntu Software Center. Remember, the menus are at the top of the screen not the top of the window, and the menus are only visible when you actually move your mouse to the top panel.

You could also tap the Alt key and type "software", and the third result from the top is Software Sources.

---

### Post by fantab on 2013-04-19
> **alhefner said:**
> Got no "Software & Sources" in the software center at all. No menu either. Hmmm... what to do, what to do. Seems very limiting.

Okay, the application to edit 'sources is called, "**Update Manager**", you can search for it from DASH. After you've opened the Update-Manager at the bottom you will find "Settings" click on it then "Other" and enable the required Sources. See the screen-shot below:


[ATTACH=CONFIG]241534[/ATTACH]             [ATTACH=CONFIG]241535[/ATTACH]

---

### Post by 3rdalbum on 2013-04-19
> **fantab said:**
> Okay, the application to edit 'sources is called, "**Software & Updates**", you can search for it from DASH. See the screen-shot:


[ATTACH=CONFIG]241524[/ATTACH]

I know you mean well, but your instructions are just confusing the poor chap. He's using 12.04, you're using 13.04. You can't get to Software Sources from the Dash in 12.04.

---

### Post by fantab on 2013-04-19
> **3rdalbum said:**
> I know you mean well, but your instructions are just confusing the poor chap. He's using 12.04, you're using 13.04. You can't get to Software Sources from the Dash in 12.04.

Thank you for pointing it out. My Bad.

I have edited my post to reflect what to do in 12.04.

---

### Post by alhefner on 2013-04-19
Managed to change the software sources like you guys have suggested. Still not finding anything for Skype though. Like I said, it's not a really big issue, jut something that would be nice to have. I'll check out the other links provided in earlier replies to this and see what happens...

---

### Post by philinux on 2013-04-19
> **alhefner said:**
> Managed to change the software sources like you guys have suggested. Still not finding anything for Skype though. Like I said, it's not a really big issue, jut something that would be nice to have. I'll check out the other links provided in earlier replies to this and see what happens...

Now you need to do this. 

sudo apt-get update && sudo apt-get install skype

For anyone else on 12.04

[http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html)

---

### Post by alhefner on 2013-04-19
> **philinux said:**
> Now you need to do this. 

sudo apt-get update && sudo apt-get install skype

For anyone else on 12.04

[http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html)


Well, now, ain't that somethin! \\:D/ Thanks! It seemed to work like a champ!

---

