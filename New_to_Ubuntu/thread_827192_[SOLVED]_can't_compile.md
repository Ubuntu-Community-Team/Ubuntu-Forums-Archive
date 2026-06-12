---
title: "[SOLVED] can't compile??"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-06-12
i downloaded some source code and when i ran the configure program in there, it did a bunch of stuff but ended with "configure: error: Library zlib is not available."

What package do i need for this?

---

### Post by avtolle on 2008-06-12
Did you install build-essential from the repositories? If not, install that, and it may well take care of the problem. Otherwise, if build-essential is installed, look in the repositories for zlib, and install it.

---

### Post by gr4nf on 2008-06-12
the package is zlib1g, i think:
```

sudo apt-get install zlib1g

```

---

### Post by the_doc on 2008-06-12
zlib1g I think.

---

### Post by Cypher on 2008-06-12
You need [zlib1g-dev]("http://packages.ubuntu.com/hardy/zlib1g-dev").
```

sudo apt-get install build-essentiall zlib1g-dev

```

---

### Post by decoherence on 2008-06-12
also keep in mind you often need to install the -dev packages from synaptic if you're going to compile against libraries.

in your case you'll probably want zlib1g and zlib1g-dev and maybe even zlib1g-dbg if you're heavy in to development.

---

### Post by ercferret18 on 2008-06-12
i thought i had all the zlib packages before i started this thread, but i found a few i didnt have and it worked. thx

---

