---
title: "Ubuntu 12.04 &amp; Catalyst v13.12 Drivers Installation"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Jetstr3am on 2014-02-25
Hi, I'd appricaited any help on how to install these [drivers]("http://support.amd.com/en-us/download/desktop?os=Linux+x86"), it keeps failing on me, is there a problem or patch needed for the current kernel?, I could do with some steps.

It is a fresh install of 12.04 then i ran apt-get update && upgrade.

Thanks

---

### Post by Mark Phelps on 2014-02-25
We're not mind readers here -- you need to tell us WHAT is it doing, not just that it's failing.

Also, it could very well be that these drivers don't work with your AMD/ATI card  For us to find out, open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA", and post those results back here.

Also, what version of 12.04 is it?

---

