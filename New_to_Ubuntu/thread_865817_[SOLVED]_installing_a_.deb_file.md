---
title: "[SOLVED] installing a *.deb file"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by slikwill on 2008-07-21
I want to install Audacity 1.3.5.
I have downloaded the .deb file to my Desktop
How do I do the install.

---

### Post by sdennie on 2008-07-21
You can either double click it to bring up a graphical installation application or you can use:

```

sudo dpkg -i name_of_the_package.deb

```

---

### Post by alienexplorers on 2008-07-21
Just double click it and select install.

---

### Post by iaculallad on 2008-07-21
Or, you could just use the Synaptics Package Manager to install audacity for you.
System-Administration-Synaptics Package Manager, and search for audacity.

---

### Post by slikwill on 2008-07-21
The add/remove applications will give me Audacity 1.3.4 and I need 1.3.5 to fix a problem.
I get the following when I double -click:
"Error: Dependency is not satisfiable libasound2"

Obviously I have the .deb file in the wrong place.

---

### Post by L815 on 2008-07-21
If there's more than one .deb file, run this in the directory they are in:
```
sudo dpkg -i *.deb
```

If there are dependency issues, run this in terminal:
```
sudo apt-get -f install
```

---

### Post by kevmitch on 2008-07-21
Ah, it appears that you're going to need a newer version of libasound as well ([http://packages.ubuntu.com/intrepid/libasound2](http://packages.ubuntu.com/intrepid/libasound2)).

---

### Post by slikwill on 2008-07-21
Yes, there were two dependencies, but you reference led me to them.
I have Audacity 1.3.5 installed and working to support my ION USB Turntable.  I can finally hear the playback of the record I am recording.

---

### Post by Joeb454 on 2008-07-21
Glad you got it working! :)

You can mark your thread as solved from thread tools at the top of this page

---

