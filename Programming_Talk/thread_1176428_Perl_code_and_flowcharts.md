---
title: "Perl code and flowcharts"
date: 2009-06-02
forum: Programming Talk
---

### Post by mrlizard123 on 2009-06-02
Anyone know of software that can generate flowcharts from source code? Something like [_visustin_]("http://www.aivosto.com/visustin.html") for windows but without the price tag :D and hopefully for ubuntu?

I have some reasonably lengthy code I've inherited and I'm hoping to get a diagrammatic representation of it without too much of the leg work if at all possible.

Thanks in advance for reading, very grateful for any suggestions!

---

### Post by unutbu on 2009-06-02
graphviz might do what you are looking for. Here are some examples, with code:
[http://www.graphviz.org/Gallery.php](http://www.graphviz.org/Gallery.php)
[http://martin.elwin.com/blog/2008/05/uml-use-case-diagrams-graphviz/](http://martin.elwin.com/blog/2008/05/uml-use-case-diagrams-graphviz/)

These are the relevant packages in the official repo:

graphviz - rich set of graph drawing tools
graphviz-doc - additional documentation for graphviz
libgv-perl - Perl bindings for graphviz

Here is the dot users guide:
[http://www.graphviz.org/Documentation/dotguide.pdf](http://www.graphviz.org/Documentation/dotguide.pdf)

---

### Post by mrlizard123 on 2009-06-02
Thanks, will check it out, had seen it but missed the perl bindings... should read and not just stare blankly at!

---

### Post by mrlizard123 on 2009-06-03
Trying to install graphviz and libgv-perl debs; graphviz installed fine but libgv-perl has an unsatisfiable dependency on perlapi-5.8.8

Any easy way round this? I think perl-base_5.8.8 satisfies this but I have a later version of perl-base installed.

---

### Post by unutbu on 2009-06-03
If you are using Jaunty, then libgv-perl (2.20.2-3ubuntu2) depends on perlapi-5.10.0, rather than perlapi-5.8.8 (See [http://packages.ubuntu.com/jaunty/libgv-perl](http://packages.ubuntu.com/jaunty/libgv-perl)).
And indeed, like you say, the perlapi package should be provided by perl-base.

Perhaps your /etc/apt/sources.list is pointing to non-Jaunty repositories?
If you are unsure what to do, please post your /etc/apt/sources.list
and the output of 
```

sudo apt-get update
sudo apt-get install libgv-perl
```

---

### Post by mrlizard123 on 2009-06-03
Rather than drip feeding info I should have said this bit earlier... sorry!

The system that has Ubuntu on does not have access to the internet... so was trying to just install the deb files.

Also I should have specified what version of ubuntu it was running.

It's running Ibex 8.10.

Thanks for your responses so far!

---

### Post by unutbu on 2009-06-03
If you wish to download packages for an Ubuntu machine not connected to the internet, check out Keryx:

[http://keryxproject.org/](http://keryxproject.org/)
[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

It should help you grab all the needed dependencies.

---

### Post by mrlizard123 on 2009-06-03
Thanks again, I think I've got the right debs now. Really appreciate your help! :)

---

### Post by unutbu on 2009-06-03
No problem. Glad you got it sorted. :)

---

