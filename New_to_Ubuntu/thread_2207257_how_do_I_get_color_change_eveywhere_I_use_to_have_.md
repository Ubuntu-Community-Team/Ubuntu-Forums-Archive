---
title: "how do I get color change eveywhere? I use to have it."
date: 2014-02-22
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-02-22
I use to have black backgrounds with white writing, everywhere on files, rhythmbox, libraoffice. On everything. But had to do a reinstall and lost it. I had changed it 3 4 years ago, but can't remember how I did it or where I found the instructions to do it. Can anyone help?

---

### Post by Habitual on 2014-02-24
a theme perhaps?

---

### Post by ibjsb4 on 2014-02-24
Dconf-editor?
org>gnome>desktop>interface>gtk-color-scheme

```
bg_color:#000000;base_color:#000000;text_color:#FCFCFC
```

Hex colors:
#FCFCFC = white and #000000 = black 

Options:
fg_color
bg_color
text_color
base_color
selected_fg_color
selected_bg_color
tooltip_fg_color
tooltip_bg_color
link_color

But it won't do everything.

---

### Post by EZZ9 on 2014-02-25
I tried this did nothing 
		 				 				 					 				 		 			 				[INDENT] 					Dconf-editor?
org>gnome>desktop>interface>gtk-color-scheme

I should have written it down it was a code or something and it changed everything in one shot. Everything that was white was changed to black & everything that was black was changed to white. It looked like the NASA Night launch theme, but was everything, it was great no white backgrounds killing your eyes. Was like taking a Stylish theme and have it run over everything everywhere. Everyone that saw my computer want it, but I could not remember how I was done, thought it would be a big thing now after all I did it back on Ubuntu 10.04. 
[/INDENT]

---

### Post by EZZ9 on 2014-02-25
I

---

### Post by ibjsb4 on 2014-02-25
Too bad ..

I just wanted a blue background.

[ATTACH=CONFIG]250662[/ATTACH]

---

### Post by vasa1 on 2014-02-25
> **EZZ9 said:**
> I use to have black backgrounds with white writing, everywhere on files, rhythmbox, libraoffice. On everything. But had to do a reinstall and lost it. I had changed it 3 4 years ago, but can't remember how I did it or where I found the instructions to do it. Can anyone help?

See if *sudo apt-get install gnome-accessibility-themes* helps. I think a high contrast theme is part of the package.

---

### Post by EZZ9 on 2014-03-06
I found it "gnome-look themes" and "tweak tool" 
 Take the theme and install it in the tweak tool setting and no more white back rounds, all backgrounds change everywhere, so much nicer on the eyes when you pick a dark backround.

---

