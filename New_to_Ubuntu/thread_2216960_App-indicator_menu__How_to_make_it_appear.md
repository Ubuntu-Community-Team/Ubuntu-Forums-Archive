---
title: "App-indicator menu : How to make it appear?"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by anumaz on 2014-04-14
Hey all!

I do have python-appindicator, and I have installed an application requiring it (Nanoshot) - However, I do not see that menu.

Any help?

Thanks!
Anthony D.

---

### Post by Bashing-om on 2014-04-14
anumaz; Hey ,

What release did you install, and if not standaard 'ubuntu' what desktop are you using ?
If standard ubuntu try:
click on the dash (top icon on the 'launcher' - the column of icons at the left of the screen -,
In the search box that appears type  "python-appindicator";
in the results below will appear the related icon for " python-appindicator".

If it is to be an oft-used ap, by all means drag that icon to the launcher, right click on it and "pin" it to the launcher.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
Hi,

I am using the most standard ubuntu ever. I am searching for 'python-appindicator' and nothing appears. Although, it is installed! 

Any clue?

---

### Post by Bashing-om on 2014-04-14
anumaz; Well !

OK, hunting mode.
find out where it is:
```

which python-appindicator
#or maybe better yet:
sudo find / -name python-appindicator

```
That 'find' command searches the whole computer for that one instance, will take bit of time to look through and match what you are looking for. Patience.

Maybe start that sucker from terminal - if the application is installed in your "path"?
```

python-appindicator

``` at least will get some amplifying info.

[INDENT]it's ubuntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
Hey!

Found it in: /usr/share/doc/pythin-appindicator

Then I did

cd /usr/share/doc/pythin-appindicator

then

python-appindicator 

but I get: command not found

---

### Post by Bashing-om on 2014-04-14
anumaz; Hey !

This is but,
> 
/usr/share/doc/pythin-appindicator

the documentation for that application, [doc = documentation].

Let's look and see what is installed for sure.
```

dpkg -l python-appindicator

```
that is python with an 'o' not with the 'i'.

Now are we barking up the wrong tree ?
do:
```

apt-cache search python-appindicator

```
that return  " python-appindicator - Python bindings for libappindicator" indicates this is a module for the library  "libappindicator"; Maybe not at all an application .

Now that begs the question, what are we hunting for ?

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-14
anumaz; Well,

Supporting evidence of my theory:
do:
```

apt-cache show python-appindicator

```
this:
> 
Description-en: Python bindings for libappindicator
 This package provides Python bindings so that you can use libappindicator from
 a Python program.


So, tell us what you are trying to do from what means , and to what end .

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
anthony@anthony-MS-7673:~$ dpkg -l python-appindicator
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python-appindi 0.4.92-0ubuntu Python bindings for libappindicator
anthony@anthony-MS-7673:~$ apt-cache search python-appindicator
python-appindicator - Python bindings for libappindicator
anthony@anthony-MS-7673:~$ 



So... what now? :p

---

### Post by Bashing-om on 2014-04-14
anumaz; Hello,

We posted at the same time. 

See my last, and we go from there.
But be aware, it always amazes me what I do not know ( and maybe what I do not want to know )_ .

[INDENT]sometimes a little help
[INDENT][INDENT][INDENT]goes a long way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
> **Bashing-om said:**
> anumaz; Hello,

We posted at the same time. 

See my last, and we go from there.
But be aware, it always amazes me what I do not know ( and maybe what I do not want to know )_ .

[INDENT]sometimes a little help
[INDENT][INDENT][INDENT]goes a long way
[/INDENT][/INDENT][/INDENT][/INDENT]

Issue is I don't see that menu, even though I installed a software using it (Nanoshot)

---

### Post by Bashing-om on 2014-04-14
anumaz; OK.

The module 'python-appindicator' is but a binder to the library libappindicator, such that [color=red]any[/color] Python program can have access.
As such I would not expect 'python-appindicator' it's self to have a menu.

Are you having problems with Nanoshot ? It must have been installed from a PPA (Personal Package Archive), is Nanoshot fully supported in the release of ubuntu that you have installed ?
We can verify;
```

lsb_release -a
cat /etc/apt/sources.list.d/*.list

``` where I expect the fetch file was installed, and we can check the source.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-15
> anthony@anthony-MS-7673:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise
anthony@anthony-MS-7673:~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/nanoshot/ppa/ubuntu](http://ppa.launchpad.net/nanoshot/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/nanoshot/ppa/ubuntu](http://ppa.launchpad.net/nanoshot/ppa/ubuntu) precise main
deb [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
deb-src [arch=amd64,i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main


This is what I get!

---

### Post by Bashing-om on 2014-04-15
anumaz, Hey,

You are covered, should workie great.
From that source list:
> 
deb [http://ppa.launchpad.net/nanoshot/ppa/ubuntu](http://ppa.launchpad.net/nanoshot/ppa/ubuntu) precise main

```

	Name	Last modified	Size
	Parent Directory	 	 -
	jaunty/	11-Feb-2011 22:03	 -
	karmic/	11-Feb-2011 22:03	 -
	lucid/	11-Feb-2011 22:03	 -
	maverick/	11-Feb-2011 22:03	 -
	natty/	11-Feb-2011 22:03	 -
	oneiric/	09-May-2011 14:51	 -
	[color=blue]precise/[/color]	21-Feb-2012 13:53	 -

```

So I must inquire again, what is the nature of the problem ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-15
Nanoshot's menu (using appindicator) doesn't show up haha.

---

### Post by Bashing-om on 2014-04-15
anumaz: yes !

Now we have a definition. So, is the problem with Nanoshot ? or elsewhere ?
check: from terminal will Nanoshot launch ?
Any errors generated ?
------------------
I am done for this session, and am retiring to rest the weary mind. Will continue this in my AM.

small steps but we get there

---

### Post by anumaz on 2014-04-15
> **Bashing-om said:**
> anumaz: yes !

Now we have a definition. So, is the problem with Nanoshot ? or elsewhere ?
check: from terminal will Nanoshot launch ?
Any errors generated ?
----------page--------
I am done for this session, and am retiring to rest the weary mind. Will continue this in my AM.

small steps but we get there

Shame on me. 

I don't know what you made me to do - but it's working.

Heh, solved! 

Thanks!!

---

### Post by Bashing-om on 2014-04-15
anumaz; Great !

Some small glitch somewhere, I recon. Maybe starting the ap from terminal resolved it (?).

In any event,
[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

