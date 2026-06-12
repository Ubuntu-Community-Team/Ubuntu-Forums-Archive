---
title: "Web designer. *Word Wrap*"
date: 2006-03-26
forum: Programming Talk
---

### Post by shigs on 2006-03-26
I'll explain my plight then you can mock and/or help me.

I have this website yeh, well yeh thing is yeh, that i wrote this news script for it yeh. Anyway if i pass really long words into a P tag in a div, It completly f**ks up the design(It will either expand the Div it is in thus making the site go nuts, or it will dissapear into a void behind the next div).

I spent ages making a word wrap function in PHP but then realised it only works for monospace fonts, if you use a truetype, variable length font the whole thing looks stupid.

"word-wrap:break-word" is a bit of non standard CSS that works but only works in IE, and as its not standard CSS I can't use it anyway.

Ideas on a postcard?

---

### Post by shigs on 2006-03-26
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaahhhhhhhhhh

---

### Post by shigs on 2006-03-26
^ That is similar to what i have at the moment but i dont like the breaks in the middle of the lines.

---

### Post by LordHunter317 on 2006-03-26
If the width of your DIV is correctly fixed then your text should wrap automatically just fine.  If it's not, you're generating invalid HTML or your CSS is wrong.  POsting some of the generated code or hell even a link to your site would be helpful.

---

### Post by wmcbrine on 2006-03-26
[QUOTE=shigs]^ That is similar to what i have at the moment but i dont like the breaks in the middle of the lines.[/QUOTE]
Ah, for a moment there I thought it was just a scream of frustration. :)

---

### Post by shawnhcorey on 2006-03-26
Obviously, your DIV is too small; make it wider. Most English words can fit into a reasonable-sized column.

You could also try inserting soft hyphens, &shy; into the word before you send it off but some older browsers do respond to it.

sc

---

### Post by shigs on 2006-03-26
The Width of the DIV and the P tag is specified and it validates to xHTML strict and the css validates.

It does wrap correctly apart from if i put something dumb in or a long URL. I've found a few blogg type articles about it and they suggested Javascript, so i made a javascript workwrap function or two but they work in the same way as my PHP. i.e. They'll only work with fixed length fonts and amounts of characters per line. Not Pixels and variable length fonts which i need.

Surely theres a trick of the trade or something?

---

### Post by shawnhcorey on 2006-03-26
[QUOTE=shigs]Surely theres a trick of the trade or something?[/QUOTE]

Yes, it's call Fluid Design or Liquid Design or Dynamic Design.

Things like really long URLs should only appear in your main content column, and it should be at 50% the width of your window. Most URLs are set as links and if your readers want the link, they can right-click on it and "Copy link location".

As I said, you can try a soft hyphen, '&shy;'. Try writing a routine that inserts into your URLs after any slash, question mark, or ampersand. That usually has enough breaks so it doesn't extend beyond the column too often.

A soft hyphen is a place where the browser may break a word if needed. It is invisible.

sc

---

### Post by shigs on 2006-03-27
Thanks for the tip man xx that actually sounds like a pretty simple thing to do as well. I'll knock something up when ive got the time.

---

