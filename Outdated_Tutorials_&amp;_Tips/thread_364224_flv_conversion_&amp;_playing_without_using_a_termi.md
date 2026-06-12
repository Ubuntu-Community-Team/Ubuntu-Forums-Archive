---
title: "flv conversion &amp; playing without using a terminal"
date: 2007-02-18
forum: Outdated Tutorials &amp; Tips
---

### Post by BRAXS69 on 2007-02-18
hay guys in the efforts I've made to learn a bit more about linux programing i decided to go with something easy like bash scripting. instead of just making random useless scripts i chose to make one that made my life easier in the .flv conversion department. so i made a script that you setup as the .flv  default application, that will play the mpg file whilst its converting. i didn't find any scripts on the forums that was like this so i decided to post it, well  enough babbling  heres the script:

use text editor and just put the code in and save it as something like "flvrun.sh"  
> 
#!/bin/bash
if zenity --question --text="This script will attempt to convert the .flv file to a .mpg file in the same directory continue?"; then
if ffmpeg -i $1 -ab 56 -ar 22050 -b 500  -s 320x240 $1.mpg; then
if zenity --question --text="do you wish to delete the .flv file now?     (this will move it to trash so don't worry if it stuffs up XD)"; then
mv $1 ./.Trash/
fi 
fi &
sleep 3
gnome-open $1.mpg 
fi ~ lol sorry about the quote tags i dont know how to just put it in a box

make sure you set the permissions on the file to be executable otherwise the script wont run. 

these directions are for people using the gnome desktop i dont know how to set it up for KDE
then go to a .flv file right click go "properties" chage the tab to "Open With" go "add" then hit the "Use  a custom command" then go "Browse..." and go to the file you saved select it and go "Open" then click "Add" and lastly make sure it toggled to be default, then you can close everything and now any .flv file you open will run the script.  
   

it does use the “ffmpeg” command so make sure you got it installed.
	sudo apt-get install ffmpeg  ~ in the terminal should do the trick

---

