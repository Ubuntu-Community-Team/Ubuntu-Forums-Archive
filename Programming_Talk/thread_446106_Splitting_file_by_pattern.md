---
title: "Splitting file by pattern"
date: 2007-05-16
forum: Programming Talk
---

### Post by cwaldbieser on 2007-05-16
I have a lage text file that looks like 1 or more lines of data followed by an end marker like:
```

blah
blah blah
xyzzy
EXIT
dasfgagagh
sdfhgwerybgf
gnnfgndf
EXIT
hgsfghf
stjrhnnnbtrf
rtshjhrthrt
EXIT

```
Where "EXIT" would be the marker.  I want to split the file into separate files such that the file contains all the lines up to and including the marker.  So in my example, the first file would contain:
```

blah
blah blah
xyzzy
EXIT

```

The csplit command sounded almost what I was looking for, but it doesn't include the matched line.  I tried using the '+1' option, but I get an error: "csplit: `1': line number out of range on repetition ..." where ... is some number of repetitions.

Does anybody have any idea how to do this?  I know I could probably write a short python or shell script to do it, but I thought there ought to already be a command that does this.

---

### Post by cwaldbieser on 2007-05-16
It seems I didn't pay close enough attention to the man pages.  I tried something like:
```

$ csplit file '/^MARKER/' '+1' '{*}'

```

I should have tried:
```

$ csplit file '/^MARKER/+1' '{*}'

```

---

