---
title: "java  path .."
date: 2010-06-28
forum: Programming Talk
---

### Post by miko5054 on 2010-06-28
if im usenig win i can load this file easy by using this path

```
  Properties props = lp.getProperties("C:\\Hagay\\file.properties");
```

im in Ubuntu and trying this command
and receiving exception 
```
Properties props = lp.getProperties("home\\mikmik\\file.properties");
```

what is the correct why to do it ...

---

### Post by Javich on 2010-06-28
Hello miko,

The "usual" way of doing it is:
```

		Properties p = new Properties();
		p.load(new FileInputStream("/home/myusername/propertiesfile.props"));
```

cheers,

Javier

---

### Post by tbastian on 2010-06-28
I recall doing this a while back, but can't remember the exact syntax.

Since windows and linux use different folder separators, theres a function you can call to get the native separator. You can then insert that into your path.

A quick google search says that its:

```

System.getProperty("file.separator")

```

but I haven't tested that...

---

