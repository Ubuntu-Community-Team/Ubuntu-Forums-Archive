---
title: "tips for vim newbie"
date: 2007-02-16
forum: Programming Talk
---

### Post by nephish on 2007-02-16
hello there all,

i want to jump into vim. i went through the tutorial last night, and it is pretty cool, i am sure even more so once you get the hang of it. 

so anyway. i am wondering.. there is no .vimrc file with my ubuntu edgy install. i know there is a copy of one in /etc/vim i tried use it with some of the reccommended options uncommented and copy over to /home/me/.vimrc but it was giving me errors. 
i would like to have some of the cooler features like syntax highlights for python, ruby, rhtml, etc.. but everywhere i look, i cannot seem to find out where to install vim scripts to, or a good example of an ubuntu vim vimrc file.

anyone have a tip for some starter points ?
thanks

---

### Post by po0f on 2007-02-16
nephish,

What were the errors?  And usually, this works for me to get a basic ~/.vimrc started:
```
[FONT="Courier New"]$ cp /usr/share/vim/vimcurrent/vimrc_example.vim ~/.vimrc[/FONT]
```

The above file might be named differently, this is from Feisty.

---

### Post by nephish on 2007-02-16
well, that line worked for me, thanks !

---

### Post by nephish on 2007-02-16
ok, find myself with another question.

i like vim because i want to use it to ssh into my server at work and tinker when i need to.
is there a vim option that will let me assume root user ( or in our case here in ubuntu ) the sudo user ? i would like to keep all my config and cool syntax highlighting even if i have to become root 

any way to do this ?

thanks

---

### Post by nereid on 2007-02-17
Maybe you would like to take a look at the script and tipp section from vim.org. There are some scripts around which do allow you to edit something as root, but IMHO, they don't work very good.

---

