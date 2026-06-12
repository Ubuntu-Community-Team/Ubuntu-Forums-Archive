---
title: "Tip:  Read compressed documentation files in /usr/share/doc using the zless command"
date: 2006-10-25
forum: Outdated Tutorials &amp; Tips
---

### Post by srf21c on 2006-10-25
You may have found yourself cursing the fact that many documentation files in /usr/share/doc are compressed, and thus somewhat tedious to read since you have to unzip them first.

Never fear, there is a much more elegant way to go about it...zless to the rescue!  Simply type zless and then the name of the gnuzipped file  *.gz like so:

```
bash$ zless README.gz
```

This will probably seem obvious to experienced users, but hopefully n00bs will find this tip helpful.

[Click here for more info about the zless command and Debian package documentation]("http://newbiedoc.sourceforge.net/tutorials/help-system.en/whats-installed-deb-help-sys.html")

---

