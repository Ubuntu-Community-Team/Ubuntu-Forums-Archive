---
title: "Tips: Open Office 3 beta 2"
date: 2008-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by slumbergod on 2008-08-06
These are just a summary of tips relating to OOo3b which I use when I set up OO. I am posting them here in the hope they might help others who get stuck. If readers have more tips (or easier solutions) add them to the thread.

1. Changing the default template font
- Open OpenOffice and start Writer. Change the font to the one you prefer
- then go File - Templates - Save
- give it a suitable name and then click Save
- next, go File - Templates - Organize
- double left-click the My Templates folder in the left pane and you should see your new template listed as the name you chose
- right click it and select Set As Default Template
- close the application, then restart it. When you open a new Writer document the default font should be the one you selected.

2. Changing the icon set
- go Tools - Options then expand OpenOffice.org so you can select View
- beside the icon size is a pulldown box that lists the availabe icon sets for the interface

3. Tweak the speed 
(these are for OOo2.x but seem to make things better for OOo3b on my old laptop)
- go Tools - Options then expand OpenOffice.org
- under Memory:
...in the UNDO section try reducing the number of steps to 30
...in the GRAPHICS CACHE section try increasing the amount of memory to 128mb 
- under Java, try deselecting the Use a Java Runtime Environment option

4. Make the auto spell-check / dictionary work
For some strange reason when I install OOo3b2 the auto-spell check option would not work. Looking online I read that English support was included yet try as I might the dictionary was not installed. 

It turns out that it was present but not imported.

- open the application and select Tools - Extension Manager from the top menu
- click Add then navigate to: /opt/openoffice.org3/share/extension/install/
- hopefully, dict-en.oxt will be present as it was for me. Select it and Open 
- restart open Office and it should now be working if you have languag
e set to English (UK) or English (US). 

If you need to change the default language you can go to Tools - Options - expand Language Settings - Languages
If you then look under Language Settings - Writing Aids, you should now see some entries in the Available Language Modules box

---

### Post by bthoward on 2008-08-17
Strange.  Great tips but the spell check bit seems to not be working for me.  I get the sun dictionary but my standard dictionary seems to not be so good.  things like GPS and WWW and "Sun Microsystems" it thinks is spelled right but general English words its not fond of... :(

---

### Post by darthbrader on 2008-08-17
> **bthoward said:**
> Strange.  Great tips but the spell check bit seems to not be working for me.  I get the sun dictionary but my standard dictionary seems to not be so good.  things like GPS and WWW and "Sun Microsystems" it thinks is spelled right but general English words its not fond of... :(

I second this.  My spell checker went from accepting everything to accepting (almost) nothing.

---

### Post by hstoellinger on 2008-10-09
With my OO3beta spell check doesn't work for German, even though the respective language settings are specified under "Options". Does that stuff actually work under V3beta? 
Regards from Salzburg-Austria

---

### Post by hstoellinger on 2008-10-09
I MUST appologise: Spellcheck now works. I really don't know - why, but it does work now...Sorry for occupying your time!

---

### Post by AmpersUK on 2009-11-21
Re:

- open the application and select Tools - Extension Manager from the top menu
- click Add then navigate to: /opt/openoffice.org3/share/extension/install/

I have no openoffice3 under opt at all.

And I have tried to modify my default templates, but it just doesn't want to do it. I have palantino as my default font, and alterations on my page margins and widows and orphans, these are OK, but when I chane Headings to 18pt, 1 to 16 pt, 2 to 14 pt and headings 3 to 12 pt, it keeps reverting to what it had before.

I have followed the instructions faithfully, and had done this in Openoffice2 successfully.

I have not given up trying to change the header fonts.

---

### Post by SJefferies on 2009-12-02
Very good and informative tips, Did you know that you can run Open office applications using your web browser? I have been doing this since I discovered [ooanywhere.com]("http://ooanywhere.com"),  great way to use open office. No need to download and install OO

---

