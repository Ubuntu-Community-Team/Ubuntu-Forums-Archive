---
title: "SCIM Japanese and Chinese Input Guide"
date: 2005-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by mrbass on 2005-04-29
[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
Lots of screenshots in Japanese but do briefly cover Chinese.  Now if we could only add Korean (dream upon a star).

---

### Post by mrbass on 2005-05-04
Added Korean input as well thanks to scim-hangul showing up in the repositories past few days.

---

### Post by rjl on 2005-06-01
I took a look at your very fine guide for inputing Japanese, Chinese & Korean, but I only need to imput Japanese.

What steps should I leave out to only end up with Japanese.

Thanks,

---

### Post by mrbass on 2005-06-01
**sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese          scim-hangul **[b]scim-tables-zh scim-tables-ja scim-tables-ko

[/b] instead do this instead
**sudo apt-get install uim anthy scim-gtk2-immodule scim-uim ****scim-tables-ja**

---

### Post by pdk001 on 2005-06-01
thanks this is good tip for me

---

### Post by baraider on 2005-06-01
how about vietnamese.....i think the only reason i think windows is far better than linux is there is little to none software to input vietnamese

---

### Post by rjl on 2005-06-02
Thank you!

---

### Post by mrbass on 2005-06-02
To install vietnamese just install scim and follow the guide.
[b]sudo apt-get install uim scim-gtk2-immodule scim-uim
[/b]There's a ton of languages that you can input.  I'll type them out here.
Here's a screenshot of the languages
[http://mrbass.org/linux/ubuntu/scim/all.png]("http://mrbass.org/linux/ubuntu/scim/all.png")

Amharic
Arabic
Assamese
Bengali
Tibetan
Greek
Gujarati
Hebrew
Hindi
Croatian
Japanese
Kazakh
Kannada
Korean
Laothian
Malayalam
Oriya
Panjabi
Russian
Slovenian
Serbian
Tamil
Telugu
Thai 
Vietnamese
Chinese

specifically Vietnamese has following input methods available
UIM-m17n-vi-viqr
UIM-m17n-vi-telex
UIM-viqr

Sidenote: One of the nice things about unbuntu compared to other distros is it comes with tons of fonts for various languages.  Mac OS X is awesome in this regard you can input in (23 languages if I remember correctly) and it's all on the install DVD.  Linux is getting better at inputting various languages.

---

### Post by baraider on 2005-06-02
Thanks..finally able to input vietnamese...i follow your guide to change asian language in openoffice but under asian language...there is no vietnamese

---

### Post by baraider on 2005-06-03
Wonder if the input method only works in text editor? I can't seem to type vietnamese in chat windows like in Gaim....

---

### Post by mrbass on 2005-06-03
should work in most apps.  Gaim doesn't support UTF-8 or at least it didn't ..current versions may not sure.
[http://www.ubuntuforums.org/showthread.php?t=30981](http://www.ubuntuforums.org/showthread.php?t=30981)
[http://www.ubuntuforums.org/showthread.php?t=12985](http://www.ubuntuforums.org/showthread.php?t=12985)

---

### Post by vladuz976 on 2005-07-21
[QUOTE=mrbass][http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)
Lots of screenshots in Japanese but do briefly cover Chinese.  Now if we could only add Korean (dream upon a star).[/QUOTE]
 hi,
installation worked fine. have japanese installled now. but i can't use it at all.
has anybody here managed to install this and was able to use it, too??
Help me please!
I simply need to be able to type in hiragana and then somehow translate it to the appropriate kanjis.  I've tried all japanese input methods but nothing works. sometimes i get only hiragana or only katakana or only kanji, nothing here let's me write in hiragana and then translate to kanji.

thanks

---

### Post by senshisteph on 2005-07-21
[QUOTE=vladuz976]hi,
installation worked fine. have japanese installled now. but i can't use it at all.
has anybody here managed to install this and was able to use it, too??
Help me please!
I simply need to be able to type in hiragana and then somehow translate it to the appropriate kanjis.  I've tried all japanese input methods but nothing works. sometimes i get only hiragana or only katakana or only kanji, nothing here let's me write in hiragana and then translate to kanji.

thanks[/QUOTE]

I could really do with some help on this too! My partner is Japanese and needs to be able to type but he is a bit of a technophobe so wants me to set it up... I have installed the Japanese language packs but haven't a clue what to do now. Is there a guide in English on how to do this?? Thanks  :wink:

EDIT:  :-#  found the pages in the wiki - working great now. Have you tried looking there vladuz? Very helpful (try the anthy/uim method)
[https://wiki.ubuntu.com/JapaneseInputHowto](https://wiki.ubuntu.com/JapaneseInputHowto)

---

### Post by a8ne on 2005-07-25
[QUOTE=rjl]I took a look at your very fine guide for inputing Japanese, Chinese & Korean, but I only need to imput Japanese.

What steps should I leave out to only end up with Japanese.

Thanks,[/QUOTE]

That's such a typically Japanese way of thinking.  ;-)

---

### Post by mrbass on 2005-07-28
It may be but in Mac OS X you can select any of 16 languages and turn them on or off very easily.  Personally I think you should install everything under the sun then just turn them off or they should be all off by default.  Mac it is like 320MB I think of fonts and files for the foreign languages.

---

### Post by vkkim on 2005-08-01
I installed everything according to the guide and everything is working fine except some hanja (&#54620;&#51088; or &#28450;&#23383;, chinese charcters) in Korean come up as little boxes with the unicode numbers and letters in them using the 2bul input method.  However, when I use the Hanja input method under Korean, all the characters are rendered correctly.  Any thoughts why?

---

### Post by dl7und on 2005-09-05
Mrbass, could your guide perhaps replace [this item](http://ubuntuguide.org/#scim)  in the [unofficial guide](http://ubuntuguide.org/) ?  If I follow the unofficial guide, I can only use Chinese in an English environment, in a Chinese environment scim will not show up. Yours is not only more comprehensive, it is also by far more "reliable"...

PS: Thanks for the guide, btw... :grin:

---

### Post by bdash on 2005-09-13
Hello.

I followed these steps on Breezy, and it "kind of" works (I can input Japanese) but:
- scim-setup produces a segfault
----
Loading Config Module gconf
Loading Config Module simple
Loading Config Module socket
Loading Setup Module hangul-imengine-setup
Segmentation fault
----
- It takes very long time for applications (for ex. gedit) to launch when scim is used. About 10 seconds while on the console "Launching a SCIM daemon with Socket FrontEnd..." is displayed.

How can I correct that ?

---

### Post by chun on 2005-10-15
hi there:

i just found this mrbass doc and been following it. however, upon "Press CTRL-SPACE to bring up SCIM input methods." nothing happened:/

when i do scim-setup, i also got segmentation falut too.

anyideas?

btw, i can have japnese input but nothing else.

hope this helps:

# scim -v
Smart Common Input Method 1.0.2

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Launching a SCIM process with x11...
Loading simple Config module ...
Creating backend ...
SCIM has exited abnormally.

erm, not sure if -v is a valid option, but it seems to give me more output than otherwise

cheers

chun

---

### Post by kairu0 on 2005-10-16
Scim and scim-setup have segfaulted on me in Breezy since Colony 3. It's a really sad state of affairs for input methods in Ubuntu.

I have been using UIM instead of SCIM for Japanese. The downfall is that Ubuntu does not include a QT immodule so you only get input in GTK apps.

The other solution is the ubuntu-ja project which uses an unofficial version of SCIM that is supposed to work out of the box. Of course, your whole system will be in Japanese if you use ubuntu-ja.

---

### Post by chun on 2005-10-16
mmm, maybe i will give hoary a try until its ok on breezy

---

### Post by drkeuk on 2005-10-16
Apparently SCIM doesn't work in breezy but the following might be helpful:

[http://www.ubuntuforums.org/showthread.php?t=76985](http://www.ubuntuforums.org/showthread.php?t=76985)

At least it worked for me :)

---

### Post by fanofcc on 2007-12-31
> **mrbass said:**
> To install vietnamese just install scim and follow the guide.
[b]sudo apt-get install uim scim-gtk2-immodule scim-uim
[/b]There's a ton of languages that you can input.  I'll type them out here.
Here's a screenshot of the languages
[http://mrbass.org/linux/ubuntu/scim/all.png]("http://mrbass.org/linux/ubuntu/scim/all.png")

Amharic
Arabic
Assamese
Bengali
Tibetan
Greek
Gujarati
Hebrew
Hindi
Croatian
Japanese
Kazakh
Kannada
Korean
Laothian
Malayalam
Oriya
Panjabi
Russian
Slovenian
Serbian
Tamil
Telugu
Thai 
Vietnamese
Chinese

specifically Vietnamese has following input methods available
UIM-m17n-vi-viqr
UIM-m17n-vi-telex
UIM-viqr

Sidenote: One of the nice things about unbuntu compared to other distros is it comes with tons of fonts for various languages.  Mac OS X is awesome in this regard you can input in (23 languages if I remember correctly) and it's all on the install DVD.  Linux is getting better at inputting various languages.

Thank you very much!!!
My English is very poor :lolflag:

---

