---
title: "How to get libaspell"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-14
I'm invoking "sudo apt-get libaspell" but getting the following response" 

"E: Invalid operation libaspell"

This is the first time I've seen that response from apt-get. Am I issuing the command wrongly? 

Is there another way to find and download libaspell?

I'm trying to install libaspell which is a support file for the writing program Scrivener. It doesn't come with the Debian download.

---

### Post by steeldriver on 2013-06-14
You're missing the 'install', it would be

```
sudo apt-get **install ***package*
```

However I think the runtime package is just called 'aspell' (it should bring in the appropriate runtime lib and local-dependent dictionary automatically) - if you need the development library that's libaspell-dev I think

---

### Post by jps2012 on 2013-06-14
Arrrrgh! 

Yes! Thank you, steeldriver! (Embarrassing.)

---

### Post by jps2012 on 2013-06-14
I discovered that libaspell was renamed, so now I'm dealing with a new problem--namely the question of what the revised name acutally IS, and _how to find it_ (that's the essence of my new question). I did, though, download an assoiated package: libaspell-dev

I'm not sure if that package contains the commands/functions that were invoked with the old libaspell. 

What I do know is that the various threads that say libaspell is required to run Scrivener don't indicate (accurately) where to find it (or its new incarnation). 

Here's a thread that explains the renaming: [http://debian.itags.org/q_debian_8702.html](http://debian.itags.org/q_debian_8702.html) ("debian/control: renamed libaspell15 to libaspell15c2 for the GCC 4.0"). 

But now libaspell15c2 can't be found by apt-get install. 

So, my apologies for the long-winded description, but in instances in which you need a package, and it keeps 'evolving' and is DANG tough to track down, is there some kind of repository that tracks the various versions of packages? Somewhere a user can go to find the history of the evolution of a package ... and maybe find the most current version? (Way noob question, I know.)

---

### Post by steeldriver on 2013-06-14
You can do something like

```
apt-cache search --names-only aspell
```

In general you shouldn't need to worry about things down at that level -  it is the package management system's job to keep track of  dependencies - if you want more specific help, please post the flavour and version of Ubuntu you are using, and how you are attempting to install 'Scrivener' (from source? from a ppa? from a .deb file?)

---

### Post by jps2012 on 2013-06-14
AWESOME. Thank you, steeldriver. I wish there was a repository where I could download your brain. It's terrifically useful. I ran the command and got a list that even tells me how to download librarians in Slovanian, which I am going to learn as soon as resolve all my Setswana-related questions in Ubuntu. 

When I dowloaded the correct version (again, thanks to you, steeldriver), I got the following message (followed by a long list of files): "The following packages were automatically installed and are no longer required:" 

The shell tells me: "Use 'apt-get autoremove' to remove them."

If I run the command, is that the ONLY text required, or do I follow that text with the name of each file (that was suggested for removal)?

---

### Post by steeldriver on 2013-06-14
Yes 'apt-get autoremove' should be all that's necessary (preceded with 'sudo' of course) - no need to list the packages (that's what the 'auto' is for)

```
sudo apt-get autoremove
```

---

### Post by jps2012 on 2013-06-14
Great. I am running it now. Thank you, steeldriver. You are incredibly helpful.

---

### Post by steeldriver on 2013-06-14
You're welcome

---

