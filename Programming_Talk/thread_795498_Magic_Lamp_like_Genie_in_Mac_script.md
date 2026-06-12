---
title: "Magic Lamp like Genie in Mac script"
date: 2008-05-15
forum: Programming Talk
---

### Post by anotherdisciple on 2008-05-15
I used [[COLOR="RoyalBlue"]this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=557491&highlight=genie") to change the magic lamp effect in compiz fusion.

I was just wondering... is there any way I could write a script that changes the <min>3</min> in /usr/lib/compiz/libanimation.so to <min>0</min> ? 

It would have to install ghex2... which I would assume is just

sudo aptitude install ghex2

then it would have to open ghex2 and do some kind of replace command... it would probably start like this...

sudo ghex2 /usr/lib/compiz/libanimation.so

but I don't know where to go from there... can anyone help?

---

### Post by slavik on 2008-05-15
> **anotherdisciple said:**
> I used [[COLOR="RoyalBlue"]this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=557491&highlight=genie") to change the magic lamp effect in compiz fusion.

I was just wondering... is there any way I could write a script that changes the <min>3</min> in /usr/lib/compiz/libanimation.so to <min>0</min> ? 

It would have to install ghex2... which I would assume is just

sudo aptitude install ghex2

then it would have to open ghex2 and do some kind of replace command... it would probably start like this...

sudo ghex2 /usr/lib/compiz/libanimation.so

but I don't know where to go from there... can anyone help?

you can easily write a C program to do this.

---

### Post by anotherdisciple on 2008-05-16
And how might I learn how to do that?

---

### Post by anotherdisciple on 2008-05-19
can anyone help me?

---

### Post by pencilcheck on 2008-05-19
Calm down man.
Use Bless Hex Editor.
It's in the repo. :)

---

### Post by Can+~ on 2008-05-19
[COLOR="DarkRed"]**ANYONE READING THIS:**

If you came here looking for a script, don't run this one! I recently updated to Hardy Heron, rechecked the position of the desired string, and it has moved! It's not a good idea to run this as it will replace a random character with a 0 : Better method would be to actually search for the full string on the file.[/COLOR]


Ok, so I went to ghex2 and found the place of the thing, if you go look for the exact place in the file, you can find the OFFSET on the bottom left corner:

[IMG]http://img.photobucket.com/albums/v517/CanXp/python/screenshot1.png[/IMG]

offset: 1B588.

Therefore, now I have the exact position of the byte I need, so it's just a matter of a little python script (tested on a copied file on my home):

[PHP]try:
	f = open(r"libanimation.so", "rb")
	
	#Move the file pointer to the given offset.
	f.seek(0x1B588)
	
	#Read 1 byte
	print f.read(1)
	
except IOError:
	print "Error loading file!"

finally:
	f.close()[/PHP]

It prints a nice 0. Exactly the same thing I got there (if I edit to "5" in ghex2, and then recheck, it's still the same). So just replacing the rb to r+b and writing just a single byte there would do it.

*edit*: Ok, I couldn't resist, I had to do it:

[PHP]try:
	#Open file on read+write bianry mode.
	f = open(r"libanimation.so", "r+b")
	
	#Move the file pointer to the cursor.
	f.seek(0x1B588)
	
	#write a 0.
	print f.write('0')
	
except IOError:
	print "Error loading file!"

finally:
	f.close()[/PHP]

I would use this with care, probably, a different version of this file could move the position of that single byte to another place, but it's more like of an idea, that you can, instead of opening a certain application and doing something, edit the file by yourself. Opening a hexadecimal file is opening just like a binary.

---

