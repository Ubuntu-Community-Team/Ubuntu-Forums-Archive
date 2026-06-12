---
title: "Make file executable?"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2011-10-27
I'm setting up lftp to backup my logs. 

If I go to terminal and run my script it works. 
However if I make the file executable I can't get it to run. 
it will pop up and ask to Execute or Execute in Terminal. Neither will work. But if I open a terminal and run bash Sync it works fine. 

here's the file. 
```

#!bin/bash
lftp -f  /home/buzz/Sync.txt

```

How can I make this run by clicking?

---

### Post by wolfen69 on 2011-10-27
Right click file, > properties > permissions > allow executing file as program.

---

### Post by BuzzStPoint on 2011-10-27
Right, Done that. 

When I click the file it pops up a box asking to execute or execute by terminal, Open or cancel. 

None of those do anything except for cancel. 

I know it work. I can open terminal manually, and run it.

---

### Post by ajgreeny on 2011-10-27
First line should be **#![COLOR=Red]/[/COLOR]bin/bash**

You missed the / before bin, and there is no executable for just bin/bash from a user terminal, though there would be I suppose if it were a root terminal;  I don't know about that, never tried!

---

### Post by Gawains Green Knight on 2011-10-27
chmod 755 file

---

