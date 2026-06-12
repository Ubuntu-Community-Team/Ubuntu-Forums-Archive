---
title: "Ubuntu 9.04 addressing problem with cp command in terminal"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-09-29
I have to copy a file from the $home/henk/... directory to another directory .  I tried to copy the file using the GNOME environment with copy/paste, it says 'permission denied' .  So I try to copy it using the cp command in a terminal : This copy command always gives me the error that the $home/henk/... file does not exist .  I tried it with 'henk/...', '/henk/...', 'home/henk/...', '/home/henk/...', '$home/henk/...' and '/$home/henk/...', and it always gives that same error : Which mistake do I make in addressing the source of the /home/henk/... file ?

---

### Post by Petro Dawg on 2013-09-29
Are you using "sudo" before your copy command?

Also does using...

```
~/
```

in the place of...

```
/home/henk/
```

work?

Alternatively you could launch your file manager from terminal using "sudo nautilus" or what ever file manager was used on 9.04.  Then you would be able to move files in the system directories in the GUI,** AS WELL AS TRASH YOUR SYSTEM**, so be careful.

---

### Post by sandyd on 2013-09-29
> **Hankbonk said:**
> I have to copy a file from the $home/henk/... directory to another directory .  I tried to copy the file using the GNOME environment with copy/paste, it says 'permission denied' .  So I try to copy it using the cp command in a terminal : This copy command always gives me the error that the $home/henk/... file does not exist .  I tried it with 'henk/...', '/henk/...', 'home/henk/...', '/home/henk/...', '$home/henk/...' and '/$home/henk/...', and it always gives that same error : Which mistake do I make in addressing the source of the /home/henk/... file ?

fyi - ubuntu 9.04 has reached end of life - I reccomend you upgrade to a LTS Release such as Ubuntu 12.04

Releases that have reached end of life will not receive software or security updates.

An upgrade is not always the best option - sometimes a new installation may be better.

Make sure backups are done before upgrading/reinstalling

---

### Post by heir4c on 2013-09-29
When you see 'permission denied' than you have no rights to change something. To which directory you want to move it.
Normally it is:
```
cp /home/henk/... /path/to/other/directory
```
Between the 2 file/directory's you need a space.
with rootrights:
```
sudo cp /home/henk/... /path/to/other/directory
```


But why you use 9.04. :confused: That is no more supported. Download 12.04 and have a new install. Don't forget: Backup al your files and bookmarks, etc....

---

### Post by oldos2er on 2013-09-29
The $HOME variable defaults to /home/user, not /home

---

### Post by Hankbonk on 2013-09-30
Nope Petro, the cp command still doesn't find the libflashplayer.so ...

---

### Post by Hankbonk on 2013-09-30
Dear oldos2er,

I tried that allready before I posted the thread . The error is always :

cp cannot stat '/home/henk/.../libflashplayer.so' : No such file or directory

I really have tried every possible combination that could come to my mind ...

---

### Post by steeldriver on 2013-09-30
Let's see exactly what the path is - either
```
find ~/ -name 'libflashplayer.*'
```
or
```
locate libflashplayer
```

---

### Post by Hankbonk on 2013-09-30
Dear heir4c,

I only get the Permission denied error when I try to copy/paste the file in the GUI, That's why I'm trying to use the cp command !
In my  original post all these things I mentioned allready, please read it fully, thank you

When I use the cp command, I get :

cp cannot stat '/home/henk/.../libflashplayer.so' : No such file or directory

Thanks for your quick reply .  Uploading the 12.04 LTS is something I would like to do, but I share this PC with a network engineer : He works and prepairs the system for future Linux programming, then He will teach me fully .  I only work on it during evenings/nights .

---

### Post by Petro Dawg on 2013-09-30
I think what **heir4c** was trying to point out is that usually if you get a "permission denied" error in the GUI, you will not be able to simply use the "cp" command in terminal without running as super user.  Doing things in terminal does not automatically grant you more privileges. You still have not answered the question... are you using "sudo" before using the "cp" command?

---

### Post by Hankbonk on 2013-09-30
This thread is to be solved (I shall do that instantly, after explaining my error

dear friends,

I had ab error in one of the directories names : It had a space behind it !  Now I renamed it and the cp command was executed !

Thanks for all your replies so quickly !!!

---

