---
title: "howto handle a password request from a shell command in a GTK GUI? any guides?"
date: 2006-08-08
forum: Programming Talk
---

### Post by rupert on 2006-08-08
Hi,

where can I find Information how i can pass a password to  a commandline tool.
I already looked through the guides on gnome.org and also tried some googling and the mailing list, but never got any detailed Information or a step by step guide.
Think it as you have a root password and type "su" as a normal user, 
so a passwort request pops up. Just that I ahve a small textfield in a gtk_dialog that sends the inserted password to just this popped up password request. Maybe there is a function for this in GTK, but never found it.
In my app the request comes from cryptsetup, this has no -p option to pass the password directly to it like mysql has :(,..

Come soneone please help, im stuck for days now 

well, i got the ubuntu soruces for gvm and now try to use the code from there..

thx

---

### Post by -Rick- on 2006-08-08
I'm using modified 'kdesu' code for my project. You can see the code here: [http://svn.berlios.de/viewcvs/nixstaller/trunk/libsu/](http://svn.berlios.de/viewcvs/nixstaller/trunk/libsu/)
The idea is basicly to create a new virtual terminal(with openpty) and use that for input/output.

---

