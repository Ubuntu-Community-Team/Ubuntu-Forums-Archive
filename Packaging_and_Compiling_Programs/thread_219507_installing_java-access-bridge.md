---
title: "installing java-access-bridge"
date: 2006-07-20
forum: Packaging and Compiling Programs
---

### Post by americux on 2006-07-20
Hi everybody,
When I try to make java-access-bridge-1.4.6, I get this error:

CLASSPATH=../../../../idlgen:../../../../impl:../../../../bridge:../../../../util javac AccessibleImpl.java
----------
1. ERROR in AccessibleImpl.java
 (at line 26)
        public class AccessibleImpl extends UnknownImpl implements AccessibleOperations {
                     ^^^^^^^^^^^^^^
The type AccessibleImpl must implement the inherited abstract method AccessibleOperations.getAttributes()
----------
2. ERROR in AccessibleImpl.java
 (at line 26)
        public class AccessibleImpl extends UnknownImpl implements AccessibleOperations {
                     ^^^^^^^^^^^^^^
The type AccessibleImpl must implement the inherited abstract method AccessibleOperations.unimplemented()
----------
3. ERROR in AccessibleImpl.java
 (at line 26)
        public class AccessibleImpl extends UnknownImpl implements AccessibleOperations {
                     ^^^^^^^^^^^^^^
The type AccessibleImpl must implement the inherited abstract method AccessibleOperations.getApplication()
----------
3 problems (3 errors)make[4]: *** [AccessibleImpl.class] Error 255

Any help?
Thanks a lot, a.

---

