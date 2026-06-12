---
title: "geany unicode support"
date: 2014-09-22
forum: Programming Talk
---

### Post by justine3 on 2014-09-22
I am trying to translate phpbb to my language. My language is in unicode format. But phpbb is in utf _**without**_ bom. How to add my unicode language to phpbb language file? what changes should I do to geany software to support geany? 

Thanks.

---

### Post by The Cog on 2014-09-22
First, set the encoding to what you want the document saved in. E.g. if you want utf8, from the menu:
Document->Set Encoding->Unicode->utf8

Then set whether or not you want a BOM written at the start of the file. In the Document menu, check or un-check Write Unicode BOM accordingly.

Then save the document.

---

### Post by justine3 on 2014-09-22
When writing unicode with utf font some flow is occuring

---

### Post by The Cog on 2014-09-23
> **justine3 said:**
> When writing unicode with utf font some flow is occuring

I have no idea what that means. Can you explain?

Unicode is a character encoding scheme, relating character shapes (glyphs) to numbers.
UTF8/16 etc are encoding schemes that say how to code the unicode numbers into byte sequences that can be stored in a file.

---

### Post by justine3 on 2014-09-23
Please download the file and place cursor at end of first line. It will go to previous letter. 

[IMG]http://s22.postimg.org/haygp0xup/test.jpg[/IMG]

---

### Post by The Cog on 2014-09-25
Is that file supposed to be containing malayalam characters? like this?
> **&#3361;&#3391;&#3384;&#3400;&#3451; &#3334;&#3451;&#3361;&#3405;* &#3372;&#3391;&#3378;&#3405;&#3361;&#3405; **
If so, then I don't see a problem. If not, what encoding scheme is the file using?

---

### Post by justine3 on 2014-09-25
How to check encoding scheme? 
In the sentence asterisk not needed.
The sentence is in unicode from google transliteration. It gets when typing "design and build"

Thanks.

---

### Post by The Cog on 2014-09-25
I'm really having trouble understanding what your problem is. 
What language are you transliterating from, and what language are you transliterating to with Google? 
Does the file look right to you when you open it in Geany? Is the text the right characters?

---

### Post by justine3 on 2014-09-25
Transliterating from english to malayalam and the file is ok and characters are correctly showing. But as I said in my sthird post when I place the cursor at the end of the line, It shows like it is placed before the last character. You can see the cursor position in the image of my third post. I think you understood me. My english is not good. Sorry for that.

Thanks.

---

### Post by ofnuts on 2014-09-25
It could have nothing to do with encoding and just be caused by incorrect font metrics. Did you try with another font? (your file displays fine with the two KDE editors I have).

Is the  Unicode Character 'ZERO WIDTH NON-JOINER' (U+200C) in the middle intentional? This could be what causes the problem.

Attached a version of the file without the character.

[ATTACH]256682[/ATTACH]

---

### Post by The Cog on 2014-09-25
I couldn't see your screenshot from work - blocked by their proxy. Also, that file doesn't render properly in geany in windows. That's the reason I had trouble understanding your problem earlier.

Now I'm at home, I can see the file properly in geany. However, I don't see your problem with cursor positioning - I can place the cursor at the end of the line without difficulty. 
Some details about my system:
I am using Xubuntu 14.04, not Ubuntu
Geany is using the font Liberation Mono (Regular, size 9)
When I open the file, it automatically chooses a document encoding of Unicode(UTF8), file type PHP source, and line endings LF (Unix). If your choices are different, try changing to these settings and then reloading the file.

There must be some difference between our systems somewhere because mine behaves properly.

---

### Post by justine3 on 2014-09-26
Changing font to Liberation Mono solved the problem. Thanks. I was using Monospace font. Between what is the problem of Monospace font. How to select the proper font for my use and which is error free font in overall? Thanks.

---

### Post by The Cog on 2014-09-27
Ah, thank you for letting me know you found a solution.

Each font carries its own description of how to draw each character - a font is basically a list of such descriptions. It also (somehow, and I don't know the details) describes how large each character is - how far along to move the cursor when a character is displayed.

I suspect that you may have discovered an error in the Monospace font in that it reports the wrong character size for one of the characters, and so from then on the characters on screen are not quite where the program thinks they are. Then it tries to draw the cursor where it thinks the gap between characters is, not where the gap actually is on screen.

I can see your problem if I switch to the Monospace font. And I can see that the spacing in the trailing [/b] is wrong. It changes when the first malay character is inserted in the line. So there is definitely something wrong with the way Monospaced calculates its character sizes. Interesting.

---

### Post by justine3 on 2014-09-30
Thanks for the answer. One more, how to set geany in 'wihout bom'. I know it is in utf8 mode. Cant see option to remove bom.

---

### Post by justine3 on 2014-10-10
Sorry you already answered that in second post.

Thanks.

---

### Post by The Cog on 2014-10-10
And sorry I didn't notice your question - I would have answered.

---

