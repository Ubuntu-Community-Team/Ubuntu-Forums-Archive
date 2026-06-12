---
title: "Is there a way back to the old desktop?"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by bamim2 on 2011-12-22
I guess I've officially turned into an old geezer. I've just upgraded to 11 & do NOT understand the 11 desktop, is there a way that I can run the old desktop? I can't get around in this one & rather than cursing this one all the time, I'd love to have my old familiar setup.

---

### Post by mikewhatever on 2011-12-22
There is no such thing as Ubuntu 11. Which one have you upgraded to, 11.04 or 11.10???

---

### Post by lisati on 2011-12-22
Depending on which of the 11.xx versions you are using, there should be an option near the bottom of the login page to use different DEs. Take a look for "Gnome classic."

If you can't find what you are looking for on the login page, there are options to install something suitable, feel free to ask.

---

### Post by Lars Noodén on 2011-12-22
You might also give Xubuntu a try.  It has a more traditional interface and is less of a shock than Unity.  It is available for whatever version you are running either 11.04 or 11.10.

---

### Post by bamim2 on 2011-12-22
THANK YOU. Sorry to be a bonehead, but this IS the bonehead section, so thank YOU for not insulting me. I guess a good place for me to start would be how can I tell which version I'm using? I know I have 11.?? How do I figure that .?? part out? I can't even figure out how to get a terminal so I can find out.

Also, my login page page says Ubuntu, Ubuntu 2D & a couple of other things; probably single user mode or something. Obviously I can't see the login screen while I have access to the web browser, so I'm not sure exactly what the other choices are. I can figure that out, if it's really helpful though. 

How do I get Xubuntu?

---

### Post by Lars Noodén on 2011-12-22
You can find out which version by going to System Settings->System Info.

If you want to do it via the terminal, hit ctrl-alt-t to bring up a terminal and then enter [font=Courier New]lsb_release -rd[/font]

If you want to try Xubuntu, you can install the package xubuntu-desktop

---

### Post by bamim2 on 2011-12-22
Thanks. I'm running Ubuntu as a vm, so sometimes going to the terminal via Ctl-Alt can cause problems. 

I WILL try Xubuntu desktop though. THANKS. Ahhmmm, sorry, but how in the WORLD to I get there from here? I can't find anything. This is driving me crazy. I REALLY do appreciate the help.

---

### Post by MG&amp;TL on 2011-12-22
First off: I know Unity can be a pain, but give it a try, you might (eventually! :P) like it.

To install xubuntu (and xfce, it's interface), open a terminal by opening the dash (click the topmost button) and typing "terminal"-you'll see an icon labeled "terminal". Click on it.


Now type:

```
sudo apt-get install xubuntu-desktop
```


I have another suggestion: Lubuntu-lighter and faster than Unity or XFCE, it is a little less full-featured, but there's nothing to stop you installing more apps as you need.


You can get the download [here]("lubuntu.net"), but you can try it by installing lubuntu desktop:

```
sudo apt-get install lubuntu-desktop
```

---

### Post by bamim2 on 2011-12-22
Thank you. Now that I've installed that, what do I do to "activate" it or access it or whatever?

---

### Post by Paqman on 2011-12-22
Log out, click on the wee cog icon by your user name and pick what desktop environment you want to log in to.

---

### Post by bamim2 on 2011-12-22
Thank you. THIS is much better!

---

### Post by bamim2 on 2011-12-22
ONE last dumb question. How do I shut this off? I only see a way to log out. I don't see a way to shut down.

---

### Post by MG&amp;TL on 2011-12-22
in XFCE or LXDE?

Try clicking on it, if it doesn't give you a menu, we can try again from #1. You can always shutdown from the login screen.

---

