---
title: "Installing Xetex on Hardy"
date: 2008-10-30
forum: Programming Talk
---

### Post by cindyrella on 2008-10-30
Hey Everyone,

I'm trying to install xetex, but am having a bit of trouble. Bison and flex are installed. I also downloaded xetex-0.996.tar.gz and xdvipdfmx-0.4.tar.gz, both of which are sitting on my desktop.

The first three commands worked fine:

```

cindyrella@cindyrella-desktop:~$ tar ~/Desktop/zxf xetex-0.996.tar.gz
cindyrella@cindyrella-desktop:~$ cd xetex-0.996
cindyrella@cindyrella-desktop:~/xetex-0.996$ sh build-xetex 
```

But after putting in the last command, I get the error:

```

cindyrella@cindyrella-desktop:~/xetex-0.996$ sudo sh install-xetex
[sudo] password for cindyrella: 
[: 52: ==: unexpected operator
texhash: Updating /usr/local/share/texmf/ls-R... 
texhash: Done.
[: 17: ==: unexpected operator
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found 
```

Will someone please explain what is going on? What should I try next?

Thanks in advance,
cindy

---

### Post by ad_267 on 2008-10-30
Can't you just do a "sudo apt-get install texlive-xetex" or a System - Administration - Synaptic Package Manager, search for xetex and install texlive-xetex?

---

### Post by cindyrella on 2008-10-30
Good point. Can you tell me if texlive-xetex is the exact same thing as what I'm trying to accomplish above?

(Apparently, I installed texlive-xetex earlier, but didn't know if it was the same.)

---

### Post by ad_267 on 2008-10-30
I'm pretty sure it's the same thing. 

It installs the following executables: 
xdvipdfmx, xetex, xelatex

Although xelatex appears to be a link to xetex.

---

### Post by cindyrella on 2008-10-30
How do you find the contents of any given package?

I now realize that I could have checked for information like this on my own.

Thanks!! (:

---

### Post by ad_267 on 2008-10-30
You can't actually look at the contents unless you download the deb package, so I did:

```
sudo apt-get -d install texlive-xetex
cd /var/cache/apt/archives
dpkg --contents texlive-xetex_2007.dfsg.2-3ubuntu1_i386.deb | grep bin
```

That downloads the package without installing it, then I used dpkg --contents to list the contents and grep to only show files in the bin directory.

If you have installed the package you can view its contents in synaptic or with "dpkg-query -L texlive-xetex".

Usually just looking at the description is enough though.

---

### Post by mali2297 on 2008-10-30
> **ad_267 said:**
> You can't actually look at the contents unless you download the deb package,...

You can browse packages and their contents at [http://packages.ubuntu.com/](http://packages.ubuntu.com/). The file list of texlive-xetex is found [here](http://packages.ubuntu.com/hardy/i386/texlive-xetex/filelist).

---

### Post by hugmenot on 2008-11-03
BTW, the problem with compilation in the OP was that rebuild-formats uses bash-sims but it only asks to be run with /bin/sh at the top. If you change it to /bin/bash it will likely work.

---

### Post by cindyrella on 2008-11-03
How do you change it to /bin/bash?

---

### Post by mali2297 on 2008-11-03
> **cindyrella said:**
> How do you change it to /bin/bash?

I think the easiest way is to run
```

sudo bash install-xetex

```

The alternative is to open the file in an editor and change the top line from #!/bin/sh to #!/bin/bash, then make the file executable with
```

chmod +x install-xetex

```
and run it with
```

sudo ./install-xetex

```

---

