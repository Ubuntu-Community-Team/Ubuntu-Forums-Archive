---
title: "ccd2iso"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by forrest898 on 2012-02-23
i installed ccd2iso and when i put "ccd2iso myfile.img myfile.iso" into terminal andhit enter, it just skips to the next line and has a ">" on the left, how do i use this program correctly to just convert my .img?????

---

### Post by alegomaster on 2012-02-23
Welcome to the Ubuntu Forums!

How big is your image?

---

### Post by forrest898 on 2012-02-23
736.8 mb

---

### Post by alegomaster on 2012-02-23
My guess is that the > is showing that the computer is processing the .img container to convert it to the .iso container. How long did you leave the terminal running after you executed the command.

---

### Post by forrest898 on 2012-02-23
a minute or two... i got kind of impatient because i didnt think it was working...

---

### Post by sffvba[e0rt on 2012-02-23
From what I can find on ccd2iso you are using it correctly (the only thing I might add you can make sure of is that you are indeed in the correct directory when you excecute the command and that you have all the needed read-write access etc. in it).

A hack you can try is to simply rename the file from .img to .iso... works for some.


404

---

### Post by alegomaster on 2012-02-23
I believe it takes a while to convert the file container especially with a large file like that. Can you rerun the tool for longer, and can you post what processor you have in your computer.

---

### Post by forrest898 on 2012-02-23
tried to just rename to iso, it was no good.
i left the tool running for some time(15-20minutes) and the ">" did not change or complete
i have an AMD Athlon II X4 965

---

### Post by jacob.david on 2012-02-23
Just a trivial one though. The > indicates the second prompt (PS2) i.e. the OS expects more to execute the command. Do you have any unclosed quotes are something like that. If you press another enter it will display another > in this case until you complete the command correctly. Do you have any unfinished quotes etc.?
Sorry if you already know about this.

---

### Post by forrest898 on 2012-02-23
i did not know that (still very new to unix...) but i do not believe that i have any unclosed things in my code

---

### Post by forrest898 on 2012-02-23
now something different happens,
when i try it i get this:

forrest@ForrestsUbuntuPartition:~$ ccd2iso /home/forrest/ISO's/cd2/sc4d2.img
/home/forrest/ISO's/cd2/sc4d2.iso
Unknown option: /home/forrest/ISOs/cd2/sc4d2.img
/home/forrest/ISOs/cd2/sc4d2.iso !

---

### Post by xumuk37 on 2012-02-23
try to put different name to second file, i.e. 
ccd2iso /home/forrest/ISO's/cd2/**sc4d2**.img
/home/forrest/ISO's/cd2/**2sc4d2**.iso

---

### Post by forrest898 on 2012-02-23
received the same error message

---

### Post by alegomaster on 2012-02-23
> **jacob.david said:**
> Just a trivial one though. The > indicates the second prompt (PS2) i.e. the OS expects more to execute the command. Do you have any unclosed quotes are something like that. If you press another enter it will display another > in this case until you complete the command correctly. Do you have any unfinished quotes etc.?
Sorry if you already know about this.

Doesn't it also stand for loading? To me it looks like he got it all perfect with the command so I discarded that idea.

---

### Post by alegomaster on 2012-02-23
> **forrest898 said:**
> now something different happens,
when i try it i get this:

forrest@ForrestsUbuntuPartition:~$ ccd2iso /home/forrest/ISO's/cd2/sc4d2.img
/home/forrest/ISO's/cd2/sc4d2.iso
Unknown option: /home/forrest/ISOs/cd2/sc4d2.img
/home/forrest/ISOs/cd2/sc4d2.iso !

Do the following commands and post any error messages you get:
```

cd /home/forrest/ISO's/cd2
ccd2iso sc4d2.img 2sc4d2.iso

```

---

### Post by forrest898 on 2012-02-23
i did exactly that and only came up with the ">" no error messages just the ">"

---

### Post by alegomaster on 2012-02-23
Try this:
```

cd /home/forrest/ISO's/cd2
ccd2iso "sc4d2.img" "2sc4d2.iso"

```

---

### Post by forrest898 on 2012-02-23
still just that same symbol....

---

### Post by alegomaster on 2012-02-23
What kind of img file are you converting?

---

### Post by forrest898 on 2012-02-23
its a game

---

### Post by alegomaster on 2012-02-23
Did you use CloneCD to get the .img file

---

### Post by forrest898 on 2012-02-23
no...
I just used a program called AcetoneISO to convert the image, problem solved.
Thanks for your help though!

---

### Post by alegomaster on 2012-02-23
Can you please use the thread tool to mark this as solved it is on the top right of the thread when you are in it.

---

