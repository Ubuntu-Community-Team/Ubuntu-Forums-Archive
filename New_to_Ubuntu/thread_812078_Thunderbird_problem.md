---
title: "Thunderbird problem"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by PinkFloydFan on 2008-05-29
I installed thunderbird the way described her:
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/](http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/)

Now when I open terminal and type

```
thunderbird
```

This error pops up:

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Any idea what that means and how to fix it?
Any help will be greatly appreciated!!

Shine On

---

### Post by shifty_powers on 2008-05-29
have you tried searching for libstdc++.so.5 in synaptic?

and why have you installed thunderbird in that way?

---

### Post by PinkFloydFan on 2008-05-29
> **shifty_powers said:**
> have you tried searching for libstdc++.so.5 in synaptic?

and why have you installed thunderbird in that way?

Well, I guess it's because I'm a Ubuntu newbie, not much experience, so I try to find answers on the web. And if I find a site that explains how to install it, I do it that way.

And what is synaptic? where do i find it?

---

### Post by shifty_powers on 2008-05-29
heh, well firstly, ubuntu has an add/remove entry in your applications menu, which should always be your first point of call ;)

there is a version of thunderbird in there as well.

Synaptic is the gui for apt, the management system for the repositories of packages/programs that ubuntu maintains.

just go system>preferences>synaptic.

but for thunderbird,, the easiest way is just add/remove under applications :D

---

### Post by sayakb on 2008-05-29
Open a terminal and type in:
```
sudo apt-get install thunderbird
```Should install TBird for you..

---

### Post by shifty_powers on 2008-05-29
heh, yes true, but think add/remove would be the best place for him to start.

oh and to check psychocats in both our sigs :D

---

### Post by sayakb on 2008-05-29
> **shifty_powers said:**
> heh, yes true, but think add/remove would be the best place for him to start.

oh and to check psychocats in both our sigs :D

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) :D 
Caution: Add remove is addictive :guitar:

---

### Post by PinkFloydFan on 2008-05-29
Oh wow, that helps a lot, that makes life a lot easier with add/Remove.

Now I completely removed Thunderbird, re installed through add/remove, but still the same problem.

And i did a search in synaptic for libstdc++.so.5 but no results.

---

### Post by jimv on 2008-05-29
I think the package that you need is libstdc++5 

To install that, just type this in a terminal:

```
sudo apt-get install libstdc++5 
```

If it says you already have it, then try these commands:

```
sudo ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
sudo ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1

```

---

### Post by PinkFloydFan on 2008-05-29
> **jimv said:**
> I think the package that you need is libstdc++5 

To install that, just type this in a terminal:

```
sudo apt-get install libstdc++5 
```

If it says you already have it, then try these commands:

```
sudo ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
sudo ln -s /usr/local/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1

```


Thank you very much, thats exactly what I needed to make it work!!!!

---

