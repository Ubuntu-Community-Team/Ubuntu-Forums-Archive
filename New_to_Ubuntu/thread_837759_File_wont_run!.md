---
title: "File wont run!"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by necronzero on 2008-06-22
I have a keygen file, when i drag it to terminal, i only get:

PERMISSION DENIED...

WTF! ive used this keygen on another machine doing the drag and drop to terminal and everything went fine... 
Any clues?

---

### Post by Biggy on 2008-06-22
put keygen in home folder

from terminal :

chmod +x keygen

./keygen

---

### Post by DGortze380 on 2008-06-22
No experience with keygen, never dragged and dropped to a terminal... but...

open a terminal, navigate to the folder that the file is in, type ls -al , copy and paste the line for the file here. Sounds like a simple permissions error which can be fixed with the following commands run in the folder where the keygen file is located:

sudo chown <username> (make sure you own the file)
sudo chmod 700 <filename> (gives owner read/write/execute privledges and no one else)

---

### Post by necronzero on 2008-06-22
> **Biggy said:**
> put keygen in home folder

from terminal :

chmod +x keygen

./keygen

wow that worked... thanks buddy

---

### Post by johnhammonds on 2009-03-02
> **Biggy said:**
> put keygen in home folder

from terminal :

chmod +x keygen

./keygen

I was trying to figure out how to run a KeyGen on my Mac and ran across this. This worked for my Mac (Leopard v10.5.6) as well!

Thanks!

---

### Post by bigbule on 2009-04-30
when you say "home folder" what do you mean? do you mean the application folder, documents, or just the Macintosh HD, or what? I tried this and it didn't work for me. I apologize for my ignorance. Thank You.

---

### Post by Perfect Storm on 2009-04-30
> **bigbule said:**
> when you say "home folder" what do you mean? do you mean the application folder, documents, or just the Macintosh HD, or what? I tried this and it didn't work for me. I apologize for my ignorance. Thank You.

Home folder, normally it's set as default, but you can do this;
```
cd
```
to take you back to you home folder (directory).
If the key is on your Desktop;
```
cd ~/Desktop
```
and then execute the key file.

---

### Post by bigbule on 2009-04-30
i keep trying different things but all i get is "bus error"

---

### Post by bigbule on 2009-04-30
> **Artificial Intelligence said:**
> Home folder, normally it's set as default, but you can do this;
```
cd
```
to take you back to you home folder (directory).
If the key is on your Desktop;
```
cd ~/Desktop
```
and then execute the key file.
does it make any difference that my mac is a powerbook G4 and not intel based?

---

### Post by DGortze380 on 2009-04-30
> **bigbule said:**
> does it make any difference that my mac is a powerbook G4 and not intel based?

yes if you didn't compile the keygen from source.
no, probably not if it's just a shell script.

---

### Post by Kd40 on 2009-08-24
> **Biggy said:**
> put keygen in home folder

from terminal :

chmod +x keygen

./keygen

I dont really get what you meen? *noob here*

i copied and pasted in ```
chmod +x keygen

./keygen
```

but all that happened was ```
chmod: cannot access `chmod': No such file or directory
chmod: cannot access `+x': No such file or directory
chmod: cannot access `keygen': No such file or directory
kd40@tango-laptop:~$ 
kd40@tango-laptop:~$ ./keygen
bash: ./keygen: No such file or directory
kd40@tango-laptop:~$ 

```

Also i moved the keygen to my homefolder.

im trying to download a windows one which im guessing wine is doing half the work in?

---

