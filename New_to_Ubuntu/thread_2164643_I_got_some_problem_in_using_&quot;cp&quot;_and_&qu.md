---
title: "I got some problem in using &quot;cp&quot; and &quot;rm&quot; command"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by linc2 on 2013-08-01
hi guys, This is the first day I use Linix OS,
I got two problem,see the picture please
[IMG]http://img.bbs.csdn.net/upload/201308/01/1375357613_971418.jpg[/IMG]

[IMG]http://img.bbs.csdn.net/upload/201308/01/1375357639_559961.jpg[/IMG]

do I use the wrong form for those two commands?(I use "mkdir"create cat,dog,etc.) Thank you!

---

### Post by GwL3eNC on 2013-08-01
Hi,

cp -r ../foo/cat1 wheretocopyit

i think and dont give the ~
after cd cool you are in it. the folder foo is one step back. you do that with ..
You have to use the -r because you want to copy a folder. Wheretocopy it is also a path.

cp -r ../foo/cat1 /home/yourname/ will copy it to your home folder

please view also cp --help

Also rm -r if you want to delete a folder.

---

### Post by sudodus on 2013-08-01
Welcome to the Ubuntu Forums :-)

***rm*** removes files, and with the ***-r*** option it also removes directories with their content, as described by  				 				 					 						 	*GwL3eNC*.

You can remove an empty directory with ***rmdir***

I use an alias to make rm safer (to get a question before remove a file).

```
 alias rm='rm -i'
```

and I add that line into the file **[FONT=courier new]~/.bashrc[/FONT]** (near the other alias commands).

You can find many tutorials about bash and command lines browsing the internet, or starting here

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by linc2 on 2013-08-05
Thank you GwL3eNC, I got it ,I have checked the help about cp and rm command.It's really helpful for me to understand how to use them.By the way,I try both ..and ~,they are the same effect,and because my current working folder is foo ,so I can just put "cp -r cat1 wheretocopyit",then I can copy direction cat1 to wheretocopyit.;)

---

### Post by linc2 on 2013-08-05
Thanks sudodus,you are a very nice gentleman! The resource you put on is very helpful to me.I will keep study in Linux!

---

