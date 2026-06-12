---
title: "How to improve fonts in Firefox 3.5"
date: 2009-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Raffles10 on 2009-12-10
If like me you're fed up with the fonts in Firefox looking fuzzy and horrible compared to the rest of your beautiful Ubuntu desktop, this should make a pleasing difference.

Open Gedit, copy & paste:
> <?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" >
<const>rgb</const>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hinting" >
<bool>true</bool>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hintstyle" >
<const>hintfull</const>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="antialias" >
<bool>true</bool>
</edit>
</match>
</fontconfig>

This file must be saved as a hidden file in your home directory, so save as ~/.fonts.conf

Restart Firefox. :P

---

### Post by jpeddicord on 2009-12-13
[s]Moved to Desktop Environments (from Tutorials & Tips) since it is really just a config file. :)[/s]

Scratch this, see my post below.

Jacob

---

### Post by jpeddicord on 2009-12-13
Moved to Desktop Environments (from Tutorials & Tips) since it is really just a config file. :)

Jacob

---

### Post by Raffles10 on 2009-12-13
So it's not a tip then.......whatever.

---

### Post by jpeddicord on 2009-12-13
On second thought, I'm going to move this back and approve. I was confusing your config file as a "do-everything-for-me" script, though it appears it is not. Thanks and sorry for the confusion! :)

---

### Post by ron999 on 2009-12-13
@Raffles10
Well, the file does make the fonts look different.
How do we reset them to the previous look?

---

### Post by wojox on 2009-12-13
Probably just delete the new file you created.

---

### Post by Can+~ on 2009-12-13
This is my fonts.conf:

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

Fonts larger than 15 are anti-aliased (14 for bold), the rest is left without anti-alias.

Any thoughts?

---

### Post by ron999 on 2009-12-14
> **Can+~ said:**
> 

Any thoughts?

Well, I've tried your file and also the Raffles10 file and some others I've found online (Google **fonts.conf**).
I can see that they all make my fonts appear differently.
But I don't think that they are an improvement.
That's just my opinion.
:biggrin:

---

### Post by timseal on 2009-12-14
Two questions: 
 Why would this only affect Firefox? 
 Doesn't the best hinting style differ depending on the type of display?

-tim

---

