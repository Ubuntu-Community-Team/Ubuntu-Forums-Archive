---
title: "How to rename multiple files."
date: 2013-04-02
forum: New to Ubuntu
---

### Post by guillaumesoucy on 2013-04-02
Hi, 

I dont know how rename multiple files at the same time. I try several program but thats not work for me because the files I have to rename are emails in .eml format and all the emails dont have the same name so I cannot put things on the fields ''change that'' for ''that''. For the command, I dont understand the rename command for Linux.

I need help please because I dont know what do with that. 

Thanks you in advance!

Guillaume

---

### Post by nerdtron on 2013-04-02
> **guillaumesoucy said:**
> Hi, 

I dont know how rename multiple files at the same time. I try several program but thats not work for me because the files I have to rename are emails in .eml format and all the emails dont have the same name so I cannot put things on the fields ''change that'' for ''that''. For the command, I dont understand the rename command for Linux.

I need help please because I dont know what do with that. 

Thanks you in advance!

Guillaume
```
sudo apt-get install prefixsuffix
```
It's a GUI tool for renaming files. Hope it helps.

---

### Post by steeldriver on 2013-04-02
We can probably help you with the 'rename' command if you explain exactly what you need to do - with a few examples

---

### Post by guillaumesoucy on 2013-04-02
Hi, 

I have tryed PrefixSuffix but thats dont work because the files I need to rename dont have the same name. But I have succesfully put a prefix to all the files but I need to change for example abc.eml and xyz.eml to 123_1.eml and 123_2.eml if possible. Can I do that with PrefixSuffix?

Thanks. 

Guillaume

---

### Post by guillaumesoucy on 2013-04-02
Hi, 

So for the commande, I need some help, so thats will be helpfull to have example please. 

Thanks,

Guillaume

---

### Post by roke1972 on 2013-04-02
I want to rename multiple files too. any suggest?

---

### Post by Derek Karpinski on 2013-04-03
```
#!/bin/bash

i=1

for f in *.eml
do
    mv "$f" 123_$i.eml
    ((i++))
done
```

Pseudo code
```
use bash interpreter

set i to equal 1

for every file with the extention .eml
do the following
     move (rename) f to 123_$i.eml
     increment i by 1
done
```

---

### Post by ronald577 on 2013-04-03
I have tried these code and it was successful too. Thanks for sharing the code.

---

### Post by guillaumesoucy on 2013-04-03
Hi, 

Thanks for the code but how I can precise in what folder I need to rename files. 

Guillaume

---

### Post by guillaumesoucy on 2013-04-04
Hi, 

I have copier the commande in the terminal and thats give me:

guillaumesoucy@zawack-003:~$ use bash interpreter
Commande 'use' non trouvée, vouliez-vous dire :
 La commande 'nse' du paquet 'ns2' (universe)
 La commande 'muse' du paquet 'muse' (universe)
 La commande 'uae' du paquet 'uae' (multiverse)
 La commande 'fuse' du paquet 'fuse-emulator-sdl' (universe)
 La commande 'fuse' du paquet 'fuse-emulator-gtk' (universe)
use : commande introuvable
guillaumesoucy@zawack-003:~$ 
guillaumesoucy@zawack-003:~$ set i to equal 1
guillaumesoucy@zawack-003:~$ 
guillaumesoucy@zawack-003:~$ for every file with the extention .eml
bash: Erreur de syntaxe près du symbole inattendu « file »
guillaumesoucy@zawack-003:~$ do the following
bash: Erreur de syntaxe près du symbole inattendu « do »
guillaumesoucy@zawack-003:~$      move (rename) f to 123_$i.eml
bash: Erreur de syntaxe près du symbole inattendu « rename »
guillaumesoucy@zawack-003:~$      increment i by 1
increment : commande introuvable
guillaumesoucy@zawack-003:~$ done


Something I do wrong? I dont understand anything.


Guillaume

---

### Post by schragge on 2013-04-04
That was a _pseudo_ code just to explain how it works. The real thing is just above it. Putting it in one line:
```
i=0; for f in ~/courriel/*.eml; do [COLOR=#ff0000]echo[/COLOR] mv -nv "$f" 123_$((++i)).eml; done
```

---

### Post by guillaumesoucy on 2013-04-04
Hi, 

The files to renames is on the folder /home/guillaumesoucy/courriel

Where in the code I need to put the directory path?

Thanks, 

Guillaume

---

### Post by schragge on 2013-04-04
I've edited my previous post and also added [COLOR=#ff0000]echo[/COLOR] for testing. If you're satisfied with the output run it without [COLOR=#ff0000]echo[/COLOR] to perform actual renaming.

---

### Post by guillaumesoucy on 2013-04-04
Hi, 

Where I need to put the path of the folder who content files to rename?

Thanks, 

Guillaume

---

### Post by schragge on 2013-04-04
```
i=0; for f in [COLOR=#0000ff]/home/guillaumesoucy/courriel/[/COLOR]*.eml; do mv -nv "$f" ${f%/*}123_$((++i)).eml; done
```

---

### Post by guillaumesoucy on 2013-04-04
Hi, 

I have entered the code but what mean 123_$((++i)) 
 
It is 123 are the new file name? And thats give the file name 123_0.eml 123_1.eml?

Thanks

Guillaume

---

### Post by guillaumesoucy on 2013-04-04
Wow thats work! I change the c of courriel for a capital c and all files was renamed. 

Thanks you very much!

Guillaume

---

### Post by schragge on 2013-04-04
++ means [increment](http://en.wikipedia.org/wiki/Increment_and_decrement_operators), i.e. increase value by one.

That will give names 123_1.eml, 123_2.eml and so on. If you want to start from 0 put ++ after i: 123_$((i++))

---

### Post by guillaumesoucy on 2013-04-04
Hi, 

Another thing, why after files was renamed the files go in /home/guillaumesoucy instead /home/guillaumesoucy/Courriel where the files was located before I rename it?

Thanks,

Guillaume

---

### Post by schragge on 2013-04-04
Oh sorry. I should have noticed that. When you state a bare file name without path prepended it, always means file in current directory, i.e. folder you're in. When you start terminal, the current directory is your home folder, i.e. */home/guillaumesoucy*.
```
mv /home/gillaumesoucy/Courriel/file fichier
``` moves */home/gillaumesoucy/Courriel/file* to */home/gillaumesoucy/fichier*.

---

