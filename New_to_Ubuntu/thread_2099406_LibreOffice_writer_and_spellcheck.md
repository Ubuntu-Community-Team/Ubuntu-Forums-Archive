---
title: "LibreOffice writer and spellcheck"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2012-12-29
Can anyone tell me if LibreOffice Writer comes with a English dicionary built in or do I have to install one?

My spellcheck is not working and I can't find why?

---

### Post by audiomick on 2012-12-29
I think it is there by default, but I am not sure. 

Open the software center and search for

libreoffice spellcheck

When I do that, I geat a long list of language packs for libre office, and can see from the green tick on the package that I have English-british, English-southafrican and German installed.

You also have to go into the settings in Libre office somewhere and tell it what to use, I think, but I don't know exactly where that is, I'm afraid.

---

### Post by grahammechanical on 2012-12-29
Try going into Tools>Options>Language Settings>Writing Aids to see if the check marks are still there against Hunspell spellchecker and Check spelling as you type.

Regards.

---

### Post by Dennis N on 2012-12-29
> **dougcumiskey123 said:**
> Can anyone tell me if LibreOffice Writer comes with a English dicionary built in or do I have to install one?

My spellcheck is not working and I can't find why?

Check: [B]Tools> Options> Language Settings> Writing Aids
[/B]
You should see the available language modules and user-defined dictionaries, and those checked are being used. The language module contains the dictionary. Default is to check spelling as you type.

Use the Help Button at the bottom of the dialog for more explanation.

Also check **Tools > Language >**

where it appears spell checking can also be turned off.

---

### Post by dougcumiskey123 on 2012-12-29
Thanks all, I'll do what you suggest...

---

### Post by Linuxisfast on 2012-12-29
Spellcheck is available for certain default languages such as English US or UK and some others, when you select your default language under options, you will see a tickmark next to them. This indicates that spellcheck is available for those languages.

---

### Post by daslinkard on 2012-12-30
> **dougcumiskey123 said:**
> Thanks all, I'll do what you suggest...

Did this suffice your question?  If so please feel free to mark this thread as solved!

---

### Post by dougcumiskey123 on 2012-12-30
Update on the "no spell check" I found that I had not installed the "Language Support" package. I put this down to having to install 12.04 without a internet connection at the time of installation.

On installing the " Language support" last night the computer crashed while working on "wamerican". I left it running over night to see if it would resolve itself but it did not.

This morning I shut down and rebooted, the re installed "Language Support" which restarted and now I have "spell checker" working.

Problem solved.

Many thanks.

---

### Post by spiders on 2012-12-30
> **Dennis N said:**
> Check: [B]Tools> Options> Language Settings> Writing Aids
[/B]
You should see the available language modules and user-defined dictionaries, and those checked are being used. The language module contains the dictionary. Default is to check spelling as you type.

Use the Help Button at the bottom of the dialog for more explanation.

Also check **Tools > Language >**

where it appears spell checking can also be turned off.

this worked for me 

thanks

---

