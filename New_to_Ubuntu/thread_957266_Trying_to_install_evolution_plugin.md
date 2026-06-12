---
title: "Trying to install evolution plugin"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-10-24
So I decided, for fun, to try evolution out. 

Everything works fine so far but I noticed I messed up and created multiple copies of email messages.

I did a google search and found a remove duplicate plugin for Evolution ([http://www.siltala.net/2007/11/18/getting-rid-of-duplicate-messages-in-evolution/](http://www.siltala.net/2007/11/18/getting-rid-of-duplicate-messages-in-evolution/))

I went to the link given and then clicked download, the file is in .gz.tar format (tarball right?) but I havent the slightest clue what to do with this file now.

Do I just plunk the extracted file into the .evolution folder and everything is set?

A heads up would help immensely.

Thanks.

---

### Post by quirks on 2008-10-24
It looks like you have to compile the package yourself.

Extract the package somewhere on your Desktop or Home Folder. There is a file named INSTALL. Installation instructions are in this file. In short, it says:

```
cd /path/to/where/you/extracted/the/package
./configure
make
make install
```

Probably, you must be root to install the package.

I recommend, testing the installation on a live CD first. If you mess things up, you can revert changes easily by rebooting.

EDIT: Almost forgot to mention: a comment on the page you linked stated, that the package evolution-dev needs to installed in order that the plug-in compiles.
```
sudo apt-get install evolution-dev
```

---

### Post by VitaminBB on 2008-10-24
> **quirks said:**
> It looks like you have to compile the package yourself.

Extract the package somewhere on your Desktop or Home Folder. There is a file named INSTALL. Installation instructions are in this file. In short, it says:

```
cd /path/to/where/you/extracted/the/package
./configure
make
make install
```

Probably, you must be root to install the package.

I recommend, testing the installation on a live CD first. If you mess things up, you can revert changes easily by rebooting.

EDIT: Almost forgot to mention: a comment on the page you linked stated, that the package evolution-dev needs to installed in order that the plug-in compiles.
```
sudo apt-get install evolution-dev
```

Back to thunderbird I go !

---

### Post by Orfintain on 2008-10-28
> **quirks said:**
> It looks like you have to compile the package yourself.

Extract the package somewhere on your Desktop or Home Folder. There is a file named INSTALL. Installation instructions are in this file. In short, it says:

```
cd /path/to/where/you/extracted/the/package
./configure
make
make install
```

Probably, you must be root to install the package.

I recommend, testing the installation on a live CD first. If you mess things up, you can revert changes easily by rebooting.

EDIT: Almost forgot to mention: a comment on the page you linked stated, that the package evolution-dev needs to installed in order that the plug-in compiles.
```
sudo apt-get install evolution-dev
```


configure: error: Package requirements (
		  evolution-plugin-2.4 >= 2.3.2
		  ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the REMOVE_DUPLICATES_PLUGIN_CFLAGS and REMOVE_DUPLICATES_PLUGIN_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

Any Idea anyone? I got the above when running the configure from root after installing dev package.

---

### Post by Vince-0 on 2008-11-28
I'm getting this exact same error, I have no idea on how to proceed with that.

I also tried a script from the following location:
[http://lists.ximian.com/archives/public/evolution/2005-January/041442.html](http://lists.ximian.com/archives/public/evolution/2005-January/041442.html)

But it also gives errors:

[I][SIZE="2"]Use of uninitialized value $_ in substitution (s///) at ./RBOX.sh line 79.
Use of uninitialized value $Message in pattern match (m//) at ./RBOX.sh line 135.
Use of uninitialized value $Message in substitution (s///) at ./RBOX.sh line 140.
Use of uninitialized value $Message in substr at ./RBOX.sh line 144.
substr outside of string at ./RBOX.sh line 144.
Use of uninitialized value in split at ./RBOX.sh line 144.
Use of uninitialized value $Message in concatenation (.) or string at ./RBOX.sh line 147.
Error in message![/SIZE][/I]

Bleh for duplicate mails!:confused:

---

### Post by Xlylith on 2009-10-05
If you have executed ./configure before installing evolution-plugins and evolution-dev, perhaps you can try installing from a freshly extracted source. Try delete the remove-duplicate-plugin folder you have configured then extract again from the remove-duplicates-plugin-0.0.4.tar.gz file. It works for me.

---

