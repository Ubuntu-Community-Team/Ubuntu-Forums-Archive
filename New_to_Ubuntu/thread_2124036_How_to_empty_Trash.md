---
title: "How to empty Trash ?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Akhj on 2013-03-09
Hello,

How to empty Trash using terminal ?

Thanks & Regards

---

### Post by Malo Kingi on 2013-03-09
I believe the the command is rm -rf ~/.Trash/*. Hope this helps, good luck.

Edit: I'm not sure how to enter the code into one of the fancy boxes you will see on other replys in the fourm. Sorry :)

---

### Post by Mr. Shannon on 2013-03-09
My trash folder is at ~/.local/share/Trash/ not at ~/.Trash/ so you may need to use
```
rm -r ~/.local/share/Trash/*
```
However, a safer method would be to install trash-cli with:
```
sudo apt-get install trash-cli
```
and then you can empty the trash with:
```
trash-empty
```

Hint: I alias rm to the trash-put command (provided by the trash-cli package) so that when I delete files from the command line they go to the trash (sudo will override this though).  This can save you a lot of hassle if you make a mistake when deleting files.

---

### Post by Akhj on 2013-03-09
Thanks Malo. But i've tried that already and not working.

---

### Post by Malo Kingi on 2013-03-09
Well, hopefully Mr. Shannons command line fu is more help, good luck.

---

### Post by Akhj on 2013-03-09
Thanks Shannon but thats too not working :(
P.S. : I don't want to install any package just because i am at learning stage.

---

### Post by Mr. Shannon on 2013-03-09
> **Malo Kingi said:**
> 
Edit: I'm not sure how to enter the code into one of the fancy boxes you will see on other replys in the fourm. Sorry :)

You do this by enclosing in [HTML]```
this is code
```[/HTML] tags.  Please ignore the HTML Code header.  I don't know of another way to escape the code tags.

---

### Post by Malo Kingi on 2013-03-09
Akhj, are you sure your trash folder resides in the directorys we listed?

---

### Post by Malo Kingi on 2013-03-09
> **Mr. Shannon said:**
> You do this by enclosing in [HTML]```
this is code
```[/HTML] tags.  Please ignore the HTML Code header.  I don't know of another way to escape the code tags.

Thanks Mr. Shannon, it was killing me trying to figure it out knowing it was probably simple.

---

### Post by Mr. Shannon on 2013-03-09
> **Akhj said:**
> Thanks Shannon but thats too not working :(
P.S. : I don't want to install any package just because i am at learning stage.

What errors did if give you?

Also, I really recommend you install trash-cli and do it that way.  Using rm with the -r flag and especially * is dangerous if you are not careful.  You could erase all of your files with a single mistyped command.

---

### Post by cheatos on 2013-03-09
hope not to confuse the questioner but in the case of external hard drives using the ```
rm -r
``` command is often the only thing to REALLY get rid of the trash on them. They simply make a directory /.Trash which you cannot remove in any way except for the rm command.

However, when doing the rm command, as long as you don't giv eit super user privileges, it cannot harm your system, your personal files it may delete though, so still to be careful.
Its best to know what the rm command does with its several flags (the -r for example) so the -r means that all directories AND their contents will be removed, and the * option just means that ANY file or directory will be deleted. YOu cannot recover files removed with rm, so that why you need to be extra careful.

---

### Post by Akhj on 2013-03-10
Thanks Shannon, this command ```

rm -r ~/.local/share/Trash/*
``` worked for me this time :)

Well what is the difference between rm -r & rm -rf ?

---

### Post by siddharth007 on 2013-03-11
For me the Trash folder was located in /home/username/.local/share/Trash/. I found it out using this command 
```
find / -type d -name *Trash*
```

Then i issued this command 
```
rm -r /home/fortunepay/.local/share/Trash/files/*
```

Voila it worked. So for those who are unable to locate their Trash folder,use the find command and then use rm -r command to remove the contents of **files **directory under Trash.:guitar:

---

### Post by lisati on 2013-03-11
> **Mr. Shannon said:**
>   Please ignore the HTML Code header.  I don't know of another way to escape the code tags.

[noparse][noparse] and [/noparse][/noparse] will do the trick.....

---

### Post by lisati on 2013-03-11
> **Akhj said:**
> 
Well what is the difference between rm -r & rm -rf ?

According to the man page, the "f" (short for "force") says to ignore nonexistent files, and to never prompt.

**Important:** be* very very very *careful with the -rf version of the rm command. When applied in the wrong place, it can cause serious frustration due to major loss of data

---

### Post by Akhj on 2013-03-11
Thanks to all of you :)

---

