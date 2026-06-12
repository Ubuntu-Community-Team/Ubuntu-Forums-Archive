---
title: "make and std::logic_error"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by itba on 2011-09-18
hi,
I run into the following error when using make. So, I compiled the same program at the commandline to check if there was a problem in my C++ code, but it works perfectly fine at the commandline. 
```

terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
make: *** [Cmain.exe] Aborted
make: *** Deleting file `Cmain.exe'

```a google search suggested:
```

$ mv .mysqlgui .mysqlgui~ 

```but when I try that, I get an error stating no such file or directory.

---

