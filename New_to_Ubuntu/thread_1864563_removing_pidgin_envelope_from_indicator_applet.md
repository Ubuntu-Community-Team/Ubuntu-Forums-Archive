---
title: "removing pidgin envelope from indicator applet"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by manuleka on 2011-10-19
i'm running xubuntu 11.10 and i'm wondering if someone can tell me how to remove the envelope icon from the indicator applet?

and also how do i add icons to the bottom quick launch set of icons

xubuntu it pretty slick

---

### Post by gsmanners on 2011-10-19
I think this can do what you want:

```
sudo apt-get remove indicator-messages
```

You may have to remove a couple other packages, as well. I forget.

---

### Post by manuleka on 2011-10-19
thanks for the prompt response, yes i just want to remove the envelope icon... i'm sure it shouldn't be too hard, just couldn't find any info on googling about approaching this

cheers

---

### Post by manuleka on 2011-10-19
remove envelope icone
```
sudo apt-get remove indicator-messages
```

add icons to bottom quick launch panel
```

- right click on panel
- go to panel
- click panel preference
- go to items tab
- add new item
- select Launcher.- Program laucher
- a new empty icon appears on panel
- right click empty icon
- go to properties
- click add item to launcher
- this will bring available applications to choose from

```

---

### Post by bford16 on 2011-10-20
Also, you can click on the Search icon (in the bottom panel), find your application there, and drag it to the panel.  Once you've dragged it there, you can move it to where you want it.

---

### Post by manuleka on 2011-10-21
im using xubuntu and can't see search

---

### Post by gsmanners on 2011-10-21
The "search" in Xfce is called Application Finder (in your Accessories menu).

---

