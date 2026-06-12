---
title: "debian/changelog multiple distroseries"
date: 2009-04-09
forum: Packaging and Compiling Programs
---

### Post by .nedberg on 2009-04-09
I am trying to build a package for both Intrepid and Jaunty, in changelog I have 
```
package (version) jaunty intrepid; urgency=low
``` (with real packagename and version).

It is rejected from launchpad with the error:
```

Unable to find distroseries: jaunty intrepid

```

Do I have to build one package for each? The "[Debian Policy Manual]("http://www.debian.org/doc/debian-policy/ch-source.html")" 4.4 states that you can use multiple dostros like this... I have also seen some examples of this around.

Am I doing something wrong?

---

### Post by jpeddicord on 2009-04-09
I've had this problem as well. You can only specify one distro per changelog entry for Launchpad/soyuz to take it and build it; builds for other distributions can be made by changing the distro and reuploading with a different version (usually the trend is to add ~jaunty or ~hardy etc. to the end of the version string.)

---

### Post by .nedberg on 2009-04-09
> **jacobmp92 said:**
> I've had this problem as well. You can only specify one distro per changelog entry for Launchpad/soyuz to take it and build it; builds for other distributions can be made by changing the distro and reuploading with a different version (usually the trend is to add ~jaunty or ~hardy etc. to the end of the version string.)

OK, so it is not me then :)

Thanks!

---

