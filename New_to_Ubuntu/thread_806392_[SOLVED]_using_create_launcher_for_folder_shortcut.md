---
title: "[SOLVED] using create launcher for folder shortcuts"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by ragele on 2008-05-24
Hey guys, another newb here using hardy

basically Im trying to make a simple desktop shortcut for a folder in my home directory by right clicking on the desktop and choosing "Create launcher". I choose "Location" as the type then put in the name and add /home/user/foldername for the command. if i click on this shortcut after making it it just says "couldnt display "/home/user/foldername" There is no application installed for this file type" 

Not sure why this isnt working because the same thing went fine with gutsy on a different machine. am i missing something?

---

### Post by NilsE on 2008-05-24
Put nautilus in front of the path with a space between them.  If it is a root level folder put gksudo in front of that,

so it would look like this using your example

nautilus /home/user/foldername

or 

gksudo nautilus /home/user/foldername

---

### Post by ragele on 2008-05-24
thanks for the fast reply.

both ways didnt not work however... is this something that only gutsy versions do im wondering? /home/user/foldername was the ticket before on gutsy

---

### Post by NilsE on 2008-05-24
Try this and tell me what happens

nautilus /home

or just

nautilus

Also, if you are on ubuntu this will work.  If you are on another veraion  then it is whatever the command is for the file browser which I forget.

---

### Post by ragele on 2008-05-24
actually if i choose the type as Application and type nautilus /home/user/foldername as the command it works... 

still racking my brain on why it wont if type is set as location. 
what is the location type good for if the setting doesnt link to anything.

anyone with a gutsy install try this to see if it works

---

### Post by ragele on 2008-05-24
using "location" as the type and with nautilus /home it give the same error.

---

### Post by ragele on 2008-05-24
Thanks NilsE

---

