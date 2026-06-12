---
title: "NASM building code what doesn't correspond to source"
date: 2010-07-30
forum: Programming Talk
---

### Post by Carl Hamlin on 2010-07-30
This evening I had a very irritating development occur with a telnet application I'm writing in assembly language.

The program uses VT100 to clear screens, control the cursor, etc. This evening I added a system whereby to monitor socket activity, built the new code, and discovered the following:

I write:
```

db	01Bh, "[??", 03Bh, "??H"

```

It builds:
```

1C 5B 3F 3F 3C 3F 3F 48

```

Notice how '1Bh' and '3Bh' are getting turned into '1Ch' and '3Ch'?

As a troubleshooting step, I reverted back to the codebase without tonight's additions and rebuilt, thinking I had somehow screwed things up in a really weird way, but NASM persists in building '1Ch' when I write '1Bh'.

Thinking I may have munged NASM in some way, I moved the code to a second server and re-assembled it there, and got the same issue.

After that, I assembled a backup from last month on both machines, and got the same issue as well.

After *that*, I dumped nasm from both systems and reinstalled it, but to no avail. Same issue.

After *that*, I tried assembling a file consisting of *just* the screen clearing escape sequence definition, and got the same issue.

Anybody else have this problem or something like it? Anybody know what the %&$^&# is going on here?

---

### Post by Barrucadu on 2010-07-31
I've just tried assembling that line and can't reproduce the problem:

```
9:24:02 tmp/misc % echo 'db 01Bh, "[??", 03Bh, "??H"' > test.asm
9:24:04 tmp/misc % nasm test.asm
9:24:06 tmp/misc % hexdump -C test
00000000  1b 5b 3f 3f 3b 3f 3f 48                           |.[??;??H|
00000008
9:24:13 tmp/misc %
```

I'm using nasm version 2.08.01.

---

### Post by Carl Hamlin on 2010-07-31
> **Barrucadu said:**
> I've just tried assembling that line and can't reproduce the problem:

```
9:24:02 tmp/misc % echo 'db 01Bh, "[??", 03Bh, "??H"' > test.asm
9:24:04 tmp/misc % nasm test.asm
9:24:06 tmp/misc % hexdump -C test
00000000  1b 5b 3f 3f 3b 3f 3f 48                           |.[??;??H|
00000008
9:24:13 tmp/misc %
```

I'm using nasm version 2.08.01.

Thanks - that's the version I'm using as well. I worked around the problem by hand-building the escape sequences with a hex editor and reading them externally.

It's a hack, but it gets the job done. Still have no idea what's going on with this.

---

