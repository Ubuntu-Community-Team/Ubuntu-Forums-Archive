---
title: "Oops...Many Applications Won't Start"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by sanjit on 2008-08-19
Somehow, in trying to get an up-to-date install of Elisa, I have broken something very basic. Many programs refuse to start, including thinsg like 'Add/Remove Applications', 'Software Sources', 'CCSM','Compiz Fusion Icon', and Screnlets.

Compiz and Emerald are in effect, and I can manage Emerald's settings. However, I cant manage Fusions settings. To make matters worse. It appears that 'Move Windows' is disabled, so the titlebars of most windows are inaccesible.

When I try to start 'Add/Remove' it APPEARS to be loading but eventually gives up wih no fedback as to why. When I try the start 'Software Sources', it asks for a password the first time, but does not do much after I enter it.

To make things even stranger, some programs work flawlessly, like Epiphany.

I should probably mention that, when I was trying to install Elisa, I input something into the terminal, and it told me that some things were not being used and that I should remove them. After a few tries, I managed it. I believe that's where the problem started. I was set up by my own computer.

I need this laptop for school. I can't afford a clean install or anything, but this issue is more than just a minor nuissance. Any help would be greatly appreciated.

---

### Post by sanjit on 2008-08-19
I entered:

sudo apt-get install libavahi-qt3-1 libarts1c2a kdelibs4c2a libtunepimp5 libgtk2-ruby1.8

I had removed those at or before the time of the disaster. Now that I installed them again, Fusion Icon is working, although the manager won't load, the menu looks different, and 'Add/Remove' still doesn't load.

UPDATE: Able to "find" titlebars by switching COmpiz off, moving them, then switching Compiz back on. Tedious but acceptable under the circumstances.

---

### Post by pastalavista on 2008-08-19
```
sudo aptitude install gdm
```

that may or may not be the problem but it could be.. this command will fix it or rule it out

---

### Post by jmszr on 2008-08-19
Sanjit,
        I don't know about the rest but for add/remove and the manager not loading, in the Terminal try: sudo rm /var/cache/apt/*.bin      with a space between sudo and rm and a space between rm and /var.

Hope this helps

---

### Post by sanjit on 2008-08-19
No, pastalavista, nothing was changed. Thanks.

Not doing anything,jmszr:

sudo: unable to resolve host planet revolution

Thanks anyway.

I tried to run Rhythmbox in terminal:

(rhythmbox:7323): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

---

### Post by meindian523 on 2008-08-19
You removed some system dependencies.Only way you can get back is find out what you removed and reinstall that.

---

### Post by pastalavista on 2008-08-19
you could try opening Synaptic package manager and search for "broken" packages and reinstall them

---

### Post by sanjit on 2008-08-19
Clicking 'Fix Broken Packages' does absolutely nothing. Do I have to designate what those packages are? I have no idea what they are.

---

### Post by sameerds on 2008-08-19
> **sanjit said:**
> Clicking 'Fix Broken Packages' does absolutely nothing. Do I have to designate what those packages are? I have no idea what they are.

Try the same on the command line using aptitude:

```
sudo aptitude -f install
```

This also tries to "fix" "broken" packages. Basically it tries to install any missing dependencies for existing packages. If nothing else, the output from aptitude might have more clues about what's wrong.

---

