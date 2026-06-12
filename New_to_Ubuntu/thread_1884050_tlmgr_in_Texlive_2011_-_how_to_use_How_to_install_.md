---
title: "tlmgr in Texlive 2011 - how to use? How to install packages?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by wildwildebeest on 2011-11-20
Hi all,

I'm trying to install the TexLive 2011. I removed my old version wth Synaptic package manager and now I've installed the new one via the 'quick install' instructions on the Tex Live website. 

It seems to have worked fine except it's asking me to install packages which I can see are already present in:
/usr/local/texlive/2011/bin/x86_64-linux
Plus I'd like to add a few extras of my own!

I've edited the ~/.bashrc file, appending:
export PATH=/usr/local/texlive/2011/bin/x86_64-linux:$PATH

I assume that the easiest way to add packages is via 'tlmgr' - but this doesn't work! The terminal simply returns 'command not found'.


Any advice on what's going wrong? I'm struggling to find anything conclusive on the internet!


Many thanks!

---

