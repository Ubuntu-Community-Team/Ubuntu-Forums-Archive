---
title: "Grub boot options"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by gerben1 on 2008-06-27
Hi,

Does anybody know a site where the different boot options for Grub are explained. I was googling trying to find out what the standard option in my menu.lst would do, but can't find any clear information. Not even in de Grub manual ([http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html))...

I got started on this by just wanting to check out what the default option in my /boot/grub/menu.lst do,
there are only these options:
ro quiet splash 
(I did find 'quiet' in the manual but not 'ro' and 'splash')

It doesn't help that when googling Grub, Google finds very very many pages which are mostly just forum entries and blogs on how to solve some specific thing with Grub. 

I would like some overview of all the options and what they do. Does anybody know a good site that has something like that?

---

### Post by Duck2006 on 2008-06-27
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

[http://www.geocities.com/thestarman3/asm/mbr/GRUB.htm](http://www.geocities.com/thestarman3/asm/mbr/GRUB.htm)

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by kansasnoob on 2008-06-27
Another guide that may be of interest:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by gerben1 on 2008-06-27
Thank you. 

I understand that grub is quite a large project with all kinds of options, but isn't there a list of options somewhere online? For example if I want to know what the 'ro' option does, how could I find out? It doesn't seem I can find this out from the manual, at least I did not manage to find it.

---

### Post by Duck2006 on 2008-06-27
> **gerben1 said:**
> Thank you. 

I understand that grub is quite a large project with all kinds of options, but isn't there a list of options somewhere online? For example if I want to know what the 'ro' option does, how could I find out? It doesn't seem I can find this out from the manual, at least I did not manage to find it.

Look in the grub manual, it is all listed there.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by gerben1 on 2008-06-27
Well, perhaps you can give me some hints on how to search a document like that then.

I have been searching in there, but can't find a list of options.
Take the 'ro' option, since it is on the 'kernel' line in menu.lst I expected it to be under the chapter entry:
13.3.20 kernel (on: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html))
which links to:
[http://www.gnu.org/software/grub/manual/grub.html#kernel](http://www.gnu.org/software/grub/manual/grub.html#kernel)
unfortunately no mention of the 'ro' option there, 
so back to the main menu then and try some other chapter? 

I have read different parts from that manual. I know how Grub generally works and do not fancy reading the whole manual. I would just like to know what the options mean.

---

### Post by Duck2006 on 2008-06-27
It,s been a wile but i think it's 'ro' Read only.

---

