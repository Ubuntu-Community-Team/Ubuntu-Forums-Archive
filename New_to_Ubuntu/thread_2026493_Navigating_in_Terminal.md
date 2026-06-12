---
title: "Navigating in Terminal"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Primus1 on 2012-07-15
Hi, I'm sure there is an obvious quick answer to this, I'm making a simple mistake I think.
Learning how to navigate directories using the Terminal. Home/dave is where the problem is I think, Home is a directory? dave is a directory? (dave=me). I can 'cd ..' up to Home but can't go from home to 'dave'. Home and 'dave' are the same folder? Then why is it set out like this - home/dave/temp for instance.

---

### Post by hakermania on 2012-07-15
Hello Primus1!

I always like explaining such things to newbies :D

Well, if you click on this icon:
[IMG]http://i.imgur.com/DYzPl.png[/IMG]
you will result into your home folder. Nautilus is the program which opens and shows you your files. As you can see, nautilus only says 'Home' as the Title of the window and it presents it as the directory in which you are in.

Now, if you press the key combination Ctrl+L you will be able to see the real current path that you are currently in:
[IMG]http://i.imgur.com/tWx3D.png[/IMG]
As you can see, you are not in /Home or whatever nautilus presents you (for beauty reasons) but in /home/username (in my occassion /home/alex/)

So, there are 2 things to keep in mind:
1) /home is a folder, under which there are the home folders of each user. That's why the /home folder is there.
2) /home/dave is a folder of a user. If you had another user installed in your PC (let's say alex), then there would also be the folder /home/alex.

When you open a terminal, you are at /home/dave, automatically.
If you
```

cd ..

```
then you go one directory up, so you are at /home and so as to go back to the dave folder you can do:
```

cd dave

```
But, because /home/dave is your home folder, which is a special folder for you, you can have many alternatives in order to go there. All the following ways will guide you to your home folder:
```

cd
cd ~
cd $HOME

```

If you open a terminal and do a 
```

cd ..

```
and result to /home, then you can also do an
```

ls

```
so as to see what folders and files are available in the directory you are.
In your occasion, you will see 'dave'.

---

### Post by eriktheblu on 2012-07-15
/Home is where all user directories are contained. If you have multiple user accounts, you would also see /Home/bob, /Home/susan etc.

To move from /Home to /Home/dave you could
```
cd dave
``` or ```
cd /Home/dave
``` or ```
cd ./dave
``` or ```
cd ~
```

---

### Post by Shadius on 2012-07-15
Nice explanation! Is there a guide or documentation for this kind of thing, navigating using the Terminal?

---

### Post by Primus1 on 2012-07-15
Thanks all :D What great explanations. I understand the special nature of 'home' now, because it can contain multiple users, makes sense. None of the tutorials I've seen have mentioned this. Thanks again for the help :D.

---

