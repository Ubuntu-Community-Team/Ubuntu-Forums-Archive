---
title: "Configuring VIM properly, cant get colorscheme to work"
date: 2013-03-12
forum: Programming Talk
---

### Post by devync on 2013-03-12
Hello, I have been trying to configure my vimrc file to my liking and for some reason I can't get colorscheme to work. It always says it can't find the colorscheme file. From what I can tell most my other settings work, just not colorscheme.

I did  my research and people were saying you have to create your .vim file in ~/.vim and I also made a dir colors in ~/.vim/colors and put my colorscheme in there, but it still doesn't work. I have also found vimrc files in both /etc/vim and /usr/share/vim, so I am unsure of where I am actually supposed to be making my changes.

I am new to linux and vim, so if you would be so kindly to explain theses shenanigans to the laymen? 

Thanks for any replies. I have been trying to figure this out for two days, and I hope the answer isn't too painfully obvious.:guitar:

---

### Post by spjackson on 2013-03-12
The default color location is /usr/share/vim/vim*/colors/. Additional personal colors can be placed in ~/.vim/colors/.

Are you using vim in a terminal or a gui version (e.g. gvim)? colorscheme is different in a gui from in a terminal, at least with respect to background color (I'm not sure what else). If you start vim and type :colorscheme<space><tab> then you can keep tabbing through the available schemes. Of course, in gvim you can select it from the menu.

---

### Post by drmrgd on 2013-03-12
Also to add to that, be sure that you're typing the color name exactly as it appears - case is important.  For example, I use the colorscheme 'molokai' in my .vimrc.  So, the line should read:

```
color molokai
```

Be careful not to enter 'Molokai' or 'MOLOKAI'.

---

### Post by devync on 2013-03-12
> **spjackson said:**
> The default color location is /usr/share/vim/vim*/colors/. Additional personal colors can be placed in ~/.vim/colors/.

Are you using vim in a terminal or a gui version (e.g. gvim)? colorscheme is different in a gui from in a terminal, at least with respect to background color (I'm not sure what else). If you start vim and type :colorscheme<space><tab> then you can keep tabbing through the available schemes. Of course, in gvim you can select it from the menu.

Thanks a lot, that cleared up my confusion nicely. Now I notice that my /etc/vim/vimrc and /usr/share/vim/vimrc files are synced and not my ~/.vim/vimrc. How can I get it so that if I make changes to the ~/.vim/vimrc file it will make the changes everywhere else? I can put colors in the ~/.vim/colors like you said, just the vimrc file doesn't do anything.

---

### Post by devync on 2013-03-12
> **drmrgd said:**
> Also to add to that, be sure that you're typing the color name exactly as it appears - case is important.  For example, I use the colorscheme 'molokai' in my .vimrc.  So, the line should read:

```
color molokai
```

Be careful not to enter 'Molokai' or 'MOLOKAI'.

Yea, I just noticed that. I was typing it as colorscheme.vim and it wouldn't recognize it with the file extension.

---

### Post by spjackson on 2013-03-13
> **devync said:**
> Thanks a lot, that cleared up my confusion nicely. Now I notice that my /etc/vim/vimrc and /usr/share/vim/vimrc files are synced and not my ~/.vim/vimrc. How can I get it so that if I make changes to the ~/.vim/vimrc file it will make the changes everywhere else? I can put colors in the ~/.vim/colors like you said, just the vimrc file doesn't do anything.
/usr/share/vim/vimrc is a symbolic link to /etc/vim/vimrc. They are not exactly synced but rather the same file.
Your personal configuration file is not ~/.vim/vimrc but ~/.vimrc . Changes to ~/.vimrc are read when vim starts, but are not reflected "everywhere else" - I am unclear what you are trying to achieve by that.

---

### Post by devync on 2013-03-13
[HTML][/HTML]> **spjackson said:**
> /usr/share/vim/vimrc is a symbolic link to /etc/vim/vimrc. They are not exactly synced but rather the same file.
Your personal configuration file is not ~/.vim/vimrc but ~/.vimrc . Changes to ~/.vimrc are read when vim starts, but are not reflected "everywhere else" - I am unclear what you are trying to achieve by that.

Thanks, I am just trying to achieve a file that is easier to access that having to go to /etc/vim/vimrc and I can just go to ~/.vimrc

---

