---
title: "[HOWTO] Convert your file to many file formats to share with other OSes"
date: 2009-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by LinuxGuy1234 on 2009-04-26
`recode' is a great utility on Ubuntu if you need to share a Ubuntu file with another OS (don't tell about dos2unix and back).

First install recode:
```
sudo apt-get install recode
```

`recode' needs to be used at the console.

Sample usages:
```
recode ..pc <file>
```
Convert the UNIX-style <file> to DOS/Windows format.
```
recode mac <file>
```
Convert the Machintosh-style file to UNIX (Linux, BSD etc.) format.

[SIZE="5"]**Simple tutorial on Usage**[/SIZE]
```
recode
```
The command.
```
<format>
```
The format. By default, convert <format>-style file to UNIX-style format. Use .. for the reserve.
```
<file>
```
The file to convert.

Enjoy!

---

