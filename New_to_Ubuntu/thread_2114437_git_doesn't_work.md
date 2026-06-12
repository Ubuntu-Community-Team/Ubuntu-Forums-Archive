---
title: "git doesn't work"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2013-02-10
Hi

I'm havin' trouble getting git to work.
I use it behind a proxy server that requires NTLM authentication, I use Cntlm ([http://cntlm.sourceforge.net/](http://cntlm.sourceforge.net/)).

I set up Cntlm using this guide ([http://www.leg.uct.ac.za/howtos/use-isa-proxies](http://www.leg.uct.ac.za/howtos/use-isa-proxies))

On trying to use git, I errors. e.g
Upon entering:
```
git clone http://git.gnome.org/gnome-shell-extensions
```I get > 
Cloning into 'gnome-shell-extensions'...
error: The requested URL returned error: 407 while accessing [http://git.gnome.org/gnome-shell-extensions/info/refs](http://git.gnome.org/gnome-shell-extensions/info/refs)
fatal: HTTP request failed
I also tried entering:
```
git clone git://git.gnome.org/gnome-shell-extensions
```and I got:
> 
Cloning into 'gnome-shell-extensions'...
fatal: unable to connect to git.gnome.org:
git.gnome.org[0: 209.132.180.173]: errno=Connection timed out
How does one fix this?

Regards

---

