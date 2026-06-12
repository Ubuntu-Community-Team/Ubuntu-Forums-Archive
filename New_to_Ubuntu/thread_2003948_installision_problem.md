---
title: "installision problem"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Hasan55 on 2012-06-14
can anyone help me to slove this problem? 
i have recently installd ubuntu 11.04 natty . i also updated it to install tarball but i can not  still install this tar.ball. i have downloaded rhythmbox-0.13.3.tar.gz which was download is Home---->Downloads folder. what command should i use ..........please let  help me out of it.

---

### Post by Shadius on 2012-06-14
What's the problem?

---

### Post by sammiev on 2012-06-14
> **Hasan55 said:**
> can anyone help to slove this problem?

Hi Hasan55 and welcome to the forums. Please post as much info as possible so we can help. We need to know what you are trying to install and on what. Give us all the info please. :)

---

### Post by Shadius on 2012-06-14
More details the better also. :)

---

### Post by afixane on 2012-06-14
> **Shadius said:**
> More details the better also. :)

And screenshot will make it better, too ;)

---

### Post by Shadius on 2012-06-14
> **afixane said:**
> And screenshot will make it better, too ;)

Agreed. So, as you can see, we're eager to offer assistance! :D

---

### Post by afixane on 2012-06-14
> **Hasan55 said:**
> can anyone help me to slove this problem? 
i have recently installd ubuntu 11.04 natty . i also updated it to install tarball but i can not  still install this tar.ball. i have downloaded rhythmbox-0.13.3.tar.gz which was download is Home---->Downloads folder. what command should i use ..........please let  help me out of it.

If the available file is in .tar.gz format, you must compile it.

---

### Post by Shadius on 2012-06-14
Why not just install Rhythmbox from the Ubuntu Software Center?

---

### Post by afixane on 2012-06-14
> **Shadius said:**
> Why not just install Rhythmbox from the Ubuntu Software Center?

Yes, you're right. Hey OP, it's easier install something from Software-Centre :P

---

### Post by Shadius on 2012-06-15
> **Hasan55 said:**
> can anyone help me to slove this problem? 
i have recently installd ubuntu 11.04 natty . i also updated it to install tarball but i can not  still install this tar.ball. i have downloaded rhythmbox-0.13.3.tar.gz which was download is Home---->Downloads folder. what command should i use ..........please let  help me out of it.

I don't know if you're new to Ubuntu Linux, but in case you are, my advice to you is if you want to install anything, the Ubuntu Software Center is the go-to place for that as well as removing what you installed. I hope we were able to solve your problem. :)

---

### Post by Hasan55 on 2012-06-15
hi, there i know that how to use ubuntu software  center for software installison . but i want to learn how to use terminal by installing a tar.ball recently i have downloaded rhythmbox-0.13.3.tar.gz which is in the "Desktop" and i also extracted it in the desktop without using terminal. but when i go to the next command for installision by using terminal e.g


hasan@Hasan-desktop:~$ cd/home/hasan/Desktop/rhythmbox-0.13.3.tar.gz
bash: cd/home/hasan/Desktop/rhythmbox-0.13.3.tar.gz: No such file or directory
hasan@Hasan-desktop:~$ 

then nothing happen what should i do right now.  what the command should i use   please help me.........:(

---

### Post by Shadius on 2012-06-15
> **Hasan55 said:**
> hi, there i know that how to use ubuntu software  center for software installison . but i want to learn how to use terminal by installing a tar.ball recently i have downloaded rhythmbox-0.13.3.tar.gz which is in the "Desktop" and i also extracted it in the desktop without using terminal. but when i go to the next command for installision by using terminal e.g


hasan@Hasan-desktop:~$ cd/home/hasan/Desktop/rhythmbox-0.13.3.tar.gz
bash: cd/home/hasan/Desktop/rhythmbox-0.13.3.tar.gz: No such file or directory
hasan@Hasan-desktop:~$ 

then nothing happen what should i do right now.  what the command should i use   please help me.........:(

Take a look here. This method seems fairly easy. [How To Install A .tar.gz File]("http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-file")

---

### Post by afixane on 2012-06-15
Umm, Hasan55, if you want to learn Command Line, i recommend you to learn to installing program from terminal :D

---

### Post by Shadius on 2012-06-15
> **afixane said:**
> Umm, Hasan55, if you want to learn Command Line, i recommend you to learn to installing program from terminal :D

Here's a good place to start. [Click Here]("http://ubuntuforums.org/showthread.php?t=1909108")

---

### Post by Financing Dragons on 2012-06-16
You can try ark archiving tool. What I normally use.

If comes installed with the operating system on kubuntu.

But this is how you install it

You can either install it with the software manager by doing a search for ark

or in the terminal type

sudo apt-get install ark

---

### Post by Hasan55 on 2012-06-16
hi, there thanks for your link for learning linux . there are lot of things for learning but i can not handle of all those things in short time ........so can u help me to tell what the command should i use in the terminal of my problem. i am waiting for your reply.....................:p

---

### Post by afixane on 2012-06-16
```
tar thefilename.tar.gz
cd extractionfolder
./configure
make
sudo make install
```
That's the code (if i'm not wrong)

---

### Post by codingman on 2012-06-16
I wouldn't recommend installing from a tarball, I would recommend learning how to use the dpkg frontend called apt-get.

---

### Post by Hasan55 on 2012-06-16
hi, there when i am going to your following command then that happend

hasan@Hasan-desktop:~$ tar rhythmbox-0.13.3.tar.gz
tar: Old option `b' requires an argument.
Try `tar --help' or `tar --usage' for more information.
hasan@Hasan-desktop:~$

now what.............................

---

### Post by codingman on 2012-06-16
open up the help file or manual for more information, those pages are really useful for beginners and even middle class and expert users.

---

### Post by Hasan55 on 2012-06-16
where i can get the help file about tar installision .........is there any command in the terminal ..............what is it please write it on the post.

---

### Post by afixane on 2012-06-16
```
sudo apt-get install build-essential
```

Then extract your package to anywhere (i recommend the /home/user folder)

```
cd extractionfolder
./configure
make
sudo make install
```

---

### Post by afixane on 2012-06-16
> **Hasan55 said:**
> where i can get the help file about tar installision .........is there any command in the terminal ..............what is it please write it on the post.

Read the readme on the .tar.gz

---

### Post by codingman on 2012-06-16
try:
```
man tar
```

---

