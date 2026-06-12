---
title: "[Java]File.isDirectory() equivalent inside jar"
date: 2008-10-22
forum: Programming Talk
---

### Post by hellblade on 2008-10-22
My file structure is:
```
myJar.jar
 |
 |-->aDirectory/
 |    |
 |    |-->aFile
 |
 |-->MyClass.class
```

and I want to do something like

```
File f = new File(getClass().getResource("aDirectory").toURI());
if(f.isDirectory())
  //do something
else
  //do something else
```

but when it runs inside a jar I get:
```
Exception in thread "main" java.lang.IllegalArgumentException: URI is not hierarchical 
```

------------------------------------------
**EDIT:** I found a solution and I give it bellow for anyone interested.

```

InputStream is = getClass().getClassLoader().getResourceAsStream("path/file");

if(is == null) {
  // file does not exist
}else if(is.getClass().getSimpleName().equals("ByteArrayInputStream")) {
  // isDirectory() equivalent
} else if(is.getClass().getSimpleName().equals("BufferedInputStream")) {
  // isFile() equivalent
}

```


------------------------------------------
**EDIT2:** Unfortunately that didn't work inside the jar since the stream returned in that case is always JarURLInputStream:(

So the question remains unanswered.

---

