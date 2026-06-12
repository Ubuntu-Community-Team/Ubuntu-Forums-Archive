---
title: "Need Help With Firefox Build"
date: 2009-07-01
forum: Packaging and Compiling Programs
---

### Post by gastly on 2009-07-01
Hi all :)
I was just learning how to compile firefox 3.5 from source and I did that too! 

The build completed without errors and it ran flawlessly. **But** the problem is that, the name appears as 'Shiretoko' everywhere, in the about box as well as the titlebar.

Is there any way to change that? I mean, I'd like it to have the name 'Mozilla Firefox' instead of 'Shiretoko' :P (who wouldn't :P )

Pleas help me out here :)

- gastly

---

### Post by wojox on 2009-07-01
Firefox 3.5 — code-named Shiretoko —

---

### Post by gastly on 2009-07-01
yes I know, but I meant is there any way to change that so it looks like an official build?
I know the Ubuntu repository folks compile it with the official name...

---

### Post by gastly on 2009-07-02
ok, I've found out the solution...
you just need to add:
```
ac_add_options --enable-official-branding
```

to your mozconfig file! :)

**EDIT:** But be careful, mozilla's distribution policy prohibits the distribution of mozilla's logo and it's brand name with custom builds of their product, so...you can't distribute your builds with that options enabled :)

But, now I have another question...

Which graphics toolkit is the best when it comes to font rendering?
I've tried alot but I can't get my firefox build to get fonts to render as smoothly as the ubuntu repository build...

So, can anyone tell me which toolkit to use and which option to choose, from xft and freetype2? :)

---

### Post by lovinglinux on 2009-07-02
I have compiled Firefox too and have a few questions. Can I hijack your thread since your problem is solved?

First question:

I have created a tutorial on how to compile Firefox and want some opinions if it sucks or if it is ok. The tutorial is in the last section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Second question: 

Everything went fine with my compilation and Firefox is running with 30% performance improvement. What I don't know is how to install the compiled version on another machine.

When I did the make install, it installed Firefox on /usr/local/lib/firefox-3.5, but I don't know what should I copy to another machine. There are similar folders in ~/mozilla/dist/firefox/, which is owned by root, and ~/mozilla/dist/bin/

---

### Post by gastly on 2009-07-03
> **lovinglinux said:**
> I have compiled Firefox too and have a few questions. Can I hijack your thread since your problem is solved?

First question:

I have created a tutorial on how to compile Firefox and want some opinions if it sucks or if it is ok. The tutorial is in the last section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Second question: 

Everything went fine with my compilation and Firefox is running with 30% performance improvement. What I don't know is how to install the compiled version on another machine.

When I did the make install, it installed Firefox on /usr/local/lib/firefox-3.5, but I don't know what should I copy to another machine. There are similar folders in ~/mozilla/dist/firefox/, which is owned by root, and ~/mozilla/dist/bin/

Hi lovinglinux :)
Your tut is cool! Nice work :)

Now, if you want to install your firefox onto another machine, you will have to make a package out of it.
Do this:

First of all cd into the objdir (default is: **ff-opt**) and once in there run the command:
```
make package
```

The package will then be created in the ff-opt/dist/ directory.

Hope this helps, good luck :)

- gastly

---

### Post by utkjamie on 2009-07-03
> **gastly said:**
> ok, I've found out the solution...
you just need to add:
```
ac_add_options --enable-official-branding
```to your mozconfig file! :)


Where is the mozconfig file located under Ubuntu?

---

### Post by lovinglinux on 2009-07-03
> **gastly said:**
> Hi lovinglinux :)
Your tut is cool! Nice work :)

Thanks

> **gastly said:**
> 
Now, if you want to install your firefox onto another machine, you will have to make a package out of it.
Do this:

First of all cd into the objdir (default is: **ff-opt**) and once in there run the command:
```
make package
```

The package will then be created in the ff-opt/dist/ directory.

Hope this helps, good luck :)

- gastly

Thanks. I got some error, but then I started all over again and now is good.


> **utkjamie said:**
> Where is the mozconfig file located under Ubuntu?

You have to create that file and put it inside the mozilla source code folder.

---

### Post by gastly on 2009-07-03
> **utkjamie said:**
> Where is the mozconfig file located under Ubuntu?

This file holds the configuration for **compiling** firefox from source. So, it's only needed to tell the compiler how to compile firefox.

It can't change the options in a pre-built firefox (that you downloaded via synaptic or the mozilla website), I think you're trying to do that no? Correct me if I'm wrong :)

---

### Post by jts0803odon on 2009-07-03
> It can't change the options in a pre-built firefox (that you downloaded via synaptic or the mozilla website), I think you're trying to do that no? Correct me if I'm wrong 

I think that may be a nightly-tools option in about:config: if 

```
 nightly.idtitle default boolean true
```

is set, then:

```
 nightly.templates.title;${DefaultTitle} (Build ${AppBuildID})
```

Maybe set nightly.idtitle to false?

---

### Post by lovinglinux on 2009-07-03
> **gastly said:**
> Hi lovinglinux :)
Your tut is cool! Nice work :)

I have updated the tutorial to make it independent of version and also replaced ***sudo make install*** with ***make*** and ***sudo checkinstall*** commands, facilitate the package removal ;)

---

