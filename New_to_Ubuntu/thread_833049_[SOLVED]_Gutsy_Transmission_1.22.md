---
title: "[SOLVED] Gutsy Transmission 1.22"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by danmeetswood on 2008-06-18
So Gutsy comes with Transmission 1.11, now. And Hardy comes with Transmission 1.22. I was wondering if it were possible to get Transmission 1.22 on Gutsy, as I like the features of 1.22, but don't want to update to Hardy.

---

### Post by milosz.galazka on 2008-06-18
You could compile it from source or probably use backports repository...

---

### Post by danmeetswood on 2008-06-18
> **milosz.galazka said:**
> You could compile it from source or probably use backports repository...

Any idea on how to do any of that?

---

### Post by RomeReactor on 2008-06-18
Hi. In Synaptic, go to 'Settings->Repositories' and on the 'Updates' tab check the box for 'Unsupported updates (gutsy backports)'. Close the softwre sources window, press the blue 'Reload' button to update the repository information, and search for Transmission. It's probable that the update manager will pop up with other updates taken from that repository. If you don't want other version upgrades, disable the repository after installing Transmission. Not sure which version you'll get ([it's listed as 1.06]("http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=gutsy-backports&section=all")).

To install from source, you need to install the tools necessary to compile Transmission:
```
sudo aptitude install build-essential
```
and Transmission's dependencies:
```
sudo apt-get build-dep transmission transmission-gtk
```
then [download the source]("http://download.m0k.org/transmission/files/transmission-1.22.tar.bz2"); instructions on how to compile it will be in a README or INSTALL file.

---

### Post by Exsecrabilus on 2008-06-18
You could try downloading Transmission 1.22 from [Getdeb](http://getdeb.net/search.php?keywords=transmission).
Packaged for Hardy, but you never know. Could work for Gutsy.

---

### Post by danmeetswood on 2008-06-18
> **RomeReactor said:**
> Hi. In Synaptic, go to 'Settings->Repositories' and on the 'Updates' tab check the box for 'Unsupported updates (gutsy backports)'. Close the softwre sources window, press the blue 'Reload' button to update the repository information, and search for Transmission. It's probable that the update manager will pop up with other updates taken from that repository. If you don't want other version upgrades, disable the repository after installing Transmission. Not sure which version you'll get ([it's listed as 1.06]("http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=gutsy-backports&section=all")).

To install from source, you need to install the tools necessary to compile Transmission:
```
sudo aptitude install build-essential
```
and Transmission's dependencies:
```
sudo apt-get build-dep transmission transmission-gtk
```
then [download the source]("http://download.m0k.org/transmission/files/transmission-1.22.tar.bz2"); instructions on how to compile it will be in a README or INSTALL file.

Thanks for the post. I'm trying it from source. Might have hit a snag, though, with this.

dan@dennis:~/transmission-1.22$ ./configure -q && make -s
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
configure: error: Package requirements (libcurl >= 7.15.0) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBCURL_CFLAGS
and LIBCURL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by RomeReactor on 2008-06-18
Did you install the dependencies? do a search for libcurl using aptitude, to see if it's installed:
```
aptitude search libcurl
```
and post back the output. I compiled Transmission when I used Gutsy, and don't remember hitting any roadblocks.

EDIT: Or you might have an older version of libcurl installed.

---

### Post by danmeetswood on 2008-06-18
> **RomeReactor said:**
> Did you install the dependencies? do a search for libcurl using aptitude, to see if it's installed:
```
aptitude search libcurl
```
and post back the output. I compiled Transmission when I used Gutsy, and don't remember hitting any roadblocks.

EDIT: Or you might have an older version of libcurl installed.

Here you go. And thanks for the interest.

dan@dennis:~$ aptitude search libcurl
p   gimp-libcurl                    - libcurl URI plugin for The GIMP           
v   libcurl-dev                     -                                           
p   libcurl-ocaml                   - ocaml curl bindings                       
p   libcurl-ocaml-dev               - ocaml libcurl bindings                    
v   libcurl-ssl-dev                 -                                           
p   libcurl3                        - Multi-protocol file transfer library (Open
p   libcurl3-dbg                    - libcurl compiled with debug symbols       
v   libcurl3-dev                    -                                           
i   libcurl3-gnutls                 - Multi-protocol file transfer library (GnuT
v   libcurl3-gnutls-dev             -                                           
v   libcurl3-openssl-dev            -                                           
v   libcurl4-dbg                    -                                           
v   libcurl4-dev                    -                                           
p   libcurl4-gnutls-dev             - Development files and documentation for li
p   libcurl4-openssl-dev            - Development files and documentation for li

---

### Post by RomeReactor on 2008-06-18
Seems I missed a package regarding the dependencies:
```
sudo apt-get build-dep transmission-common transmission-gtk
```

Try building it then. If you keep getting the error, try:
```
sudo aptitude install libcurl3 libcurl3-gnutls
```

---

### Post by danmeetswood on 2008-06-18
> **RomeReactor said:**
> Seems I missed a package regarding the dependencies:
```
sudo apt-get build-dep transmission-common transmission-gtk
```

Try building it then. If you keep getting the error, try:
```
sudo aptitude install libcurl3 libcurl3-gnutls
```

Still getting this after trying both of your steps. This is where I would normally give up, haha, unless you have some other piece of wisdom.

dan@dennis:~/transmission-1.22$ ./configure -q && make -s
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
configure: error: Package requirements (libcurl >= 7.15.0) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBCURL_CFLAGS
and LIBCURL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by RomeReactor on 2008-06-18
It's looking for libcurl.pc, which is provided by **libcurl4-openssl-dev** or **libcurl4-gnutls-dev**, so try with:
```
sudo aptitude install libcurl4-openssl-dev
```

---

### Post by danmeetswood on 2008-06-18
> **RomeReactor said:**
> It's looking for libcurl.pc, which is provided by **libcurl4-openssl-dev** or ```
libcurl4-gnutls-dev
```, so try with:
```
sudo aptitude install libcurl4-openssl-dev
```

Hey, it worked! I'm pleasantly surprised.
You're a pretty cool guy, cool guy.

---

### Post by RomeReactor on 2008-06-18
Glad you got it working. Welcome to the forums!

---

### Post by neostead on 2008-11-21
> **RomeReactor said:**
> It's looking for libcurl.pc, which is provided by **libcurl4-openssl-dev** or **libcurl4-gnutls-dev**, so try with:
```
sudo aptitude install libcurl4-openssl-dev
```

Tank You, master
i love ubuntu support ^^

---

