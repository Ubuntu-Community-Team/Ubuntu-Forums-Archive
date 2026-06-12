---
title: "How to install Winrar"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-04
I went to download it from here:
[http://www.rarsoft.com/download.htm](http://www.rarsoft.com/download.htm)

And I have absolutely no idea how to install it.

---

### Post by 4t0m1c_w07f on 2008-07-04
You can go System >> Administration >> Synaptic Package Manager
Search rar and install :)

---

### Post by adobrakic on 2008-07-04
What the hell, i've always search for this, but i used "winrar" instead of "rar"

It says it's already installed, i press alt+f2 and typed in "rar" but nothing opened
any idea what's going on? :/

---

### Post by iaculallad on 2008-07-04
Just install unrar, that could handle your rar archives. It's available in the repository:

```
sudo apt-get install unrar
```

Or, you could try peazip. Its available in the repository and could handle numerous compression format.

```
sudo apt-get install peazip
```

---

### Post by adobrakic on 2008-07-04
I have Peazip, but i really dislike it. I'll try unrar if i can't get winrar to work

---

### Post by iaculallad on 2008-07-04
> **adobrakic said:**
> What the hell, i've always search for this, but i used "winrar" instead of "rar"

It says it's already installed, i press alt+f2 and typed in "rar" but nothing opened
any idea what's going on? :/

RAR and UNRAR are terminal commands. What about using the terminal:

```
rar
```

By simply doing this would display available options used by rar.

---

### Post by 4t0m1c_w07f on 2008-07-04
rar runs through the active archive manager. You can just simply open, extract or compile with the standard archive manager.

---

### Post by bhadotia on 2008-07-04
> **adobrakic said:**
> What the hell, i've always search for this, but i used "winrar" instead of "rar"

It says it's already installed, i press alt+f2 and typed in "rar" but nothing opened
any idea what's going on? :/
I  think you should try running it from CLI , I am not in ubuntu , so cannot check for you.

---

### Post by adobrakic on 2008-07-04
ah aite, i see
thanks

---

### Post by erginemr on 2008-07-04
When you follow the directions by @4t0m1c_w07f, rar will be added to the list of formats that file-roller (Gnome's default graphical archive manager), so that you can now create and extract rar files with file-roller.

Alternatively, you can install and use xarchiver, another graphical archive manager. But you also need to install rar from Synaptic first. 

I can also suggest you to use 7-zip as a worthy achive format, which is available in Synapptci under the name "p7zip-full".

---

### Post by Canis familiaris on 2008-07-04
You could always install the windows version of WINRAR in WINE.
But installing RAR in Add/Remove works very well, and you could use the Archive Manager for RAR files.

---

