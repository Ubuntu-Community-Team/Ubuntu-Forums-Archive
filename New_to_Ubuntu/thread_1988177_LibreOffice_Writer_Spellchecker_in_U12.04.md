---
title: "LibreOffice Writer Spellchecker in U12.04"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by afz12 on 2012-05-27
I am asking if there is something I haven't done to make the spell checker "work" in Libre Office. I have starting using it a bit more - mainly in areas that don't need any complex equations but I think Inkscape may be quite usable for diagrams. I tried setting it to "US" but it doesn't highlight spelling errors e.g. mistypes - how do I make this automatic as in Windows Office? I'm sure it should - is this just a U12.04 thing or what do I need to enable. As always, whether this works on others machines is neither here nor there - all machines differ. I am interested in enabling spell checking in Libre Office so all replies on solutions are welcome.

---

### Post by fantab on 2012-05-27
> **afz12 said:**
> I am asking if there is something I haven't done to make the spell checker "work" in Libre Office. I have starting using it a bit more - mainly in areas that don't need any complex equations but I think Inkscape may be quite usable for diagrams. I tried setting it to "US" but it doesn't highlight spelling errors e.g. mistypes - how do I make this automatic as in Windows Office? I'm sure it should - is this just a U12.04 thing or what do I need to enable. As always, whether this works on others machines is neither here nor there - all machines differ. I am interested in enabling spell checking in Libre Office so all replies on solutions are welcome.

LibreOffice-Tools-Options-Language Settings-Languages-- then change all language settings to the language you prefer, for example English (USA)

---

### Post by afz12 on 2012-05-27
I did that -  it did not work

I prefer replies from people with real solutions rather than those in their minds

---

### Post by critin on 2012-05-27
> **afz12 said:**
> I did that -  it did not work

I prefer replies from people with real solutions rather than those in their minds

Why so unfriendly when asking for help?

                                  To Check Spelling Automatically While You Type activate the AutoSpellcheck icon     on the Standard bar. 

 The icon is the ABC with a blue check mark.  If it isn't there, look in TOOLS. Spelling and Grammar.
Also be sure the dictionary is installed.

Also see HELP in the tool bar.

Clicking on the first ABC icon will open a page of word suggestions.  At the bottom of that page you'll see OPTIONS.  Be sure all your preferences are checked there.

---

### Post by BrianH_1 on 2012-08-27
> **critin said:**
> Why so unfriendly when asking for help?

                                  To Check Spelling Automatically While You Type activate the AutoSpellcheck icon     on the Standard bar. 

 The icon is the ABC with a blue check mark.  If it isn't there, look in TOOLS. Spelling and Grammar.
Also be sure the dictionary is installed.

Also see HELP in the tool bar.

Clicking on the first ABC icon will open a page of word suggestions.  At the bottom of that page you'll see OPTIONS.  Be sure all your preferences are checked there.

I just switch to 12.04 and have the same problem.
  
I checked and the hunspell-en-us dictionary is installed. And the languages (in Tools-options-language settings-languages) are set as User interface: english(USA)and Default language Western: English (Canada).

In the tool bar, clicking on the ABC with the red underline and the check mark icon has no effect. Clicking on the ABC and check mark only or "Tools-Spelling and Grammar" to check spelling manually brings up a dialog with "The Spellcheck is complete" and behind it another window labeled "spellcheck" where the "text language" shows as blank.  The only option for the "the spellcheck is complete" window is "ok" which immediately closes both windows so you cannot set the language.

Any suggestions would be appreciated.

Thanks

---

### Post by rburkartjo on 2012-08-27
working fine on my end

---

### Post by BrianH_1 on 2012-09-03
> **BrianH_1 said:**
> I just switch to 12.04 and have the same problem.
  
I checked and the hunspell-en-us dictionary is installed. And the languages (in Tools-options-language settings-languages) are set as User interface: english(USA)and Default language Western: English (Canada).

In the tool bar, clicking on the ABC with the red underline and the check mark icon has no effect. Clicking on the ABC and check mark only or "Tools-Spelling and Grammar" to check spelling manually brings up a dialog with "The Spellcheck is complete" and behind it another window labeled "spellcheck" where the "text language" shows as blank.  The only option for the "the spellcheck is complete" window is "ok" which immediately closes both windows so you cannot set the language.

Any suggestions would be appreciated.

Thanks

Found and answer on the LibreOffice site: Using launcher tried to launch "Language Suport" which immediately returned an error that packages were missing and requesting password to install them.  Entered password, packages installed and Language Support window was live: Check that language for menus and windows was correct, clicked "Apply System Wide" and closed Language Support.  Spellcheck in LibreOffice now works.;)  BHH

---

### Post by tienlbhoc on 2012-09-03
And how to check grammar with libreoffice?
I can check spelling but with grammar, only a simple :"he have a cat", libre can't check ?

---

### Post by nyamina on 2012-09-03
> **tienlbhoc said:**
> And how to check grammar with libreoffice?
I can check spelling but with grammar, only a simple :"he have a cat", libre can't check ?
No, it totally can do that. Try this LibreOffice extension [http://extensions.libreoffice.org/extension-center/languagetool](http://extensions.libreoffice.org/extension-center/languagetool)

---

