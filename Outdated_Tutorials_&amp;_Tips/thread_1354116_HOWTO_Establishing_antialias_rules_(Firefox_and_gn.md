---
title: "HOWTO: Establishing antialias rules (Firefox and gnome)"
date: 2009-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Can+~ on 2009-12-13
[SIZE="5"]Why do this?[/SIZE]
After installing karmic and firing up firefox for the first time, I noticed a serious problem with the fonts. I like having small fonts without antialias, while big fonts (titles and bold) aliased. Something like:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-6.png[/IMG]

The h1 title is aliased with RGB hintfull, while the body font isn't aliased at all. If you consider that the body font should be aliased too, then it's just a matter of tweaking the pixelsize in the following config file. (Also, I made a lot of tweaks after uploading this image, so don't expect the same results)

[SIZE="5"]Building the font config[/SIZE]
To create these "rules", first a file named [FONT="Courier New"].fonts.conf[/FONT] (notice the dot, it means hidden file, obviously, use nautilus with "show hidden files") must be created in your home directory. Copy and paste this if you are too lazy to open nautilus, Alt+F2 for quick launch and copy:

```
gedit ~/.fonts.conf
```

Now, with gedit opened, copy and paste this inside.

[HTML]<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
	<!-- See: man 5 fonts-conf -->
	<!-- Antialias rules -->
	<match target="font">
	
		<!--Subpixel smoothing: rgb, bgr, vrgb, vbgr, none-->
		<edit mode="assign" name="rgba"><const>none</const></edit>
		
		<!-- Use hint? true/false. Usually true-->
		<edit mode="assign" name="hinting"><bool>true</bool></edit>
		
		<!-- Hint: hintfull, hintmedium, hintslight, hintnone -->
		<edit mode="assign" name="hintstyle"><const>hintmedium</const></edit>
		
		<!-- By default, apply antialias to all, filter on the following lines -->
		<edit mode="assign" name="antialias"><bool>true</bool></edit>
	</match>
	
	<!-- If fonts are smaller than X, then don't antialias-->
   	<match target="font">
		<test compare="less" name="size" qual="any">
			<int>15</int>
		</test>
		<edit mode="assign" name="antialias">
			<bool>false</bool>
		</edit>
	</match>
	
	<!-- If BOLD fonts are smaller than Y, then don't antialias-->
	<match target="font">
		<test compare="more_eq" name="weight" qual="any">
			<const>medium</const>
		</test>
		<test compare="less" name="size" qual="any">
			<int>13</int>
		</test>
		<edit mode="assign" name="antialias">
			<bool>false</bool>
		</edit>
	</match>
	
	<!-- Firefox fix (it uses pixelsize, instead of size) -->
	<match target="font">
		<test compare="less" name="pixelsize" qual="any">
			<int>15</int>
		</test>
		<edit name="antialias" mode="assign">
			<bool>false</bool>
		</edit>
	</match>
	
	<!-- Firefox fix BOLD (it uses pixelsize, instead of size) -->
	<match target="font">
		<test compare="more_eq" name="weight" qual="any">
			<const>medium</const>
		</test>
		<test compare="less" name="pixelsize" qual="any">
			<int>13</int>
		</test>
		<edit name="antialias" mode="assign">
			<bool>false</bool>
		</edit>
	</match>
</fontconfig>[/HTML]

Now, save. Wait a few seconds, and you'll notice that gnome will lag for a second. Just to make sure that X picked up the changes, rebuild the font cache:

```
fc-cache -fv
```

When this finishes, you can freely modify the file and gnome will pick up the changes (usually, three seconds after saving the file). (If you still don't see any changes, make sure to have everything right, and restart X, or just restart your computer)


[SIZE="5"]Tweaking the file[/SIZE]
[SIZE="4"]Antialias settings[/SIZE]

First of all, I recommend opening nautilus, and zooming in to have big fonts. Firefox requires restarting to check the changes, so it can become cumbersome to restart firefox each time you want to see what you're doing. Nautilus, on the other hand, it reloads the configuration each time you save (along with the rest of gnome).

The one posted above, works fine for me, if you want to change how aliased looks, then modify the first <match> configuration:

[HTML]	<!-- Antialias rules -->
	<match target="font">
	
		<!--Subpixel smoothing: rgb, bgr, vrgb, vbgr, none-->
		<edit mode="assign" name="rgba"><const>none</const></edit>
		
		<!-- Use hint? true/false. Usually true-->
		<edit mode="assign" name="hinting"><bool>true</bool></edit>
		
		<!-- Hint: hintfull, hintmedium, hintslight, hintnone -->
		<edit mode="assign" name="hintstyle"><const>hintmedium</const></edit>
		
		<!-- By default, apply antialias to all, filter on the following lines -->
		<edit mode="assign" name="antialias"><bool>true</bool></edit>
	</match>[/HTML]

Using "none" in rgba, implies that it will use grayscale smoothing, on the other hand, any other (rgb, bgr ...) will break down the smoothing into red-green-blue (or different orders, or vertical), here's a comparison between RGB and grayscale:

[Click here](http://img.photobucket.com/albums/v517/CanXp/screenshot5.png)

And try hinting until you like it.

[SIZE="4"]Size configuration[/SIZE]

After the aliasing is right, make sure sizes are ok. There are two sections in the xml, first:

[HTML]	<!-- If fonts are smaller than X, then don't antialias-->
        ...
	<!-- If BOLD fonts are smaller than Y, then don't antialias-->[/HTML]

Specifies the rules for most of the gnome applications, one for normal fonts, and one for bold fonts. Immediatley after, it comes the firefox section (it uses pixelsize instead of size), also with normal and bold.

Each one of this, has:

Conditions:
[HTML]<test compare="less" name="size" qual="any">
	<int>15</int>
</test>[/HTML]

And rules:
[HTML]<edit mode="assign" name="antialias">
	<bool>false</bool>
</edit>[/HTML]

So the above piece, inside the <match> block, means that, if the condition is met, then apply the rule. In this case, *"if size is less than 15, then turn off antialias"*.

With this in mind, it's easy to make changes, if you want to have fonts smaller than 10 and everything else with anti alias, then do this inside the text block:

[HTML]<int>10</int>[/HTML]

In the case of the firefox specific settings (pixelsize), you'll need to restart firefox each time. Although, I think my configuration is pretty much spot on. I tried it on google, digg, endgadet and arstechnica and it certainly matches most of the cases.

To add more conditions and rules, see the "Sources" section.

[SIZE="5"]Test suit[/SIZE]

Here are some different sized texts to try:

[CENTER]
[SIZE="7"]Huge | **Huge**[/SIZE]
[SIZE="6"]Very Big | **Very Big**[/SIZE]
[SIZE="5"]Bigger | **Bigger**[/SIZE]
[SIZE="4"]Big | **Big**[/SIZE]
[SIZE="3"]Slightly Big | **Slightly Big**[/SIZE]
[SIZE="2"]Normal | **Normal**[/SIZE]
[SIZE="1"]Small | **Small**[/SIZE]
[/CENTER]

[SIZE="5"]Sources[/SIZE]

[LIST]
[*]man fonts-conf
[*][Arch Font configuration manual]("http://wiki.archlinux.org/index.php/Font_Configuration")
[/LIST]

---

### Post by jpeddicord on 2009-12-13
Complete tutorial for something as intricate as font smoothing. Approved, and thank you for your Tutorials & Tips contribution!

---

