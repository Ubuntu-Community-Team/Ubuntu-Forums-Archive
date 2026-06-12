---
title: "[SOLVED] Trying to Write a &amp;quot;tick&amp;quot; symbol"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Andavane on 2008-08-29
Hello

A friend & I have phone chats where we work on a "Google Docs" file, and we want to be able to write a "tick" symbol.

In the document you go "insert/special character/advance" then type in the unicode symbol;
because of the thousands of combinations I assumed that there would be a combo one could use as a "tick", as I thought Linux would have everything.

I searched far and wide on google and found lots of other people trying to get ticks as well.

I realise this may not be an ubuntu things as such, but as I can't find an answer elsewhere, I'd thought I'd try here.

Regards

John

---

### Post by squaregoldfish on 2008-08-29
The unicode code for a basic tick mark is U+2713. See the [Wikipedia page]("http://en.wikipedia.org/wiki/Check_(mark)").

Steve.

---

### Post by Andavane on 2008-08-30
> **squaregoldfish said:**
> The unicode code for a basic tick mark is U+2713. See the [Wikipedia page]("http://en.wikipedia.org/wiki/Check_(mark)").

Steve.
Many thanks dear friend,
This has saved many hours' frustration and hair pulling.
I just have a residual query:

Does "U+2713" mean I have to type "U" then "2713"? Somehow I still can't get the symbol to appear.

In Google docs I had actually to type "0x2713" and then the tick symbol appeared as desired.

Kind regards

John

---

### Post by airtonix on 2008-08-30
This has also baffled me, on windows you could hold the left alt key and type numbers on the numpad to produce these 'extra' characters.

Is there such a key combination for gnome?

---

### Post by Vivaldi Gloria on 2008-08-30
&#10003;

Try copying that.

In gedit I can do

<Ctrl><Shift><u><Unicode number><Enter>

to get unicode characters.

In google docs try Andavane's method above.

---

### Post by Rhubarb on 2008-08-30
Hold down ctrl + shift, then type in: u 2 7 1 3, then release ctrl + shift.

---

### Post by Andavane on 2008-08-30
> **airtonix said:**
> This has also baffled me, on windows you could hold the left alt key and type numbers on the numpad to produce these 'extra' characters.

Is there such a key combination for gnome?

Indeed, easy to hold down the 'alt' key and type in the number.
I've never been able to figure out what the "U+" is, and what you're supposed to do.

John

---

### Post by Rhubarb on 2008-08-31
> **Andavane said:**
> I've never been able to figure out what the "U+" is, and what you're supposed to do.
The "U" part stands for Unicode.
If you open up the Character Map (Applications --> Accessories --> Character Map), you can search for the character, and find out it's unicode number.
There are far more characters you can use by key combinations in Ubuntu, due to the fact you can refer to any unicode characters you like.
For example you can output to Braille &#10269;, Tamil &#3058;, Thai &#3596;, or even Canadian Aboriginal &#5549;.

---

### Post by Andavane on 2008-08-31
> **Rhubarb said:**
> Hold down ctrl + shift, then type in: u 2 7 1 3, then release ctrl + shift. 
mmm, I remembered: I've been here before.
Unfortunately this doesn't work on my keyboard (in Open Office) which is  a little Cherry ML4100.
I bought it because I have physically limited reach.
It's a small keyboard just under 28 cm in width & 12.5 cm depth.
I guess this is something to do with it.

Regards

John

---

### Post by Andavane on 2008-08-31
> **Vivaldi Gloria said:**
> &#10003;

Try copying that.

In gedit I can do

<Ctrl><Shift><u><Unicode number><Enter>

to get unicode characters.

In google docs try Andavane's method above.
Aha Vivaldi!
This works on my little keyboard (see my response to rhubarb);
the only difference is that when I type nothing happens, but when I release
ctr-shift the tick appears! :)

Regards

John

---

### Post by airtonix on 2008-08-31
Cheers, that is the behaviour I was seeking.

---

### Post by Rhubarb on 2008-08-31
If you commonly use a few / several special characters, it may be of benefit to you to add a "Character Palette" to your panel.
-This way you don't have to remember or type the complex key combination 

Right click on an empty part on one of your panels (up the top or down the bottom of the screen somewhere), Select "Add to Panel...".
Select "Character Palette", and press the  "+ Add" button.
To configure your new Character Palette, right click on it, and go to "Preferences".
From there you can select several pre-set palettes, or you can create your own.

To use the Character Palette, click on the character you wish to copy into the clipboard, then you may paste it into your application by pressing the middle mouse button, or Ctrl + V, or via the Edit Menu.

---

### Post by Andavane on 2008-08-31
> **Rhubarb said:**
> If you commonly use a few / several special characters, it may be of benefit to you to add a "Character Palette" to your panel.
-This way you don't have to remember or type the complex key combination 

Right click on an empty part on one of your panels (up the top or down the bottom of the screen somewhere), Select "Add to Panel...".
Select "Character Palette", and press the  "+ Add" button.
To configure your new Character Palette, right click on it, and go to "Preferences".
From there you can select several pre-set palettes, or you can create your own.

To use the Character Palette, click on the character you wish to copy into the clipboard, then you may paste it into your application by pressing the middle mouse button, or Ctrl + V, or via the Edit Menu.

Yes I use the character palette with great frequency. However it doesn't have a tick in it, AND I never knew that you could create your own. Not sure how you do that!

Regards

John

---

### Post by Rhubarb on 2008-08-31
Please refer to the Pictures at the bottom of this post for your reference:

1) Open up the Character Palette Preferences
Press the "Add" Button

2) This is where you enter in your Palette

3) Copy all the characters you need to use for your own palette

4) Paste them into the Add Palette box
Press "Ok"

5) Your new palette should appear in the Character Palette Preferences

...(continued next post, due to a 5 attached photo limit)...

---

### Post by Rhubarb on 2008-08-31
6) Push the hat symbol that appears at the bottom left of the character palette, and select your new character palette that you just created.

7) Your new character palette is ready to use!

---

### Post by Vivaldi Gloria on 2008-08-31
Good method Rhubarb. Thanks.

---

