---
title: "PIDA install new version 0.3.1"
date: 2006-07-30
forum: Programming Talk
---

### Post by GStubbs43 on 2006-07-30
Hi all,
   I am trying to install pida, and since a really old version is in the repos, I am trying to install the pida_0.3.2-3_all.deb But when I try to, it says I need Python-central, which isn't even a package, but I looked around and saw that all it is, is

[LIST]
[*]python2.3 (>= 2.3.5-14)
[*]python-doc
[*]python-profiler
[*]python-tk
[/LIST]

And I have all of that, but when I open the Deb file it always says Error: Dependancy not satisfiable: python-centrel. I have also tried doing it manually through the terminal witk dpkg. But I can't get it. I have tried a lot of different mirrors as well. Anyone know how to install pida 0.3.1? :confused: THANKS!

---

### Post by GStubbs43 on 2006-07-30
Does anyone know how to install the latest version of PIDA?

---

### Post by GStubbs43 on 2006-07-30
Okay, I managed to install it from source and it runs fine, now do I need the folder that contained the install files, or will that mess it up if I delete it?

UPDATE: Yup... I can, and I did. Ciao. :rolleyes:

---

### Post by s0undt3ch on 2006-08-10
Great, care to share your experience?

I'd like to get latest pida running here too :)

---

### Post by s0undt3ch on 2006-08-12
For anyone who also want's to know.
Pida 0.3.1 is on the testing branch of debian. If you try to use the deb the testing provides you'll need to cover alot of dependencies.

[FONT="Verdana"][SIZE="4"][COLOR="Red"]Try this at your own risk!!!
Don't make me responsible for ANY damage caused to your system.[/COLOR][/SIZE][/FONT]

So, until it reaches (X/K/ED)ubuntu, here's a hackish way:
```
 [FONT="Courier New"]sudo apt-get install pida[/FONT]
 [FONT="Courier New"]sudo rm -rf /usr/lib/site-python/pida/[/FONT]
 [FONT="Courier New"]wget [http://download.berlios.de/pida/pida-0.3.1.tar.gz](http://download.berlios.de/pida/pida-0.3.1.tar.gz)[/FONT]
 [FONT="Courier New"]tar zxvf pida-0.3.1.tar.gz[/FONT]
 [FONT="Courier New"]cd pida-0.3.1[/FONT]
 [FONT="Courier New"]sudo apt-get python2.4-setuptools[/FONT]
 [FONT="Courier New"]sudo python setup.py install[/FONT]
```

And that's it!

P.S.: You'll probably want some other packages installed, you decide.

---

### Post by Note360 on 2006-08-12
You could just install from source. Like I did. Its not that hard. Go to their site download the source cd to the directory, then type.
```

sudo python ./setup.py install

```

and it installs

---

### Post by s0undt3ch on 2006-08-13
> **Note360 said:**
> You could just install from source. Like I did. Its not that hard. Go to their site download the source cd to the directory, then type.
```

sudo python ./setup.py install

```

and it installs

That's what I did above, but I installed Xubuntu's Pida first to be able to have a menu entry and icons with no fuss, then I overrrided the "heart" of pida.

---

### Post by aafshar on 2006-08-16
> 
That's what I did above, but I installed Xubuntu's Pida first to be able to have a menu entry and icons with no fuss, then I overrrided the "heart" of pida.


Hi,

Could you explain what you mean by this? Is there a problem with icons? and what is a menu entry? Are we talking about desktop manager stuff?

In general, I would not advise attempting to override pida 0.2.* with pida 0.3.* because the "heart" changed a fair bit. A clean install is the way to go, as there will not be any unexpected namespace clashing. Of course, if it works, great!

More good news is that pida 0.3.1 is in Edgy.

Thanks,

Ali (PIDA Author)

---

### Post by s0undt3ch on 2006-08-16
> **aafshar said:**
> Hi,

Could you explain what you mean by this? Is there a problem with icons? and what is a menu entry? Are we talking about desktop manager stuff?
There's no problem, and yes we're talking about the desktop manager. The thing is, if we do an install from source, we won't get menu entries nor icons for that matter for our desktop manager.

> **aafshar said:**
> 
In general, I would not advise attempting to override pida 0.2.* with pida 0.3.* because the "heart" changed a fair bit. A clean install is the way to go, as there will not be any unexpected namespace clashing. Of course, if it works, great!
Well, I did do 2 clean installs, one for 0.2 with an ububtu package, which gives me all desktop manager stuff, then I deleted the heart of that in python's site-packages dir, then I installed 0.3.1 from source, all this to keep desktop manager stuff and aviod a possible namespace clash.

> **aafshar said:**
> 
More good news is that pida 0.3.1 is in Edgy.
The bad news is that, it needs some dependencies not in Ubuntu yet :)

Oh, and by the way, great work, somethng I was looking for sometime because now I've gotten used to Vim, and want no other :)

---

