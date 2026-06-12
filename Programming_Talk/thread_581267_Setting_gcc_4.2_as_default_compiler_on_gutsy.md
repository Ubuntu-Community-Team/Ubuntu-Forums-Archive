---
title: "Setting gcc 4.2 as default compiler on gutsy ?"
date: 2007-10-19
forum: Programming Talk
---

### Post by FredB on 2007-10-19
Hello.

I have both gcc 4.1 and 4.2 on my gutsy install.

4.1 get installed with build essential, and 4.2 get installed when I entered :

```
sudo apt-get builddep firefox-dev
```As I am building nearly every single day firefox and thunderbird trunk, I wanted to know if I can set for my whole system gcc and g++ 4.2 as default compilers ?

Thanks a lot for your help.

---

### Post by Soybean on 2007-10-19
Well, gcc and g++ are just symbolic links to a particular version's executable. So if you change the links (in /usr/bin) to point to gcc-4.2 and g++-4.2, that should effectively make them the default compilers. 

It seems to me like this could cause unexpected problems later, though, so be careful! At the very least, don't forget that you did this, so that you can undo it later if you run into trouble.

---

### Post by FredB on 2007-10-19
> **Soybean said:**
> Well, gcc and g++ are just symbolic links to a particular version's executable. So if you change the links (in /usr/bin) to point to gcc-4.2 and g++-4.2, that should effectively make them the default compilers. 

It seems to me like this could cause unexpected problems later, though, so be careful! At the very least, don't forget that you did this, so that you can undo it later if you run into trouble.

Well, I think I will use export CC and CXX every time I want to build a source.

Thanks for the info.

---

