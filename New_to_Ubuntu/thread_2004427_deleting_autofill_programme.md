---
title: "deleting autofill programme"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by zirgut on 2012-06-15
Hi
Some time ago I installed the ubuntu autofill programme and have found it confusing and not been able to switch it off. I have also been unable to work out how to delete it. Could someone please tell me how to do this.
Thanks

---

### Post by the.phantom on 2012-06-15
i am not a expert but

what did you use to install the autofill?

if you used the software center to install it, then just go back and you can click to "remove/uninstall"

if you used symantic you can do the same thing and remove it

and what is the real name of the autofill program?

---

### Post by pharpend on 2012-06-15
I concur with phantom. If you used Synaptic or USS, just find the package and uninstall it. 

With Synaptic, click on the check box, and select [FONT="Courier New"]Mark for Removal[/FONT]. Move your cursor up to the top of the window and click [FONT="Courier New"]Apply[/FONT].

With USS, click the tab on the left labeled [FONT="Courier New"]Installed Software[/FONT]. Find the program, click on it, and click the [FONT="Courier New"]Remove[/FONT] button.

If you did happen to use apt, and you remember the package name, type this into your command line:

```
sudo apt-get -y autoremove <package name>
```

Replace [FONT="Courier New"]<package name>[/FONT] with your package name.

---

### Post by zirgut on 2012-06-18
> **pharpend said:**
> I concur with phantom. If you used Synaptic or USS, just find the package and uninstall it. 

With Synaptic, click on the check box, and select [FONT="Courier New"]Mark for Removal[/FONT]. Move your cursor up to the top of the window and click [FONT="Courier New"]Apply[/FONT].

With USS, click the tab on the left labeled [FONT="Courier New"]Installed Software[/FONT]. Find the program, click on it, and click the [FONT="Courier New"]Remove[/FONT] button.

If you did happen to use apt, and you remember the package name, type this into your command line:

```
sudo apt-get -y autoremove <package name>
```

Replace [FONT="Courier New"]<package name>[/FONT] with your package name.
Hi,
Thanks for your advice.
I tried what you suggested but cannot still find the package. The package is a Firefox Mozilla add on called Autofill Forms. I am sure I downloaded it from the Ubuntu software centre when I was on 10.02 but can find no record of it in the history and the installed programmes. I remain perplexed.

---

### Post by MG&amp;TL on 2012-06-18
> **zirgut said:**
> Hi,
Thanks for your advice.
I tried what you suggested but cannot still find the package. The package is a Firefox Mozilla add on called Autofill Forms. I am sure I downloaded it from the Ubuntu software centre when I was on 10.02 but can find no record of it in the history and the installed programmes. I remain perplexed.

You can remove/disable it from the firefox add-on menu, surely?

---

### Post by zirgut on 2012-06-18
Thanks MG &TL. 
After a little faffing around I found out how to access the add-ons and then how to remove. Now all is done and life is a little simpler.

---

