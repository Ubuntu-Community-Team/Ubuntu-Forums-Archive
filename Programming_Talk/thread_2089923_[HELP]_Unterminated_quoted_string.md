---
title: "[HELP] Unterminated quoted string"
date: 2012-11-30
forum: Programming Talk
---

### Post by krzysiekkarolak1 on 2012-11-30
Hello,

When I try to run LiveSuit for Linux, I get an error message: Syntax error: Unterminated quoted string

Code:
```
#!/bin/bash
set  -e

if [ -L $0 ]; then
	AbsPath=`readlink $0`
else
	AbsPath=$0
fi

AppName=`basename $AbsPath | sed s,\.sh$,,`
AppDir=bin

BinDir=`dirname $AbsPath`
tmp="${BinDir#?}"

if [ "${BinDir%$tmp}" != "/" ]; then
	BinDir=$PWD/$BinDir
fi

BinDir=$BinDir/$AppDir

LD_LIBRARY_PATH=$BinDir
export LD_LIBRARY_PATH

os=`cat /etc/issue | head -n 1 | cut -d\  -f1`
echo "You are running on" $os

$BinDir/$AppName "$@" >/dev/null
```

Thanks.

---

### Post by Cheesehead on 2012-11-30
That script runs fine for me.

---

### Post by krzysiekkarolak1 on 2012-11-30
Do you run it on a 64 or 32-bit system?

---

### Post by Cheesehead on 2012-12-02
Why would that matter for a simple shell script?

Your original issue was an unterminated quote. It does not seems to be in the script you provided. So it's somewhere else. 32/64-bit does not seem relevant to that issue. If it is indeed relevant, please explain.

Or is there some other issue that is really the problem?
Or are you looking for troubleshooting ideas?

---

