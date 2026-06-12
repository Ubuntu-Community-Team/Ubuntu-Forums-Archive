---
title: "can i find my desktop again ????"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by sprightlyone on 2008-06-02
hi
 i have also posted in another category without much luck
today i set about customising my ubuntu install. i uninstalled evolution e-mail client &replaced it with thunderbird everything seemed ok
but alas the system rebooted or something &was stuck on the splash screen when i returned from work  
 some more info it seems my wife was playiny a game i left open &went on abutton pressing spree afterwards tryiny to get to windows &somehow managed to either minimise or close the desktop
amongst other things
hope i can get my desktop back so i can do some sort of a check to see what other damage she`s done to my system
i rebooted to dual-boot selection screen &noticed 2 of everything except the windows xp sel. line
tried to enter -no luck
go to edit the kernel &add previous fix to enter &load to log-in
log-in ok
the backgroud pops up BLANK what have i done by removing the evolution program ????
any ideas ?????
how do i repair ??????
thanks lyle

---

### Post by Joeb454 on 2008-06-02
If you can get to a terminal (you can always hit Ctrl+Alt+F1) then you can try running ```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by sprightlyone on 2008-06-02
hi 
 when i log-in all i`ve got is a blank background completely bare 
  if i right click i can see all my d/top items there just doesn`t seem to be an option to turn the desktop on again 
 don`t know if this makes sense i will try your suggestion &report 
 lyle

---

### Post by sprightlyone on 2008-06-02
hi
> **Joeb454 said:**
> If you can get to a terminal (you can always hit Ctrl+Alt+F1) then you can try running ```
sudo aptitude reinstall ubuntu-desktop
```
this repairs  my desktop files 
 but i think i need the save command to complete the process
  i very new but i`m getting used to the way ubuntu does things just can`t put command together to do basic things
 lyle

---

### Post by Thanoulis on 2008-06-02
When you uninstalled Evolution you sure unistalled and the *evolution-data-server-common*...if you had checked you should be aware that you also unistalled alacarte (menu management application) and gnome-panels (this is the "taskbar").
So, reinstall *ubuntu-desktop* as said, and when uninstalling evolution, keep the *evolution-data-server-common*.

What save command???

---

### Post by Joeb454 on 2008-06-02
> **sprightlyone said:**
> this repairs  my desktop files 
 but i think i need the save command to complete the process
  i very new but i`m getting used to the way ubuntu does things just can`t put command together to do basic things
 lyle

So you have your desktop back now?

---

### Post by sprightlyone on 2008-06-02
hi 
  NO i can watch a reload of the desktop  files but it doesn`t seem to save the rebuild of the files 
it finishes @a prompt .
 the only thing is the dual boot selection screen withthe double entries which one might have the desktop installed 
 i will check this posssibility 1st then dealwith that next 
lyle

---

### Post by sprightlyone on 2008-06-02
hi 
  what i watched didn`t include the desktop iwasn`t in the package for it to reinstall 
 so i need to approach this fronm a different direction 
  so how do i repair / reinstall the evolution files i need to make the desktop work??????
  thanks lyle

---

### Post by Dougie187 on 2008-06-02
I would assume you could try going to the termial again (CTRL+ALT+F1) and typing
```
sudo apt-get install evolution
```
alternatively, you can install all the other packages Thanoulis mentioned in his post.

---

### Post by sprightlyone on 2008-06-02
[QUOTE=Dougie187;5100365]I would assume you could try going to the termial again (CTRL+ALT+F1) and typing
```
sudo apt-get install evolution
```
ok i appear to have reinstalled evolution  but i can`t seem to make the reinstall desktop  command line work 
  do i have to make evolution active or how do i check what is loaded &what isn`t ?????
 lyle

---

