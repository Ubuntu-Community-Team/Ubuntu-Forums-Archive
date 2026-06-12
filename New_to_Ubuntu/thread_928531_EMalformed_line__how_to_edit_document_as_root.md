---
title: "E:Malformed line / how to edit document as root?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by 3ra on 2008-09-24
As the title says, how do i do it? Guessing i have to be logged in as root, but how exactly do i do that? 

Got an error; E:Malformed line 56 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

And iam guessing i can just "#" that line out, then update aye?

Sorry if this is posted in the wrong section..

---

### Post by Sef on 2008-09-24
> As the title says, how do i do it? Guessing i have to be logged in as root, but how exactly do i do that? 

Got an error; E:Malformed line 56 in source list /etc/apt/sources.list (URI parse), E:The list of sources could not be read.'

And iam guessing i can just "#" that line out, then update aye?

Sorry if this is posted in the wrong section..Applications > Accessories > Terminal

then paste or type this code:

```
gksudo gedit /etc/apt/sources.list
```Once in Gedit, then Edit > Preferences > View > check line numbering  

Next, find line 56 and put a # in front of it to comment it out.

I will move this to Absolute Beginners.

---

### Post by 3ra on 2008-09-24
Hmm well, it wont work. And i did try that command before. It will only open an empty document :/

But with the same name and treepath as the file i want.

---

### Post by Elfy on 2008-09-24
Change ect to etc

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by ad_267 on 2008-09-24
If you run gksu gedit then you should be able to click on open and browse to find the file too. Although if you typed in the file name correctly it should open it.

Edit: I was a bit slow, yeah didn't notice that, it should be etc.

---

### Post by Sef on 2008-09-24
> Change ect to etc

 	Code:
 	gksudo gedit /etc/apt/sources.list 


Thank you for spotting my error.   I have corrected it.

---

### Post by 3ra on 2008-09-24
Thanks guys, but just out of interest, what does gksudo stands for? Have to learn this as well ^^

---

### Post by Idefix82 on 2008-09-24
It means that you mistyped the file name or are looking for it in the wrong directory.
Tip: if you start typing a directory or file name and then hit Tab then the name will be completed if you have typed enough characters to identify the name uniquely. If there are several possibilities then the first Tab won't do anything but hitting it twice will display all the possible completions. This way you can make sure that you don't mistype anything.

---

### Post by Idefix82 on 2008-09-24
gksu is like sudo but you use it for graphical programs

---

### Post by Sef on 2008-09-24
> but just out of interest, what does gksudo  stands for?gksudo is used when going into root and using a graphical appliation in Ubuntu and Xubuntu.  (In Kubuntu, the equivalent is kdesu.)   If you are not using a graphical application, then sudo is what is used for all three oses.

---

### Post by Orange_and_Green on 2008-09-24
In a very nutshell..

"sudo" prepended to a command will execute that command with root privileges. Only system administrators (the "sudoers") can sudo.

"gksu" or "gksudo" must be used instead of "sudo" when executing graphical commands.

[Sorry I was late... and thanks Idefix82 and Sef:)]

---

### Post by 3ra on 2008-09-24
Thanks for clearing things up : )

---

