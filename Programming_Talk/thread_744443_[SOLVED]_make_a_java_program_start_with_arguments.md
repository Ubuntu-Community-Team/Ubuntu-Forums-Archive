---
title: "[SOLVED] make a java program start with arguments?"
date: 2008-04-03
forum: Programming Talk
---

### Post by Griff on 2008-04-03
I'm working on writing a server/client program and I'd like to be able to set the ip address that the client needs to connect to by passing in as an argument.
For example:
```
RegisterClient 192.168.1.50
```
As opposed to hardcoding the address in the client and having to recompile.

Thanks,
Griff

---

### Post by smartbei on 2008-04-03
You may want to check this out: [http://java.sun.com/docs/books/tutorial/essential/environment/cmdLineArgs.html](http://java.sun.com/docs/books/tutorial/essential/environment/cmdLineArgs.html)

---

### Post by CptPicard on 2008-04-03
```

public static void main(String[] args) {
  String myArg = args[0];
}
```

---

### Post by Griff on 2008-04-03
Well I thought it would be a *little* more difficult than that.  I feel like I wasted your time! :)
Thanks!
-Griff

---

