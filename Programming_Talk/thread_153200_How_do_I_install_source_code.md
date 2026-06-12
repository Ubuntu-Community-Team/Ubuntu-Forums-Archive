---
title: "How do I install source code?"
date: 2006-03-31
forum: Programming Talk
---

### Post by jazzmuzik on 2006-03-31
I would like to install the xmms source package, make a simple change, recompile and reinstall the package. I'm somewhat familiar with the rpm system but I'm completely new to deb files. How do I do go about this?

---

### Post by xenmax on 2006-03-31
I could be wrong on this one, but i think installing from source and using .deb packages are different things. [I hope anybody more knowledgable will correct me if this is wrong].

This is what i know abt source installation: You get the source code, probably in a archive. You unpack it to a dir and follow the instructions in the README and INSTALL files. Usually it involves the following steps:
```
./configure
make
make install

```

---

### Post by hod139 on 2006-03-31
[quote=xenmax]Usually it involves the following steps:
```
./configure
make
make install

```[/quote] 
The above steps are what you will see in most readmes, but I suggest you do the following:
```
./configure
 make
 sudo checkinstall
 
``` and accept the default answers to most questions.

Checkinstall is an application you can install from the repos, and when run will create a .deb file for you which then gets installed. This allows for easy removal later.

---

### Post by jazzmuzik on 2006-03-31
Thanks for the compilation steps. I guess what I'm asking is how do I install the xmms source code from Synaptic? And then once the package is compiled, how do I create a .deb package?

---

### Post by hod139 on 2006-03-31
[quote=jazzmuzik] I guess what I'm asking is how do I install the xmms source code from Synaptic? [/quote]
```
apt-get source xmms
```
See [http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html) for more gory details about working with source packages.

> And then once the package is compiled, how do I create a .deb package?

Use checkinstall.  See my previous post.

---

### Post by jazzmuzik on 2006-03-31
Thanks, I'll look into that. 

"Use checkinstall. See my previous post."

Oops. I overlooked that suggestion. I guess I assumed checkinstall had nothing to do with .deb file. I'll study that as well. Thank you.

---

### Post by jazzmuzik on 2006-03-31
With your help I was able to end up with a .deb file using debuild. It looks correct on the inside, however I ended with one error that the process wasn't able to sign the file with pgp or gpg. I did install gpg but it must need something else, perhaps a key?. Is this more of a warning than an error? Should I fix it? How?

My second question, if the .deb file is okay, how do I install it from its current location which is in my home directory?

And I'm still stumped by checkinstall... but I'm making progress.

---

### Post by toojays on 2006-03-31
checkinstall is not necessary for the source you get with "apt-get source".

The warning about a missing gpg key is just a warning, it's more important if you are going to distribute your package to other people.

You can install your package using the dpkg command.

---

