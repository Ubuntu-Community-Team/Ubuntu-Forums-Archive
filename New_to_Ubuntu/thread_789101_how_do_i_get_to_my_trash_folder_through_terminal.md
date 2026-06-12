---
title: "how do i get to my trash folder through terminal?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by savethewabbit on 2008-05-10
there's a folder in my trash that i can't delete permanently because it says i don't have permission to read/move/anything it.
so i thought i should login as root and go remove the file manually, meaning via terminal, but i can't find my trash folder anywhere on my computer. what is the path to it? searching in File System only got me a  "trashapplet" folder...
or, is there a way to log in as root without using the terminal therefore deleting said file through nautilus?

thanks.

---

### Post by joshsmith on 2008-05-10
hey
if you run in terminal 
gksu nautilus
you open up the root file browser giving you permission to do whatever you want to your file system 

(warning it will also let you delete system files, so dont use it permanently, and only use it on things you know what you are doing)

but the other piece of info you need for both doing it in nautilus or in the terminal is that your trash folder is located in
/home/{your username}/.local/share/Trash
 
(you cant just go into trash on the left panel in the root file browser as this will take you to the root trash (ie not yours))

---

### Post by savethewabbit on 2008-05-10
great, it worked wonderfully. thanks a lot!

---

