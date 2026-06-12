---
title: "help with expect"
date: 2011-11-11
forum: Programming Talk
---

### Post by Drenriza on 2011-11-11
Hi all.
I'am trying to create an expect script to temporarily change user to root with su (i cant use sudo)
and run a series of commands before terminating.

But i cannot get it to work properly.
Anyone who can help?

```
#!/bin/bash
echo "expect is inside bash"

/usr/bin/expect - << EndMark

spawn su
expect 'Password:'
send "xxx\r"
send "apt-get update\r"
expect "Building Dependency Tree... Done"
sleep 2
send "apt-get -s upgrade |sed '1d' |sed '1d' |head -1 |awk -F ',' '{print $1}' > package.output\r"
sleep 1
send "sed 's/packages upgraded/Packages can be upgraded/' package.output > package.output2\r"
sleep 1
send "rm package.output\r"
send "chown nice:nice package.output2\r"
EndMark

echo "more bash commands"
exit 0

```

Kind regards.

---

### Post by Drenriza on 2011-11-14
Is expect rarely used anymore? Since i find it hard to get help or find useful tutorials on the subject :p

No one who can help me?

---

