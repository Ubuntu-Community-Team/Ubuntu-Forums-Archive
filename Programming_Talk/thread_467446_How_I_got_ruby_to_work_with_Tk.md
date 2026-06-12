---
title: "How I got ruby to work with Tk"
date: 2007-06-07
forum: Programming Talk
---

### Post by hasimir44 on 2007-06-07
It bugged me that the "Simple Tk Application" from the pickaxe book wasn't working:

     [http://www.rubycentral.com/book/ext_tk.html](http://www.rubycentral.com/book/ext_tk.html)

Everytime I ran a ruby script with:

```
require 'tk'
```

I got the following error:

```
`require': no such file to load -- tk (LoadError)
```

So I.. 

1. Uninstalled ruby from apt-get 
```
sudo apt-get remove ruby
```

2. Found out what version of tk I have installed: 

```
ls -d /usr/lib/tk*
/usr/lib/tk8.4
```

3. Found out what version of tcl I have installed: 

```
ls -d /usr/lib/tcl*
/usr/lib/tcl8.4
```

4. Found out where my tcl includes are:

```
 ls -d /usr/include/tcl*
/usr/include/tcl8.4

```

5. Downloaded the source for ruby (link for 1.8.6): 

    [ftp://ftp.ruby-lang.org/pub/ruby/ruby-1.8.6.tar.gz](ftp://ftp.ruby-lang.org/pub/ruby/ruby-1.8.6.tar.gz)

6. Unpacked the tar and entered the source  (sorry Bruce, no dragons :))

```
tar zxvf ruby-1.8.6.tar.gz
cd ruby-1.8.6
```

7. Configured (using steps 2, 3, and 4), built and installed:

```
./configure --with-tcl-include=/usr/include/tcl8.4/ --with-tcllib=tcl8.4 --with-tklib=tk8.4 --enable-pthread
make
make test
sudo make install

```

The above may not be the best way to accomplish this task, but hey.. it worked for me :)

---

### Post by winch on 2007-06-08
Or you could have installed libtcltk-ruby from universe ;)

---

### Post by hasimir44 on 2007-06-08
now you tell me :)

---

