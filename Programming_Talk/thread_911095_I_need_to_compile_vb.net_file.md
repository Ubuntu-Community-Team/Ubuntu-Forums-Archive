---
title: "I need to compile vb.net file"
date: 2008-09-05
forum: Programming Talk
---

### Post by Uchiha_madara on 2008-09-05
hi every one 

.............


i use mono develop program to create My own .net projects but 
the problem is when i need to run it there well be an error 
message :

I read the tutorial in this site :

[http://www.monodevelop.com](http://www.monodevelop.com)

but I don't understand , I need some body to tell me how can I compile My project and run it .......

please help me ...

---

### Post by cb951303 on 2008-09-05
you forgot the error msg

---

### Post by dgoosens on 2008-09-05
hi,

you probably forgot to install the gmcs

```
sudo apt-get install mono-gmcs
```

should make it work...

---

### Post by Zugzwang on 2008-09-05
> **dgoosens said:**
> 
you probably forgot to install the gmcs


I would say he/she rather needs vbnc: [http://www.go-mono.com/docs/index.aspx?tlink=8@man%3avbnc(1)]("http://www.go-mono.com/docs/index.aspx?tlink=8@man%3avbnc(1)")

---

### Post by themusicwave on 2008-09-05
The only way anyone can help you is if you tell us the exact error message and the snippet of code it relates to.

Otherwise, it is all just guessing.

---

### Post by Uchiha_madara on 2008-09-05
> **themusicwave said:**
> The only way anyone can help you is if you tell us the exact error message and the snippet of code it relates to.

Otherwise, it is all just guessing.

I am now fixing My Laptop The Screen is broken .....

how ever the message Like this form :
if we have this small Application :

Book.vb // there is no error in the Syntax
        // but the message is seems Like this form :

> there is an error in Book.exe 

I don't Know what does this Mean......:confused:

---

### Post by Uchiha_madara on 2008-09-05
> **dgoosens said:**
> hi,

you probably forgot to install the gmcs

```
sudo apt-get install mono-gmcs
```

should make it work...


mono-gmcs..... what does it make in mono develop:confused:

---

### Post by themusicwave on 2008-09-05
> **Uchiha_madara said:**
> I am now fixing My Laptop The Screen is broken .....

how ever the message Like this form :
if we have this small Application :

Book.vb // there is no error in the Syntax
        // but the message is seems Like this form :



I don't Know what does this Mean......:confused:

I think we will really need the exact error message and code to help.  I don't even have a clue from this message.

---

### Post by true_friend on 2008-09-06
mono-gmcs is the c# 2 compiler for mono. vbnc is for visual basic. But *recommended* is to use c# with mono, it is more mature and error free. VB.net is not a standard and not implemented wholly yet perhaps 60 to 70%.
Regards

---

### Post by Uchiha_madara on 2008-09-06
> **themusicwave said:**
> The only way anyone can help you is if you tell us the exact error message and the snippet of code it relates to.

Otherwise, it is all just guessing.

this is the error : 

> 
[FONT="Courier New"]
Building Solution vesa

Building Project: vesa (Debug)
Performing main compilation...
vbnc -out:"/home/laroza/vesa/vesa/bin/Debug/vesa.exe" -nologo -utf8output -target:exe  "/home/laroza/vesa/vesa/Books.vb" "/home/laroza/vesa/vesa/AssemblyInfo.vb" "/home/laroza/vesa/vesa/BooksMenu.vb"

Build failed. ApplicationName='vbnc', CommandLine='"@/tmp/tmp277e3d44.tmp"', CurrentDirectory='/home/laroza/vesa/vesa', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'

[/FONT]

:KS:KS:KS:KS

---

### Post by Steveway on 2008-09-06
> /home/**laroza**/vesa/vesa/bin/Debug/vesa.exe
Wait, what?
Is that a double-account by laroza or just a coincidence?

---

### Post by Uchiha_madara on 2008-09-06
> **Steveway said:**
> Wait, what?
Is that a double-account by **laroza** or just a coincidence?

don't worry .. this is the user name.....
i use it in ubuntu on My Laptop....

....do you solve My problem ??

---

### Post by Uchiha_madara on 2008-09-07
> **true_friend said:**
> mono-gmcs is the c# 2 compiler for mono. vbnc is for visual basic. But *recommended* is to use c# with mono, it is more mature and error free. VB.net is not a standard and not implemented wholly yet perhaps 60 to 70%.
Regards

i give you the error message......

so ..... do you advice me to install mono-gmcs, and vbnc .....??


the problem I am better in vb.net more than c#:popcorn:

---

### Post by Zugzwang on 2008-09-07
vnbc *must* be installed if you want to compile vb.net in mono. It is *not* automatically installed when you install monodevelop.

Apart from that, it seems like the error message is actually swallowed by monodevelop. Try to execute the main building command from the terminal:
```

vbnc -out:"/home/laroza/vesa/vesa/bin/Debug/vesa.exe" -nologo -utf8output -target:exe "/home/laroza/vesa/vesa/Books.vb" "/home/laroza/vesa/vesa/AssemblyInfo.vb" "/home/laroza/vesa/vesa/BooksMenu.vb"

```

And paste here what you get.

---

### Post by Uchiha_madara on 2008-09-10
> **Zugzwang said:**
> vnbc *must* be installed if you want to compile vb.net in mono. It is *not* automatically installed when you install monodevelop.

Apart from that, it seems like the error message is actually swallowed by monodevelop. Try to execute the main building command from the terminal:
```

vbnc -out:"/home/laroza/vesa/vesa/bin/Debug/vesa.exe" -nologo -utf8output -target:exe "/home/laroza/vesa/vesa/Books.vb" "/home/laroza/vesa/vesa/AssemblyInfo.vb" "/home/laroza/vesa/vesa/BooksMenu.vb"

```

And paste here what you get.


how can i install vbnc ?

because there was an error : vbnc : command not found

---

### Post by Zugzwang on 2008-09-10
> **Uchiha_madara said:**
> how can i install vbnc ?

because there was an error : vbnc : command not found

It's always best to search for a solution yourself first. Searching in the Ubuntu Forums would have given you the following thread containing a solution: [http://ubuntuforums.org/showthread.php?t=481686&highlight=vbnc]("http://ubuntuforums.org/showthread.php?t=481686&highlight=vbnc")

---

### Post by Uchiha_madara on 2008-09-10
> **Zugzwang said:**
> It's always best to search for a solution yourself first. Searching in the Ubuntu Forums would have given you the following thread containing a solution: [http://ubuntuforums.org/showthread.php?t=481686&highlight=vbnc]("http://ubuntuforums.org/showthread.php?t=481686&highlight=vbnc")



Thanks A lot ..... I'll try ....

-- can i write the vbnc statement to compile the vb file as you said above ???

> -- Add/remove Applications give me Open source .. does that it give non-complete Software, so i need to install the Application From the Official site ..... is that true or not ?

---

### Post by Zugzwang on 2008-09-10
> **Uchiha_madara said:**
> Can i write the vbnc statement to compile the vb file as you said above ???

Don't know. Why don't you just try?

BTW: There seems to be no apparent reason why you tend to repeat punctation marks. Also please spent a little bit more time on writing your posts since it's hard to guess what you are actually trying to say.

---

