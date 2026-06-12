---
title: "Keyboard layout"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by gdgardnerw on 2008-05-03
I have just switched to xubuntu 8.04 and am having trouble getting a new keyboard layout to take effect. I added the new laout for latin america by

applications>settings>settingsmanager>keyboard>layouts

and added the latam layout for Spanish in Latin America.

But how do I get it to work? I do not see how I can activate it. When I was working with Ubuntu 6.06, I could configure the keyboard to allow me to switch languages with a keyboard combination of <alt><shift>.

Is there a way to do that in xubuntu?

---

### Post by gdgardnerw on 2008-05-03
I just solved part of the layout probllem: 

right click on the panel and add the configure keyboard layout switcher plugin to the panel.

That´s the good news.

The bad news is that it will not put the accents over the vowels in Spanish. It prints the accent first and then the vowels. How can I configure the composing (which I could do in Ubuntu 6.06) so that the accent appears over the vowel?

---

### Post by Victormd on 2008-05-03
This happens with Brazilian layout as well (in ubuntu). You have to change the language settings in ubuntu to spanish (in your case), then it should work...
```
SYSTEM>ADMINISTRATION>LANGUAGE SUPPORT
```
that's how I got the ç for instance to work on mine... had to put it in portuguese...

---

### Post by gdgardnerw on 2008-05-03
Thanks for your quick response! By following the above proceudres you suggested, My whole system did switch to Spansih, which is ok with me....but....I still can't get the accents to go over the vowels.

Does Portuguese use accents as does Spansih and French? 

If so, how did you get them to appear over the vowels (which technically is another ascii character) instead of along side them?

---

### Post by Victormd on 2008-05-03
yes it does... and I can get all of them to work...
á é í ó ú à è ì ò ù ã õ ü ç...

What is your current keyboard model and layout (SYSTEM>PREFERENCES>KEYBOARD)?
my model is set to:
generic 105-key (Intl) PC
and the layout is:
USA Alternative international (former us_intl)

---

### Post by gdgardnerw on 2008-05-03
Victormd you are an angel! 

I had my keyboard to 

generic 105-key (Intl) PC

but I had the keyboard set to these two others

latam  nodeadkeys
es nodeadkeys

neither of which worked.

But with the layout

USA Alternative international (former us_intl)

it works perfectly with the accents! But I have lost the ñ key, which I must switch back to the latam layout to get. I wonder if there is a layout that allows me to do both. It is interesting that the latam and the es layouts do not allow for the accents, as that is a vital part of the language.

---

### Post by Victormd on 2008-05-03
That's odd... I can get ñ working on that same config...
Ok, just an observation, I set my OS to English and the accents work just fine... the only problem is to get the ç where I have to type "ALT + ," then "c" but can still get ñ as I'm doing right now simply by "~ + n"...
Another layout you might want to try is USA International with dead keys, the accents also work fine with that one...

---

### Post by gdgardnerw on 2008-05-04
Thank you very much! With Ubuntu 6.06 I had been using the latam layout which is the standard typewriter layout for Spanish (one of which I still have laying around the house). It had never occurred to me to type the ~ and then the n key! The location for the ñ is just to the right of the l key with the latam layout.

Thank you very much! I can now get my work done!

---

### Post by Victormd on 2008-05-04
No problem, glad I could help...

---

