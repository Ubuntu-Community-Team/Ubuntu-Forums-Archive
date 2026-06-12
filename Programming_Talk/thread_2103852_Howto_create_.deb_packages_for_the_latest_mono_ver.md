---
title: "Howto create .deb packages for the latest mono version ?"
date: 2013-01-11
forum: Programming Talk
---

### Post by WitchCraft on 2013-01-11
Question:

Mono 3.0 is out, but I found no ppa from where I could install it.

There is this one:
[https://launchpad.net/~directhex/+ppa-packages](https://launchpad.net/~directhex/+ppa-packages)

but it's mono 2.10.8.1-5.

I'm playing with ASP.NET MVC4, which is why I need the 3.0 release.

Now I can compile & install mono 3.0 myself. 
How I do it, I tutorialized here:
[http://ubuntuforums.org/showthread.php?t=1591370](http://ubuntuforums.org/showthread.php?t=1591370)

My problem now is, for every new ubuntu installation I have/want to make (server, laptop, desktop, renewed installation when HD breakes) I need to go through this lengthy procedure again.

So I want to compile it once, and then upload it to a PPA, so that I (and everybody else) don't need to install it from source again.

Now the question:
The entire build process needs configure run with options, post-configure makefile fixes, post-configure sourcecode fixes, etc.

Is there an easy way I can create .deb packages from the already compiled files ?

So that in the installation script, I only need to write several times:
```

cd package_directory_1/
make install
cd package_directory_2/
make install
cd package_directory_3/
make install

```

etc. 

?


[B]Edit:
Double posted due to timeout bug.
Please delete.[/B]

---

### Post by howefield on 2013-01-11
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2103730](http://ubuntuforums.org/showthread.php?t=2103730)

---

