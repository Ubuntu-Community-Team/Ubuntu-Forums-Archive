---
title: "alias - mine doesn't last"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-08
OK I thought it nifty to create an alias for "sudo apt-get update && upgrade && autoremove etc,  and call it 'upgrade' as la roza has done and demonstrates in this nifty thread that I wish more people would contribute too (hint).
[http://ubuntuforums.org/showthread.php?t=936906](http://ubuntuforums.org/showthread.php?t=936906) 
 My problem lies in that I have made this alias twice and every time it works once but doesn't seem to last beyond the life of the terminal.  What's wrong with here?

---

### Post by Nxion on 2008-10-08
What has to be done is added to the .bashrc file in your "/home/user" directory.

How are you are creating the alias?

EDIT: The other thing to do is once you add it to the .bashrc file is run this command:

```
source ~/.bashrc
```

This command saves the bashrc file and then your alias should be in there for good.

Hope this helps.

---

### Post by bodhi.zazen on 2008-10-08
/me stalks Nxion

---

### Post by Nxion on 2008-10-08
> **bodhi.zazen said:**
> /me stalks Nxion


AHHHH! [SIZE=1]*me thinks I am being watched*[/SIZE] :)

---

### Post by Nxion on 2008-10-08
> **bodhi.zazen said:**
> /me stalks Nxion

I am digging the little skulls under your name that look like Jack Skellington. That was a good movie.

---

### Post by adamogardner on 2008-10-08
> **Nxion said:**
> What has to be done is added to the .bashrc file in your "/home/user" directory.

How are you are creating the alias?

EDIT: The other thing to do is once you add it to the .bashrc file is run this command:

```
source ~/.bashrc
```

This command saves the bashrc file and then your alias should be in there for good.

Hope this helps.

can you explain how to "add to the .bashrc file in my /home/usr directory"?
I am merely creating the alias by...~$alias upgrade="then the lengthy but well known command here"  Thats it.  That's all I have done to make an alias.  Thanks for your help.

---

### Post by bodhi.zazen on 2008-10-08
Open a terminal

```
gedit ~/.bashrc
```Add your alias at the bottom of the file

alias update='command and automagic you want to alias'

Save and exit

log off and back on ...

{
or you can :```
 . ~/.bashrc
```
}

See also : [http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)

Nxion you are too slow :twisted:

---

### Post by Nxion on 2008-10-08
> **bodhi.zazen said:**
> Open a terminal

```
gedit ~/.bashrc
```Add your alias at the bottom of the file

alias update='command and automagic you want to alias'

Save and exit

log off and back on ...

{
or you can :```
 . ~/.bashrc
```}

See also : [http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)

Nxion you are too slow :twisted:

I am getting slow :oops:

---

### Post by Nxion on 2008-10-08
> **bodhi.zazen said:**
> Open a terminal

```
gedit ~/.bashrc
```Add your alias at the bottom of the file

alias update='command and automagic you want to alias'

Save and exit

log off and back on ...

{
or you can :```
 . ~/.bashrc
```}

See also : [http://ubuntuforums.org/showthread.php?t=679762](http://ubuntuforums.org/showthread.php?t=679762)
  

What he said  :)

---

