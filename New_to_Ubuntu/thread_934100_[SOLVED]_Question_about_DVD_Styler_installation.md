---
title: "[SOLVED] Question about DVD Styler installation"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by sdim on 2008-09-30
Hi,everyone.
Just trying to install DVD Styler on Mint (Ubuntu Gutsy),but although I've downloaded the .deb package,when I click on it I get a message saying 
"_Error: Dependency is not satisfiable: libwxsug0_".
I searched Synaptic but no such package is to be found.
Any suggestions?
Thank you.

P.S. I googled it,but nothing.Instead,I got something about  "libwxsvg".

---

### Post by kpkeerthi on 2008-09-30
Where did you download the deb from?

Both the debs are available for download here: [http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html)

* Look under Debian and Ubuntu packages.

---

### Post by sdim on 2008-09-30
Installed the package "libwxsvg0",but still it doesn't work.

---

### Post by brommage on 2008-10-07
The version of libwxsvg in the Ubuntu repository is old.  DVDsyler relies upon >= 1.0b11

Add the following to your repositories in Synaptic:

```

deb http://dvdstyler.sourceforge.net/repository/ubuntu/ hardy testing

```

That should allow you to download the new version.  It installs like a charm after that.

BTW: I'm currently having problems making NTSC discs with the new version of DVD Styler (1.7.0).  When I set NTSC under Settings, it automatically changes itself back to PAL.  Anyone have a similar problem?

---

