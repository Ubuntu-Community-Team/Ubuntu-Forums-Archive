---
title: "quick rebuild of Lucid"
date: 2010-05-05
forum: Packaging and Compiling Programs
---

### Post by Netdes on 2010-05-05
Hi, I downloaded and rebuild Lucid using the ubuntu build process (... AUTOBUILD=1....).
It took 8 hours but work great. Then I tried to work on my problem by turn on some debug in the ../net/bluetooth/*.c files.  Without "  [FONT=&quot]fakeroot debian/rules clean[/FONT]" I just
run "AUTOBUILD ..." but look like none of the debian/build/build-generic/net/bluetooth/*.ko updated.  Is there a way just clean up the ../net/bluetooth/  only and let it recompile. Do I just delete the directory or there is a better way to it?

Thanks.

---

