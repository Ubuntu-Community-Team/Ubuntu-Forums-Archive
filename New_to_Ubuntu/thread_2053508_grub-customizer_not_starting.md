---
title: "grub-customizer not starting"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by klein de usa on 2012-09-05
hi 
i tried running grub-customizer in terminal and it gives me an error: 

grub-customizer: /build/buildd/grub-customizer-2.5.7.1/src/model/grublistCfg.cpp:454: bool GrublistCfg::compare(const GrublistCfg&) const: Assertion `piter->dataSource != __null' failed.
Aborted

i installed it sometime ago, and set it up to boot an iso from the menu list in grub everything works good no problems but i wonted to shorten my kernel list. i'm lost

---

### Post by Bashing-om on 2012-09-05
klein de usa; Hi !

   If I may I suggest the easy way resolve the error is to un-install (purge) grub-config and re-install the utility.

  For removing old kernels and associated header files, I prefer to use synaptic. ( ask and thou shalt receive)..

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by klein de usa on 2012-09-05
thanks Bashing-om
but i have tried that, and i still get the same message, i'm wondering if it is the nv video card but it worked before fine, when i un installed it i even went through and made sure it deleted all the configure files i could find, reinstalled and get the same error. if i do a update-grub , grub runs its config without a problem so it has to be in the program grub-customizer i would think .

---

### Post by Bashing-om on 2012-09-06
I also have difficulty decyphering the error. when you un-installed  grub-customizer did you  do 
```
sudo apt-get purge remove grub-customizer
```that to delete the config files too.....???
[INDENT]BDQ
[/INDENT]

---

### Post by klein de usa on 2012-09-06
hi Bashing-om
i ran sudo apt-get purge remove grub-customizer this is what i get 


xxxx@27nnwd1:~$ sudo apt-get purge remove grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remove

---

### Post by Kopkins on 2012-09-06
Purge and remove are two different apt-get functions. Remove simply removes the package, but purge does so and removes all config files associated with the package.

When you run the commands the syntax is as follows.

```
sudo apt-get function package1 package2 package3
```

Apt-get interprets your command as trying to purge a package called remove. 

Just do ```

sudo apt-get purge grub-customizer
```

Best of luck,
Kopkins

---

### Post by Bashing-om on 2012-09-06
sorry my error, correct the code to :
```
sudo apt-get --purge remove grub-customizer
```Them two little dashes is important, huh?

Then to reinstall grub-cutomizer:
```
sudo apt-get install grub-customizer
```[INDENT]this should work <==BDQ
[/INDENT]

---

