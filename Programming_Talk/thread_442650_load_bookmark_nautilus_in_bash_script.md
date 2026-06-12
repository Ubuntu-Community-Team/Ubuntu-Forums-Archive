---
title: "load bookmark nautilus in bash script"
date: 2007-05-13
forum: Programming Talk
---

### Post by jovial on 2007-05-13
hello

I need to load the list of bookmarks nautilus in a zenity dialogue
Do you know where they are locate and how i can load them in a bash script?

Bye

Jean-Luc

---

### Post by jyba on 2007-05-14
I use Kubuntu and don't have Nautilus installed so I can't try this out, but it might work :confused:  :

```
#! /bin/bash

cat $HOME/.gtk-bookmarks | \
     zenity --list \
            --title "Nautilus Bookmarks" \
            --width=500 \
            --height=300 \
            --text "" \
            --column "Listing contents of ~/.gtk-bookmarks..."

```

---

### Post by jovial on 2007-05-14
Hello

YES your code works
Just the result must be convert for space and spécial caracter : 
   file:///home/jovial/Desktop/rep%20de%20mp3 -> file:///home/jovial/Desktop/rep de mp3
   file:///home/jovial/Vid%C3%A9o -> file:///home/jovial/Vidéo

The locate is /home/user/..gtk-bookmarks:

Thanks a lot jyba  :) 

Bye bye

jean-luc

---

