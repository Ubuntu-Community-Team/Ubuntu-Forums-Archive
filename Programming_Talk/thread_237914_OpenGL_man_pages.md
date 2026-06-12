---
title: "OpenGL man pages?"
date: 2006-08-16
forum: Programming Talk
---

### Post by Roque on 2006-08-16
Hi guys,

Sorry for the dumb question: how can I install the OpenGL man pages? They are not present in Breezy and I don't know in which package they belong. 

I'd appreciate any help.

---

### Post by biocrasher on 2006-08-17
If I'm not mistaken ,they do not exist in either breezy or daper. Last time I've seen them in a package was in hoary in xlibmesa-gl-dev. 
So you probably have to add them manually.

---

### Post by Roque on 2006-08-17
Thanks for the help. You are right: unfortunately they are only available in Hoary. I've downloaded them from the sgi site:

[ftp://ftp.sgi.com/sgi/opengl/doc/](ftp://ftp.sgi.com/sgi/opengl/doc/)

but I have no idea in which folder the pages must be installed. The README doesn't say much about this. Could someone give me a hint? Thanks.

---

### Post by biocrasher on 2006-08-17
The path should be /usr/X11R6/man/man3

Last time I needed them (was on breezy a few months ago), I downloaded the hoary package from [here]("http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xlibmesa-gl-dev_6.8.2-10.2_i386.deb").
If you do this you can then run :
~$dpkg --extract xlibmesa-gl-dev_6.8.2-10.2_i386.deb ./xlibmesa-gl-dev
and you'll get a dir named xlibmesa-gl-dev with the filesystem structure showing you were to place the files.(though if you do this, remember not to copy the whole dir on the root directory, cause you'll ovewrite the headers, too).

---

### Post by Roque on 2006-08-17
Many thanks! 

I followed your instructions and got everything installed correctly. What confused me most was the fact that those man pages from sgi had an extension (.3gl) that I didn't see before, and didn't follow the usual man naming convention. I couldn't call the respective page even when I placed them in my MANPATH. The Hoary ones are OK though.
Thanks again.

---

### Post by lahiker on 2006-08-28
> **Roque said:**
> Thanks for the help. You are right: unfortunately they are only available in Hoary. I've downloaded them from the sgi site:

[ftp://ftp.sgi.com/sgi/opengl/doc/](ftp://ftp.sgi.com/sgi/opengl/doc/)

but I have no idea in which folder the pages must be installed. The README doesn't say much about this. Could someone give me a hint? Thanks.

----------

After I downloaded the file "mangl.tar.Z" from the above ftp site, 
and untarred it, I looked at the subdir "release/xc/doc/man/GL/gl".
(Note: Untarring also creates a subdir called "release/xc/doc/man/GL/gl_ftn"
but these man pages are for FORTRAN which I am not using. So I ignored
ot!)

Anyway, I noticed there was an "Imakefile" in "release/xc/doc/man/GL/gl"

So I did 

# xmkmf

foloowed by 

# make install

as root. This installed the man pages in the right place
(/usr/X11R6/man/man3) and everything worked !

Hope this helps.

---

### Post by Roque on 2006-08-29
Thanks for your help: I'll investigate that command.

---

