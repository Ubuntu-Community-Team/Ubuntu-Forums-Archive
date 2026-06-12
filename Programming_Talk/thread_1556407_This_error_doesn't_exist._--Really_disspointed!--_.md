---
title: "This error doesn't exist. --Really disspointed!-- --&gt;gconftool-2"
date: 2010-08-19
forum: Programming Talk
---

### Post by hakermania on 2010-08-19
Ok, so the script reads the image from an other file....
The mad thing is that in the script I have:
```
echo $image
gconftool-2 --type string --set /desktop/gnome/background/picture_filename $image
```
And the output is:
```
"/home/alex/Documents/MyCurrentProjects/1176464322_black_045.jpg"
(Then my background turns black (like the image was not found))
(Then the script ends) 
```
Apf....I cannot understand this.. the image does exist and when I write down to the terminal
```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/alex/Documents/MyCurrentProjects/1176464322_black_045.jpg"
``` the Desktop Background changes perfectly.... I am really disappointed...... :(

---

### Post by spjackson on 2010-08-19
> **hakermania said:**
> s:
```
"/home/alex/Documents/MyCurrentProjects/1176464322_black_045.jpg"
(Then my background turns black (like the image was not found))
(Then the script ends) 
```
I take it that you mean that this output comes from echo $image . In that case your problem is the quotation marks, and ls $image would give you an error.

You need to remove the quotation marks, e.g.
```
image=`echo $image | sed 's/^"//
s/"$//'`
```

---

### Post by hakermania on 2010-08-19
I need the " in case the dir has spaces.

---

### Post by MadCow108 on 2010-08-19
the quotations must not be in the variable itself, they must only surround the variable containing the spaces
echo "my dir"
> my dir
is correct
echo "\"my dir\""
> "my dir"
is wrong, other programs will not be able to handle this

remove the quotation marks from the variable and do this:
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$image"
this will handle spaces correctly

---

