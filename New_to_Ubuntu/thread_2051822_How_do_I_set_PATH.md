---
title: "How do I set PATH?"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-09-02
Hi
TexLive via Synaptic doesn't have everything I need, so I've installed a native TexLive from the Tex Users Group. I need to set PATH, MANPATH & INFOPATH. If I can get one right, I can get them all right. I think I have to edit my .profile. I'm not sure whether to add:

```
PATH=/usr/local/texlive/2012/bin/x86_64-linux:$PATH; export PATH

```

or

```
PATH=/usr/local/texlive/2012/bin/x86_64-linux

```

Do either of these look right?

I know, I know---just test it! To cut a long story short (which I rarely ever do), I'd appreciate it if someone could look at this and say: The answer is ....
 
As always: eternally grateful. Any comments appreciated.
Thanks.

---

### Post by Lars Noodén on 2012-09-02
The first one is what you want.  The second one would make your regular programs unavailable.  

.profile will be run when you log in, .bashrc will be run any time you start a shell.

---

### Post by seeker.k3 on 2012-09-02
Thank you very much for your help.

---

