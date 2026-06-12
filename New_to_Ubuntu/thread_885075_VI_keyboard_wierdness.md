---
title: "VI keyboard wierdness"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by marcusesses on 2008-08-09
When I attempt to scroll down in VI (Use any of the arrow keys), it prints out A, B, C or D on a new line, depending on whether I try to scroll up, down, right or left, respectively. Also, when I try to move the lines back up, or delete the letters, I'm unable to unless I hit <esc>, and use x, or dd. My keyboard works properly when writing in a browser, and when writing in gedit...any suggestions?

---

### Post by RealPSL on 2008-08-10
That is VI at work. By default from my Unix experience up and down arrows exhibit the behavior you describe. Linux provides VIM which is an improved and more usable editor. Most people will say not by much. Using VIM will solve the problem. The details are in the link below.

[http://ubuntuforums.org/showthread.php?t=636601](http://ubuntuforums.org/showthread.php?t=636601)

---

### Post by pauper on 2008-08-10
If it's default vi (=vim.tiny) that comes with Ubuntu run:

:version
:set cp?

If it yields "compatible" try the following:

Invoke vim instead vi from now on.

Or

```
sed -i '1i \                                        
> set nocp' ~/.vimrc
```

Or

```
echo "alias vi=vim" >> ~/.bash_aliases
```

Read more on the subject:

:h compatible

[http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell](http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell)

---

### Post by scorp123 on 2008-08-10
First thing I do after a fresh Ubuntu installation is to get rid of "vim-tiny" by installing the "full" package with all the bells, whistles and other goodies:
```
sudo apt-get install vim-full
```

This should resolve most issues (it does for me :)  ). Also I edit vim's config file in **/etc/vim/vimrc** so it has these options turned on:
```

...
" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
syntax on
set paste
...
``` The first line "syntax on" should already be there, but it's turned off. Per default there will be a "#" in front of it. So you'd have to remove that one. And then hit the 'Enter' key and add the option "set paste". In newer Ubuntu releases this makes sure that copy & paste from other applications towards plain good old "vim" works as intended and vim doesn't mess with the formatting.

Just my 0.02 € ;)

---

### Post by marcusesses on 2008-08-10
Thanks all, I think that did the trick! (I should have looked at the forum more extensively, I suppose)

---

