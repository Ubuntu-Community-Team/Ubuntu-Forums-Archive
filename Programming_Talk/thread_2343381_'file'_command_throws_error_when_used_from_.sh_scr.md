---
title: "'file' command throws error when used from .sh script with var as parameter"
date: 2016-11-15
forum: Programming Talk
---

### Post by pablogener on 2016-11-15
Hi, all.

this code:
```

            echo $(file -n "$i");

```


throws this error:
> 
/home/pablo/Imágenes/1\ 2\ 3\ 4.jpg: ERROR: cannot open `/home/pablo/Imágenes/1\ 2\ 3\ 4.jpg' (No such file or directory)


anyone has any idea what is going on?
after that line comes another line with the 'montage' command who is throwing weird errors just like that one, regarding not being able to find the file.
also, worthy of mention, the "file..." command, when entered at a terminal window runs smoothly without any setbacks.

thanks in advance for your time and concern.

Pablo.

---

### Post by spjackson on 2016-11-16
How are you setting $i?

The problem is that when "$i" is evaluated, you get a token containing literal '\' characters followed by literal spaces rather than having these pairs interpreted as escaped spaces.

---

### Post by pablogener on 2016-11-16
> **spjackson said:**
> How are you setting $i?

The problem is that when "$i" is evaluated, you get a token containing literal '\' characters followed by literal spaces rather than having these pairs interpreted as escaped spaces.

yes yes yes yessss!! the problem, absolutely, is that which you describe.

I'll show you how I defined $i
here:

first, fill an array of strings with every file the user wants to process:
```

#ka is 'keep asking'

while [ $ka -ge 1  ]
    do
        nImg=$(zenity --file-selection --file-filter=""*.jpg" "*.gif" "*.png"" --title="Seleccionar imagenes..." --width 640 --height 480)
        if [ -z "$nImg" ]; then
            ka=0;
        else
            nImg=$(printf %q "$nImg")       #this was so 'backslashes' were added where appropriate
            lstImagenes[ka]=$nImg;
            tput cup 4 18
            echo $ka
            ((ka++));
        fi;
    done;

#if nothing was selected, no need to process anything, just quit.
if [ "${#lstImagenes[@]}" -eq 0 ]; then
    quitPanic;    
fi;


```

Then, later on down te code, process every file in that array:

```

#    sequence: create img tiles

    nTile=1;
    for i in "${lstImagenes[@]}"
        do
            montage "$i" -geometry 360x -tile 1x1 -border 5 -trim result_360_$nTile.jpg
             
            ((nTile++));
        done


```

so that's that.
while I was waiting for your answer and others answer's I thought of embedding zenity into the montage call.
Like:

montage $(zenity bla bla bla) -geometry bla bla bla result.jpg

would that work?

---

### Post by steeldriver on 2016-11-16
If you properly quote the array variable where you use it (which it appears you are doing) then there should be no need to add any backslashes

---

### Post by pablogener on 2016-11-17
> **steeldriver said:**
> If you properly quote the array variable where you use it (which it appears you are doing) then there should be no need to add any backslashes

Seems to be so, cause now it works. Everything is solved. Thanks everyone!!

---

