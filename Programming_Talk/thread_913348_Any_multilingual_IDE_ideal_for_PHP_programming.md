---
title: "Any multilingual IDE ideal for PHP programming?"
date: 2008-09-07
forum: Programming Talk
---

### Post by japtar10101 on 2008-09-07
I found out that both Eclipse and jEdit, two IDE I use the most, does not support Japanese.  I prefer to have an editor similar to both IDE, that also supports Japanese characters to program a half-Japanese website.  What would you suggest?

Note I use Ubuntu, so a Gnome IDE would be ideal.

Thank you!

---

### Post by ad_267 on 2008-09-07
What do you mean by supporting Japanese? Doesn't that just depend on the encoding of the text file? You probably need it to be UTF-8 if you have English and Japanese characters. Anyways I found geany pretty good for php.

---

### Post by japtar10101 on 2008-09-07
> **ad_267 said:**
> What do you mean by supporting Japanese? Doesn't that just depend on the encoding of the text file? You probably need it to be UTF-8 if you have English and Japanese characters. Anyways I found geany pretty good for php.

Technically, yes.  However, in jedit and eclipse, if I try to type Japanese via SCIM, I get blocks and question marks, respectively.

What I need is an IDE that can both encode Japanese characters (UTF-8 is, you're correct, sufficient), and display the language as well.  As an example, BlueFish actually displays Japanese, but I don't like it's beefy UI.

lemme try geany, though:).

EDIT: hey, neat, it works.

---

### Post by ad_267 on 2008-09-07
Ok well I've used both gedit and geany with a php file encoded in UTF-8 with Chinese and English characters and haven't had a problem.

Sometimes there's issues when changing the encoding of a text file if it isn't initially correct and it can be better to start from scratch with a blank file with the correct encoding.

---

### Post by cb951303 on 2008-09-07
As far as I know eclipse is fully capable of what you're stating. Just look at the settings. Maybe the default font doesn't have japanese chars? Try changing it to a UTF-8 font like bitstream mono or dejavu mono

:popcorn:

---

