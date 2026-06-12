---
title: "Vi editor"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-05
Hi,
I'm very interesting Vi. So i want to install it and i google it. But i'm not found how to install it. So how can i install it ? Any Idea ?

---

### Post by Amstell on 2008-05-05
just go to your console and type sudo vi <filename>

it should load up whatever filename you choose.

Be careful as the commands are a little hard to get use to.

---

### Post by T-Virus on 2008-05-05
It should be installed by default, yes. But if by any chance it's not.

```
sudo apt-get install vi
```

Actually, I'm not sure even sure it may be available at repos. :)


EDIT: It was a funny try, he heh. No it's default all the time, there is no Vi at repositories.

---

### Post by Zeck on 2008-05-05
> **T-Virus said:**
> It should be installed by default, yes. But if by any chance it's not.

```
sudo apt-get install vi
```

Actually, I'm not sure even sure it may be available at repos. :)


EDIT: It was a funny try, he heh. No it's default all the time, there is no Vi at repositories.

Thanks for your advice. He he.

Regards,
Zeck

---

### Post by Monicker on 2008-05-05
> **T-Virus said:**
> It should be installed by default, yes. But if by any chance it's not.

```
sudo apt-get install vi
```

Actually, I'm not sure even sure it may be available at repos. :)


EDIT: It was a funny try, he heh. No it's default all the time, there is no Vi at repositories.

Vim (VI Improved) is in the repos, and vim-tiny is installed by default on Ubuntu.

---

### Post by T-Virus on 2008-05-05
Thanks for heads up mate. I remember using Vi with Unix System V Release 4.2 all the way back in 1993.

---

### Post by Tart on 2008-05-05
You probably should try to get vim-full. It is available through symantec. When i tried to use regular vi, it didn't do spell checking. :set spell didn't do anything. vim-full on the other hand  works perfectly

```

sudo apt-get install vim-full

```

---

### Post by Zeck on 2008-05-05
> **Tart said:**
> You probably should try to get vim-full. It is available through symantec. When i tried to use regular vi, it didn't do spell checking. :set spell didn't do anything. vim-full on the other hand  works perfectly

```

sudo apt-get install vim-full

```


Thanks a lot. So how to use it. Could you teach me simple tutorials ?

---

### Post by scorp123 on 2008-05-05
> **Tart said:**
> You probably should try to get vim-full. It is available through symantec.  Symantec??? What in the world have they to do with this???

... Or you probably meant Synaptic? :)

---

### Post by spec-chum on 2008-05-05
> **Zeck said:**
> Thanks a lot. So how to use it. Could you teach me simple tutorials ?

There's a tutorial here.
[http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html")

I had to learn vi a few years back as it was the only text editor on the machines at work (we were basically telnetting into Unix boxes so had to use vi).  I'm so glad I learned how to use it though as it is a brilliant editor.

---

### Post by Zeck on 2008-05-05
> **spec-chum said:**
> There's a tutorial here.
[http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html")

I had to learn vi a few years back as it was the only text editor on the machines at work (we were basically telnetting into Unix boxes so had to use vi).  I'm so glad I learned how to use it though as it is a brilliant editor.

Wow. Great. Thank you.

Best Regards,
Zeck

---

### Post by Xiong Chiamiov on 2008-05-05
> **Zeck said:**
> Hi,
I'm very interesting Vi. So i want to install it and i google it. But i'm not found how to install it. So how can i install it ? Any Idea ?

I think it's also important that you understand how installing software in Ubuntu works.  [This]("http://monkeyblog.org/ubuntu/installing/") is an excellent guide.

---

### Post by Nepherte on 2008-05-05
You might want to enable syntax highlighting right away as it can be very useful. Just open up /etc/vim/vimrc:
```
sudo vim /etc/vim/vimrc
```
and remove the " from syntax on.

---

### Post by Tart on 2008-05-05
I'm noob, I just started learning Vi few days ago. 
If you type vimtutor in your terminal it starts "interactive" tutorial, which teaches you basics.

> **Zeck said:**
> Thanks a lot. So how to use it. Could you teach me simple tutorials ?

---

### Post by stchman on 2008-05-05
> **Zeck said:**
> Hi,
I'm very interesting Vi. So i want to install it and i google it. But i'm not found how to install it. So how can i install it ? Any Idea ?

Vi or as it is called now Vim is included by default on Ubuntu and very nearly EVERY Linux/UNIX OS made in the last 30yrs.

The editor while functional is cryptic to say the least.  There are numerous text editors that are orders of magnitude easier.  I have read posts of Vi's incredible prowess, but I personally don't use it unless forced to.

Ubuntu comes with Gedit which is an awesome text editor.  There is also Geany, Kate, and Xemacs (very powerful).  I personally use Gedit as it is powerful and very easy to use.  Gedit also has lots of plugins to increase functionality.

---

### Post by SlappyPappy on 2008-05-05
Hey, doesn't anybody use Nano anymore? I use it to edit files like fstab and such. Nothing fancy and gets the job done.  :)

---

### Post by Oldsoldier2003 on 2008-05-05
> **SlappyPappy said:**
> Hey, doesn't anybody use Nano anymore? I use it to edit files like fstab and such. Nothing fancy and gets the job done.  :)

nano works just fine for me. of course i would use pico, but since PINE has some licencing issues attached to it in ubuntu pico is just a symlink to nano, pines licence unchallenged brother...

---

### Post by Tart on 2008-05-05
> **SlappyPappy said:**
> Hey, doesn't anybody use Nano anymore? I use it to edit files like fstab and such. Nothing fancy and gets the job done.  :)

How do you enable spell check in nano? For some reason when I try to use spell check it complains (can't remember exact message, I'll check it at home). Maybe i didn't install full version of nano, as it was a case with vim for me.

---

### Post by stchman on 2008-05-06
> **SlappyPappy said:**
> Hey, doesn't anybody use Nano anymore? I use it to edit files like fstab and such. Nothing fancy and gets the job done.  :)

I use nano if I have to go into recovery mode.  It works, and is a lot easier that vi.

---

### Post by SupaSonic on 2008-05-06
+1 to nano. Or gedit, even through ssh. I know vi is supposed to be great and all, but for editing config files, I don't need great.

---

### Post by kerry_s on 2008-05-06
> **Zeck said:**
> Thanks a lot. So how to use it. Could you teach me simple tutorials ?

type> vimtutor <in terminal if you have the full version.

---

