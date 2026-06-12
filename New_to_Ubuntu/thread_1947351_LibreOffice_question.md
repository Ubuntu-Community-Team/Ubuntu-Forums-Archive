---
title: "LibreOffice question"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by mk.alien.22 on 2012-03-26
hi guys, I would like to know wether I can change the text input in an already written text? for example, if my text is "ubuntu", I would like to select that text, then change the text input to cyrilic in order to make it say "&#1091;&#1073;&#1091;&#1085;&#1090;&#1091;" which is the same in Macedonian :)

the reason why I am asking this is because I have a huge document written in the regular English keyboard input + a Macedonian font, and I would like to change it to (for example) arial, but with Macedonian (cyrilic) input.

any thoughts?

---

### Post by nazar91 on 2012-03-26
Are you talking about transliteration?
Don't know about office but [http://www.translit.ru/](http://www.translit.ru/) do it perfectly, but has russian interface.

---

### Post by grahammechanical on 2012-03-26
I would say that you have to use Find and Replace.

The different keyboard layouts are using the same font so Ubuntu uses different characters to &#965;&#946;&#965;&#957;&#964;&#965; (Greek keyboard layout).

Copy the Cyrillic word characters. Then select Ubuntu and when you open the Find and Replace dialog you will see that Ubuntu is in the Find panel. Now paste the Cyrillic replacement into the Replace dialog and either Find and Replace one instant at a time to be careful or click Replace All.

Oh, make sure that Whole word is checked and maybe make the search case sensitive if that is what you want.

That should work but test it out on a sample of the document.

Regards.

---

