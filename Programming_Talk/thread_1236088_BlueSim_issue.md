---
title: "BlueSim issue"
date: 2009-08-09
forum: Programming Talk
---

### Post by bubuzzz on 2009-08-09
Hi all, 

I am doing a research for my university and there is a small part about transferring data from pc to phone using bluetooth. Becoz my laptop doesn't have any bluetooth stuff, i have to use BlueSim  ([http://www.javabluetoothstack.com/bluesim.htm](http://www.javabluetoothstack.com/bluesim.htm)) to emulate the bluetooth stack. When i ran this app on window xp, it works find. However, when running with ubuntu 9.04, it ends with the error 
```

Failed to load Main-Class manifest attribute from
/home/bubuzzz/Softwares/BlueSim/BlueSimSample.jar
```

The command i use to run it is 
```

java -Dconfig.file=BlueSimServer.config -classpath ./BlueSim.jar;./BlueSimSample.jar test.TestServer

```

which i found in the .bat file. Can you give me any advice, please?

---

