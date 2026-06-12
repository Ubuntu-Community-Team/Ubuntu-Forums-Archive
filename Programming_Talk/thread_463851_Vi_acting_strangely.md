---
title: "Vi acting strangely"
date: 2007-06-04
forum: Programming Talk
---

### Post by HAL98 SE on 2007-06-04
I've just upgraded to 7.04 and I'm loving some of the new features that are there such as the new window effects, but I'm having a small problem with the text editor vim, it isn't responding to keyboard input in the same way as it did in LTS and Dapper, is there some configuration that needs to be edited?

for example, when I use the arrow keys to navigate, its doing weird things like adding carriage return and certain characters, is this because its running in a certain mode as default or something??

This also occurs when I SSH into the box from a different machine and open vi from the SSH shell.

Please, if anyone can help, I love vi, its my favourite editor and I really want to be able to use it, and I don't know why is behaving this way!!!

---

### Post by HAL98 SE on 2007-06-04
I've just upgraded to 7.04 and I'm loving some of the new features that are there such as the new window effects, but I'm having a small problem with the text editor vi, it isn't responding to keyboard input in the same way as it did in LTS and Dapper, is there some configuration that needs to be edited?

for example, when I use the arrow keys to navigate, its doing weird things like adding carriage return and certain characters, is this because its running in a certain mode as default or something??

This also occurs when I SSH into the box from a different machine and open Vi from the SSH shell.

Please, if anyone can help, I love vi, its my favourite editor and I really want to be able to use it, and I don't know why is behaving this way!!!

---

### Post by nitro_n2o on 2007-06-04
i truly hate this when it happens.. although you shouldn't use arrow keys in vim, it's really annoying to see strange things when you use them.... 
you can use my .vimrc just put it in your home directory, it has nice features and will solve your problem

---

### Post by dfreer on 2007-06-04
for some EXTREMELY weird reason, I have found vi to be not completely installed in feisty. I've been meaning to file a bug report but haven't got around to it. Anyways, to fix your problem, simply type:
```
sudo apt-get install vim
```

If anyone knows why vi is broken on feisty...?

---

### Post by tseliot on 2007-06-04
I have merged the 2 threads about Vi since one was a duplicate of the other

---

### Post by HAL98 SE on 2007-06-05
> **dfreer said:**
> for some EXTREMELY dumb reason, I have found vi to be not completely installed in feisty. I've been meaning to file a bug report but haven't got around to it. Anyways, to fix your problem, simply type:
```
sudo apt-get install vim
```

If anyone knows why vi is broken on feisty...?

Thank you this solved the problem straight away!

---

### Post by HAL98 SE on 2007-06-05
> **nitro_n2o said:**
> i truly hate this when it happens.. although you shouldn't use arrow keys in vim, it's really annoying to see strange things when you use them.... 
you can use my .vimrc just put it in your home directory, it has nice features and will solve your problem

Thanks for that, I 'ill have a looksee, what kind of features are added? :-)

---

### Post by dfreer on 2007-06-05
Anyone else think this is worth a bug report?

---

### Post by HAL98 SE on 2007-06-06
> **dfreer said:**
> Anyone else think this is worth a bug report?

I think so, couldn't see anything on launchpad

---

### Post by dfreer on 2007-06-06
Alright, I put it in. Here's the link:
[https://bugs.launchpad.net/ubuntu/+source/vim/+bug/118970](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/118970)
Please contribute if you can confirm whether this is limited to feisty or if it affects Edgy as well (I'm trying to remember if my Dapper Server install had this problem)

---

### Post by vayde on 2007-06-27
I have vim-full installed, but I've noticed a strange quirk.

When you yank a line (Vy)  and then open the file explorer (:e.) and scroll to a new file, pasting (p) pastes a blank line, not what you put into the buffer.

If you do the same, but open a known file (:e <filename>) it pastes as expected.  You can also get around the quirk by yanking lines into a named buffer, and likewise pulling them from the buffer.

I work on RHEL systems, with vim 6 and vim 7.1, also gvim 7.1 on windows, none of these installations exhibit this quirk, nor do my Dapper servers.

Has anyone else seen this?  Perhaps it's a config issue that used to be default but now isnt?

---

