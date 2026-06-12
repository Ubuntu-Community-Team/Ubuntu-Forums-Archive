---
title: "Printer Driver, ip1800"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by watnazn on 2008-07-16
Does anyone know how to get my printer (Canon ip 1800) to work. Or can anyone direct me to a thread on how to because I've been looking.
Thanks

---

### Post by maddog39 on 2008-07-16
Whats the problem with it precisely? Can you provide more details as to whats wrong? By the way, as far as I can tell your printer isnt supported at all ([http://openprinting.org/printer_list.cgi?make=Canon](http://openprinting.org/printer_list.cgi?make=Canon)) so which driver are you referring to?

---

### Post by PmDematagoda on 2008-07-16
Perhaps [this]("http://software.canon-europe.com/software/0027403.asp?model=") may help, but you may have to use Alien to convert the rpm to a deb to use it on Ubuntu.

---

### Post by watnazn on 2008-07-17
ok, thanks, but now i have cnifilter-common-2.70.tar.gz, and I forgot how to install it because i haven't done it in such a long time. sorry for my noobness
thanks

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> ok, thanks, but now i have cnifilter-common-2.70.tar.gz, and I forgot how to install it because i haven't done it in such a long time. sorry for my noobness
thanks

When you extract it, try and see if the README file within the extracted directory can help you install it. If there isn't a README file then post the output of doing:-
```
ls
```
in the directory.

---

### Post by watnazn on 2008-07-17
Theres no read-me, and i don't really understand what you mean by ls. sorry im a no0b.

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> Theres no read-me, and i don't really understand what you mean by ls. sorry im a no0b.

Ok, the command is to be executed in the terminal which can be started through Applications>Accessories>Terminal, then you should move to the directory containing the extracted files using:-
```
cd name-of-directory
```
but you can find out what directories you need to navigate or move to with the help of ls so as to show you the viable options or you could press Tab which is a sort of auto-completion for commands. After you reach the directory you extracted the files to, execute ls and then copy and paste the result here.

---

### Post by Sef on 2008-07-17
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by watnazn on 2008-07-17
Thank you for all the posts, but i just can't get this to work. I followed  the tutorials too.

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> Thank you for all the posts, but i just can't get this to work. I followed  the tutorials too.

What is the problem you are facing?

---

### Post by watnazn on 2008-07-17
I have the extract of the tar.gz. I opened terminal, typed desktop:~$ cd '/home/watnazn/Desktop/cnijfilter-common-2.70'. Then, ./configure. It says  
bash: ./configure: No such file or directory
so then i type make, so it says,```
for dir in libs cngpij ppd pstocanonij ; do (cd $dir; make $target)|| exit 1; done
make[1]: Entering directory `/home/kyle/Desktop/cnijfilter-common-2.70/libs'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/kyle/Desktop/cnijfilter-common-2.70/libs'
make: *** [all] Error 1

```
so i don't know

---

### Post by PmDematagoda on 2008-07-17
Can you post the contents of the directory with:-
```
ls
```
please.

---

### Post by watnazn on 2008-07-17
it says no such file or directory

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> it says no such file or directory

Did you just execute it in the directory containing the extracted files, or:-
```
ls /home/watnazn/Desktop/cnijfilter-common-2.70
```

---

### Post by watnazn on 2008-07-17
I did both, but i just did the code you posted antd it worked, 
253  294  cngpij                  lgmon                         Makefile
291  295  cngpijmon               libs                          ppd
292  311  cnijfilter              LICENSE-cnijfilter-2.70E.txt  printui
293  312  cnijfilter-common.spec  LICENSE-cnijfilter-2.70J.txt  pstocanonij

---

### Post by PmDematagoda on 2008-07-17
Now change directory to the libs directory in the extracted folder and then try doing:-
```
./configure
```

---

### Post by watnazn on 2008-07-17
can you tell me exactly haw to do this, with the exact terminal lines, sorry for asking for so much.

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> can you tell me exactly haw to do this, with the exact terminal lines, sorry for asking for so much.
You change directory with:-
```
cd /home/watnazn/Desktop/cnijfilter-common-2.70/libs
```
and then execute:-
```
./configure
```

---

### Post by watnazn on 2008-07-17
it didn't work
```
desktop:~$ cd /home/kyle/Desktop/cnijfilter-common-2.70/libs
desktop:~/Desktop/cnijfilter-common-2.70/libs$ ./configure
bash: ./configure: No such file or directory
```
its ok though. I am joing going to use someone elses printer, thanks so much for trying though.

---

### Post by PmDematagoda on 2008-07-17
> **watnazn said:**
> it didn't work
```
desktop:~$ cd /home/kyle/Desktop/cnijfilter-common-2.70/libs
desktop:~/Desktop/cnijfilter-common-2.70/libs$ ./configure
bash: ./configure: No such file or directory
```
its ok though. I am joing going to use someone elses printer, thanks so much for trying though.

Well, you could always try using the link I gave in my first post and then converting the rpm to deb using Alien and then installing it.

---

### Post by org.ale on 2008-09-18
hey... I'm a linux freshman, I installed alien and I wanna to convert my rpm drivers into deb drivers

alien -k cnijfilter-ip1800series-2.70-1.i386.rpm

but I've got some errors
____________________________________________________________________________________

Warning: Skipping conversion of scripts in package cnijfilter-ip1800series: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-ip1800series
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libgmodule-1.2.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libXi.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libXext.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libX11.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libm.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/cnijfilter-ip1800series/usr/local/bin/cngpijmonip1800 shouldn't be linked with libxml.so.1 (it uses none of its symbols).
dpkg-shlibdeps: warning: couldn't find library libcnbpcmcm312.so needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libcnbpess312.so needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: failure: couldn't find library libpng.so.3 needed by debian/cnijfilter-ip1800series/usr/local/bin/cifip1800 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
dpkg-deb: building package `cnijfilter-ip1800series' in `../cnijfilter-ip1800series_2.70-1_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: cnijfilter-ip1800series-2.70: No such file or directory

____________________________________________________________________________________

like I said, I'm a newbie in linux and forums...  could you please help me, those are my printer drivers and I really need them...

thanks

---

