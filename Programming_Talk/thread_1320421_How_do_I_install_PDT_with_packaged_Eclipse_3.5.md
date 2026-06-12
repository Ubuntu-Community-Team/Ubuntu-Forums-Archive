---
title: "How do I install PDT with packaged Eclipse 3.5?"
date: 2009-11-09
forum: Programming Talk
---

### Post by tawmas on 2009-11-09
Hello all,

I'm trying to install the PDT (PHP Development Tools) plugin over the packaged Eclipse 3.5 available in the official repositories. I followed the instructions at [http://wiki.eclipse.org/PDT/Installation](http://wiki.eclipse.org/PDT/Installation), but Eclipse is complaining about missing dependencies and the error message is obscure enough to leave me puzzled about what dependencies are missing.

I hope that someone who already went through that process can post a list of dependencies to install, or at least point me in the right direction. I searched for instructions on how to decipher the missing dependency error messages, but found nothing useful. Feel free to slap me in my face if I missed something obvious.

BTW, I don't need the full fledged eclipse, complete with its Java development dependencies, so I just installed the eclipse-platform package instead of the eclipse package.

Cheers,
Tommaso

---

### Post by izg on 2009-11-10
bump.

I need to install pdt, but likewise getting dependency issues.  I ran into a bug report, but haven't found solution.

---

### Post by SevenMachines on 2009-11-10
on eclipse eclipse 3.5.1+repack~1-0ubuntu3 (karmic).
eclipse dependencies can become a tangled web, but using the main eclipse software repositories shouldn't have unresolved dependencies and if you can get it there its always the best, first try.
From a new eclipse install from the main karmic repository,
* Add the main galileo repository site in 'Install new software' 
Galileo - [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/)
* php tools (PDT) is in programming tools and installs fine here

You might also then want to add the release update site
Galileo updates - [http://download.eclipse.org/eclipse/updates/3.5/](http://download.eclipse.org/eclipse/updates/3.5/)

If you need to update direct from the pdt site to a newer version it might then be worth a try after the above steps have been done

---

### Post by tawmas on 2009-11-10
Thank you, SevenMachines, this works fine for the eclipse-platform package as well!

---

### Post by RedgeOnline on 2009-11-24
> **SevenMachines said:**
> on eclipse eclipse 3.5.1+repack~1-0ubuntu3 (karmic).
eclipse dependencies can become a tangled web, but using the main eclipse software repositories shouldn't have unresolved dependencies and if you can get it there its always the best, first try.
From a new eclipse install from the main karmic repository,
* Add the main galileo repository site in 'Install new software' 
Galileo - [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/)
* php tools (PDT) is in programming tools and installs fine here

You might also then want to add the release update site
Galileo updates - [http://download.eclipse.org/eclipse/updates/3.5/](http://download.eclipse.org/eclipse/updates/3.5/)

If you need to update direct from the pdt site to a newer version it might then be worth a try after the above steps have been done

So why isn't this site included in Eclipse from the default Ubuntu package, I wonder?

---

### Post by SuilAmhain on 2010-02-04
Registered to say Thank you very much :)

---

### Post by lionstone on 2010-05-03
I had a stock install of eclipse on ubuntu lucid 10.04, and this was not working. The installation went with no errors but the PHP items did not appear in the menus, and the perspective wasn't available. Uninstalling and running eclipse as root, then reinstalling fixed the issue.

This is a really annoying bug. If I had known that you have to run eclipse as root to install plugins I would've saved 3 hours today...

---

