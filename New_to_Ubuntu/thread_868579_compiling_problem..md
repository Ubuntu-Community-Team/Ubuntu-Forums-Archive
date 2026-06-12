---
title: "compiling problem."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by msmr on 2008-07-24
I recently (after being unable to somehow find a way to add the universe and multi verse repositories to my synaptic) decided to compile bitchx.

Unfortunately, i ran into this problem.

configure: WARNING: cannot find setupterm - trying tgetent
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
configure: error: cannot find setupterm or tgetent


^^^ i install ubuntu maybe 3-4 hours ago and was just going around messing about trying to get linux how I wanted it.

I honestly have no idea wtf I did wrong or what I did, this is my first time really trying to do anything on linux of this sort and am stumped.

---

### Post by iaculallad on 2008-07-24
> **msmr said:**
> I recently (after being unable to somehow find a way to add the universe and multi verse repositories to my synaptic) decided to compile bitchx.

Unfortunately, i ran into this problem.

configure: WARNING: cannot find setupterm - trying tgetent
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
configure: error: cannot find setupterm or tgetent


^^^ i install ubuntu maybe 3-4 hours ago and was just going around messing about trying to get linux how I wanted it.

I honestly have no idea wtf I did wrong or what I did, this is my first time really trying to do anything on linux of this sort and am stumped.

What about doing it the easy way as bitchx is available in the repository:

```
sudo apt-get install bitchx
```

---

### Post by RomeReactor on 2008-07-24
Hi. Did you install **build-essential**? If you haven't, look for it in Synaptic (System->Administration->Synaptic). You need at least the GCC compiler, which build-essential provides, along with other useful tools; or, to install it from the terminal:
```
sudo aptitude install build-essential
```

Have you tried Pidgin?

---

### Post by ApOgEEs on 2008-07-24
To add Universe and Multiverse repositories, Click on **System > Administration > Software Sources**.
On the **Ubuntu Software** Tab, Check on the checkbox with lines ended with (universe) and (multiverse). Then close.

---

### Post by msmr on 2008-07-24
Eh, as much as I'd like to do this, whenever I did the apt-get install bitchx it didn't come up.
And honestly, compiling the software so far is more fun than I thought it'd be. 

I'd rather like to feel more accomplished with myself and actual compile something. 

I hope you understand my feeling on it.

also I have checked and I do have both the multiverse and the universe boxes checked.

It still only comes put with Pork as the only option that I come up with.

so if I want to get the program I want, I have to go and compile it. 

and yes I do have build-essentials.

---

### Post by SNuxoll on 2008-07-24
I'd like to remind you that development of bitchx has haulted and there are still numerous security vulnerabilities in it.  I would recommend switching to irssi.

---

### Post by iaculallad on 2008-07-24
> **msmr said:**
> Eh, as much as I'd like to do this, whenever I did the apt-get install bitchx it didn't come up.
And honestly, compiling the software so far is more fun than I thought it'd be. 

I'd rather like to feel more accomplished with myself and actual compile something. 

I hope you understand my feeling on it.

also I have checked and I do have both the multiverse and the universe boxes checked.

It still only comes put with Pork as the only option that I come up with.

so if I want to get the program I want, I have to go and compile it. 

and yes I do have build-essentials.

Yap, that's what they call the user's preference. Either you install applications by manually compiling the source or install it from the repo. I too prefer compiling from source as you have the flexibility over its source if you want to tweak it or merely just out of curiosity on how does a tarball become an application when compiled.
Anyway, that's just a suggestion. Happy compiling...

---

### Post by ibutho on 2008-07-24
> **msmr said:**
> I recently (after being unable to somehow find a way to add the universe and multi verse repositories to my synaptic) decided to compile bitchx.

Unfortunately, i ran into this problem.

configure: WARNING: cannot find setupterm - trying tgetent
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
configure: error: cannot find setupterm or tgetent


^^^ i install ubuntu maybe 3-4 hours ago and was just going around messing about trying to get linux how I wanted it.

I honestly have no idea wtf I did wrong or what I did, this is my first time really trying to do anything on linux of this sort and am stumped.
Install a package called ncurses-dev to resolve that problem.

---

### Post by msmr on 2008-07-24
yes, I have installed irssi, it's just..ehh...want to try bitchx. oh well.

---

### Post by ApOgEEs on 2008-07-24
If you're interested in adding Repo from command line, check this out [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by RomeReactor on 2008-07-24
> **msmr said:**
> Eh, as much as I'd like to do this, whenever I did the apt-get install bitchx it didn't come up.
And honestly, compiling the software so far is more fun than I thought it'd be. 

I'd rather like to feel more accomplished with myself and actual compile something.

I hope you understand my feeling on it.
Nothing wrong with compiling; it can be a lot of fun, as long as you know what you're doing.

> so if I want to get the program I want, I have to go and compile it.
Only if you can't find a precompiled version. You can search on [GetDeb]("http://www.getdeb.net/") for programs that are usually not available in Ubuntu's repositories.

I agree with Snuxoll's comment regarding BitchX; better try another client. If you still want to install it, try ibutho's suggestion.

---

### Post by SNuxoll on 2008-07-24
irssi is pretty bleh until you install a decent theme and some scripts, check out irssi.org for a list.

---

### Post by ApOgEEs on 2008-07-24
> **msmr said:**
> 
configure: WARNING: cannot find setupterm - trying tgetent
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
configure: error: cannot find setupterm or tgetent


if you still wanna compile this and you have **build-essential** installed, you should verify that you have **ncurses-term** to avoid such error.

Install ncurses-term
[HTML]sudo apt-get install ncurses-term[/HTML]

you may also wanna check that you have **libterm-query-perl** and **libncurses5-dev**

---

