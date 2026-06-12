---
title: "Bash and filenames with spaces."
date: 2012-05-04
forum: Programming Talk
---

### Post by hakermania on 2012-05-04
I was making the other day a script, in order to put it under ~/.gnome2/nautilus-scripts/ 

The script will be able to set as your desktop background your selected wallpaper (right click->set as background)
This is what I've made so far:
```

#!/bin/bash
path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
#The variable NAUTILUS_SCRIPT_SELECTED_FILE_PATHS comes with an extra " " (space) in the end
#So I need to remove it.
path=${path%?}
#making the variable as (including the quotes) "file:///path/to/file/a.png"
quoted="\"file://$path\""
#echoing the result so as to see how it went
echo $quoted > /home/alex/Desktop/asdf
#command to set the background
gsettings set org.gnome.desktop.background picture-uri $quoted

```

The above code works fine for filenames without spaces.
Then I tried it for filenames with spaces. My wallpaper turned black!
I checked the file /home/alex/Desktop/asdf to see what was the problem and I got
```

"file:///home/alex/Desktop/a b c d e f g.png"

```
So, everything seemed fine, so I opened a terminal and I gave the exact same command that my script does in the end so as to change the wallpaper:
```

gsettings set org.gnome.desktop.background picture-uri "file:///home/alex/Desktop/a b c d e f g.png"

```
As you see, where $quoted in my script, I placed its equal, "file:///home/alex/Desktop/a b c d e f g.png", that I had outputed to the file. And..... the background changed fine....

Isn't this madness :(

---

### Post by Bachstelze on 2012-05-04
```
bash-3.2$ ls -lh
total 0
-rw-r--r--  1 firas  staff     0B  4 May 01:31 foo bar
bash-3.2$ FILE="\"foo bar\""
bash-3.2$ echo $FILE
"foo bar"
bash-3.2$ ls $FILE
ls: "foo: No such file or directory
ls: bar": No such file or directory
bash-3.2$ FILE="foo bar"
bash-3.2$ echo $FILE
foo bar
bash-3.2$ ls "$FILE"
foo bar

```

---

### Post by emiller12345 on 2012-05-04
> **hakermania said:**
> ```

gsettings set org.gnome.desktop.background picture-uri $quoted

```

I think you might need double quotes around  $quoted

```
gsettings set org.gnome.desktop.background picture-uri "$quoted"
```

---

### Post by Bachstelze on 2012-05-04
> **emiller12345 said:**
> I think you might need double quotes around  $quoted

```
gsettings set org.gnome.desktop.background picture-uri "$quoted"
```

Yes, but not only...

---

### Post by emiller12345 on 2012-05-04
> **Bachstelze said:**
> Yes, but not only...
ah yeah, thats strange, dunno

---

### Post by Bachstelze on 2012-05-04
> **emiller12345 said:**
> ah yeah, thats strange, dunno

Look carefully at what I posted above.

---

### Post by emiller12345 on 2012-05-04
I missed that he had already added quotes in the incorrect place.

```

#!/bin/bash
path="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
#The variable NAUTILUS_SCRIPT_SELECTED_FILE_PATHS comes with an extra " " (space) in the end
#So I need to remove it.
path="${path%?}"
#making the variable as (including the quotes) "file:///path/to/file/a.png"
quoted="file://$path"
#echoing the result so as to see how it went
#echo $quoted > /home/alex/Desktop/asdf
#command to set the background
gsettings set org.gnome.desktop.background picture-uri "$quoted"

```this seems to work okay

---

### Post by hakermania on 2012-05-04
Thanks everybody!

---

