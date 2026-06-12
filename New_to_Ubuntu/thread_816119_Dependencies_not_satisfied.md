---
title: "Dependencies not satisfied"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by EmiSic on 2008-06-02
Hello all.
I want to install AWN in Hardy.

The dependencies has been download from [[COLOR="RoyalBlue"]www.packages.ubuntu.com/hardy[/COLOR]]("http://www.packages.ubuntu.com/hardy") one by one.
I got this error when installing **automake_1.10.1-2_all.deb** using GDebi.

'Dependencies not satisfied'

For your information, I don't have internet connection for using APT-Get, update or download necessary dependencies automatically.

I do it manually.

Need some guide.

Thanks & regards.

---

### Post by bumanie on 2008-06-02
You can get AWN via synaptic in 8.04. You won't have dependancy issues either.

---

### Post by unutbu on 2008-06-02
Run Synaptic (even though you don't have a connection.) Mark avant-window-navigator for installation. Then go to File>Generate package download script. Save the file as, say, ~/download.sh.

You can run the script on a linux box with a connection to the internet, or you can open download.sh in a text editor and find out all the packages you need to have installed.

---

### Post by Joeb454 on 2008-06-02
Did you get it from the following page?

[http://packages.ubuntu.com/hardy/automake](http://packages.ubuntu.com/hardy/automake)

---

### Post by EmiSic on 2008-06-02
Yes, correct.I'm  download the .deb from **[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)** & **Launchpad**

Below is the .deb file that I've download:
[LIST=1]
[*]gnome-common 
[*]automake 
[*]build-essential
[*]gtk-doc-tools 
[*]libglib2.0-dev 
[*]python2.5-dev **=OK **
[*]bzr **=OK** 
[*]python-gtk2-dev 
[*]python-cairo-dev 
[*]libglade2-dev 
[*]libdbus-glib-1-dev 
[*]libgnome-desktop-dev 
[*]libgnome-dev 
[*]libgsf-gnome-1-dev
[*]libwnck-dev 
[*]libsexy-dev 
[*]libnotify-dev 
[*]librsvg2-dev 
[*]libgnome-menu-dev 
[*]libgtop2-dev 
[*]libvte-dev 
[*]python-alsaaudio **=OK** 
[*]python-feedparser **=OK** 
[*]python-gnome2-extras-dev
[/LIST]

I do the download process not from my machine.

Not try the Synaptic yet. I'll try later.

Thanks buddies! :)

---

### Post by EmiSic on 2008-06-02
Eventhough i use the terminal to execute this command 
**./autogen.sh --prefix=/usr && make** for installing AWN but why
it contain error?automake and several dependecies not installed.

Thanks & regards.

---

### Post by unutbu on 2008-06-02
EmiSic, I'm not sure what you are doing with autogen and automake. These are tools for compiling programs. Since you are downloading .deb files, it appears you are installing pre-made packages, thus avoiding the need to compile these things yourself.

Once you download the .deb files, you can install them (I think) by just double-clicking on them from a nautilus window, or you can run
```

dpkg -i <.deb filename>
```
Of course, substitute the real .deb filename for "<.deb filename>".

Note that order is important -- you have to install the .deb files in an order such that all dependencies are satisfied. For example, avant-window-navigator depends on libc6, so you must install libc6 before you install avant-window-navigator. But libc6 depends on libgcc1, so you must install libgcc1 before you install libc6. And on and on. This is a bit of an annoyance, and why it is much easier to install packages after you have a network connection (if possible). Synaptic or apt-get would take care of the ordering for you.

---

### Post by shifty_powers on 2008-06-02
would it not be simpler to just download the awn deb, rather than mess around with make?

[http://packages.ubuntu.com/hardy/avant-window-navigator](http://packages.ubuntu.com/hardy/avant-window-navigator)

---

### Post by EmiSic on 2008-06-04
> **shifty_powers said:**
> would it not be simpler to just download the awn deb, rather than mess around with make?

[http://packages.ubuntu.com/hardy/avant-window-navigator](http://packages.ubuntu.com/hardy/avant-window-navigator)

(sigh) Already download the .deb package,but it doesn't work..Still mention the error 'Dependences not satisfiable". :(

---

### Post by unutbu on 2008-06-04
EmiSic, follow post #3. The script that Synaptic generates will tell you all the packages you need that you currently don't have.

---

