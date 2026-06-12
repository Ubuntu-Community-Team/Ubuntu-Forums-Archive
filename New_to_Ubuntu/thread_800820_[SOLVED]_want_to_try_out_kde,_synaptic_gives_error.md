---
title: "[SOLVED] want to try out kde, synaptic gives error"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-05-20
I am running gnome atm, and I decided to give ked a spin.

I opened up synaptic, found kubuntu-desktop, and hit apply. It gave a whole bunch of dependencies that it said that it would need (seems perfectly reasonable), so I clicked ok. then it hit me with this

> kubuntu-desktop:
 Depends: kde-guidance but it is not going to be installed
 Depends: kdm but it is not going to be installed
 Recommends: kde-guidance-powermanager but it is not going to be installed


WHA?! 

can you please help me fix this, so I can give kde a whirl.
thanks.

---

### Post by Joeb454 on 2008-05-20
Do you get the same if you run ```
sudo apt-get install kubuntu-desktop
``` from a terminal?

Also you should note your menu's will be forever clogged up with the KDE applications ;)

---

### Post by barbedsaber on 2008-05-20
```
harry@lenovo:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kde-guidance but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Recommends: kde-guidance-powermanager but it is not going to be installed
E: Broken packages
harry@lenovo:~$ 



```

yes, I know that it will be clogged, I want to try it, and if I prefer it, I will install kubuntu from the beginning.

---

### Post by forestpixie on 2008-05-20
I'd use aptitude

```
sudo aptitude install kubuntu-desktop
```

and when joeb says "your menu's will be forever clogged up with the KDE applications" he really means it :D

---

### Post by Joeb454 on 2008-05-20
:lolflag: I reinstalled after doing that.

And did you update the repo's before? It looks like some of the packages are broken (which is very odd :confused:)

---

### Post by barbedsaber on 2008-05-20
hang on, when you say clogged, can I do a sudo apt-remove kubuntu-desktop afterwards, and make it all go away, or just use the menu editor to make them go away, or is it going to be permanent?

---

### Post by nowshining on 2008-05-20
u should be able to remove the orphaned entries, also u should try gtkorphan - see my ubuntu/kubuntu gatherings site in my sig.

---

### Post by forestpixie on 2008-05-20
When I installed with apt-get removing kubuntu-desktop did just that and removed about 46Kb of nothing and left ALL the programmes it installed behind.

You can of course - get rid of each as you will and also remove them from the menu.

Just my experience :)

---

### Post by barbedsaber on 2008-05-20
ok, I am gonna give it a go. thank you again ubuntu forums, garrgh I hope I dont have to do a fresh install.

i am just imaging, the latest in destructive commands, sudo aptitude install kubuntu-desktop

:lolflag:

---

### Post by Joeb454 on 2008-05-20
I don't know what would happen if you tried ```
sudo aptitude purge kubuntu-desktop
``` that may work, I don't know.

Good Luck ;)

Edit: And thanks for marking it solved :)

---

### Post by barbedsaber on 2008-05-20
arrgh, the K's, the K's, there everywhere. they are coming, garrgh.

I suppose I should give it a fair go before I dismiss it for overuse of the letter K.

---

### Post by Joeb454 on 2008-05-20
Yeah, though if I remember rightly, KDE does actually stand for "K Desktop Environment" so that may explain the K's

K? ;)

---

### Post by jtibau on 2008-05-20
> **barbedsaber said:**
> hang on, when you say clogged, can I do a sudo apt-remove kubuntu-desktop afterwards, and make it all go away, or just use the menu editor to make them go away, or is it going to be permanent?

kubuntu-desktop is a meta-package... It doesn't download any code for itself, but depends on a lot of others, in this case the whole kubuntu desktop. However, if you apt-get remove the meta-package you are not removing its "dependencies".

---

