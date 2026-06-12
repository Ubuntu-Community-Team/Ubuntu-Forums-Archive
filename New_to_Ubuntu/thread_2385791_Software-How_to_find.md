---
title: "Software-How to find?"
date: 2018-02-25
forum: New to Ubuntu
---

### Post by xipho2 on 2018-02-25
Hello, 

There are at least 4ways to find and install software:
1. Via &#8222;Software&#8220;
2. Synaptic
3. Via terminal
4. PPA
A software,&#8222;Hardinfo&#8220;(System Profiler) is neither in &#8222;Software&#8220;available nor via terminal installable, but with Synaptic. 
I found that software solely because I watched a vid on installing software. How can I find software, generally? What places I have to search for that purpose? Or is there a central site where all available software is listed? What about the pros and cons considering different software sources and ways to install them? Are websites, docs or vids concerning mentioned topics available you would recommend?

Thanks in advance!

---

### Post by vasa1 on 2018-02-25
I ran```
apt list --all-versions | grep -i _H_ardinfo
```and got```
_h_ardinfo/xenial 0.5.1-1.4ubuntu1 amd64
```

See *man apt* for how to make the best use of that command. Note that the terminal is usually case-sensitive.

And, just like you, I install additional software only after coming to know of it from other users or blogs or tech sites or videos and then deciding whether I really need it :)

---

### Post by The Cog on 2018-02-25
```
apt search hardinfo
apt show hardinfo
sudo apt install hardinfo
```all show that hardinfo is in fact command-line installable. 
However, I do prefer to use synaptic. 

> Or is there a central site where all available software is listed?My first recourse would be synaptic. It will indeed list all available packages in the repositories. Unfortunately there are so many that it can be like looking for a needle in a haystack - a problem that the Software Centre tries to solve by only listing the more significant/popular applications. Both apt and synaptic can search through description text so it's a bit like using google, trying different words and phrases. Actually, using google might be a better bet because it is more flexible about what it considers to be a search match.

---

### Post by oldos2er on 2018-02-25
> **xipho2 said:**
> r is there a central site where all available software is listed? 

packages.ubuntu.com shows all software from the four default repositories (main, universe, restricted, multiverse). To search for PPAs I usually use google advanced, for example: foo software site:launchpad.net

---

### Post by xipho2 on 2018-03-03
vasa1: How do you know about the existence of "Hardinfo"? How do I know that code as an average newb?

---

### Post by xipho2 on 2018-03-03
My first recourse would be synaptic. It will indeed list all available packages in the repositories. Unfortunately there are so many that it can be like looking for a needle in a haystack - a problem that the Software Centre tries to solve by only listing the more significant/popular applications. Both apt and synaptic can search through description text so it's a bit like using google, trying different words and phrases. Actually, using google might be a better bet because it is more flexible about what it considers to be a search match.[/QUOTE]

Seems I will never find software, unless I know the name of the software? Considering software names are often enigmatic.... Why is software via "Software" available, while others not?

---

### Post by xipho2 on 2018-03-03
> **The Cog said:**
> ```
apt search hardinfo
apt show hardinfo
sudo apt install hardinfo
```all show that hardinfo is in fact command-line installable. 
However, I do prefer to use synaptic. 

My first recourse would be synaptic. It will indeed list all available packages in the repositories. Unfortunately there are so many that it can be like looking for a needle in a haystack - a problem that the Software Centre tries to solve by only listing the more significant/popular applications. Both apt and synaptic can search through description text so it's a bit like using google, trying different words and phrases. Actually, using google might be a better bet because it is more flexible about what it considers to be a search match.

[COLOR=#000000][INDENT]Seems I will never find software, unless I know the name of the software? Considering software names are often enigmatic.... Why is software via "Software" available, while other not?[/INDENT]


[/COLOR]

---

