---
title: "[SOLVED] Perl + Glade = How?"
date: 2008-04-20
forum: Programming Talk
---

### Post by Cerberus108 on 2008-04-20
Hello guys, would you help me, please?

In the last days I was trying to make an interface to an encrypter I wrote in Pascal, and since I realized that no gtk or glade headers existed for that language, I started a port in Perl, which seems to be supported by libglade, as stated in the homepage of the Glade site. 
But, I'm still to n00b for this... :oops: So, after trying all the ways I found on the web for creating perl interfaces with glade, (included glade2perl-2, which returns me some errors...) I gave up with doing it by myself. 
Does someone knows how to create Perl interfaces with Glade-3 (or even Glade-2), and explain it here, please? (like[*** this***]("http://www.perlmonks.org/?node_id=104432"), sadly dated 2001)

Thanks, and sorry for my bad english, in advance!

---

### Post by bigearsbilly on 2008-04-29
try here: [GladeXML.pm]("http://search.cpan.org/~tsch/Gtk2-GladeXML-1.006/GladeXML.pm")
it's dead easy.

if you need more help let me know.

---

### Post by Cerberus108 on 2008-06-06
Thank you very much! 
I installed the .pm module, and now I'm exercising with this extension. Since I have a little confidence with the Python's glade extension, I just need some documentation on how to control widgets and theirs proprieties, like visibility, size, and controls too. Can someone help me about this, please? Thanks in advance! (and sorry for eventual bad English :))

---

### Post by samjh on 2008-06-06
There are quite a few tutorials online.  Try Google. :)

I have also attached an example here: [http://ubuntuforums.org/showpost.php?p=5123844&postcount=5](http://ubuntuforums.org/showpost.php?p=5123844&postcount=5)

---

### Post by Cerberus108 on 2008-06-15
Thank you, anyway I googled for each widget I needed info about, and I bumped in the official documentation, where I found help about widgets' syntax.

I'm attaching here the source of a program I wrote, in case someone is interested (it's a self-installing deb package, you will find the source in /usr/bin/perlcrypt and /etc/perlcrypt/perlcrypt).:)

---

