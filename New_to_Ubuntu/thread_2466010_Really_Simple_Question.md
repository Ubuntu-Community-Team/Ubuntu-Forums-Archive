---
title: "Really Simple Question"
date: 2021-08-17
forum: New to Ubuntu
---

### Post by jackdusty on 2021-08-17
Hi Guys

Really simple question and sorry to be a numpty - been told to delete some files in this folder:-

[COLOR=#000000][FONT=monospace]~/.config/Insync

How do I get there please.

Thanks


Jack[/FONT][/COLOR]

---

### Post by T6&amp;sfpER35% on 2021-08-17
go to your file manager and then press Ctrl+H which will display the hidden folders (folders starting with a dot (.) )

---

### Post by alanthelinuxguy on 2021-08-17
> **jackdusty said:**
> 
[COLOR=#000000][FONT=monospace]~/.config/Insync
How do I get there please.
[/FONT][/COLOR]

As [[COLOR=#000000]3nd[/COLOR]]("https://ubuntuforums.org/member.php?u=2146576")[COLOR=#000000] stated, Ctrl-H in File Manager or, if you want to stick with the GUI, navigate to View - Show Hidden Files.  [/COLOR]

---

### Post by TheFu on 2021-08-17
Keeping it simple, 
```
rm -i ~/.config/Insync/*
```
That will prompt for each file in the directory to be deleted ... or not.

---

### Post by ActionParsnip on 2021-08-18
The period at the start of the name means it is hidden. You can see more hidden files if you compare the output of
```

cd $HOME
ls

```
To
```

ls -a

```

---

