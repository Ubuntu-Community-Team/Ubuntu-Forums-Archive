---
title: "HOWTO: Acroread / CUPS printer problem"
date: 2007-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Copter on 2007-06-22
Hi!

This small howto solves some printing problems caused by applications like Acrobat Reader 7.0 and GtkLP while printing n-up sheets (several pages per sheet). In my case every application that used lpr printed empty sheets or sheets with rectangle scaled pages (like 5:1 or so).

It seems that one of the printing application wrote a config file and not deleted it after printing. The file has been used constantly while printing other things. After some search this command solved the problem
```

mv ~/.cups/lpoptions ~/.cups/lpoptions_old

```

Thats all. My system: Xubuntu 6.10, 2.6.17-11-generic, cups 1.2.4.

copter :]

---

