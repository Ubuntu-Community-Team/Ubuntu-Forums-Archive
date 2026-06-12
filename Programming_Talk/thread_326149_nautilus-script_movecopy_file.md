---
title: "nautilus-script move/copy file"
date: 2006-12-27
forum: Programming Talk
---

### Post by bro on 2006-12-27
Hi, I'd like to have a nautilus scritp that moves a file to my home directory. I found the script below that should copy it. It doesn't work. why not? 

```
#!/bin/sh
# copyhome:  copies the selected file(s) to home directory
# (if able)

for arg 
do
   if [ -f ~/"$arg" ];    then
      MSG="File: '$arg' already exists in home directory. Overwrite?"
      if    
         gdialog --title "Overwrite?" --defaultno --yesno "$MSG" 200 100 
      
      then
         cp "$arg" ~/"$arg"
      fi
   else
     cp "$arg" ~/"$arg"
   fi

done
```

---

### Post by hadiriazi on 2006-12-27
do you have to issue a command in a terminal to do this?

---

### Post by bro on 2006-12-27
no i use nautilus scripts located in /home/~user/.gnome2/nautilus-scripts/ and I find them in the menu under my right mouse button. Like the ones at [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) only I can't find out how to actually make them myself (properly). Hence the question above, what's wrong with the script?

---

### Post by Keith Hedger on 2007-01-16
make sure the execute bit is set for the script also when copying/creating a new nautilus script in the scripts folder you may have to click the reload button to make nautilus regonize the changes

---

