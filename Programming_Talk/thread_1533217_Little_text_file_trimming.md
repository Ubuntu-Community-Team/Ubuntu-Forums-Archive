---
title: "Little text file trimming"
date: 2010-07-17
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-07-17
Hi, dear sir(s)!

How can I trim this piece of text with sed, head or whatever:
```
# [version=0]
songbird.version=1.9.0a
songbird.branch=trunk
songbird.build.number=1759
songbird.build.startRevision=19163
songbird.build.endRevision=19171
songbird.build.sourceRoot=http://publicsvn.songbirdnest.com/client/trunk
songbird.translate.sourceRoot=https://svn.songbirdnest.com/client/trunk
songbird.translate.moz.langpacks.location=https://svn.songbirdnest.com/vendor-binaries/trunk/noarch/mozlocalization
songbird.translate.moz.langpacks.rev=11764
songbird.translate.moz.langpackList.location=https://svn.songbirdnest.com/vendor/trunk/mozbrowser/locales/shipped-locales
songbird.translate.moz.langpackList.rev=11307
```
...to just show the number of the "*songbird.build.number=*" line:
```
1759
```
...and separately the version of the "*songbird.version=*" line:
```
1.9.0a
```
There's many ways of achieving this but I'd really appreciate, if someone posted a non-ugly solution.
Thanks! Have some of this popcorn for being so kind to answer: :popcorn:

---

### Post by ju2wheels on 2010-07-17
> **Intrepid Ibex said:**
> 
...to just show the number of the "*songbird.build.number=*" line:
```
1759
```


```

grep "songbird.build.number" /path/to/songbirdfile.conf | cut -d "=" -f2

```

> **Intrepid Ibex said:**
> 
...and separately the version of the "*songbird.version=*" line:
```
1.9.0a
```


```

grep "songbird.version" /path/to/songbirdfile.conf | cut -d "=" -f2

```

---

### Post by soltanis on 2010-07-17
```

awk -F "=" '/(version|number)/{print $2}' /path/to/file

```

More than one way to do it.

---

### Post by Intrepid Ibex on 2010-07-17
Thanks, hope the popcorn's good.

**E:**
> **soltanis said:**
> More than one way to do it.
That's why I was so cleaver:
> **Intrepid Ibex said:**
> There's many ways of achieving this but I'd really appreciate, if someone posted a non-ugly solution.

---

### Post by ghostdog74 on 2010-07-23
```

$ sed -r -n '/songbird/s/.*(version|build.number)=//p' file
1.9.0a
1759


```

---

