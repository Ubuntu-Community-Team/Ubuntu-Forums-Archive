---
title: "EditPlus Replacement?"
date: 2007-12-05
forum: Programming Talk
---

### Post by HOLOGRAPHICpizza on 2007-12-05
I used to use EditPlus when I had windows, and I can not find a suitable replacement for it, and using it is wine is ugly.

I want a text editor that has
[LIST]
[*]HTML Syntax Highlighting
[*]Little buttons to insert snippets of code for links, images, etc.
[*]Templates that you can start a new file from.
[/LIST]

Do you know of a text editor with these features? Is there a way to have these features in a text editor such as gedit or vim? Mostly I just want buttons I can press to insert snippets of code.

---

### Post by LaRoza on 2007-12-05
Gedit has plugins, but I don't use them, as far as I know. You might want to look into Geany, an IDE.

If what you want works in Wine, use that.

EDIT- I just installed Geany, it has autocompletion for html but no buttons to write the code for you.

---

### Post by Geekkit on 2007-12-05
I think you'll want to check Geany. It's not perfect (i.e., syntax highlighting changes need to be made via the config files in the Geany directory) but it definitely has most of what Editplus has and is quite fast to use.

---

### Post by HOLOGRAPHICpizza on 2007-12-05
I checked our Geany, and it looks really good, but no snippets. Snippets of code are extremely useful. For example, instead of typing out the code for a picture, you can just press the image button and it will insert a generic image tag, and then all you have to do is fill in the blanks, making it a huge time-saver. I guess I will just use editplus in wine, but I was just hoping i could find an actual linux equivalent to it.

---

### Post by wolfbone on 2007-12-05
BlueFish can do that IIRC. 

So can Emacs of course, but I'd guess the culture shock would be too much ;-)

---

### Post by Vadi on 2007-12-05
There's a vi thread started by ThinkBuntu here somewhere, check it out.

---

### Post by Mirge on 2009-05-02
Hi folks,

I know this is resurrecting a pretty old thread, but I ran into this specific thread several times when I was trying to find a GOOD Linux native alternative to Editplus 3.

I really tried to force myself to like Bluefish, Gedit, and a few other editors, but I ended up just using Editplus with Wine until I ran into Geany...

I changed up the syntax highlighting a bit and changed the font to courier new 10pt instead of the default Monospace (editplus uses courier new)... and it actually does MORE than my editplus did for what I needed (PHP).

So for those who happen to run into this thread on a quest for an Editplus alternative like I did, I encourage you to try Geany... use your synaptic package manager & search Geany.

---

### Post by Vadi on 2009-05-02
+1 for Geany... switched to it from wine+notepad++

---

### Post by DocForbin on 2009-05-02
Geany is very nice and lightweight. The find in files is similar to editplus, which is easily the feature I use editplus most for on windows.

Mirge, if you haven't tried it, the current Netbeans is excellent for PHP too. I never used it for anything but Java til recently. Now I use it for PHP, Javascript, and CSS, and it's very comfortable (but it's a massive IDE, I still prefer geany for quick edits).

---

### Post by Mirge on 2009-05-02
Hey cool I will check out Netbeans too :).

One thing I just ran into with Geany that I couldn't find, but I used frequently in Editplus...

keystroke recording/playback (macro?).

Is that functionality in Geany anywhere? Via plugin form maybe?

I'd like the ability to record keystroke & bind it to a certain key for playback, control+Q in Editplus if you're familiar with it.

Thanks in advance!

---

### Post by Vadi on 2009-05-02
That's not present in geany

---

### Post by Mirge on 2009-05-02
Oh bummer... Geany was perfect for me otherwise. Maybe I can find some sort of add-on or work-around for it.

EDIT: Well I looked around, but didn't find anything. I emailed one of the developers listed on their web-site to put in a plugin request, but even without this feature it's still a fantastic editor. Two thumbs up for Geany from me! And to this forum! You guys are great!

---

### Post by Matty_pants on 2011-05-19
Gleany is nice and lightweight, but doesn't have an internal browser preview - a dealbreaker for me.

I have yet to find a n editor/ide for linux that has this feature :(

---

### Post by cgroza on 2011-05-19
> **Matty_pants said:**
> Gleany is nice and lightweight, but doesn't have an internal browser preview - a dealbreaker for me.

I have yet to find a n editor/ide for linux that has this feature :(
Yes, but it launches the default browser instead, which for me, is far more superior.

---

### Post by Petrolea on 2011-05-20
Geany also has an interesting function that autocompletes the tags.

Lets say you typed <b> - it will get automatically completed to <b></b> and you can continue writing between the tags. This also works over a whole line or even more lines:

<b> LaLALALA 
<b> LaLALALAlalaa aaka </
autocomplete to: <b> LaLALALAlalaa aaka </b>

It works for nested tags too. This is the function I just love about Geany.

---

