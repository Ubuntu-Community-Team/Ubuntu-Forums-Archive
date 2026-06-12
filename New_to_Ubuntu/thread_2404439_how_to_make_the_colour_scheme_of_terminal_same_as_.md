---
title: "how to make the colour scheme of terminal same as text editor(gedit)"
date: 2018-10-24
forum: New to Ubuntu
---

### Post by santanu++ on 2018-10-24
Hello Ubuntu Community ! I am Santanu ! I hope everyone is doing great.

I am a newbie here. I never thought that the text editor's colour scheme would be so awesome.
**Is there anyway to make the colour scheme of terminal like text editor ?** I am using Ubuntu 18.04 LTS on my hp laptop.

A screenshot link is added below -This is how I want to make the terminal to look like. Please look into it. [https://drive.google.com/file/d/12sfu7cUL2YBzpHQmukvED8use9kFjihO/view?usp=sharing](https://drive.google.com/file/d/12sfu7cUL2YBzpHQmukvED8use9kFjihO/view?usp=sharing)

Thank You

---

### Post by dino99 on 2018-10-24
If you glance at the terminal menu, select 'edit' then 'preferences', you will see tabs and settings you can tweak as you wish  :p

---

### Post by Holger_Gehrke on 2018-10-24
The terminal just gives a character-based display to programs that expect one. It offers a palette of 16 colours for programs to use. You can change these in the settings (menu: edit->profile preferences->colors). How programs use these colours is up to each program itself, so the results will probably not be quite what you expect. What the editor offers and the shell (the program that runs in the terminal if you don't explicitly tell it to run something else; by default the shell is a program named 'bash') does not is syntax highlighting. There are shells that can do this ('fish' and 'zsh' with some kind of plugin / extension), but those are different shells with different command languages, so I wouldn't recommend these to a newbie.

Holger

---

### Post by Impavidus on 2018-10-24
The terminal has some indexed colours available to programs running in the terminal. Not every terminal has the same number of colours available. xfce4-terminal, the default on Xubuntu, has 256 colours, 16 of which can easily be redefined by the user. All an application running in the terminal can do is request colour #1 or #2 or something else, and it's up to the terminal to decide which colour that is. By default, 1 and 2 are dark red and dark green. There are text editors with syntax highlighting that run in the terminal. My favourite is vim. It should be possible to tweak them to look similar to gedit.

I once found a script to demonstrate escape codes in the terminal to show colours and some other effects:```
#!/bin/bash

# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.

#Background
for clbg in {40..47} {100..107} 49 ; do
    #Foreground
    for clfg in {30..37} {90..97} 39 ; do
        #Formatting
        for attr in 0 1 2 4 7 9 ; do
            #Print the result
            echo -en "\e[${attr};${clbg};${clfg}m ^[${attr};${clbg};${clfg}m \e[0m"
        done
        echo #Newline
    done
done

exit 0


```

---

### Post by santanu++ on 2018-10-24
thanks a lot. I will do that.

---

### Post by santanu++ on 2018-10-24
Thanks for replying.

---

### Post by santanu++ on 2018-10-24
Thanks for replying. Yeah, that's true - shell and text editor have their own characteristic colour.

---

