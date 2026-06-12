---
title: "new to ubuntu :: gcc not installed"
date: 2006-01-21
forum: Repositories &amp; Backports
---

### Post by josif on 2006-01-21
I have just installed ubuntu yesterday and I realized that gcc was not working on the terminal shell.

I am used to red hat linux and didn't really understand the idea of repositories.

Also I don't have a network connection to that computer.

Can someone show me how to install gcc ( and also g++, gcj etc..) ?

Thank you all !!!

---

### Post by benguin on 2006-01-21
Hi,
Ubuntu does not install gcc by default. So pop in the installation cd in your drive, open up a terminal, and type the following:

```
sudo apt-get install build-essential
```

That should give you a basic gcc install. You do not need an internet connection for that.

-J-

---

### Post by josif on 2006-01-21
[QUOTE=benguin]Hi,
Ubuntu does not install gcc by default. So pop in the installation cd in your drive, open up a terminal, and type the following:

```
sudo apt-get install build-essential
```

That should give you a basic gcc install. You do not need an internet connection for that.

-J-[/QUOTE]

Thank you benguin!

By the way can you provide me a list of apps embedded in the 'build-essential' package ?

Or if you can,
 would you please show me a list of all apps available in the cd, BUT not installed automatically?

---

### Post by SSTwinrova on 2006-01-22
[http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential) is a list of everything available in build-essential

For your second question, all I could think of would be opening up Synaptic and browsing through the packages (assuming the CD is your only repo in sources.list, only packages on the CD should be there)

---

### Post by josif on 2006-01-25
[QUOTE=SSTwinrova][http://packages.ubuntu.com/breezy/devel/build-essential](http://packages.ubuntu.com/breezy/devel/build-essential) is a list of everything available in build-essential

For your second question, all I could think of would be opening up Synaptic and browsing through the packages (assuming the CD is your only repo in sources.list, only packages on the CD should be there)[/QUOTE]

this problem is solved and gcc is working ok.

but when trying to compile some programs it gave me strange errors :
some basic libraries couldn't be found. so it complained about not finding glib-config, libpng, etc. 

I tried to learn something about this problems from the net and I realized that  
the problem can be because the *-dev versions of the libraries aren't found.
one solution was to edit the repositories in synaptic from "main restricted" to 
"main restricted universe multiverse", but in my ubuntu cd no universe or multiverse directories is found under dist directory.

I have to add that I don't have network connection on my pc.

where can I find a CD iso (or whatever) containing universe and multiverse directories? to conclude I wellcome every suggestion ...

thank you.

---

### Post by ivanceras on 2008-08-06
> **benguin said:**
> Hi,
Ubuntu does not install gcc by default. So pop in the installation cd in your drive, open up a terminal, and type the following:

```
sudo apt-get install build-essential
```

That should give you a basic gcc install. You do not need an internet connection for that.

-J-

I had my installation CD on the drive, tried the command, but throws "unable to find build-essential.."

:(

---

### Post by plastichero on 2008-08-06
> **ivanceras said:**
> I had my installation CD on the drive, tried the command, but throws "unable to find build-essential.."

:(

try this:
sudo aptitude install build-essential

---

### Post by plastichero on 2008-08-06
by the way, whats the difference between:
[COLOR="DarkOrange"]sudo apt-get install build-essential[/COLOR]
and
[COLOR="YellowGreen"]sudo aptitude install build-essential[/COLOR] ?

---

### Post by cszikszoy on 2008-08-06
> **plastichero said:**
> by the way, whats the difference between:
[COLOR=DarkOrange]sudo apt-get install build-essential[/COLOR]
and
[COLOR=YellowGreen]sudo aptitude install build-essential[/COLOR] ?

It used to be that aptitude would keep track of dependencies, making your life easier if you wanted to uninstall things, where apt-get would not.

For example, if you wanted to install program x, but program x depends on program y, both apt-get and aptitude would do the same thing.  Both of them would download program x, notice that it depends on program y, then download and install program y before installing program x.

Now, it used to be, that apt- get would not keep track of this.  For example, if you wanted to uninstall program x, you would naturally want to uninstall program y as well (that is, if nothing else depended on it).

If you used sudo apt-get remove x, it would only remove x, and not y.

Where sudo aptitude remove x would remove x and y.

HOWEVER, this is not the case any more.  apt-get can keep track of orphaned packages.  For example, if you were to type sudo apt-get remove x, and look at the output, it would show you that program x is being removed, but also warn you that program y is an orphan (no other programs depend on it).  So, if you type sudo apt-get autoremove, it will remove any orphaned packages.

Currently, I do not think there is any difference between aptitude and apt-get for installing / uninstalling.  Of course aptitude can do many, many other things that apt-get can't do.  Which is why they have other apt-... programs such as apt-source etc etc.

Any aptitude / apt-get experts want to clarify further if I missed anything?

---

### Post by acolyte12 on 2010-05-19
Hi, all.

I'm running 10.04 in Sun VirtualBox. The problem is that with a full install to the hard drive, I cannot access the ISO/CD in order to install GCC in the Terminal. I imagine there's a combination of boot device/storage settings that'll get this done, but I haven't discovered them yet.

Any suggestions? The only workaround I've discovered is booting 10.04 from the ISO without a full install of Ubuntu, but then I have to re-install GCC every time I boot (right?)

Thanks in advance.

---

### Post by acolyte12 on 2010-05-19
I think I discovered the answer to my own question. The following command lines in Terminal did the trick on 10.04:

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

Much to learn...

---

### Post by chenxinghao on 2012-01-09
I just installed Ubuntu using the Windows installer; I will need to access gcc as well. Are things said here (in this thread) also apply in my case (e.g., need to do the suggested steps to install the gcc package)?
 
Does the gcc package include the gdb (the C/C++ debugger)?
 
I am new to Ubuntu and am at the beginning on the learning curve. Advices are very much appreciated.

---

