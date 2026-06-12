---
title: "OpenOffice.org; Keyboard Shortcuts.  Stored in a config file?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-08-03
Is there a file that can be edited for the keyboard shortcuts in Open Office?

Eg, 
In Writer, I can go Tools-->Customize-->Keyboard and can edit Shortcut keys.  From this interface I can only set certain keys.  I would like to set the shortcuts to be similar to MS Office.  eg changing the font size with CTRL + [ and ].

This option is not available in the shortcut keys, and would like to know if I can edit some sort of file for their inclusion..

Thanks.

---

### Post by pauper on 2008-08-03
OpenOffice.org is not MS Office. Adjust.

```
wget http://oooauthors.org/en/authors/userguide2/migration/published_final/0604MG-GeneralDifferencesInUse.pdf
```

Version 2.3.0

Writer: Tools--Customize

Select "Format" under Category window. Scroll down to "Increase Font" under
Functions window. Now, select any vacant keybinding under Shortcut keys window.
Click on "Modify" button, Enter. Same applies to "Reduce Font".

When you press keybinding it will increase/decrease by two. (10->12, 13->11,etc.)

You might want to assign "Font Name" as well. 

The actual file with defined key shortcuts is here:
```
gedit $HOME/.openoffice.org2/user/config/soffice.cfg/modules/swriter/accelerator/en-US/current.xml
```

Note: "Font Size" and "Font Name" do the same thing (cursor appears in Font
window), which is an odd thing for the former one. Bug?

---

### Post by SonOfOdin on 2008-08-03
Hey, thanks for the reply.  Thats the file that I am after alright :)

Im able to change the options through the gui, that isnt my problem.  Its just that MS Office makes use of more of the available keys on the keyboard, and I was hoping to do the same in OO.o

ie
	 <accel:item accel:code="KEY_[" xlink:href=".uno:Shrink" accel:mod1="true"/>
	 <accel:item accel:code="KEY_]" xlink:href=".uno:Grow" accel:mod1="true"/>

to use the ] and [ to make the font size change with the CTRL key depressed, as in MS Office.

Im doing something wrong though, or the shortcut config isnt wired to use certain keys... 

Cheers again.

---

### Post by jackn on 2009-01-02
Thank you, Pauper, for this specific advice.

I'm afraid I can't see a 'function' window in my 'cutomize' dialogue box, however. 
Functions are listed in the 'shortcut keys' window, but they have nothing on font, which is what I'd like to have a shortcut for (size and type).
When I change the category in the category window, the list of shortcuts and keys in the 'shortcut keys' window stays put. I thought it would display a new list according to category, which doesn't happen.
I've tried the help button, but the instructions leave me wondering.
I've also looked at the file you referred to, and couldn't find anything to do with 'font', 'size', 'increase' or 'decrease' in it.

What am I missing?

Thank you kindly.
jackn

---

