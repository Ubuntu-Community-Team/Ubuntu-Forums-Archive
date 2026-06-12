---
title: "JDK directory, making API etc..."
date: 2006-09-15
forum: Programming Talk
---

### Post by mokmoki on 2006-09-15
i have just installed jdk 1.5 using apt-get

```
sudo apt-get install sun-java5-jdk sun-java5-plugin sun-java5-fonts
```

now, i want to make an API of the classes using javadoc... I seem to have heard it in my class that you can use javadoc to create an API, just cant remember how...

and another question, where does the jdk files go after installation? what directory?

any form of help is much appreciated, thanks!

---

### Post by hod139 on 2006-09-16
> **mokmoki said:**
> i have just installed jdk 1.5 using apt-get

```
sudo apt-get install sun-java5-jdk sun-java5-plugin sun-java5-fonts
``` 

This isn't quite enough.  You still need to do
```

sudo update-java-alternatives -s java-1.5.0-sun
```to tell ubuntu you want to make Sun's java the default.

> 
now, i want to make an API of the classes using javadoc... I seem to have heard it in my class that you can use javadoc to create an API, just cant remember how...

This doesn't make sense to me.  Javadoc is used to make documentation, not design an application programming interface (unless your API means something else)

> 
and another question, where does the jdk files go after installation? what directory?

after running the update-java-alternatives commmand you shouldn't need to know this, but anyways it is:
```
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/
```

---

