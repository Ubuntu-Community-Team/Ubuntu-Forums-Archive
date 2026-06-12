---
title: "Best PHP Development Tool"
date: 2008-06-26
forum: Programming Talk
---

### Post by JoshHendo on 2008-06-26
Hi,

Basically, I am looking for the best PHP development tool for Ubuntu.

What I am looking for is a IDE that I can edit a script in, and then just run it. I am also looking for something that will allow me to use mySQL with PHP as well.

So basically, a IDE that integrates with a localhost for PHP development.

Thanks, Josh.

---

### Post by ibutho on 2008-06-26
I don't know of a "best", but you could try [Zend Studio]("http://www.zend.com/en/products/studio/"). I prefer HTML editors like Quanta, BlueFish and Aptana.

---

### Post by henchman on 2008-06-26
Some people would suggest using [Eclipse PDT]("http://www.eclipse.org/pdt/"), but personally i don't like eclipse :(

Personally I like using netbeans for c++ and now they released a  [php/javascript/css-plugin]("http://www.netbeans.org/features/web/ajax.html"), which is very good :)

Or just use gedit, there you lern php at it's best (: syntax highlighting, tabbing and stuff is included

You can also make your mind up for yourself by trying out these : [http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#PHP](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#PHP)

---

### Post by dgoosens on 2008-06-26
hi,

I am PHP developper and work in Ubuntu.
I personally love to work with Zend Studio as it is a tool that was especially designed for PHP. (Eclipse as well by the way but I have not tested their latest version).

Next to that, I believe you can try it for free during 30 days after registering on their website... so just give it a shot !

Be aware though there is a little issue after the installation and you might want to check out the following link:
[http://www.zend.com/forums/index.php?t=msg&goto=13573&S=3e0417c64806b5f759e3d79040f3f48d]("http://www.zend.com/forums/index.php?t=msg&goto=13573&S=3e0417c64806b5f759e3d79040f3f48d")

hope it helps,

---

### Post by henchman on 2008-06-26
zend seems to be really nice, but if you dont't need it professionaly, nearly 500 bucks is a bit much :(

---

### Post by JoshHendo on 2008-06-26
I have decided with just going with setting up a local server on my computer. I figured it would be the best, and most customizable way. What I wanted was to save the hassle of uploading it to a webserver and testing it.

Zend looks great, but as henchman said, 500 bucks is a bit too much, as I don't need it professionally (just a student).

- Josh

---

### Post by Mickeysofine1972 on 2008-06-26
Hi

I'm a professional PHP developer as my job and this is what I use.

I recommend gPHPEdit as the best editor I've used, (i've used eclipse and it didn't impress me), its just straightforward and has code complete as well as code debugger.

Also, install a LAMP server to help with running them and testing database driven things.

I have a windows xp virtual box machine running too to test with ie6 as I dont get good behaviour of ie4linux on my machine. to access my apache server on the same machine I set the hosts file in C:/windows/system32/drivers/etc/hosts to point to the IP of my ubuntu machine so that I can just type [http://webserver/](http://webserver/) and I get the same site via the local LAN.

And finally, install the firebug and web developer plugins for firefox and together they make a kick *** set of dev tools that will work really well.

Well thats what works for me, hope that helps.

Mike

---

