---
title: "[java] must class files be in a folder hierarchy corresponding to the package name?"
date: 2011-05-17
forum: Programming Talk
---

### Post by guest_user on 2011-05-17
because when I added a package line in, and tried executing the program, it gave me some error whereas when I removed the package line, everything works fine. My class files are not in a folder hierarchy corresponding to the package name.

---

### Post by PaulM1985 on 2011-05-17
Yes.  If you have a class with the declaration:
package myPackage;
Then your Java file for the class has to be in a folder called myPackage.

Paul

EDIT:
So if you have:
```

package some.package;
class AClass
{
}

```


AClass needs to be /SOME_LEADING_FOLDERS/some/package/AClass.java

---

