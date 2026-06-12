---
title: "Verify binary against source"
date: 2011-06-16
forum: Packaging and Compiling Programs
---

### Post by 1proof on 2011-06-16
If you have a .deb package and a source package (say tar.gz), then is there a way to verify that the binary package behaves exactly as it would if it had been built from that source?

I'm thinking, I can compile the source and then compare the 2 binaries. But if the initial binary was PGP signed by someone else, the 2 binaries can't be the same... So I'm not sure.

The main point is that I want to be able to tell people: Here is my binary package. If you don't trust that its not a malicious program, then look at the source and you verify that this source corresponds to that binary.

Thanks

---

### Post by sanderd17 on 2011-06-16
I don't think there is. People need to trust the one that build the package (or build it themselves).

I think this because e.g. the Fdroid community for Android (they provide an APT-way to get open source apps) does not get the packages from the software writers, but they inspect the code and build it themselves. So I guess they would have sought easier options if those existed.

---

### Post by tjoff on 2011-06-16
That is not possible in general. There does not exist a one-to-one relationship between source code and executable code.
Two different source codes can produce the same executable on the same system, and two identical source codes can produce very different binaries on different systems.
This is because information is thrown away and added in the compilation process, and how this happens depends on many things; the compiler, the compilation flags and the target system. 
If it was not like that, there would be nothing called platform dependence.

---

