---
title: "Searching for apps from command line"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by francisquare on 2013-03-07
I am new in ubuntu and want to change from windows to linux, my question is

in command line, how search a app or locate that i want to install without using the ubuntu software center

thx

---

### Post by thermion on 2013-03-07
There are many ways of doing this.

```
apt-cache search *argument* 
```
You can also use aptitude
```
sudo apt-get install aptitude
aptitude

```

Another way is to simply type* sudo apt-get install* and use autocomplete (tab key) to "search" for software.

---

### Post by schragge on 2013-03-07
```

[apt-cache]("http://manpages.ubuntu.com/manpages/precise/en/man8/apt-cache.8.html") search [regex_pattern]("http://manpages.ubuntu.com/manpages/precise/en/man7/re_format.7.html")

```
or
```

sudo apt-get install apt-xapian-index debtags
sudo update-apt-xapian-index
[axi-cache]("http://manpages.ubuntu.com/manpages/precise/en/man1/axi-cache.1.html") search [search_terms](http://enricozini.org/2010/debian/axi-cache/)

```

---

### Post by Xgen on 2013-03-07
The terminal command line is fine, but synaptic is also a superior program to USC ('sudo apt-get install synaptic') with search functions.

---

### Post by francisquare on 2013-03-07
thank you guys

---

