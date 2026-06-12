---
title: "Perform an action on file changed"
date: 2010-08-18
forum: Programming Talk
---

### Post by hakermania on 2010-08-18
So, I have 2 files. The actual file and a copy of it...
I want when the actual file changes, then overwrite it with the copy of it instantly...
Is this possible to be done?

So...
```
#permform a check every 5 secs if the 2 files are similar...
while file1 != copyoffile1 do
cp copyoffile /directory/of/actual/file/
done
```?

---

### Post by diesch on 2010-08-18
Should be possible using *incron* (not installed by default)

---

### Post by MadCow108 on 2010-08-18
the keyword for this is inotify which monitors filesystems and can act on any changes.
there are a several tools which use this, like already mentioned incron or the command line tools of inotify-tools:
```

#wait on change of file or its attributes (includes a touch)
inotifywait -e modify -e attrib file
#do something

```

but for simple problems you could also just compare the file sizes and modification dates in a loop

---

### Post by hakermania on 2010-08-18
Thanks for your replies... ):P

---

