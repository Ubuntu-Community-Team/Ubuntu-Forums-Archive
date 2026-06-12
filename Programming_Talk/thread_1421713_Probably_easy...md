---
title: "Probably easy.."
date: 2010-03-04
forum: Programming Talk
---

### Post by MikeVaughanG on 2010-03-04
I found a 'command' online that, when you type a bad command it gives you a smiley face, and when you type a good command it gives you a sad face. 

```

[COLOR=#007800]PS1[/COLOR]=[COLOR=#FF0000]"\[COLOR=#780078]`if [ \$? = 0 ]; then echo \[\e[33m\]^_^\[\e[0m\]; else echo \[\e[31m\]O_O\[\e[0m\]; fi\`[/COLOR][\u@\h:\w]\[COLOR=#000099]**\$**[/COLOR] "

```

[COLOR=Black]My question is..
Is there a way to get terminal to open up with code already done?
So when I opened terminal it already gve me the :( or :)?

Thanks for any help. You guys are always helpful.. 
[/COLOR][/COLOR]

---

### Post by Bachstelze on 2010-03-04
Just put the code in your .bashrc. ;)

---

### Post by MikeVaughanG on 2010-03-04
That worked flawlessly. Thank You :)

---

### Post by wmcbrine on 2010-03-04
> **MikeVaughanG said:**
> I found a 'command' online that, when you type a bad command it gives you a smiley face, and when you type a good command it gives you a sad face.That sounds backwards... and indeed it is. What that code does is give you a smiley face on a return code of 0, which is the code for successful completion.

---

### Post by MikeVaughanG on 2010-08-25
It is backwards. Lol
Good eye.

---

