---
title: "Having trouble with Vim installation"
date: 2011-08-11
forum: Programming Talk
---

### Post by Cosmopolitan1 on 2011-08-11
Hello guys :)

I do php programming in gedit but I would also like to try a more advanced text editor and everyone says that Vim is the one of the best ones.

Now, when I type:
```
sudo apt-get install vim
```

I get:
```
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
```

Would someone tell me how to change /etc/sudoers from 0777 to 0440?

---

### Post by Zugzwang on 2011-08-11
Which user does the "sudoers" file belong to? Is it you or "root"?

---

### Post by Cosmopolitan1 on 2011-08-11
I am really not sure but etc folder is placed in the File System.
How could I check it?:confused:

---

### Post by sisco311 on 2011-08-11
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT: there is an easier way. Simply run:
```
pkexec chown root:root /etc/sudoers
pkexec chmod 0440 /etc/sudoers
```

This should restore the default ownership and permissions of the file.

---

### Post by Cosmopolitan1 on 2011-08-11
I've already done the instructions from your link and it worked.
Thanks.
By the way, this Vim is terrifying :(
No colors, nothing, and must learn how to save, open files for ages.
Do you know any other good text editor for php in Ubuntu (better than gedit but more simple to cope with than Vim?

---

### Post by unknownPoster on 2011-08-11
> **Cosmopolitan1 said:**
> I've already done the instructions from your link and it worked.
Thanks.
By the way, this Vim is terrifying :(
No colors, nothing, and must learn how to save, open files for ages.
Do you know any other good text editor for php in Ubuntu (better than gedit but more simple to cope with than Vim?

Personally, I think Gedit is very good for beginning programmers or even simple tasks for advanced programmers. Just use whatever allows you to work as efficiently as possible.

---

### Post by Cosmopolitan1 on 2011-08-11
> **unknownPoster said:**
> Personally, I think Gedit is very good for beginning programmers or even simple tasks for advanced programmers. Just use whatever allows you to work as efficiently as possible.

Thank you for encouraging advice :)

---

### Post by unknownPoster on 2011-08-11
> **Cosmopolitan1 said:**
> Thank you for encouraging advice :)

There are so many arguments on IDEs and text editors that they are usually locked.

Ultimately, it's personal preference and if you're learning to program, you should should be focusing on the code, not how to get an editor to do some operation.

---

### Post by Cosmopolitan1 on 2011-08-12
Yap, I agree.
I've been learning php which is quite difficult.
I'm gonna stay with gedit ;)

---

### Post by Cosmopolitan1 on 2011-08-12
> **sisco311 said:**
> [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT: there is an easier way. Simply run:
```
pkexec chown root:root /etc/sudoers
pkexec chmod 0440 /etc/sudoers
```This should restore the default ownership and permissions of the file.

Ooppss!
Again same error.
I can install things but always get this message before I am asked for the password:
```
sudo: /etc/sudoers.d/README is mode 0777, should be 0440
```I tried the things from the link above and also typed those two commands but the mistake still exists.

Any suggestion guys?

---

### Post by sisco311 on 2011-08-12
> **Cosmopolitan1 said:**
> Ooppss!
Again same error.
I can install things but always get this message before I am asked for the password:
```
sudo: /etc/sudoers.d/README is mode 0777, should be 0440
```I tried the things from the link above and also typed those two commands but the mistake still exists.

Any suggestion guys?

You have to replace **/etc/sudoers** with **/etc/sudoers.d/README**.

---

### Post by Cosmopolitan1 on 2011-08-12
Would you please tell me how to perform that?
Manually, renaming some folders or running a command in the terminal?

Thanks :)

---

### Post by sisco311 on 2011-08-12
Sorry, I wasn't clear enough. You have to change the filenames in the commands I posted:
```
pkexec chown root:root /etc/sudoers.d/README
pkexec chmod 0440 /etc/sudoers.d/README
```

---

### Post by Cosmopolitan1 on 2011-08-12
Thank you my fellow country citizen.
Hugs from Serbia :D

---

### Post by chenpoyang on 2011-08-12
> **Cosmopolitan1 said:**
> I've already done the instructions from your link and it worked.
Thanks.
By the way, this Vim is terrifying :(
No colors, nothing, and must learn how to save, open files for ages.
Do you know any other good text editor for php in Ubuntu (better than gedit but more simple to cope with than Vim?
vim is terrified.
what you need to do is to learn it by viewing its documents;
to begin with, you can type the command "vimtutor" in terminal to get 30 minutes' tutor...!
for more tips, here is a bunch of tutors about vim:/usr/share/vim/vim72/doc
once your get familiar with vim, text edit will by more efficient.
hope you enjoy!

---

### Post by krazyd on 2011-08-12
@OP: Don't go back to gedit, stick with vim! :-D

Some suggestions to help you ease your way into it:
- Install gvim. It's vim with a GUI which will help you initially become familiar with vim commands.
- Read this: [https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)
- Read this: [https://wiki.archlinux.org/index.php/Vim](https://wiki.archlinux.org/index.php/Vim) (see the links to tutorials, screencasts etc. down the bottom)

---

### Post by cgroza on 2011-08-12
Do yourself a favor and learn Vim or Emacs. I did and now I find normal editors clumsy and slow to work with because they require a lot of mouse usage. After learning 15-20 commands you will be a real keyboard ninja.

---

