---
title: "Issues with installation of certain PPA."
date: 2014-07-29
forum: New to Ubuntu
---

### Post by vladimir18 on 2014-07-29
Good morning.
So, I have decided to install this package(Infinality-ultimate) off PPA Launchpad - [https://launchpad.net/~blue-shell/+archive/ubuntu/infinality-ultimate](https://launchpad.net/~blue-shell/+archive/ubuntu/infinality-ultimate)
I have successfully added it via terminal and updated my system afterwards, however, I am troubled as to what to do after all that.
I have tried to run command and other variations of it:
```
sudo apt-get install infinality-ultimate
```
Yet it simply outputs an error saying that package is nonexistent.
I, however, had no issues with installing this PPA -  [https://launchpad.net/~no1wantdthisname/+archive/ubuntu/ppa](https://launchpad.net/~no1wantdthisname/+archive/ubuntu/ppa)
What do I do to resolve this issue?

---

### Post by howefield on 2014-07-29
Sounds like you got the package name incorrect ?

Try opening a terminal and search apt-cache

```
apt-cache search keyword
```

---

### Post by bapoumba on 2014-07-29
[https://launchpad.net/~blue-shell/+archive/ubuntu/infinality-ultimate/+packages](https://launchpad.net/~blue-shell/+archive/ubuntu/infinality-ultimate/+packages)
Please have a look at the packages the ppa contains and install one of them.

Last thing, please consider installing ppa-purge should you consider to revert packages back to their original distribution version.
Edit : ninja'd :)

---

### Post by vladimir18 on 2014-07-29
After the search it doesn't seems like any packages are added via PPA.
Oh well, seems like an issue within a PPA itself, looks like I am bound on compiling via GitHub now.

Bapoumba, both
```
sudo apt-get install cairo
sudo apt-get install fontconfig
sudo apt-get install freetype
```
Output with "Unable to locate package" error.

---

### Post by bapoumba on 2014-07-29
Hmm.
```
apt-cache policy cairo
```
or fontconfig, or freetype. May be the ppa did not install correctly ?
```
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by vladimir18 on 2014-07-29
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy cairo[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Outputs with same error.
As of second command, it seems like it is installed properly:
[/FONT][/COLOR]```
 tail -v -n +1 /etc/apt/sources.list.d/rjvbertin-infinaltimate-trusty.list==> /etc/apt/sources.list.d/rjvbertin-infinaltimate-trusty.list <==
deb http://ppa.launchpad.net/rjvbertin/infinaltimate/ubuntu trusty main
deb-src http://ppa.launchpad.net/rjvbertin/infinaltimate/ubuntu trusty main

```

---

### Post by kira-yamato-2008 on 2014-07-29
This is what the Packages look like on the launch pad.

```
cairo-infinality-ultimate-*
 fontconfig-infinality-ultimate-*
freetype2-infinality-ultimate-*
```

So in my experience this is what the code should look like:

```
sudo apt-get install cairo-infinality-ultimate-*
```
 
and/or

```
sudo apt-get install fontconfig-infinality-ultimate-*
```

and/or

```
sudo apt-get install freetype2-infinality-ultimate-*
```

My question is; do you need all three, or a specific one and another, or just one for these to work?

Note: Might not need the -* at the end.

---

### Post by vladimir18 on 2014-07-29
Kira,
Nope, same error:
```
sudo apt-get install cairo-infinality-ultimate-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cairo-infinality-ultimate-*
E: Couldn't find any package by regex 'cairo-infinality-ultimate-*'
```
Or
```
sudo apt-get install cairo-infinality-ultimate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cairo-infinality-ultimate
```
> [COLOR=#000000]My question is; do you need all three, or a specific one and another, or just one for these to work?[/COLOR][COLOR=#000000]
All three is preferred, they look gorgeous when combined.[/COLOR]

---

### Post by newb85 on 2014-07-29
As bapoumba said, you need to look at what packages are in that ppa.  This one contains two: fontconfig-infinality and freetype.  I would venture a guess that what you're looking for is a font contained in or installed by one of those two.

And don't forget to run
```
sudo apt-get update
```
after you've added the repository, so that the packages in it will be added to your machine's list of available packages.

---

### Post by vladimir18 on 2014-07-29
Yes, I did update.
I got [COLOR=#000000]fontconfig-infinality from another PPA and 
```
 sudo apt-get install freetype
```
Outputs with yet another "package missing" error.[/COLOR]

---

### Post by bapoumba on 2014-07-29
I'll need to reboot into Trusty to check, currently on Utopic. Did add th eppa on Utopic and tweaked a bit, but none of the packages are available from this repo. I already have freetype installed so tested it with cairo and could not find it.

---

### Post by newb85 on 2014-07-29
Hmm...looks like I was wrong.  The list I looked at can't be trusted.  On my test system (trusty), the packages freetype2-demos, libfreetype6, and libfreetype6-dev were made available through this ppa.  (Actually, the last two are already in the repos, just different versions.)

---

### Post by bapoumba on 2014-07-29
Thanks for testing newb85 :)

---

### Post by vladimir18 on 2014-07-29
> **newb85 said:**
> Hmm...looks like I was wrong.  The list I looked at can't be trusted.  On my test system (trusty), the packages freetype2-demos, libfreetype6, and libfreetype6-dev were made available through this ppa.  (Actually, the last two are already in the repos, just different versions.)
Oh, that installed perfectly, thanks.

---

### Post by ajgreeny on 2014-07-29
In these situations it is worth using synaptic to search for the packages that you think should be available.  By using the Origin filter in the left hand pane you can also see exactly which packages are provided and available from each and every ppa repository you have enabled.

I use synaptic for just about every package management activity I carry out and other than the terminal, it is undoubtedly the most informative way to carry out installations, removals and upgrades of packages.  You will probably have to install it before you can use it, depending on which version of *ubuntu you are using, but give it a try; I don't think you'll regret it.

---

