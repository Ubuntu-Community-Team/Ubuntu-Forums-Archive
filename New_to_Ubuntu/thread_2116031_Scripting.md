---
title: "Scripting"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by theondr on 2013-02-14
Could somebody kind of walk me through the following? What areas would one study to get a handle on what the below requirements are?

This is for disk usage.

I have had one course in Linux/Unix. I have had C programming.
Is Bash ok to use?





Create a [COLOR=#ff950e]script[/COLOR] that sends an [COLOR=#ff950e][SIZE=3]email[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]message[/SIZE][/COLOR] to the [COLOR=#ff950e][SIZE=3]user[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]specified[/SIZE][/COLOR] on the command line if any of the filesystems are at more than 70% of capacity. The script should [COLOR=#ff950e][SIZE=3]not[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]process[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]special[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]filesystems[/SIZE][/COLOR] as /proc . It should only [COLOR=#ff950e][SIZE=3]process[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]filesystems[/SIZE][/COLOR] which are either [COLOR=#ff950e][SIZE=3]locally[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]mounted[/SIZE][/COLOR] or are [COLOR=#ff950e][SIZE=3]mounted[/SIZE][/COLOR] via [COLOR=#ff950e][SIZE=3]NFS.[/SIZE][/COLOR]
 An individual [COLOR=#ff950e][SIZE=3]email[/SIZE][/COLOR] should be [COLOR=#ff950e][SIZE=3]sent[/SIZE][/COLOR] for [COLOR=#ff950e][SIZE=3]each[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]filesystem[/SIZE][/COLOR] which is at the [COLOR=#ff950e][SIZE=3]warning[/SIZE][/COLOR] [COLOR=#ff950e][SIZE=3]level.[/SIZE][/COLOR] There should be a [COLOR=#ff950e][SIZE=3]subject[/SIZE][/COLOR] on the [COLOR=#ff950e][SIZE=3]email[/SIZE][/COLOR] with a [COLOR=#ff950e][SIZE=3]message[/SIZE][/COLOR] "Warning: Filesystem <put filesystem the>here is at <X>% of capacity" If the filesystem is at greater than 90% of capacity, the "Warning" should be changed to "Critical Warning".

---

### Post by |{urse on 2013-02-14
More than OK!

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) <--- lots of good stuff to start with here.

---

### Post by Frogs Hair on 2013-02-14
The following is informative also. ```
man bash
```

---

### Post by schragge on 2013-02-14
Besides bash, you probably should read up at least about [df(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/df.1.html"), [mount(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/mount.8.html"), and [mailx(1)]("http://manpages.ubuntu.com/manpages/precise/en/man1/bsd-mailx.1.html").

---

