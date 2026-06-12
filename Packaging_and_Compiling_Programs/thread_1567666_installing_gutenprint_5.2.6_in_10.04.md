---
title: "installing gutenprint 5.2.6 in 10.04"
date: 2010-09-04
forum: Packaging and Compiling Programs
---

### Post by dryder on 2010-09-04
Hi
I am trying to install the latest version of gutenprint (5.2.6) on 10.04 as it supports my printers and is the interface I want for printing from gimp.

I have followed the instructions in the (attached) guide and successfully matched the 'Configuration Summary:' on page 11 of the attached file.

I did 'make' -I assume make is a trial run prior to 'make install'?

Yes, I am obviously new to installing non-debian packages - but at least I managed to reach the Configuration Summary successfully - although the guide gives> Compiler options:
-Disfinite=finite -O6 -Wall -Wcast-
align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs
-Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-
limit=131072 -pedantic -Waggregate-return -Wcast-qual -Wshadow -Wredundant-decls I only could get > -Disfinite=finite  -O6  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=131072

On make install I get:> david@ubuntu64:~/Desktop/gutenprint-5.2.6$ make install
Making install in include
make[1]: Entering directory `/home/david/Desktop/gutenprint-5.2.6/include'
Making install in gutenprint
make[2]: Entering directory `/home/david/Desktop/gutenprint-5.2.6/include/gutenprint'
make[3]: Entering directory `/home/david/Desktop/gutenprint-5.2.6/include/gutenprint'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/gutenprint" || /bin/mkdir -p "/usr/local/include/gutenprint"
/bin/mkdir: cannot create directory `/usr/local/include/gutenprint': Permission denied
make[3]: *** [install-nodist_pkgincludeHEADERS] Error 1
make[3]: Leaving directory `/home/david/Desktop/gutenprint-5.2.6/include/gutenprint'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/david/Desktop/gutenprint-5.2.6/include/gutenprint'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/david/Desktop/gutenprint-5.2.6/include'
make: *** [install-recursive] Error 1
david@ubuntu64:~/Desktop/gutenprint-5.2.6$ 

I would be very grateful for help, please.

Many thanks,

David

---

### Post by SevenMachines on 2010-09-05
hi. In a general sense, 'make' builds the things, 'make install' tries to copy the built files to the configured directory hierarchy (default is usually /usr/local). These are system directories so you'd need to do 

$ sudo make install

Alternatively you could run 'checkinstall' in the build directory to make a fake debian package which makes it easier to uninstall the files when you want to.

Alternatively alternatively, you could try using the newer maverick versions 
[https://launchpad.net/ubuntu/+source/gutenprint](https://launchpad.net/ubuntu/+source/gutenprint)

---

### Post by dryder on 2010-09-06
SevenMachines

Thanks so much for your reply.

> Alternatively, you could try using the newer maverick versions
[https://launchpad.net/ubuntu/+source/gutenprint](https://launchpad.net/ubuntu/+source/gutenprint)

Yes - ideal! But I am struggling to remove 10.04's gutenprint 5.2.5 and all its libraries (to avoid conflicts) installed when installin 10.04. (In 5.2.6 notes).

I'm not sure if, or how to, installing to another directory, say in /home, is possible and still work in gimp 5.2.5? Although I do have gimp 2.7.1 installed in /home and the build files as detailed [COLOR="Blue"]_[here]("http://blog.bloke.com/2010/06/howto-build-gimp-2-7-1-from-source-step-by-step-ubuntu/")_[/COLOR]

David

---

### Post by stevebu56 on 2010-09-07
I'm not sure if this is the setup you're trying to go for but I was able to build the latest gimp with your provided link.  Then I build the latest version of gutenprint (5.2.6) from source as well.  I was able to then run the gimp & it loaded the gutenprint plugin.  Whether it actually prints or not I don't know but hopefully you'll be able to test that now.  Here's my steps. 

```
sudo apt-get install libgtk2.0-dev libglib2.0-dev libcairo2-dev libpango1.0-dev libatk1.0-dev libgimp2.0-dev
tar -xjf gutenprint-5.2.6.tar.bz2
cd gutenprint-5.2.6
./configure --with-gimp2 --enable-libgutenprintui2  CPPFLAGS="-I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/include/pango-1.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/gimp-2.0"
make 
sudo make install 
```

I initially ran the gimp and it gave the following error.  
libgutenprintui2.so.1: cannot open shared object file: No such file or director
So it looked like the make dropped libgutenprintui2.so into my /usr/local/lib directory so I added it to the LD_LIBRARY_PATH and then the gimp could find it. 
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
gimp &
```

You may have to change some of the CPPFLAGS paths in the ./configure line to match where your library headers are.  Hopefully that will work though, but let us know. 

Hope this helps.

---

### Post by dryder on 2010-09-09
stevebu56

Thank you for your post and instructions (which I'm dissecting to understand the process).

> sudo apt-get install libgtk2.0-dev libglib2.0-dev libcairo2-dev libpango1.0-dev libatk1.0-dev libgimp2.0-dev
tar -xjf gutenprint-5.2.6.tar.bz2
cd gutenprint-5.2.6
./configure --with-gimp2 --enable-libgutenprintui2  CPPFLAGS="-I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/include/pango-1.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/gimp-2.0"
make 
sudo make install worked a treat (after I rebooted) in gimp 2.6. Thank you! :D

I have gimp 2.7.1 installed in my home directory - gutenprint of any version does not show in that. I assume it is the path - presumable that will be the 'make' process I need to edit to point to it?

Many, many thanks
David

---

### Post by stevebu56 on 2010-09-09
I'm glad it's working in 2.6. 

I actually built gimp 2.7.1 & then I think while I was testing I was actually running 2.6 by accident. Ooops.  You won't have to build anything else since the plugin is built for the 2.x gimp so it should work with 2.6 & 2.7.1.  

I was able to do the following to get it to work.  There may be a more correct way that gimp does this but I don't know it. 
```
ln -s /usr/lib/gimp/2.0/plug-ins/gutenprint ~/.gimp-2.7/plug-ins/
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
cd ~/gimp-2.7.1/bin
./gimp-2.7 & 
```

You may have to change where you set LD_LIBRARY_PATH to if you set the prefix to somewhere different when building the plugin.  Gimp will complain about missing libraries on startup if it can't find anything.

---

### Post by dryder on 2010-09-10
stevebu56

Thanks - again!

I did not use ./gimp-2.7 & as I put the launch in the Graphics menu.

All went smoothly and well - in both versions of gimp.

I will study and read up on your commands so I can learn.

David:D

---

### Post by stevebu56 on 2010-09-10
No problem, glad to help.

---

