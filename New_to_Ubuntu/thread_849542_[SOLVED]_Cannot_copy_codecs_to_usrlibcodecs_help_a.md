---
title: "[SOLVED] Cannot copy codecs to usr/lib/codecs help a newbit please"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by downs on 2008-07-04
So I've been very impressed so far with ubuntu aside from this issue most every other problem I've had (not many) I have been able to fix on my own.

So here I have downloaded a bunch of videos killer find, but they are all real media.  

Found a link telling me to intsall mplayer and lib++s or somethign along those lines, got them all installed.

Now I need to install the codecs, no luck.

I've done into the terminal and navigated to the folder on my desktop using cd Desktop
cd codecs

but when i try and copy to the folder i created in user/lib/ which is codecs I get an error cp missing destination file operand

i cant tell you which version i have unfortunatley unless maybe i reboot? is that how you tell? 

and im sure this is an easy thing but i have looked and looked and looked 
and searched and searched and searched

totally new to terminal so im probably screwing something up 

any help would be fantastic

---

### Post by kostkon on 2008-07-04
I assume you mean you want windows codecs, which are copied in this folder (/usr/lib/codecs). You don't need to do anything yourself. There is a package containing the codecs that will setup everything for you.

Just add the [*Medibuntu* repository]("http://medibuntu.org/") to your software sources list (instructions on how to do it are in the site) and then from Synaptic install the package named *w32codecs*.

I hope that helps.

---

### Post by downs on 2008-07-04
windows codecs? maybe
i followed instructions on a page that had me download mplayer and its associated files
i have mplayer installed 
but following the instructions on that site it seems i need to copy these files
actuallyyes the original source to copy was usr/lib/win32
neither seem to let me copy in terminal 

anyway i just want to watch the movies so i dont really care how 
ill follow your link and post my results

thanks for the speedy reply

---

### Post by downs on 2008-07-04
NICEEEE
thanks so much 
Medibuntu worked perfectly 

thanks again very much for your speedy and helpful reply

---

### Post by kostkon on 2008-07-04
> **downs said:**
> actuallyyes the original source to copy was usr/lib/win32
Then indeed you are talking about the windows codecs. Actually the *w32codecs* package will create a soft link from */usr/lib/win32* to */usr/lib/codecs*. 

This is done because some applications search for these codecs in */usr/lib/win32* and others in */usr/lib/codecs*.

So, don't worry, just install the *w32codecs* package and you'll be ready.

---

### Post by kostkon on 2008-07-04
> **downs said:**
> NICEEEE
thanks so much 
Medibuntu worked perfectly 

thanks again very much for your speedy and helpful reply
No problem! :)

---

