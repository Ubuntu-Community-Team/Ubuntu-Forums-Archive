---
title: "FireFox, why you have to be so UK all the time?"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by snowpensi on 2015-03-04
browser default spellcheck UK English
Right click Languages, change US English
reboot, now UK English again ("colour" insteadda "color")
how can make permanent so no more spelling mistakes? is this feature?

---

### Post by Mark Phelps on 2015-03-04
> how can make permanent so no more spelling mistakes? iIn the UK,  "colour" is the correct spelling.

To change the language, go to: Edit --> Preferences --> Content --> Languages.

---

### Post by snowpensi on 2015-03-04
Edit --> Preferences --> Content --> Languages  number 1 top choice "English/United States (en-us)" I check.
Spell checker dis respect me, he default option "UK English" every page every time. Right click change US but Ubuntu go back UK next time.
Ubuntu red line "color" but "color" ok in dictionary book! Why tell me mistake Ubuntu but no mistake? ! 
Why Ubuntu "ok" make red line mistake? America people say "ok" is ok. :)

---

### Post by grahammechanical on 2015-03-04
When we install Ubuntu we are asked to set a location and a keyboard layout. If we set the location to somewhere in the UK and the keyboard to English UK then certain systems settings such as time and spell checkers will match what is normal in the UK.

We can go to System Settings>Language Support and install variants of the English language used in other parts of the world. We can install English (United States).  Once that language is installed we can move it up to the top of the list of installed languages so that it becomes default. We will also be offered the option to install relevant language packs and writing aids that must include dictionaries/spell checkers.

You ask, is this a feature? Yes it is. It is a feature that when I install and set my language to English (United Kingdom) and my location to London (UK) I do not get a US spell checker. It also means that my internet searches give results in the UK and not in the US.

A very useful feature if you ask me.

Regards.

---

### Post by snowpensi on 2015-03-05
You very kind but not understand question. Never say UK, not desired UK, not live in UK, desired US. Is feature desired cannot change? How change this make US default now??? Google tell me he not only user with bug. Ubuntu can you not say "color" wrong spelling?? Color ok spelling I know!

---

### Post by buzzingrobot on 2015-03-05
If you are certain that both Firefox and Ubuntu are configured to use U.S. English, then you might try the brute force approach of deleting the Firefox folder in the .mozilla folder in your home directory. (.mozilla is a hidden folder so, if using the file manager be sure to set it to display hidden files.)

That has the effect of wiping out all Firefox configuration information, bookmarks, etc., so when you launch it again it will be as if that was the first time you've launched it.  Reconfigure it as you wish. If it continues to use UK English, something else is very likely wrong. (Perhaps not all necessary language packages are installed?)

---

### Post by michael-piziak on 2015-03-05
When does Firefox do spell checking any ways ?

---

### Post by coffeecat on 2015-03-05
> **michael-piziak said:**
> When does Firefox do spell checking any ways ?

Every time I use it to post a reply here. You might want to right-click in the forum message editor (or many fields on some websites where you can enter text), tick check spelling, and choose a language under Languages. You might find it useful. I do.

---

### Post by Holger_Gehrke on 2015-03-05
> **snowpensi said:**
> Edit --> Preferences --> Content --> Languages  number 1 top choice "English/United States (en-us)" I check.


That setting has nothing whatsoever to do with spell checking. It sets the Accept-Language field in the request header, which tells the server what language you would like the page to be delivered in. If the server has the page in multiple languages it will choose from the list you send in that header field.

For spell checking it takes the language (and variant) in the page or if the page doesn't set these, your lokal default. If a language is set but no variant it seems to go by alphabetical order of the installed dictionaries, so en-uk before en-us. You could check in Extras -> Add-ons -> Dictionaries. If you installed the dictionaries yourself, you can probably remove the en-gb one. If you didn't, then it and the en-us one probably installed system-wide, and I don't know where they are. On my system (Ubuntu 12.04), '/usr/lib/firefox/dictionaries/' is a symbolic link to /usr/share/hunspell, which has all the dictionaries I see in Firefox, but YMMV.

---

### Post by Yellow Pasque on 2015-03-06
Do you have myspell-en-gb package installed? Maybe you want to remove it...

---

### Post by snowpensi on 2015-03-06
FINALLY someone understand question!
This bug Ubuntu, search ubuntuforums I not only one, search launchpad many other complain. Ubuntu global all nations but not spell check I guess.

Thank you Ubuntu Forums
THANK YOU Bishop Desmond Tutu!!!

---

### Post by buzzingrobot on 2015-03-06
Ok, in Firefox 36, when I right-click to expose the spell check option, immediately below "Check Spelling.." is "Languages". Mine is set to "English (United States). A "Dictionaries" option is displayed which takes you to a Mozilla page where additional dictionaries can be installed. I added a UK English dictionary and now I have the option of choosing either the UK English or the US English dictionary for spell checking. These dictionaries don't appear to be in the Ubuntu repos.

---

### Post by Yellow Pasque on 2015-03-06
@buzzingrobot: You can add dictionaries within firefox, and they will be installed in only that user's profile. The myspell/hunspell packages get installed system-wide (in /usr/share).

As for Firefox changing dictionaries on its own accord, I've heard people complain about that. Even on my system with only one dictionary (us-en), I sometimes find spell-checking disabled and have to select us-en again. *shrug*

---

