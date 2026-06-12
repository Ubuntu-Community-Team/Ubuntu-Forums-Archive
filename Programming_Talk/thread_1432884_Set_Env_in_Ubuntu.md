---
title: "Set Env in Ubuntu"
date: 2010-03-18
forum: Programming Talk
---

### Post by huangyingw on 2010-03-18
Hello,
    I have updated my environment variable in /etc/profile, as bellow
```
CLASSPATH=/media/myproject/git/java/lucene/lucene-3.0.1/lucene-core-3.0.1.jar:/media/myproject/git/java/lucene/lucene-3.0.1/lucene-demos-3.0.1.jar
```
    So, I could see it through ```
echo $CLASSPATH
```.
    But, I could not see it through ```
env
```.
    This account for my following command failure:
    ```
java org.apache.lucene.demo.IndexFiles /media/myproject/git/java/lucene/lucene-3.0.1/docs/
```.
    For I got following exception:
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/lucene/demo/IndexFiles
```

    what is the difference between ```
env
``` and ```
echo $CLASSPATH
```?

---

### Post by roccivic on 2010-03-18
try [PHP]export CLASSPATH=/media/myproject/git/java/lucene/lucene-3.0.1/lucene-core-3.0.1.jar:/media/myproject/git/java/lucene/lucene-3.0.1/lucene-demos-3.0.1.jar[/PHP]

---

### Post by huangyingw on 2010-03-18
> **roccivic said:**
> try [PHP]export CLASSPATH=/media/myproject/git/java/lucene/lucene-3.0.1/lucene-core-3.0.1.jar:/media/myproject/git/java/lucene/lucene-3.0.1/lucene-demos-3.0.1.jar[/PHP]
Is this a once-for-all solution. I means, after rebooting, does this env still take effect?
However, I will try this after returning home.

---

### Post by roccivic on 2010-03-19
yeah should work all the time, if you put it into /etc/profile, bashrc or similar

---

### Post by huangyingw on 2010-03-19
> **roccivic said:**
> yeah should work all the time, if you put it into /etc/profile, bashrc or similar
No, please notice in my context, I have updated this in my /etc/profile, and I could see it through echo $CLASSPATH, but was not shown in env command output.
And the worst thing is that, the java could not found the classpath variable:(..

---

### Post by roccivic on 2010-03-19
You need to export the variable. Hopefully this will make it all clear:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] cat /etc/profile | tail -n 2
CLASSPATH1="foo"
export CLASSPATH2="bar"
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] env | grep -i class
CLASSPATH2=bar
```
This was (obviously) after restarting X.

Peace, Rouslan.

---

### Post by huangyingw on 2010-03-20
> **roccivic said:**
> You need to export the variable. Hopefully this will make it all clear:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] cat /etc/profile | tail -n 2
CLASSPATH1="foo"
export CLASSPATH2="bar"
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] env | grep -i class
CLASSPATH2=bar
```
This was (obviously) after restarting X.

Peace, Rouslan.
Great, thank for your patient, simple demo, and this indeed make it all clear.

---

