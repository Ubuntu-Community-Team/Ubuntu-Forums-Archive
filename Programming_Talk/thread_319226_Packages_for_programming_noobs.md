---
title: "Packages for programming noobs"
date: 2006-12-15
forum: Programming Talk
---

### Post by amiga_os on 2006-12-15
OK... as a noob programmer, the biggest, most confusing and most irritating problem is dependencies.  It's just confusing and depressing for KDevelop/Anjuta to produce some sample code, only for it to fail to build and give you an obscure message which is unclear.  After Googling, it turns out you need to install a dev package that you didn't know/think about... and you can do the whole dependency hell thing over and over again.

I don't think I'm alone in saying that I've wasted a lot of time with this problem and it's very frustrating.

The solution, I think, is very simple.  As well as the standard build-essential package.  There should be a whole slew of meta-packages that form a little "build-essential" family.  These meta-packages can make the assumption that more really is more, and don't take anything for granted in what should be installed.

In an ideal world, Synaptic / apt-get / smart package manager, or whatever we're using in Feisty+2 would be intelligent enough to spot that if I have build-essential-gtk and then I install python, the package manager will automatically include the python gtk bindings... if I do it in the other order, then vica-versa.

Until that day, I recommend meta-packages that just have an "install everything and hope for the best philosophy"... those who aren't noob's don't need to install them.

Finally, documentation needs to be transparently accessible.  In my opinion, when I download Anjuta, it should bare minimum prompt me to install the documenation (edgy repos - I can't even find the Anjuta docs).

I suggest:
[LIST]
[*]build-essential (as-is)
[*]build-essential-ubuntu (dev's and bindings for C/C++ and python)
[*]build-essential-kubuntu (dev's and bindings for C/C++ and python)
[*]build-essential-ubuntu-extras (dev's and bindings for other languages)
[*]build-essential-kubuntu-extras (dev's and bindings for other languages)
[*]build-essential-docs-tutorials
[*]build-essential-docs-languages
[*]build-essential-docs-apis
[/LIST]

What do people think?  If you like the idea, and you are a more experienced programmer, then could you please recommend a list of packages for these to depend on?

---

### Post by po0f on 2006-12-15
amiga_os,

As a "programmer" (I use the term loosely ;)) and a geek who likes to build his software from source, I know what libraries I need to use with my programs and will automatically install the needed *-dev packages.  I agree that for a newbie, these packages would be worthwhile, but as you progress, you will become more confident in knowing what you need and will install just the needed packages to get your programs compiled.

---

### Post by pmasiar on 2006-12-15
and you always can ask, or even (gasp!) read the FAQs :-)

---

### Post by cocteau on 2006-12-15
Well, I can see the benefit in what you suggest but my own masochistic nature actually likes things failing once in a while. It reminds me what I need to read up on and learn about. 

I tried to strip the kernel of the SCSI drivers thinking I didn't need them and SCSI was a thing of the past anyway only to have every single USB thing fail after that. Moral of that story is that tweaking and experimenting is what enables us to grow familiar with our OS instead of horrible general default settings that work for everyone and ideally suits none. 

I am not a superuser and I probably never will be but I enjoy falling off the ramp every once in a while to pick myself up again and go 'OK, so I won't do that again...'

---

