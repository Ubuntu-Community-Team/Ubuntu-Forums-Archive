---
title: "How to make functioning the adding dictionary wizard with OpenOffice 2"
date: 2005-12-08
forum: Outdated Tutorials &amp; Tips
---

### Post by VosaxAlo on 2005-12-08
Hi,

I have installed the new OpenOffice 2.0 and I have seen that the wizard to add new dictionaries don't work.
After a little search I have discovered how to make it functioning:

1) download the macro DicOOo.sxw from here:
[http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw]("http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw")

2) place the file in this folder:
    **[COLOR="DarkRed"]/usr/share/myspell/dicts[/COLOR]**

3) don't convert this sxw document to the new opendocument format.

now when you call the wizard from the File menu you are ready to add new dictionaries.

**[COLOR="Red"]NOTE:[/COLOR]** OpenOffice use MySpell dictionaries, therefore don't install dictionaries with DicOOo.sxw, but only hyphen and thesaurus modules. Dictionaries can be installed from Synaptic.

bye.

---

### Post by Limulus on 2005-12-09
I was asked how to do install the Thesaurus; thanks, it works! :) For those interested, here's a more detailed walk-through:

(Step 0a) the version of OO.o that shipped with Breezy (1.9.x) is a
Beta.  Get version 2.0.x as per [my website]("http://members.shaw.ca/Limulus/ubuntu.html"):

OpenOffice.org 2.0 isn't in backports yet (and might not be for a
while), so if you want it, go to Terminal, run:

sudo gedit /etc/apt/sources.list

add the following as a single line:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

(Step 0b) Then go to Synaptic.
Press "Reload".
When that finishes, press "Mark All Upgrades".

It should tell you that OO.o is going to upgrade; it will give you a
"not authenticated" error, but that's ok.

(Step 1a) When OO.o 2.0.0 is installed, download this file:

[http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw](http://ftp.services.openoffice.org/pub/OpenOffice.org/contrib/dictionaries/dicooo/DicOOo.sxw)

(Step 1b) Using root privileges, move it into /usr/share/myspell/dicts
(e.g. run 'sudo nautilus' from Terminal)

(Step 2) Run OO.o2
Go File -> Wizards -> Install new dictionaries...
A document with links will open; click the language of your
choice (e.g. english). Press the "Start DicOOo" button.

(Step 3a) A Window ("DicOOo") will open; press Next.
The window contents will change to offer "Spelling checker
dictionaries"; press Next.
The window contents will change to offer "Hyphenation dictionaries"; press Next.
Finally you will be offered "Thesaurus dictionaries"; press the
"Retrieve the list" button.

(Step 3b) Click the thesaurus you want, e.g. "English (United
States)"; if you want more than one, press [CTRL] while clicking the
ones you want. Press Next.
The window contents will change; press Next to download.
Press Finish when done.

(Step 4) close all OO.o windows that are open. Restart OO.o
Thesaurus should now work! :)

---

### Post by briguy on 2005-12-15
Cool!  Now my computer speaks Canadian, eh!  Thanks! :D

---

### Post by ubuntu27 on 2005-12-15
I've installed Spanish dictionary, and it doesn't work :(
If I run Spell Check (F7 or Tools/SpellCheck) Spanish is not dictionary language, only English (US) and English (UK)

---

### Post by Limulus on 2005-12-15
[QUOTE=ubuntu27]I've installed Spanish dictionary, and it doesn't work :(
If I run Spell Check (F7 or Tools/SpellCheck) Spanish is not dictionary language, only English (US) and English (UK)[/QUOTE]
From the very first post in this thread: "NOTE: OpenOffice use MySpell dictionaries, therefore don't install dictionaries with DicOOo.sxw, but only hyphen and thesaurus modules. Dictionaries can be installed from Synaptic."

Close all instances of OO.o
Run Synaptic and install the "myspell-es" package.
Restart OO.o; does that fix the problem?

---

### Post by ubuntu27 on 2005-12-18
[QUOTE=Limulus]From the very first post in this thread: "NOTE: OpenOffice use MySpell dictionaries, therefore don't install dictionaries with DicOOo.sxw, but only hyphen and thesaurus modules. Dictionaries can be installed from Synaptic."

Close all instances of OO.o
Run Synaptic and install the "myspell-es" package.
Restart OO.o; does that fix the problem?[/QUOTE]
Thanks Limulus! Now it works!!

By the way. in synaptic I saw a pakage called "aspell" what is that for ?

Thank you so much!

---

### Post by Limulus on 2005-12-19
[QUOTE=ubuntu27]By the way. in synaptic I saw a pakage called "aspell" what is that for ?[/QUOTE]
From the info in Synaptic, it seems to be for a whole bunch of programs, but not for OO.o :)

What you'll often find in the open source world is that there can be several projects that do more-or-less the same thing (consider graphical web browsers for example: there's Firefox, Epiphany, Galeon, Konqueror, Amaya, Chimera, Dillo and probably a few more).  The trick is finding the one that best suits your needs ;)

---

### Post by ubuntu27 on 2005-12-19
Thank you again Limolus! :D

---

### Post by esperantisto on 2005-12-21
There were rumors that ASpell would replace MySpell for OOo, but ASpell seems to be dead. Instead, Hunspell emerged ([http://hunspell.sourceforge.net/)](http://hunspell.sourceforge.net/)). It's already very good, but so far is not ready to finally replace MySpell.

---

### Post by rasmusbp on 2005-12-29
Many thanks for this thread! I love this forum!!:KS

---

### Post by sunny_nwho on 2006-01-01
My internet connection is thru a proxy and i specify the environment in OO and the process freezes when i query for new thesauruses...doe anyone know a workaround...plz help

---

### Post by Limulus on 2006-01-01
[QUOTE=sunny_nwho]My internet connection is thru a proxy and i specify the environment in OO and the process freezes when i query for new thesauruses...doe anyone know a workaround...plz help[/QUOTE]
In OOo, go Tools -> Options; on the left, select Internet -> Proxy; where it says "Proxy server", you probably have "None" selected.  Change that to "System", press OK and see if that works to allow you to get the Thesauruses list.  If not, try "Manual" and enter the info.  Let us know if this works or not.

---

### Post by sunny_nwho on 2006-01-01
i tried everything but later i installed the thesaurus thru dialup but my office crashes every time i press ctrl+F7

---

### Post by Limulus on 2006-01-01
[QUOTE=sunny_nwho]i tried everything but later i installed the thesaurus thru dialup but my office crashes every time i press ctrl+F7[/QUOTE]
I just checked and CTRL+F7 brings up the Thesaurus just fine...

If you go Tools -> Language, is "Thesaurus" an option?  If you click it instead of using CTRL+F7, does it work?

Also, did you follow all of the instructions in my walk-through? (e.g. are you using version 2.0.0?)

---

### Post by sunny_nwho on 2006-01-01
yes i did the same but now it is ok I installed the dictionaries manually...from mirrors.isc.org.....thanks 4 the help limulus

---

### Post by KhanArash on 2006-01-13
How do I move the file DicOOo into the folder?It will not allow me!

---

### Post by sunny_nwho on 2006-01-13
Hi Khan....use th sudo cp command....for example if u want to move file from /home/<username>/<dictionary file name> to /usr/lib/openoffice2/share/dict/ooo/ then u must type 
sudo cp /home/<username>/<dictionary file name> /usr/lib/openoffice2/share/dict/ooo/

and u must edit the directory.lst file in /usr/lib/openoffice2/share/dict/ooo/ and change the file names to the new dictionary file names......the above path i specified for ooo dictionary is the default unless u change it during installation.....u can confirm this by opening ooo writer Tools --->  Options --> Paths and look for writing aids.....I hope this helps....if u need info on specific dictionary u can mention in ur next post and i will try to help u

---

### Post by thojoh on 2006-03-25
Also for me very informative and useful for today's problem I had.

Thanks, fellow forum members!!!

;) :-D

---

### Post by yetanotherpunter on 2006-04-24
Hey many thanks. One  thing tho, i have installed the thesaurus and its there in my settings but I cant accsess it (tools language...thes is grayed out). any ideas?

Ben

---

### Post by TaiChi on 2006-05-05
Man, you are the bomb!
That was amazing and should be published far and wide.
Thanx so much for your time in figuring this out.

---

### Post by Ensnared on 2006-05-05
Anyone know how to make it save the "default language for new documents" setting? There's a checkbox there that says "only for this document", and it's checked and greyed out so I can't uncheck it.

I want Norwegian to be the default language, but every time I start OpenOffice the default is reset to US English.

---

### Post by Limulus on 2006-05-05
[QUOTE=Ensnared]Anyone know how to make it save the "default language for new documents" setting? There's a checkbox there that says "only for this document", and it's checked and greyed out so I can't uncheck it. I want Norwegian to be the default language, but every time I start OpenOffice the default is reset to US English.[/QUOTE]
Um... maybe go:
Tools -> Options...
Language Settings -> Languages
and change the various settings to Norwegian?

---

### Post by Ensnared on 2006-05-06
Um... Yea, right. Then again, maybe that's where I've actually been trying to set it, and seen it get reset every time I launch the application as I described in my question ;)

It seems to be impossible to save - if I set the interface language to Norwegian, that gets saved, and the default for new documents is also switched to Norwegian (and can't be changed permanently). But I don't want a Norwegian interface, but I do want my documents to default to Norwegian. And currently that seems impossible.

---

### Post by Limulus on 2006-05-06
[QUOTE=Ensnared]if I set the interface language to Norwegian, that gets saved, and the default for new documents is also switched to Norwegian (and can't be changed permanently). But I don't want a Norwegian interface, but I do want my documents to default to Norwegian. And currently that seems impossible.[/QUOTE]
Ah, ok, I understand now.  And I can duplicate the problem you're having too: I went into OO.o and set the "Default languages for documents" -> "Western" to "Norwegian (Nynorsk)" closed OO.o and reopened it and it was set back to English.  This looks like it might be this bug: [https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/35936](https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/35936)

---

