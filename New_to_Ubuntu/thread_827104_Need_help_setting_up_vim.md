---
title: "Need help setting up vim"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by chez17 on 2008-06-12
I am trying to start using vim as a text editor. I am having problems even finding where its located on the system. I want to try to getting some of the syntax highlighting and script files I found to work but I don't even know where to begin. I have tried searching for some good tutorials and haven't been able to find any. Can somebody point me in the direction of some good sites or post a mini tutorial on how to get vim working with php?

Thanks,
Dave

---

### Post by sdennie on 2008-06-12
You can figure out where vim is by typing:

```

which vim

```

You can install customized settings by creating a file called .vimrc and putting things in there.  I usually create a directory called .vim and put individual vim config files in that directory and then fill my .vimrc with things like:

```

source /home/my_username/.vim/some_file1.vim
source /home/my_username/.vim/some_file2.vim
source /home/my_username/.vim/some_file3.vim

```

Also, you should be able to turn syntax highlighting on by typing :syntax on.  You can also just add "syntax on" to your .vimrc.  Although the default version of vim in Hardy doesn't support this so you may need to first do a:

```

sudo apt-get install vim-gnome

```

Which will also give you a graphical version of vim (gvim) that has menu items that may help to ease you into using vim.

You can also find a vim tutorial by type:

```

vimtutor

```

Hope that helps.

---

### Post by AndThenWhat on 2008-06-12
go here
[http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim](http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim)

and scroll down to the section called "**Configure Vim for PHP Debugging**"

---

### Post by bhold on 2008-06-12
Been a while, but I recall I had much better results with vim after I installed vim-full. The vim on my system after a fresh Ubuntu install was vim-tiny. As the name would imply, vim-tiny is a smaller version with limited features.

---

### Post by chez17 on 2008-06-12
Is there a difference between vim-gnome and vim-full?

---

### Post by sdennie on 2008-06-12
It doesn't look like it.  This is what the package description for vim-full is:

Description: Vi IMproved - enhanced vi editor (transitional package)
 This package is simply a transitional package from vim-full to vim-gnome.

So, either one should work just fine.

---

### Post by chez17 on 2008-06-12
So I found this script which I think will be helpful:

[http://www.vim.org/scripts/script.php?script_id=1571](http://www.vim.org/scripts/script.php?script_id=1571)

I followed the install instructions and it doesn't work. Can somebody help me out and tell me why it might not be working?

---

### Post by stchman on 2008-06-12
I have never understood the attraction to using vi when there are way better text editors out there (like gedit).  Some sort of UNIX rite of passage I guess.

That is the beauty of Linux, choice.

---

### Post by sdennie on 2008-06-12
> **stchman said:**
> I have never understood the attraction to using vi when there are way better text editors out there (like gedit).  Some sort of UNIX rite of passage I guess.

That is the beauty of Linux, choice.

The learning curve on something like vi is exceedingly high but, once you get good at it, it's incredibly powerful.  Once you've really accustomed to the features available in vi (or dare I say, emacs), an editor like gedit just seems like a cute toy.  ;)

---

### Post by stchman on 2008-06-12
> **vor said:**
> The learning curve on something like vi is exceedingly high but, once you get good at it, it's incredibly powerful.  Once you've really accustomed to the features available in vi (or dare I say, emacs), an editor like gedit just seems like a cute toy.  ;)

I have used vi and it leaves a lot to be desired.

---

### Post by bodhi.zazen on 2008-06-12
vim takes some time to learn and is an invaluable tool in CLI (server) environments.

Tools like nano are quick to learn, but not as powerful.

Learning vim pays off in spades ...

If you want to user vi, I suggest :

```
sudo apt-get intall vim
```

vim-full adn vim-gnome == lots of extras, like gvim (gui tools). I I use X I am not as big a fan of gvim ...

Look at the packages for info :

vim : [http://packages.ubuntu.com/hardy/vim](http://packages.ubuntu.com/hardy/vim)

vim-gnome (vim-full) : [http://packages.ubuntu.com/hardy/vim-gnome](http://packages.ubuntu.com/hardy/vim-gnome)

---

### Post by gr4nf on 2008-06-12
> 
I have used vi and it leaves a lot to be desired. 

then you havn't really used vi :).

You might try vile, as it has all of the features of vi, but is a bit more intuitive.

---

