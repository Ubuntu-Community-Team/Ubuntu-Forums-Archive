---
title: "gwt: how to compile server side classes?"
date: 2008-11-13
forum: Programming Talk
---

### Post by angustia on 2008-11-13
hi

i was trying gwt in ubuntu, i one thing i don't understand is the server side classes, how are they compiled.

i downloaded the gwt sdk from google, and went to samples/ directory. There is DynaTable project, that is one that have a service implementation class in it's bin directory. 

The example works OK if i launch it, and if i remove the bin/ directory, the example alerts of missing classes.

now, i try to compile the clases to recreate the bin directory this way:

```
javac -cp ~/Escritorio/gwt-linux-1.5.3/gwt-user.jar  -cp bin/ -d bin/ src/com/google/gwt/sample/dynatable/client/Person.java
```

but i got this error:

```
src/com/google/gwt/sample/dynatable/client/Person.java:18: package com.google.gwt.user.client.rpc does not exist
import com.google.gwt.user.client.rpc.IsSerializable;
                                     ^
src/com/google/gwt/sample/dynatable/client/Person.java:24: cannot find symbol
symbol: class IsSerializable
public abstract class Person implements IsSerializable {
                                        ^
2 errors
```

i don't understand why it can't locate the rpc package inside gwt-user.jar, if i open it it is there...

thanks for any help

excuse my english

---

