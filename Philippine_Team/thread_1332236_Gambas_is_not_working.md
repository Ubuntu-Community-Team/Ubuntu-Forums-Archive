---
title: "Gambas is not working"
date: 2009-11-20
forum: Philippine Team
---

### Post by QuinceARJ on 2009-11-20
I was trying to upgrade my install Gambas into v2.18 then suddenly it stop working, tried already uninstall and reinstall the app but no luck, any same experience?

---

### Post by loell on 2009-11-20
is it the Gambas IDE or the Gambas Compiler?

what's the output from the terminal?

---

### Post by QuinceARJ on 2009-11-20
the compile via terminals says : ERROR: #2: Cannot load class 'Project': Unable to load class file

the IDE after clicking it , does nothing ...

---

### Post by loell on 2009-11-20
```
sudo chmod -R o+w /usr/share/gambas2/examples
```

from [http://www.linuxbasic.net/index.php?PHPSESSID=c0049c082d4f09b72f3e4e9a95f8cca2&topic=528.0]("http://www.linuxbasic.net/index.php?PHPSESSID=c0049c082d4f09b72f3e4e9a95f8cca2&topic=528.0")

---

