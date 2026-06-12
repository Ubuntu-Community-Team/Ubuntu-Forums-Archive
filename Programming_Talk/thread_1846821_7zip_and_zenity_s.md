---
title: "7zip and zenity ?s"
date: 2011-09-19
forum: Programming Talk
---

### Post by lance bermudez on 2011-09-19
looking around the net I was able to find out how to kill the zipping 
progress when i hit the cancel button but do not know how to kill the script when i hit any of the other cancel buttons. to kill them i have to hit all the "x"

#!/bin/bash
zenity --info --text "Choose source file to 7zip using deflate64 /dir in box or click file";
szSavePathfrom=$(zenity --file-selection --multiple --save); #--confirm-overwrite);
zenity --info --text "Choose file destination";
szSavePathto=$(zenity --file-selection --multiple --save --confirm-overwrite);
7z a -mm=deflate64 $szSavePathto.zip $szSavePathfrom | (if `zenity --progress --text="zipping" --percentage=1 --auto-close`;
                 then
                     echo 'Zipping Job completed'
                 else
                     killall 7z p7zip p7zip-full 
                     exit
                 fi)

---

