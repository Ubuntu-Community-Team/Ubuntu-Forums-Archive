---
title: "Zenity --radiolist variables"
date: 2012-06-08
forum: Programming Talk
---

### Post by paul_be on 2012-06-08
I was wondering if there was a way to set pre-defined variables as an option in a zentiy radiolist?

```
int="$(zenity --height=275 --list --radiolist --text 'Select the interface to be used:' --column 'Select...' --column 'Interface Name' FALSE '$opt1' FALSE '$opt2' FALSE '$opt3' FALSE '$opt4' FALSE '$opt5' FALSE '$opt6')"
```variables are set higher up in the script, and when this code runs i get a zenity radiolist with option '$opt1' '$opt2' etc, not the variables they are set to.

Any help would be appreciated!

---

### Post by Azdour on 2012-06-08
Hi,

How about:

```

opt1="option1"
opt2="option with spaces"
opt3="1 2 3 4 5 6 7 8 9"
opt4="option 4"
opt5="option 5"
opt6="option 6"
int=`zenity --height=275 --list --radiolist --text 'Select the interface to be used:' --column 'Select...' --column 'Interface Name' FALSE "$opt1" FALSE "$opt2" FALSE "$opt3" FALSE "$opt4" FALSE "$opt5" FALSE "$opt6"`
echo "Chosen option: "$int

```

---

### Post by paul_be on 2012-06-08
Did the trick, thanks a bunch!!!

---

