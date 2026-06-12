---
title: "create metapackage that depends on other repos"
date: 2011-06-11
forum: Packaging and Compiling Programs
---

### Post by 1proof on 2011-06-11
I want to create a metapackage that depends on packages from non standard repositories. I thought of adding

```

sudo add-apt-repository <ppa:user/ppa-name>
sudo apt-get update

```

to the preinst script.

But this runs after the dependencies are installed.

So what's the standard way of doing this?

---

