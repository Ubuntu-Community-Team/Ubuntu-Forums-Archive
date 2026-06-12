---
title: "[Bash] Simple mv nautilus script question"
date: 2009-05-21
forum: Programming Talk
---

### Post by AlucardArg on 2009-05-21
Hi all!
As you will see, my knowledge in programming is VERY limited, but all in all I wanted to see if I could make a simple script to move selected folders to another folder (when I download music, I want the script to automatically move the selected folder to my music folder)

This is what I've got so far:
```
#!/bin/bash

# Mueve la carpeta seleccionada a /media/secdisk/My Music


if zenity --question --title "Seguro?" --text "Mover $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS a la carpeta Music? (Se sobreescribiran datos de ser necesario)"

then
mv "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" "/media/secdisk/My Music"
zenity --info --title "Completado" --text "Transefencia completada"
exit 0

else
zenity --info --title "Abortando" --text "Movimiento cancelado. Saliendo."
fi

exit 1
```

Now, the problem is that, well, it won't move the folder. When running the script from a Terminal, this is the output:
```
nicolas@nicolas-desktop:~/.gnome2/nautilus-scripts$ ./MusicMover.sh
mv: cannot stat `': No such file or directory
```
(Of course I'm not selecting any file by running it like this, but when right-clicking a file, and running the script, it doesn't work either, and so far, I don't know how to dump the output of the script to a file...)

I know the script is extremely simple, and I was doubting if I should post it in the Programming forum, but, please help? :D


PS: The zenity messages are in Spanish, because I'm from Argentina, therefore, my main lang is Spanish :P

---

### Post by odyniec on 2009-05-21
$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS is a newline-delimited list of file paths. Set the internal field separator (IFS) to a newline character, and process the file paths one at a time, in a for loop:
```
IFS='
'
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    mv "$file" "/media/secdisk/My Music"
done
```

---

### Post by AlucardArg on 2009-05-21
Thank you odyniec for taking time to help me out!
Well, I set the IFS like you said, and it works, but only when moving files, not folders.
Sorry to bother you, but I tried googling it, but no avail...
And thank you for the fast response!

---

### Post by odyniec on 2009-05-22
Can you post the script after the changes?

---

### Post by AlucardArg on 2009-05-22
Sure
```
#!/bin/bash

# Mueve la carpeta seleccionada a /media/secdisk/My Music


if zenity --question --title "Seguro?" --text "Mover $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS a la carpeta Music? (Se sobreescribiran datos de ser necesario)"

then

IFS='
'
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    cp "$file" "/home/nicolas/Desktop"
done

zenity --info --title "Completado" --text "Transefencia completada"
exit

else
zenity --info --title "Abortando" --text "Movimiento cancelado. Saliendo."
fi

exit
```

Note: I changed "mv" to "cp", and the destination folder to the Desktop for testing purposes. When it's finished, I'll modify it to the correct values.

---

### Post by odyniec on 2009-05-23
The script seems fine to me, so maybe there's some other problem. Try printing the file/folder names that are being processed in the for loop, to make sure the script is picking them up correctly. Example:
```
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    zenity --info --text "$file"
    cp "$file" "/home/nicolas/Desktop"
done
```

---

### Post by AlucardArg on 2009-05-23
The modification you posted reported the selected file just fine.
But I found the problem... I just needed the -R modifier in the cp command (not needed in mv, from what it says in --help) to make it recursive... Simple enough.

**Odyniec, thanks a lot for taking the time to help me out!**

Now I'll see if I can make it uncompress the files automagically :P (I have a similar script, so I'll see what I can take from it)

---

