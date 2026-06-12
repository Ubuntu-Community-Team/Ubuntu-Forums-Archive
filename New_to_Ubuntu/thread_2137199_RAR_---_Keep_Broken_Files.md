---
title: "RAR --- Keep Broken Files"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by czgirb on 2013-04-20
I was a Windows user before.
I often received a **RAR** file, which are stated to be "**there is an ERROR**". But, since there is a **Keep Broken Files** option. So, I successfully extract the compressed file.
But in Ubuntu, I unable to found that options.
Please guide me ......

---

### Post by matt_symes on 2013-04-20
Hi

From the terminal....

```
unrar -kb .......
```

From man unrar

> -kb    Keep broken extracted files.

Does that help ?

Kind regards

---

### Post by czgirb on 2013-04-20
> **matt_symes said:**
> Hi
From the terminal....
```
unrar -kb .......
```
From man unrar
Does that help ?
Kind regards

[SIZE=5]**SORRY !!!!! SORRY !!!!!**[/SIZE]
I'm a newbie and my knowledge for Ubuntu is very very limited.
So ... please do a favor by described above process more detail
Thank you ...

---

### Post by matt_symes on 2013-04-20
Hi

Sometimes i make assumptions. Sorry about that.

I'll look around to see if i can find a GUI (window) way for you to do it.

This method uses the terminal.

In my directory there is a rar file called a.rar.

```

matthew-S206:/home/matthew/rara % ls
a.rar
matthew-S206:/home/matthew/rara % 
```

i can unzip the file using the command unrar. It has the -kb switch to keep broken file and uses the e command to extract the files.

Take a look at this.
```

matthew-S206:/home/matthew/rara % ls       
a.rar
matthew-S206:/home/matthew/rara % unrar e -kb a.rar

UNRAR 4.10 freeware      Copyright (c) 1993-2012 Alexander Roshal


Extracting from a.rar

Extracting  a                                                         OK 
Extracting  aa                                                        OK 
Extracting  aaa                                                       OK 
All OK
matthew-S206:/home/matthew/rara % ls
a  aa  aaa  a.rar
matthew-S206:/home/matthew/rara % 
```

I'll look at see if i can't find a method that does not use the terminal for you though.

Kind regards

---

