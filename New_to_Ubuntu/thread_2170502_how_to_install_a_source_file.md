---
title: "how to install a source file?"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by tjb2 on 2013-08-26
I currently have Xubuntu 12.10 installed.
I have my source file downloaded. The file name is "higan_v093-source.tar.xz" 
after opening terminal and locating the file with cd Downloads/ ls 

I was wondering if anyone could show me how to install this file. 
"[higan v093 (GPLv3 source)]("http://byuu.org/higan/release/higan_v093-source.tar.xz")" 

thanks

---

### Post by SeijiSensei on 2013-08-26
You cannot install a source file.  You must compile an executable binary from the source code first.  Read [this guide](https://help.ubuntu.com/community/CompilingSoftware) for more details.

---

### Post by Elfy on 2013-08-26
Not often that I actually need to do it - and I always forget ... 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

This usually gets me through it.

---

### Post by Impavidus on 2013-08-26
I don't know how it is for others, but I get http error 403 (forbidden) when I try to download that file, so I can't give specific instructions. Judging from the extension it must be an archive. Unpack it and with some luck you'll find a file called README or INSTALL. It may give you some instructions.

---

### Post by tjb2 on 2013-08-26
thanks guys, i'll check those links and see what i can do to get this thing running.. i'll update if it works or not.

---

### Post by Petro Dawg on 2013-08-26
That is not an easy question to answer unless someone who just happened to install that exact file on a system simalar to yours decides to help out. Also the link you provided does not appear to work for me "Error 403 - Forbidden"...

Generally you would need to first extract the contents of the tar file into a folder.  If you are lucky there will be a README with instructions on how to install from there.  Otherwise you will have to do your research to figure out what you need to do.  Sometimes it is as simple as running...

```

./configure
make 
sudo make install

```

in teminal from the directory that you extracted the files into.  But I wouldn't count on it being that easy.

---

### Post by Elfy on 2013-08-26
I've managed to grab it from [http://byuu.org/higan/release/](http://byuu.org/higan/release/)

---

### Post by tjb2 on 2013-08-26
I went through most of the notions..im gonna try again tomorrow. thanks for the help guys. this was helpful.

---

