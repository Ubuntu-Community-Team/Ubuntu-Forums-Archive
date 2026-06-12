---
title: "Is Mono on Ubuntu out of date?"
date: 2011-02-21
forum: Programming Talk
---

### Post by vernondcole on 2011-02-21
I am a developer of cross-system software. I am working on a project to add IronPython on Mono capability to a product I support (adodbapi).

Part of this work involves helping with the release of IronPython 2.7.  I have been worried by the fact that the IronPython on my Ubuntu development environment is still a beta version -- which is a bad sign when the NEXT beta version is being released. From what I read in my recent exchange on the IronPython mailing list, the Mono version on Ubuntu is similarly old.

1) Is this information correct?

2) What, if anything, can I do about it?
--
Vernon Cole

v v v here is the exchange from IronPython v v v v My comments first v v v v v

Or we can find the bloke who is not keeping Ubuntu Mono and Iron Python releases up to date and kick his....
errr...  ummm....  (mumble)...
  It is pretty weird that the distro which always has the latest of  everything is the one with the old IPy/Mono, where the one which is  NEVER up to date (RHEL) has it.  I'll do some investigating.  I'm afraid  my experiences with SUSE and Red Hat are what drove me to Ubuntu. I do  almost all of my open source work on a laptop, and there is a limit to  what I dare ask it to do.  Two operating systems and six IDEs/languages  are pushing it a bit.  Running VM would be over the top.  Perhaps I can  set up another desktop when I get home.  
  Thanks for the advice.
Vernon

On Mon, Feb 21, 2011 at 2:48 PM, Steve Dower <s.j.dower@gmail.com> wrote:
[INDENT]Ubuntu doesn't have the latest version of Mono, which is required for
the .NET 4.0 equivalent compiler (dmcs). You would have to build Mono
from sources to get it. Alternatively, most other distributions seem
to use the latest version (in particular, OpenSUSE and RHEL are
actively supported by Mono). You can get a ready-made OpenSUSE VM from
the Mono site.

You may not even need to build IronPython using Mono. I'm using
msbuild binaries on OpenSUSE at the moment and haven't had any issues
(yet).

Also, buying a Mac for testing appears to be the only option, since
they don't allow the use of MacOS in VMs (legally, anyway). (I'm sure
that will be taken into consideration when setting up CI, right...?)

On Tue, Feb 22, 2011 at 08:41, Vernon Cole <[EMAIL="vernondcole@gmail.com"]vernondcole@gmail.com[/EMAIL]> wrote:
> I agree with all of  you.  I was trying to get something that works in the
> default case (no switches, IronPython on Windows).
> I am not really equipped to test the other options. I'ld like to, but I'm
> not going to run out and buy a Mac just to test on.  (If only I could.)
> If it only works in the default case, but not the edges, it's better than
> not working at all, IMHO.
>
> I'll spend more time working on it, then learn to make a patch file (last
> time I tried, Mark could not read it, and I ended up sending him the whole
> text) and re-submit.
>
> Will someone please volunteer to help me figure out why I can't build IPy on
> Ubuntu?  I'll pay the phone/connection charges.
> --
> Vernon
>
>


> _______________________________________________
> Users mailing list
> [EMAIL="Users@lists.ironpython.com"]Users@lists.ironpython.com[/EMAIL]
> [http://lists.ironpython.com/listinfo.cgi/users-ironpython.com](http://lists.ironpython.com/listinfo.cgi/users-ironpython.com)
>
>


[/INDENT]

---

### Post by directhex on 2011-02-22
> **vernondcole said:**
> 1) Is this information correct?

Yes.

> 2) What, if anything, can I do about it?

[http://www.amazon.de/gp/registry/registry.html?ie=UTF8&type=wishlist&id=2NG3JCK7VAAM7](http://www.amazon.de/gp/registry/registry.html?ie=UTF8&type=wishlist&id=2NG3JCK7VAAM7)

---

### Post by MadCow108 on 2011-02-22
maverick and natty ship 2.6.7
for lucid there is badgerports:
[http://badgerports.org/](http://badgerports.org/)

---

