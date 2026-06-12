---
title: "installing pascal"
date: 2011-03-13
forum: Programming Talk
---

### Post by noxified on 2011-03-13
Hello.
I`m pretty new in ubuntu community,and pretty new ubuntu user,so i am a newbie.
I need help installing and using pascal(for school)
Of what i found on the internet,i could use lazarus,but i don`t want beacuse i`m not used to it.
So i`ll need pascal.(free pascal ,good too)
Anyone help me ,step by step,installing it?
i use ubuntu 10.10
Thanks in advance.

---

### Post by johnl on 2011-03-13
to install:
```

sudo apt-get install gpc

```

then to compile:
```

gpc yourfile.pas -o program_name

```

---

### Post by noxified on 2011-03-13
good.i installed it.(thanks)
But how can i start it?
I can`t find in applications.
I like terminal,but i want to run pascal,like normal.I mean not to use it in terminal.
What`s the command to run it?Or,where is he?

---

### Post by sanderj on 2011-03-13
> **noxified said:**
> Hello.

I need help installing and using pascal(for school)
Of what i found on the internet,i could use lazarus,but i don`t want beacuse i`m not used to it.


Have you tried Lazarus (install it via the Ubuntu Software Center)?
It is a TP / Delphi lookalike.

If you're not used to TP / Delphi, *what* are you used to then?

---

### Post by noxified on 2011-03-13
With this.
[http://gallery.harnata.com/albums/userpics/10001/turbo_pascal.png](http://gallery.harnata.com/albums/userpics/10001/turbo_pascal.png)

---

### Post by sanderj on 2011-03-13
> **noxified said:**
> With this.
[http://gallery.harnata.com/albums/userpics/10001/turbo_pascal.png](http://gallery.harnata.com/albums/userpics/10001/turbo_pascal.png)

Cool! That feels like 1987: programming in Turbo Pascal 1.0.

OK, here's the recipe, using [http://en.ubucentrum.net/2009/04/turbo-pascal-programming-in-ubuntu.html](http://en.ubucentrum.net/2009/04/turbo-pascal-programming-in-ubuntu.html)

So: start up synaptic package manager.
search for "free pascal", and then in the search results, find "fp-ide". Select that for installation. A few more packages will be add.
Select "Apply" and the installation will begin; it will take 30 seconds. Then quit Synaptic
After installing, on the prompt, just type 'fp', and you will get the Turbo Pascal 1.0 interface.

I just did that and wrote a three line program; see the included screendump.

---

### Post by noxified on 2011-03-14
That guy was right.
Here`s full of genious.Thanks man!

---

