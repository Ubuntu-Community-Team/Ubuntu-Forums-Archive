---
title: "can't set british english as default on libreoffice"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by al.adab on 2013-01-19
hello,

have been looking at some 15 forum threads on spell-check in libreoffice, and can't find a solution that applies to the issue I'm having. Perhaps you can help. Here it goes: 

- i have libreoffice version 3.6.0.2;
- myspell-en-gb is installed; 
- other packages are installed (plz see Synaptic screenshot); 
- UK English is set as the libreoffice locale (plz see LO screenshots); 
-  a couple of dictionaries have been uploaded (plz see LO screenshots). 

Now, no matter what I do, libreoffice ignores my setting "English (UK)" at* tools>options>language settings>edit*. The moment I close the window, it reset itself to "English (USA)". The spell-check seems to be off by default, and the only way to activate is to go to *tools>language>for all text* and set it to "English USA"...

...and then right-click to set *language for paragraph* on "English (UK)"... 

what am I supposed to do to 
a) have permanently british english as the default spell-check language,
b) and make sure that spell-check is ON the moment I open a libreoffice document?

---

### Post by Merrattic on 2013-01-19
Well, I'm in England, so my PC is setup with English / gb locales in the first place.

On checking my settings in Libre Office (which "stick" with English GB) I have a couple of differences:

In Writing Aids: I have en-US unticked in dictionaries

In Language:

Interface:  Default-English USA (it's the only choice)
Locale: Default-English UK
Decimal Separator key is ticked
Currency: Default GBP (different from yours)
Western: Default-English UK
Complex Text Layout (CTL) is unticked

Does any of that help?

---

### Post by al.adab on 2013-01-19
thanks Merrattic. I'm afraid, it doesn't. I recall choosing UK English upon installing Xubuntu, but other than that...

it looks like a bug to me - any idea?

---

### Post by grahammechanical on 2013-01-19
May I ask what settings you have in System Settings>Language Support under Language and then under Regional formats?

What keyboard layout did you choose at installation?

Regards.

---

### Post by sunfromhere on 2013-01-19
To add to the upper post: Regional formats is what counts (and "Apply system wide"). 

F.e. in Languages I set English for menus and desktop etc, and in Regional formats I set Croatian. Only then was I able to select Croatian as the default language (for spell checker) in Libre Office. And don't forget you need to have English-UK installed on Ubuntu first (it's in that Languages tab). Easy to forget that part. :p

---

### Post by al.adab on 2013-01-20
ok, just looked at "settings>language support" and all seems to be in place there (plz see screenshots). "English UK" is in the list, as far as i can see it's installed, and it's also the system-wide language of ref...I definitely choose English UK as keyboard settings when I installed Xubuntu - and the keyboard does behave like a UK one - am i missing something here?

---

### Post by westie457 on 2013-01-20
Looking at your screenshots, English (United States) is set as your default language.

English (United Kingdom) needs to be dragged from the lower part to the top line in order to be used. Log out then log in again. The changes will be accepted.

---

### Post by Merrattic on 2013-01-20
Agreed, you need to get English (United Kingdom) up to the top (it may need to be installed ?)

---

### Post by Elfy on 2013-01-20
> **Merrattic said:**
> Agreed, you need to get English (United Kingdom) up to the top (it may need to be installed ?)

It certainly doesn't appear to be installed to me.

---

### Post by grahammechanical on 2013-01-20
I think we are coming to an agreement here and I do not mean to upset anybody :) but I suggest removing English (United states). I do not have it in my set up and it is the only difference I see between my settings and that of al.adab. Give it a try. And then see if changing the Libreoffice default language to English UK sticks in place.

Regards.

---

### Post by al.adab on 2013-01-20
good news: English UK was indeed installed and all I had to do was (as you suggested) drag it up to the top in language support + logout/in. I didn't have to remove English US. 

When I launched libreoffice I found out that 

a) at  libreoffice>tools>options>language settings>writing aids>edit English UK automatically replaced English US. All I had to do was to tick off Hunspell SpellChecker; 

b) spell-check is now always on and English UK is the default language.

thank you all for your help. I really appreciate it.

---

### Post by Merrattic on 2013-01-20
:)

---

