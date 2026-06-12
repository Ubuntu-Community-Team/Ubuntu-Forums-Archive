---
title: "Khmer input - some vowels don't appear system wide 18.04"
date: 2018-05-16
forum: New to Ubuntu
---

### Post by epidemiks2 on 2018-05-16
Shifting back to Ubuntu after about 5 years away (adobe needs), and trying to get Khmer unicode working. 

Khmer is installed in the language settings.

I've imported my font library,&#8203;&#8203;&#8203; placed in /usr/local/share/fonts

The fonts all appear in Libre office, Inkscape etc, but I can't get various Khmer vowels and diacritics to appear. All I got was "TOFU" when typing: &#6017;&#6098;&#6025;&#6140; 

Rebuilt the font cache using fc-cache -f -v, rebooted.

Now, I don't get TOFU in applications, just blank spaces:

[IMG]https://i.gyazo.com/d1ce2745a8d6021b023003174efd9686.png[/IMG]

The characters appear in the character map:

[IMG]https://i.gyazo.com/6060a1142f86f999c725c4c82421ffe2.png[/IMG]

And text appears normal in the browser, and text copied into Inkscape, Open Office, anywhere, in any Khmer font:

[IMG]https://i.gyazo.com/f7cd2b6d5137e2abcfa4749bbaac520a.png[[/IMG]


But I cannot type Khmer and have all the characters appear.

Advice appreciated.

---

### Post by dino99 on 2018-05-16
Related links  [https://duckduckgo.com/?q=ubuntu+gen+khmer+vowels+font&t=canonical&ia=qa](https://duckduckgo.com/?q=ubuntu+gen+khmer+vowels+font&t=canonical&ia=qa)

---

### Post by epidemiks2 on 2018-05-16
Thanks, will try fonts-khmeros. Pretty sure ttf-khmeros was installed, not sure about fonts-khmeros

---

### Post by epidemiks2 on 2018-05-17
no dice.

I've looked at all the input methods, keyboard layout options, installed anything and everything to do with khmer in the apt archive, and can't get anything but boxes for selected vowels: &#6017;&#6098;&#6025;&#6139;

---

