---
title: "can\t compile!!!"
date: 2005-02-16
forum: Programming Talk
---

### Post by gogodidi on 2005-02-16
ok, dont mind the \s thats just me attempting to make an apostrophe  (i\m in kde and I cant change the keymap cos I don\t have the link to the contrl center) 

second of all...

I can\t compile...

when i try to compile a basic hello world cprogram (c++) in kdevelop I get the following error message>

```
 cd '/home/gogodidi/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/gogodidi/test/debug' && cd '/home/gogodidi/test/debug' && CXXFLAGS="-O0 -g3" "/home/gogodidi/test/configure" --enable-debug=full && cd '/home/gogodidi/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
*** Exited with status: 2 ***
 
``` 

can anyone help me?

I have the gcc and g++ copilers instaled, plus the automake files, whats wrong_

---

### Post by gogodidi on 2005-02-16
Any Help?

---

### Post by az on 2005-02-16
sudo apt-get install build-essential.

You will also need the -dev packages for the libraries that you need. (for example, if you need to compile something that requires libgnome2-0, you need the libgnome2-dev package)

To compile kernel modules, install linux-headers

Maybe kdevelop is not properly installed?  Maybe your program is not written properly.  Can you compile it from the command line?

---

### Post by trygvebw on 2005-02-17
Heisann :) Hyggelig å se en nordmann her.
For å kunne kompilere programmer må du installere pakken build-essentials. For å gjøre det, er det bare å kjøre "apt-get install build-essentials". Lykke til! :)

---

### Post by shaunc on 2005-09-16
Thanks azz, the sudo apt-get install build-essential command fixed my broken gcc. Now it actually works properly, so I will be able to ./configure too. I was pretty screwed if my gcc was broken, but that fixed it. Thanks!

---

