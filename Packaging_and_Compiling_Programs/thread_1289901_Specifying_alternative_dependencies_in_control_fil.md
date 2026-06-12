---
title: "Specifying alternative dependencies in control file"
date: 2009-10-12
forum: Packaging and Compiling Programs
---

### Post by duncan_bayne on 2009-10-12
Hi All,

I'm currently testing our [OBZVault](http://www.offbyzero.com/obzvault) encrypted text editor on the Karmic beta, and I've noticed there's no more Sun JRE 1.5 package.  Our existing control file specifies a dependency upon 1.5:

```
Depends: sun-java5-jre
```

Does anyone know a way of specifying alternative dependencies?  OBZVault runs happily on both 1.5 and 1.6; I'm imagining something like:

```
Depends: sun-java5-jre||sun-java6-jre
```

... but can't find anything in the documentation.

TIA for any help.  I'll be sure to update [this HOWTO](http://www.offbyzero.com/resources/java_deb_ubuntu) with the solution.

Yours,
Duncan Bayne

---

### Post by dinxter on 2009-10-13
almost, what your looking for is

Depends: sun-java5-jre | sun-java6-jre

i'll see if i can find some documentation

---

### Post by dinxter on 2009-10-13
its usually in there somewhere :)  see in particular section 4.1, but its all a useful read really
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by duncan_bayne on 2009-10-13
> **dinxter said:**
> its usually in there somewhere :)  see in particular section 4.1, but its all a useful read really
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
Thanks - missed that.  Will rebuild our software to be Karmic-compliant & update the HOWTO.

---

### Post by dinxter on 2009-10-13
specifically on java, you should try to add dependencies based on capability rather than sun java specifically. ie, with the virtual packages java-runtime, java2-runtime, java5-runtime, java6-runtime

so instead of 
Depends: sun-java5-jre | sun-java6-jre

you could add
Depends: sun-java5-jre | sun-java6-jre | java5-runtime | java6-runtime

or even just
Depends: java5-runtime | java6-runtime
(since the sun6 packages provide these virtual packages too)

This will allow you app to install with all compatible jre's instead of being vendor specific

---

### Post by dinxter on 2009-10-13
theres a little about java virtual packages here
[http://wiki.debian.org/Java#Developers-JavapackagingworkinDebian](http://wiki.debian.org/Java#Developers-JavapackagingworkinDebian)

---

### Post by duncan_bayne on 2009-10-13
> **dinxter said:**
> This will allow you app to install with all compatible jre's instead of being vendor specific

We considered this - but the thing is, we *are* vendor specific to a slight extent.

We've tested OBZVault on both the non-free Sun JRE and OpenJDK and found that the latter tends to dump a bunch of warnings to console when running our app.  Also (if memory serves) there were some layout issues too.  Everything *works*, it just lacks polish.

Perhaps, though, the utility of being able to run on any JVM outweighs the cost of quirkiness on some JVMs?

---

### Post by dinxter on 2009-10-14
To be honest, I often found debugging java programs on 2 different platforms using the same sun jre a pain, with layout problems, crashes in one and not in the other and so on. 
Obviously you have given it some thought to what jre's to depend on, its a difficult decision as to whether you go for a narrow well tested dependency or a wider set that might not work well with your app. 
I'd probably go for putting your preferred sun jre first and then other acceptable dependencies after, the 'install sun jre if i have none but leave my default jre if i've got that' approach, obviously that'll depend on how well your app works with things like the current openjdk though

---

