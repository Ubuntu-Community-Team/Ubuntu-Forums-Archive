---
title: "Absolute Beginner install question..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by samthetrue on 2008-06-03
As I was well aware before switching to linux, installing is certainly different... So I have some questions.

First off, I've read [This]("http://monkeyblog.org/ubuntu/installing/") page though and through, made notes, and just about every other page on installing (As its a rather important thing, cant do anything without installing.

So far (for two or three days) I've managed to fake it, not to mention EVERYTHING you could possibly want is in the synaptic packet manager.
But that doesn't mean i don't need to know this stuff.  

My question is currently about the install sequence for source packages, in this case a .tgz file. I have extracted it and placed the resulting file in my home directory. I navigate to said directory using terminal. Now what?

I type make... nothing happens, but i do recieve a error message saying 
[ -x /usr/local/bin/alephone ] || ( echo /usr/local/bin/alephone is not executable && false)
/usr/local/bin/alephone is not executable
make: *** [sanity] Error 1

(I chuckle at sanity error one, its usually not unwell much later in the install that there are problems with sanity)
This is asking for more files, some of the handy packs that files come in correct? I need to run and find (perhaps in the support section of where I acquired this installer) it, install that, then try again?

I will attempt that in the mean time, but if i might ask, would it be possible to have an install guide with example files on it? something that you could test as it taught you? if theres already such a thing, would someone point me to it?

These are probably stupid questions... but it certainly would be helpful to know

Thank ye! (First post hehe)



#Edit1:minor spacing fix
#Edit2:I emailed my suggestion of example file installers to Simon Gray, the guy who's name is at the bottom of the install anything in Ubuntu... I probably should wait until i know what I'm doing in ubuntu, Ohh well, I've never been that good at keeping my mouth shut.

---

### Post by Tomatz on 2008-06-03
> **samthetrue said:**
> As I was well aware before switching to linux, installing is certainly different... So I have some questions.

First off, I've read [This]("http://monkeyblog.org/ubuntu/installing/") page though and through, made notes, and just about every other page on installing (As its a rather important thing, cant do anything without installing.

So far (for two or three days) I've managed to fake it, not to mention EVERYTHING you could possibly want is in the synaptic packet manager.
But that doesn't mean i don't need to know this stuff.  

My question is currently about the install sequence for source packages, in this case a .tgz file. I have extracted it and placed the resulting file in my home directory. I navigate to said directory using terminal. Now what?

I type make... nothing happens, but i do recieve a error message saying 
[ -x /usr/local/bin/alephone ] || ( echo /usr/local/bin/alephone is not executable && false)
/usr/local/bin/alephone is not executable
make: *** [sanity] Error 1

(I chuckle at sanity error one, its usually not unwell much later in the install that there are problems with sanity)
This is asking for more files, some of the handy packs that files come in correct? I need to run and find (perhaps in the support section of where I acquired this installer) it, install that, then try again?

I will attempt that in the mean time, but if i might ask, would it be possible to have an install guide with example files on it? something that you could test as it taught you? if theres already such a thing, would someone point me to it?

These are probably stupid questions... but it certainly would be helpful to know

Thank ye! (First post hehe)

#Edit1:minor spacing fix

Try:

```
./configure
```

then

```
make
```

then

```
sudo make install
```

When you do the ./configure command you may see a message asking for a dependency to be installed. Just install it via synaptic if possible.

If you encounter errors post the error message here ;)

---

### Post by spiderbatdad on 2008-06-03
Generally, I right click the tar package and select 'extract here' Then open the newly created folder and look for the 'readme' or install instructions...sometimes these are even in a folder called docs, inside the package folder.

Also, the package build-essential is necessary for compiling from source:
```
sudo apt-get install build-essential
```

Anyway, from the terminal you generally cd into the new folder after extracting the package in order to run ./configure  make and sudo make install

Directories are case sensitive. Tab will auto complete most directory names for you. If a folder is on your Desktop, Desktop needs to be in the path, so,```
cd Desktop/folder_name
```

Also checkinstall is a good program to know about:[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by hyper_ch on 2008-06-03
and you also need to compiling tools
```

sudo apt-get install build-essential

```

and then you will need to satisfy the dependencies for that thing you want to compile (mostly you will miss the -dev packages that can be installed through apt)

---

### Post by iaculallad on 2008-06-03
You might also need to install the build essential files

```
sudo apt-get install build-essential
```

---

### Post by samthetrue on 2008-06-05
Thanks for the advice :)

---

