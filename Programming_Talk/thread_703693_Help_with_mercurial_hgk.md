---
title: "Help with mercurial hgk"
date: 2008-02-21
forum: Programming Talk
---

### Post by hardskinone on 2008-02-21
Hi,
hgk is the mercurial extension to view repository history inside a GUI. hgk is distributed with hg package in Gutsy.
When I invoke the command inside a repo folder I get the following error:

```
$ hg view
extension 'hgext/gpg' overrides commands: sigs sigcheck sign
extension 'hgk' overrides commands: debug-cat-file debug-diff-tree  debug-rev-parse ^view debug-rev-list debug-merge-base
Error in startup script: tip                               18:afa352e3ebfe
extension 'hgext/gpg' overrides commands: sigs sigcheck sign
extension 'hgk' overrides commands: debug-cat-file debug-diff-tree debug-rev-parse ^view debug-rev-list debug-merge-base
    while executing
"exec $env(HG) tags"
    (procedure "readrefs" line 4)
    invoked from within
"readrefs"
    (file "/usr/share/mercurial/hgk" line 3682)
$ 
```

I use the hgk wiki page [0]. Mercurial users out there?

Thanks

[0] [http://ubuntuforums.org/newthread.php?do=postthread&f=39](http://ubuntuforums.org/newthread.php?do=postthread&f=39)

---

### Post by Ches Martin on 2008-04-01
> **hardskinone said:**
> 
When I invoke the command inside a repo folder I get the following error:

[snip]


Hi hardskinone,

I had an almost identical issue on Hardy. There's something wrong with your ~/.hgrc file most likely -- notice the "Error in startup script". Could also possibly be in /etc/mercurial/hgrc if any options have been set system-wide.

In my case I'd copied over my config file from another system where I had options specific to mercurial 1.0, though I'm using the 0.9.5 package on Hardy.

Once I commented out the offending option, the error went away and I could run hgk. The error reference (something about "tip" in your case) wasn't really helpful for me, but just trim down your hgrc to the bare minimum and see if it helps.

Cheers.

---

