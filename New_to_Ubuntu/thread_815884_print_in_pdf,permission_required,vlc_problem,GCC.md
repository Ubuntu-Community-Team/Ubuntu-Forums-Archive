---
title: "print in pdf,permission required,vlc problem,GCC"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-06-02
1.I m using ubuntu 7.10,how do i print a page(i.e from web) in pdf.

2. How should i get permission for pasting a source file from desktop to                 
/usr/local/src... or to any folder in file system

3.when i play any movie in vlc i m just getting sounds but no video.Is there any good player than vlc(i m really getting mad).

4.Can any one please provide me material for GCC.

---

### Post by rraj.be on 2008-06-02
you can get root privilages by typing 

```
sudo -i
```

and entering your password when prompted, in terminal.

You are not allowed to past or introduce any thing from system folders unless you have root privilages.

To copy there you can use terminal with command

```
sudo cp [source path] [destination path]
```

Vlc is the player that supports a wide range of formates.
the problem occured for you is due to missing codecs.

Just install necessary codecs to support  your file formate.

I hope you should install gstreemer codecs.


for GCC get here.

[www.gc.maricopa.edu/ic/gcchelp/tutorials]("www.gc.maricopa.edu/ic/gcchelp/tutorials")

[users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html]("users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html")



[www.tutorialized.com/tutorial/GCC-Based-Cross-Compiler-for-Linux]("www.tutorialized.com/tutorial/GCC-Based-Cross-Compiler-for-Linux")

---

