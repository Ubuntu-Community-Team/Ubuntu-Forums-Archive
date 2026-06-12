---
title: "Problems installing software with 11.1"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by DrScum on 2012-02-24
I am Ubuntu user since several years now and have recently installed 11.1. At this point, after about a week of intese trying I am beginning to hate the new "software center". All I get is the information about some software being available for download and when trying it I get a bogus error message either like: "downloading failed, check your internet connection" (the internet connection is perfectly ok by the way as proven with already installed software), or, even more annoying, something like "installing would require softwarepackages of untrusted origin. 
This happened for example with VLC media player and with Controlaula.

What can I do to overcome this? Am I missing something? Help would be greatly appreciated.

---

### Post by idoitprone on 2012-02-24
simple question
did you update your package data from ubuntu repositories?

there should be a refresh button

this is the terminal command to update packages but ubuntu software center must be closed
i only know terminal commands
sudo apt-get update

If you want an better gui
```
sudo apt-get install synaptic
```synaptic package manager has historically been installed in ubuntu but removed for the 11.10 release

---

### Post by raja.genupula on 2012-02-24
That problem we can solve easily . please give me the output of 
```
sudo apt-get update
``` 

and +1 to above post , I agree as synaptic is best and better than Software center . 

post that output . 

All the best .

---

### Post by idoitprone on 2012-02-24
> **raja.genupula said:**
> That problem we can solve easily . please give me the output of 
```
sudo apt-get update
```and +1 to above post , I agree as synaptic is best and better than Software center . 

post that output . 

All the best .

Sigh....I kidda wish Mark Shuttleworth stop dumbing down the desktop. Sigh I learned linux from Ubuntu

---

### Post by DrScum on 2012-02-24
Thanks for the quick replies. I will do the sudo apt-get thing, although I did this a few days ago already. Posting the output of this particular machine micht be a bit tricky, since the installation is in German.

However, when I run the command I see a lot of updating going on. I did, by the way, check the boxes in all available software sources too. 

Thanks for the synaptic tip, I have been using synaptic extensively during the past years and was very happy with it.

Now the output of the apt-get update command summarized:

a total of 3 GPG-errors: signatures where invalid (and are updated now, I hope). My working day starts now (European time zone). I'll keep you posted about the progress.

Thanks for the help again.

---

### Post by raja.genupula on 2012-02-24
Ok I understand . 
open your terminal and do this and let us know what you got .

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

All the best .

---

### Post by DrScum on 2012-02-24
THX a lot! With controlaula it works now. I hope it keeps.

---

