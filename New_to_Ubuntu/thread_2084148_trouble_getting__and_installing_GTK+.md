---
title: "trouble getting  and installing GTK+"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by nycap on 2012-11-14
to install wireshark i need to install GTK+ versions => 2.12 and < 3

having no luck after downloading a bunch of tar.gz files none of which i can install.  when i extract the files the folder is empty.  Thanks in advance.

---

### Post by MG&amp;TL on 2012-11-14
Why do you need a version of wireshark that is not in the repositories?

---

### Post by nycap on 2012-11-14
i got the latest version of wireshark from wireshark but when i try to install wireshark the error says i need to install GTK+ versions 2.12.0 and up but less than version 3.   i dont know why wireshark wants this.  i dont even know what the repositories are (sorry learning as i go its been less than a day using ubuntu). is there some easier way to install wireshark.

---

### Post by MG&amp;TL on 2012-11-14
> **nycap said:**
> when i try to install wireshark the error says i need to install GTK+ versions 2.12.0 and up but less than version 3.   i dont know why wireshark wants this.

Is that the version from the repositories? That is weird...it should really install those on its own if you used the package manager.

```
sudo apt-get install wireshark
```

...if you didn't. :)

---

### Post by nycap on 2012-11-14
> **MG&TL said:**
> Is that the version from the repositories? That is weird...it should really install those on its own if you used the package manager.

```
sudo apt-get install wireshark
```...if you didn't. :)

sweet.  thanks a bunch!  its installed and working

---

### Post by nycap on 2012-11-14
> **MG&TL said:**
> Why do you need a version of wireshark that is not in the repositories?

maybe i shouldnt get happy yet.  i want to sniff digital radio signals so i have to "patch the sources and rebuild it".  i dont know what this means exactly  but i think it means i have to use the source code?

---

### Post by nycap on 2012-11-14
```
sudo apt-get install wireshark
```...if you didn't. :)[/QUOTE]

"Most GNU/Linux distributions provide a source code package and so you  should follow the appropriate procedure to download and install the  sources."

is this what the command above does?

---

### Post by MG&amp;TL on 2012-11-14
> **nycap said:**
> maybe i shouldnt get happy yet.  i want to sniff digital radio signals so i have to "patch the sources and rebuild it".  i dont know what this means exactly  but i think it means i have to use the source code?

Yes, it does. Link me to the page, but normally you'll need the original source code and a .patch file (basically a list of differences you need to apply), which you'll need to apply with the *patch* program.

To build wireshark, you'll need to install the development libraries. You can get Ubuntu to do this for you, with:

```
sudo apt-get build-dep wireshark
```

Hope that helps a bit, see if you can find a tutorial on building wireshark. I suggest you build the original wireshark first and see if that works or not.

---

### Post by MG&amp;TL on 2012-11-14
> **nycap said:**
> ```
sudo apt-get install wireshark
```...if you didn't. :)

"Most GNU/Linux distributions provide a source code package and so you  should follow the appropriate procedure to download and install the  sources."

is this what the command above does?[/QUOTE]

Ahah, no. Right:

In Ubuntu (and its big daddy, Debian), the *apt* program provides various utilities to automatically install, upgrade, and remove stuff. The packages it downloads and uses are pre-built binaries, rather than source packages.

To build something from source, you can either get a dump of the source code for package <x> (e.g. 'wireshark') with:

```
apt-get source <x>
```

or you can just pull it from wherever the project keeps its source code.

```
sudo apt-get install <x>
```

Just installs package <x> :)

---

### Post by nycap on 2012-11-14
> **MG&TL said:**
> Yes, it does. Link me to the page...
This is the page that contains what im trying to do. 

[http://op25.osmocom.org/wiki](http://op25.osmocom.org/wiki)

its an awesome software defined radio but hard for me to get it up and running especially since i am new to ubuntu.

any help will be much appreciated

---

### Post by MG&amp;TL on 2012-11-14
Looks like a pretty cool project. :)

Well, the instructions seem pretty comprehensive, but you'll need the source tree first: [http://www.wireshark.org/docs/wsdg_html_chunked/ChSrcObtain.html](http://www.wireshark.org/docs/wsdg_html_chunked/ChSrcObtain.html)

...have fun!

---

