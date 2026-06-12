---
title: "Enabling foreign language spell-check on OpenOffice"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by amabuntu on 2008-05-02
So, how would I go about enabling spell-check in Russian when I am writing documents in OpenOffice?

---

### Post by mano cazalet on 2008-05-02
hello it should be

file --» wizards --» install new dictionaries

after installed u can select it in tools -- options -- language settings

oops Edit: forgot to warn you, if you have compiz enabled, it must be disabled before installing a dic. Otherwise u can't see the install manager

---

### Post by amabuntu on 2008-05-02
As for "disabling" compiz, do you mean uninstalling the program or is there a way to just "disable" it?

Also, weird thing is that when I go to the Install New Dictionaries... wizard, it takes me to a French site that has a list of languages, but Russian isn't even there in the options.

---

### Post by mano cazalet on 2008-05-02
not, it's enough just disabling it, reloading metacity. But since russian is not on the list, I've just checked it, you won't have to do it. 

Instead you can download it [here]("http://wiki.services.openoffice.org/wiki/Dictionaries#Russian_.28Russia.29")

---

### Post by zvacet on 2008-05-02
Do you have locales installed? I ask you that because I just tried what you asking for and I didn´t need to import any dictionary.I was able to do spell check automatically (and my native language is not English).

---

### Post by amabuntu on 2008-05-02
Ok, I'm kind of an idiot here, but I downloaded the zip file, unzipped it, but what do I do now?  Do I put it in a certain directory or something for it to work?

Mine doesn't do Russian spell-check automatically because right now it's only configured for English dictionaries.  So if I type in a Russian nonsense word, it will be underlined, but there will be no suggestions when I go to spell-check it.

---

### Post by mano cazalet on 2008-05-02
ok first u will have to open nautilus in terminal with ```
sudo nautilus
```

then in nautilus (the file manager) copy this 2 files: ru_RU.aff and ru_RU.dic to 
/usr/lib/openoffice/share/dict/ooo

and the final step should be again in terminal
```
sudo gedit /usr/lib/openoffice/share/dict/ooo/dictionary.lst
```

after the file opens copy this line
DICT ru RU ru_RU
to the bottom line

close the file and restart openoffice including the quickstarter
it should work 

at least I hope it works

---

### Post by Hagar Delest on 2008-05-03
See here for further information: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

---

