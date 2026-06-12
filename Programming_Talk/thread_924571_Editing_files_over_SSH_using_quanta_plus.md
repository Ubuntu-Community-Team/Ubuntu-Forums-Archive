---
title: "Editing files over SSH using quanta plus"
date: 2008-09-19
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-09-19
Hi,

I have been working on a project over SSH using vim. Everything is pretty cool with vim, except when it comes to copying and pasting from X to vim and vice versa. I'm able to copy from X to vim on the server, but when I copy some code, the indenting gets messed up. Some of the codes are written in python which is a very picky about indenting.

I'm wondering if there is an easy way to use quanta plus to connect to ssh and edit files directly on the remote machine? I noticed there are 4 options available in quanta plus when creating a project: Local, FTP, webdav and webdavs.

I read somewhere that using fish, I can connect to SSH, but I can't find any information about fish in quanta plus or repository. 

Any idea how to achieve that?

---

### Post by LaRoza on 2008-09-19
Make sure both editors are using the same settings. For Python, the standard is four spaces.

---

### Post by mohtasham1983 on 2008-09-19
But, sometimes I need to copy and paste some code from web as well. I use a lot of the examples in YUI documentations and customize them based on my needs.

---

### Post by LaRoza on 2008-09-19
> **mohtasham1983 said:**
> But, sometimes I need to copy and paste some code from web as well. I use a lot of the examples in YUI documentations and customize them based on my needs.

Any decent editor can convert tabs to spaces if they are used.

---

### Post by mohtasham1983 on 2008-09-19
> **LaRoza said:**
> Any decent editor can convert tabs to spaces if they are used.

Do you know how I can convert the following:

def hi():
        some thing here
                   another here
                                 third one here


to this in vim:

def hi():
        something here
        another here
        third one here

When I pased python code to vim, it adds indenting to every line. I don't have such problem with gvim, though. However, I cannot use gvim here.

In gui based text editors, I select the whole paragraph and using tab, correct the indenting, but I don't know how to do that in vim. :(

---

### Post by LaRoza on 2008-09-19
> **mohtasham1983 said:**
> 
When I pased python code to vim, it adds indenting to every line. I don't have such problem with gvim, though. However, I cannot use gvim here.

In gui based text editors, I select the whole paragraph and using tab, correct the indenting, but I don't know how to do that in vim. :(

I do not understand the problem (use [noparse]```

```[/noparse] tags to preserve formatting, read your post ;))

What is the .vimrc like?

---

### Post by mohtasham1983 on 2008-09-19
Sorry my bad. It should be something like this:

def hi():
********some thing here
****************another here
************************third one here


to this in vim:

def hi():
********something here
********another here
********third one here

Assuming * means space.

---

### Post by mohtasham1983 on 2008-09-19
Sorry, I'm not able to copy the content of the vimrc here. It's pretty much the basic one with debian. I just enabled the following:

set mouse=a

syntax on

---

### Post by lobo235 on 2008-11-23
mohtasham1983,

It's not to hard to work around the indenting problem you are seeing when you paste into vim before pasting type in the command
```
:set paste
```
Then, after pasting type in the command
```
:set nopaste
```
This enables you to paste into vim without it indenting each line like you are seeing.

---

