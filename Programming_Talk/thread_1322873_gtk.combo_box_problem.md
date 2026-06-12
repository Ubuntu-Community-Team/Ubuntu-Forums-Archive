---
title: "gtk.combo_box problem"
date: 2009-11-11
forum: Programming Talk
---

### Post by Sandsound on 2009-11-11
Hi all

I'm working on a python-frontend to the grub2 theme-file, I call it [grub2l]("http://www.sandgreen.dk/index.php?side=python_grub2l") (or just grubtool).

I have a combobox where you can select the font-color, and when the program is loaded, I do a :
```
combobox.append_text(color_from_theme_file + "(Current)")
```

I would like this item to be non-selectable, I was thinking something simple like set_sensitive(False), but cant figure out how to do this ?

It is of course not all the items in the combobox that I want to be non-selectable (or grayed out), just the color loaded from the theme-file.

---

### Post by Sandsound on 2009-11-11
I have made a rather clumsy solution to my problem :redface:
```
if color_normal == 'black':
	normal_combobox.set_active(0)
if color_normal == 'blue':
	normal_combobox.set_active(1)
if color_normal == 'brown':
	normal_combobox.set_active(2)
if color_normal == 'cyan':
	normal_combobox.set_active(3)
if color_normal == 'dark-gray':
	normal_combobox.set_active(4)
if color_normal == 'green':
	normal_combobox.set_active(5)
if color_normal == 'light-cyan':
	normal_combobox.set_active(6)
if color_normal == 'light-blue':
	normal_combobox.set_active(7)
if color_normal == 'light-green':
	normal_combobox.set_active(8)
if color_normal == 'light-gray':
	normal_combobox.set_active(9)
if color_normal == 'magenta':
	normal_combobox.set_active(10)
if color_normal == 'red':
	normal_combobox.set_active(11)
if color_normal == 'white':
	normal_combobox.set_active(12)
if color_normal == 'yellow':
	normal_combobox.set_active(13)
```
("color_normal" is the font-color I read in the theme-file)

I'm sure that this can be done more efficiently, something like :

```
for x in range(0, 13):
	if color_normal == normal_combobox.get_text(x):
		normal_1_combobox.set_active(x)
```
But there's no combobox.get_text(x) ](*,) or is there ?

---

