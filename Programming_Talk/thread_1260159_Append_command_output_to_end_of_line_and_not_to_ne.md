---
title: "Append command output to end of line and not to newline"
date: 2009-09-07
forum: Programming Talk
---

### Post by Gen2ly on 2009-09-07
I can think of a couple ways to do this but neither would be real elegant.  I got two commands and I'd like their output to go onto one line.  This is probably real easy but I've never seen it before so I'd appreciate the help.  The lines I got are:

```
xset -q | grep -o "Standby: [0-9]*[0-9] " | sed -e "s/Standby: //" > /tmp/dpmsvalues
xset -q | grep -o "Off: [0-9]*[0-9]" | sed -e "s/Off: //" >> /tmp/dmpsvalues
```

Obviously though, this is going to write the output to two separate lines.  Is there a way to do this without having to edit the output file?

---

### Post by Arndt on 2009-09-07
> **Gen2ly said:**
> I can think of a couple ways to do this but neither would be real elegant.  I got two commands and I'd like their output to go onto one line.  This is probably real easy but I've never seen it before so I'd appreciate the help.  The lines I got are:

```
xset -q | grep -o "Standby: [0-9]*[0-9] " | sed -e "s/Standby: //" > /tmp/dpmsvalues
xset -q | grep -o "Off: [0-9]*[0-9]" | sed -e "s/Off: //" >> /tmp/dmpsvalues
```

Obviously though, this is going to write the output to two separate lines.  Is there a way to do this without having to edit the output file?

You can use some ideas from here: [http://linux.dsplabs.com.au/rmnl-remove-new-line-characters-tr-awk-perl-sed-c-cpp-bash-python-xargs-ghc-ghci-haskell-sam-ssam-p65/](http://linux.dsplabs.com.au/rmnl-remove-new-line-characters-tr-awk-perl-sed-c-cpp-bash-python-xargs-ghc-ghci-haskell-sam-ssam-p65/)

---

### Post by Gen2ly on 2009-09-07
Ha, just what I needed.  'echo -n', will do the trick.  Thanks Arndt.

---

