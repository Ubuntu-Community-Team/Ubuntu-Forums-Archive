---
title: "Open sublime text 2 from terminal"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by elieobeid7 on 2012-09-22
i am using zsh, i want to open files from terminal using sublime, like so:

    sublime text.txt

instead of

    nano text.txt

i used to know how to do it, i did it on my old computer, i had linux mint 12, now i forgot how, and i can't find the tutorial, now i am on ubuntu 12.04 lts

---

### Post by Hadaka on 2012-09-22
hi, this might work..

```
echo export EDITOR=sublime >> .bashrc 
```



*Note: this will also add an editor of your choice to crontab.

---

### Post by elieobeid7 on 2012-09-22
> **Hadaka said:**
> hi, this might work..

```
echo export EDITOR=sublime >> .bashrc 
```



*Note: this will also add an editor of your choice to crontab.
didn't work, i need to do something else, in some file, to specify the path of sublime

---

### Post by Hadaka on 2012-09-22
hi, try this link

[http://askubuntu.com/questions/155119/how-to-use-sublime-text-2-as-quickly-default-editor](http://askubuntu.com/questions/155119/how-to-use-sublime-text-2-as-quickly-default-editor)

note the EDIT section of the page and the SCRIPT in red letters.

---

### Post by Toz on 2012-09-22
Where is sublime installed? What it the path to the executable? If possible, copy or create a link in ~/bin (create the directory if it doesn't exist) so that you can run it with just "sublime".

Also, since you are using zsh, if you want to try to specify the editor as above, you need to use .zsrch (.bashrc is for the bash shell).

---

### Post by elieobeid7 on 2012-09-23
thanks Toz it worked! I forgot about .zshrc but didn't need it, i made a link to /bin

---

