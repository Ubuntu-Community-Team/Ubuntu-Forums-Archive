---
title: "é and ü in LibreOffice Writer"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-18
Say I want to type French or Spanish on LibreOffice Writer, then I'm gonna need letters with accents like[COLOR=Blue] é[/COLOR] and[COLOR=Blue] ü[/COLOR] . 

In windows you type [COLOR=DarkSlateGray][COLOR=Blue]'[/COLOR] [/COLOR]followed by [COLOR=Blue]e[/COLOR], and it gives you [COLOR=Blue]é[/COLOR] automatically. 
However on LibreOffice (and this forum) it just gives you [COLOR=Blue]'e[/COLOR] .

Is there a fast way to type those characters [COLOR=Blue] é[/COLOR] and[COLOR=Blue] ü ?
[/COLOR]

---

### Post by Grenage on 2012-07-18
It's been a while but:

right-alt+e for é
right-alt+shift+: then u for &#369;

There are a lot of accent shortcuts, most of which I think involve using right-alt and the symbol to be used in conjunction with the letter (ish).  Hopefully someone will have a chart or the like, which they can link.

---

### Post by audiomick on 2012-07-18
If you are getting the behaviour in Libre Office and on here, then I think the problem you have is due to keyboard mapping or maybe language settings. I can't help much further than that other than to say that it works as you describe for me. I get é and è just as you describe. My keyboard is a German one, and the computer is set to German for the benifit of my girlfriend, so I have ä ö and ü as a matter of course.

I think the thing with é should work. If you want some others, maybe you will find some info here
[https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions]("https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions")

edit: I meant to ask what Language your system is set to, and what keyboard you have. I think this is relevant. The combinations from Grenage in the post above give me &#8364; and &#8593;  ;)

---

### Post by sanderj on 2012-07-18
> **aef54 said:**
> Say I want to type French or Spanish on LibreOffice Writer, then I'm gonna need letters with accents like[COLOR=Blue] é[/COLOR] and[COLOR=Blue] ü[/COLOR] . 

In windows you type [COLOR=DarkSlateGray][COLOR=Blue]'[/COLOR] [/COLOR]followed by [COLOR=Blue]e[/COLOR], and it gives you [COLOR=Blue]é[/COLOR] automatically. 
However on LibreOffice (and this forum) it just gives you [COLOR=Blue]'e[/COLOR] .

Is there a fast way to type those characters [COLOR=Blue] é[/COLOR] and[COLOR=Blue] ü ?
[/COLOR]

During the Ubuntu install, you can choose the keyboard. I always choose "English international keyboard with AltGr dead keys". That way I can type any accented letter the way you describe.

OK, I found how to set it up after install:

Click the Super-key (with the Windows logo),
in the Dash, type "keyboard layout". Ubuntu will offer ... Keyboard Layout. Start that.
In the lower corner of Keyboard Layout, click the "+" symbol, and add  "English international keyboard with AltGr dead keys".
Probably good to remove the existing keyboard setting.

HTH

---

### Post by aef54 on 2012-07-20
I solved it. I went to the application "Keyboard Layout" and I changed the keyboard Layout I originally chose:  *English, (US, with euro on 5)* to *English (US, international with dead keys)*.

Now it works just fine. Thanks for posting everybody.

---

