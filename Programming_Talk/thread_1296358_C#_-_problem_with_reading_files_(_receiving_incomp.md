---
title: "C# - problem with reading files ( receiving incomplete data )."
date: 2009-10-20
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-20
```

FileInfo info = new FileInfo(dlgOpen.FileName);
long flen = info.Length;
long start = flen - 125;

StreamReader stream = new StreamReader(dlgOpen.FileName);
stream.BaseStream.Seek(start, SeekOrigin.Begin);
string data = stream.ReadToEnd();
``````
File size: 5397518 bytes
Seeking ..
Reading from: 5397393
Reading finished! Current position: 5397518
Data received: Ring My Bells

```The problem is that, data should be something like this ( dot = empty byte sequence ):
```
Ring My Bells .... Enrique Iglessias .... 
```Any ideas, why it returns incomplete data, tough it finished reading from starting point to EOF ?

---

