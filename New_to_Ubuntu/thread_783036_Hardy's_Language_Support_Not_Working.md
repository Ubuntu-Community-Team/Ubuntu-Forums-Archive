---
title: "Hardy's Language Support Not Working"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by A.Scotchmer on 2008-05-05
Hi

I've just install Ubuntu 8.04 (Hardy Heron) onto my laptop.  I need Japanese input as I had on 7.10.  I don't need a full Japanese system, just the ability to input Japanese characters via scrim. 

Unfortunately language support found on the System> Administration menu only displays English.  There is no other languages to choose from.  In 7.10 it lists all the available languages and you just checked the right ones you need.

In 8.10 however there is only the option for English.  Any suggestions?

Andrew

---

### Post by jboy012000 on 2008-05-05
[http://packages.ubuntu.com/language-pack-gnome-ja](http://packages.ubuntu.com/language-pack-gnome-ja)

I found this link above, if you scroll to the bottom it has some language package updates for Japanese for 8.04

I hope this helps.

Cheers

---

### Post by Michl on 2008-05-05
That's odd.  In System -> Admin ->
Language Support I get a long list
of supported languages including
Japanese.  I'm not sure what happened.

When I need a language I also go to
synaptic and find language-support and
language-pack for the language I want
and install via synaptic.  In your case
you would look for language-support-ja
and language-pack-ja.  Just checked
and these are in synaptic.

---

### Post by mikebravo on 2008-05-05
Andrew, no suggestions but with upgrade from gutsy to hardy I can confirm what Michl says about having a long list of languages available, including Japanese. Will have Japanese visitors this summer, so I am interested in getting it to work. Half way there, Japanese pages display like a champ BUT Evolution Mail will input nothing but English. My visitors need to be able to input Kanji if they are to write home. I will watch this post for further advice.   

Would it not be cool if developers would make pages/menus/ and so on that were in English with foreign subtitles or vice-versa? It would make the language handicapped much easier to set things up for others.     MikeBravo

---

### Post by TokyoYank on 2008-05-05
I&#12288;also experienced strange behavior from System > Administration > Langauge Support   .. I started going through several settings, however I think most problems went away after I switched to a less busy server.  I also suddenly got other ubuntu updates.  

System > Administration > Software Sources > Download from: > Other > Select Best Server

The search took a couple minutes takes, but updates are better for me now.  

Sorry if this indirect advice doesn't help you.  Good luck

---

### Post by TokyoYank on 2008-05-05
> **mikebravo said:**
> Would it not be cool if developers would make pages/menus/ and so on that were in English with foreign subtitles or vice-versa? It would make the language handicapped much easier to set things up for others.     MikeBravo

A comment on that:  I've seen a dictionary application that added this functionality to Windows, though I've only seen English to Chinese.  With the mysterious way my Chinese classmates were able to get copies of software, I have no idea if it was open source or not, but at least I wanted to tell you that this technology exists *somewhere*.  ...  We have GNOME dictionaries & spell checkers.. so how far off would a mouse-over translator be?  Worth googling, at least.

.. By the way, most Japanese under 60 use enough every-day English to do fine with a computer with English menus (though they may feign incompetence because they think it's polite).  But if you want to really impress them, once you get Japanese working, just log into GNOME with the language set to Japanese!

---

### Post by Michl on 2008-05-06
I agree that adding language support through System ... Language
Support has odd results. From my experience, the stable way
to do it is adding the support and pack packages through
synaptic.

---

### Post by seshomaru samma on 2008-05-07
If you just need to input Japanese you don't need the whole gnome-support package, first install fonts-
run this command
```
sudo apt-cache search japanese
```
it will give you a list of japanese related software, install anything that looks like a font
then install SCIM```

sudo apt-get install SCIM scim-anthy scim-bridge
```
I think that should be enough
To see if it works open "gedit" , right click anywhere and look for SCIM under input method , space+ CTRL should invoke it

---

