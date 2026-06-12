---
title: "HOWTO: Change nautilus sidebar icon size"
date: 2007-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Laterix on 2007-09-12
This is just a little mod that allows you to change Nautilus file manager's Places sidebar icon size. See modified Nautilus screenshot below. This guide is **tested only with Feisty Fawn**!

[[IMG]http://www.aijaa.com/img/00094/963377.t.png[/IMG]](http://www.aijaa.com/v.php?i=963377.png)

**STEP 1. Get source and install needed dependencies**
Get nautilus source
```
apt-get source nautilus
```
Install needed dependencies (these are needed for compiling)
```
sudo apt-get build-dep nautilus
```

**STEP 2. Edit Nautilus source**
Move to nautilus source directory
```
cd nautilus-2.18.1/src
```
Open source code file with Gedit
```
gedit nautilus-places-sidebar.c
```
Line 191 should look like this **(In Gutsy it's line 200)**:
```
pixbuf = nautilus_icon_factory_get_pixbuf_from_name_with_stock_size (icon, NULL, GTK_ICON_SIZE_MENU, NULL);
```
Change that line to:
```
pixbuf = nautilus_icon_factory_get_pixbuf_from_name_with_stock_size (icon, NULL, 5, NULL);
```
Save changes and close editor.

**STEP 3. Compile and install**
Move to nautilus source root (this dir contains *configure* file)
```
cd..
```
Then configure, compile, install
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```

**STEP 4. Restart X**
You might need to restart X, before changes occur.

[COLOR="Red"]**UNINSTALL**[/COLOR]
You should be able to uninstall this simply by reinstalling nautilus package with Synaptic

---

### Post by Rusna on 2007-09-13
Thanks!

---

### Post by Yuzem on 2008-01-21
Thanks!

I have one question.
Do you know how to remove the sidebar selection thing.
It takes room it is ugly and I only use places anyway.

I mean to make it look like this:
[[IMG]http://www.aijaa.com/img/t/00026/1483651.t.png[/IMG]](http://www.aijaa.com/v.php?i=1483651.png)

I think that "nautilus-side-pane.c" must be edited but I don't know what to edit.

---

### Post by Laterix on 2008-03-16
> **Yuzem said:**
> Thanks!

I have one question.
Do you know how to remove the sidebar selection thing.
It takes room it is ugly and I only use places anyway.

I mean to make it look like this:
[[IMG]http://www.aijaa.com/img/t/00026/1483651.t.png[/IMG]](http://www.aijaa.com/v.php?i=1483651.png)

I think that "nautilus-side-pane.c" must be edited but I don't know what to edit.
This answer took two months. :) The answer is that I don't know, but I will look into this. I would like achive the same thing as you.

---

### Post by Laterix on 2008-03-16
I managed to remove that Dropdown menu from nautilus sidebar. It was quite easy after all. Just comment out one line of code.

Open **nautilus-side-pane.c** and comment out line 331 (in Gutsy). So the line should look like this after modification:
```

//gtk_box_pack_start (GTK_BOX (side_pane), frame, FALSE, FALSE, 0);

```

[[IMG]http://www.aijaa.com/img/t/00623/1765811.t.png[/IMG]](http://www.aijaa.com/v.php?i=1765811.png)

---

### Post by Yuzem on 2008-03-16
Wow, thanks a lot. Better later than never. :)
I never liked that drop down menu on the sidebar.

Now, I am having one little problem, when I run this command:
```
sudo apt-get build-dep nautilus
```
I get:
```
E: No se pudieron satisfacer las dependencias de construcción de nautilus.
```
Which means something like: The build dependencies for nautilus could not been satisfied.
I am running Gutsy, any ideas?

---

### Post by Laterix on 2008-03-16
> **Yuzem said:**
> 
Which means something like: The build dependencies for nautilus could not been satisfied.
I am running Gutsy, any ideas?
Hmm... have you enabled source repositories? Synaptic -> Settings -> Repositories -> Source Code (Does it have tick?) There should be no problems with downloading dependencies if all repositories are set.

---

### Post by Yuzem on 2008-03-16
Yes, source code is enabled.
I found the problem:
[http://ubuntuforums.org/showthread.php?t=204922](http://ubuntuforums.org/showthread.php?t=204922)

I have the mac menu hack installed with a fake version number to not be overwritten every time by updates. I think that is the cause of my problem.

Thanks again. :)

---

### Post by svtfmook on 2008-03-16
i get
bash: cd: nautilus-2.18.1/src: No such file or directory

when i try to cd

---

### Post by Yuzem on 2008-03-16
On Gutsy it is:
```
cd nautilus-2.20.0/src
```

---

### Post by MyKal on 2008-05-05
anyone get this working on hardy???

i have gotton as far as editing the nautilus-places-sidebar.c file but none of the lines you have mentioned here are present in it

i am trying to make the icons bigger and get rid of the little box to change veiws in and i cant find either of the lines in the file that  need to change

---

### Post by BilliShere on 2008-05-13
your best luck would be to use thunar file manager... it has a expandible sidebar and is a lot more customizable.

---

### Post by Superevil on 2008-05-22
I get as far as changing the source code and once I get the the cd.. command

```
calvin@superevil:~/nautilus-2.20.0/src$ cd..
```
```
bash: cd..: command not found
```

now am I supposed to be in ~/nautilus-2.20.0 or in ~/nautilus-2.20.0/src when i run the cd.. command? I've tried running ./configure --prefix=/usr in both and it tells me no such directory which obviously is because I've done something wrong somewhere and I just can't figure out where. And I'm usuing Gutsy BTW so I know it's 2.20.0

---

### Post by bigbrovar on 2008-05-22
> **MyKal said:**
> anyone get this working on hardy???

i have gotton as far as editing the nautilus-places-sidebar.c file but none of the lines you have mentioned here are present in it

i am trying to make the icons bigger and get rid of the little box to change veiws in and i cant find either of the lines in the file that  need to change

+1

tried it too but i dont know how this can be done on hardy .. the codes seem to hav be rewritten .

---

### Post by BlueSkyNIS on 2008-05-22
you should type **cd ..** (space inserted between) NOT **cd..**

---

### Post by ixlam on 2008-06-19
Looking at this in Hardy (nautilus-2.22.3 )and also not sure of what to change although it looks like it would be somewhere in and about line 207 - 224 (perhaps)

```

	icon_size = nautilus_get_icon_size_for_stock_size (GTK_ICON_SIZE_MENU);
	icon_info = nautilus_icon_info_lookup (icon, icon_size);

	pixbuf = nautilus_icon_info_get_pixbuf_at_size (icon_info, icon_size);
	g_object_unref (icon_info);
	gtk_list_store_append (sidebar->store, &iter);
	gtk_list_store_set (sidebar->store, &iter,
			    PLACES_SIDEBAR_COLUMN_ICON, pixbuf,
			    PLACES_SIDEBAR_COLUMN_NAME, name,
			    PLACES_SIDEBAR_COLUMN_URI, uri,
			    PLACES_SIDEBAR_COLUMN_DRIVE, drive,
			    PLACES_SIDEBAR_COLUMN_VOLUME, volume,
			    PLACES_SIDEBAR_COLUMN_MOUNT, mount,
			    PLACES_SIDEBAR_COLUMN_ROW_TYPE, place_type,
			    PLACES_SIDEBAR_COLUMN_INDEX, index,
			    -1);
	if (pixbuf != NULL) {
		g_object_unref (pixbuf);

```

Anyone ??

---

### Post by RodrigoJol on 2008-09-19
Same problem, in nautiluis-2.22.3 i don't know where to make the cheanges or haow to make it... does anybody solved that already??

thanks

---

### Post by elusive on 2009-02-06
hi @all

i found the solution for Gnome 2.24.1. The part, which ixlam posted is the right part. Just replace:
```

icon_size = nautilus_get_icon_size_for_stock_size (GTK_ICON_SIZE_MENU);
```

with:

```
icon_size = 24;
```

or whatever pixelsize you like.

---

