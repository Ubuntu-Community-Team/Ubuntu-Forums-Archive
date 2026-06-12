---
title: "How to view special characters in text files ?"
date: 2008-07-24
forum: Programming Talk
---

### Post by cudjoe on 2008-07-24
Hi !

I was looking for a way to see all special characters in text files (like CR/LF,tabs,...). Gedit doesn't seem to have this. Geany neither...

I ended up with Notepad++ with Wine ! 

[IMG]http://cudjoe.org/dotclear/images/2008/Screenshot-new%201%20-%20Notepad++.png[/IMG]

I guess you guyz know a better way !
Thanks !

---

### Post by Def13b on 2008-07-24
Geany has the option at least for Tabs/LF/CR,

Edit > Preferences > Display > Tick, Show whitespace (tabs) & Show Line endings(CR/LF)

---

### Post by cudjoe on 2008-07-24
Thank you ! Was not able to find it myself ! :roll:

---

### Post by pmasiar on 2008-07-24
Midnight Commander, the universal tool, has old-fashioned hex editor (where on split screen you see ASCII and hex codes of a line). And many many other useful features.

---

### Post by nanotube on 2008-07-24
also try scite

---

### Post by nvteighen on 2008-07-24
There's a plugin that does that in gedit (Edit->Preferences->Plugins). You can also configure it a bit.

---

### Post by PJOS13 on 2011-01-10
> **nvteighen said:**
> There's a plugin that does that in gedit (Edit->Preferences->Plugins). You can also configure it a bit.

Which plugin?

---

### Post by jsampaio57 on 2011-05-25
I agree, PJOS13. It seems to be a costume, among the geniuses of computing, to give an answer without being toooo clear. It seems that they want to say: "I know how to do it, but you have to find out yourself!" If the genius know the plug-in, he could easy just to key some additional characters and put the name of the plug-in. But these guys are too busy and are too important to do that. Well, I am interested in this too. Uuse synaptic to add gedit-plugins, Then you open gedit and look for the new plugins added to the list. Maybe ont of those it "the plugin" the genius had suggested. Cheers! << the eye that sees everything >>

---

### Post by cudjoe on 2011-05-25
No need to fan the flames. 

Even if I use Geany, I looked out and found this for gedit :

> 
Re: how to show the non-printing symbols in the	text	editor?  
by Curtis Hovey Oct 15, 2008; 11:23pm

Hi Ewgeni, 

The Draw spaces plugin will show spaces and tabs. I don't think it will 
display other characters. You can enable the plugin from the gedit menu 

Choose Edit > Preferences > Plugins 
Select Draw Spaces from the list 
Choose the Configure button and verify that spaces, non-breaking spaces, 
and tabs are selected. 
Close the window. 

You can toggle the display of whitespace from the gedit menu 

Choose View > Show white space. 


[http://old.nabble.com/how-to-show-the-non-printing-symbols-in-the-text-editor--td20000818.html](http://old.nabble.com/how-to-show-the-non-printing-symbols-in-the-text-editor--td20000818.html)

---

### Post by Blackbug on 2011-05-25
well, VI has some options for this
:set list
 
it shows tab, new line characters for sure..

---

