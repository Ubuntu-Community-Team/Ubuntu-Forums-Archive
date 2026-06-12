---
title: "cannot get Eclipse running"
date: 2008-07-02
forum: Programming Talk
---

### Post by fmpfmpf on 2008-07-02
i am using ubuntu 7.10
i downloaded "Eclipse IDE for Java EE Developers" from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/)
version: Linux 32bit
After extracting, i double click the eclipse icon to run it.
After choosing the workspace and eclipse finishes the loading, i get this problem (see attachment)
it wont proceed.
what is wrong?
tq

---

### Post by tinny on 2008-07-02
> **fmpfmpf said:**
> i am using ubuntu 7.10
i downloaded "Eclipse IDE for Java EE Developers" from [http://www.eclipse.org/downloads/packages/](http://www.eclipse.org/downloads/packages/)
version: Linux 32bit
After extracting, i double click the eclipse icon to run it.
After choosing the workspace and eclipse finishes the loading, i get this problem (see attachment)
it wont proceed.
what is wrong?
tq

Hi

Whats the output of...

```

java -version

```

---

### Post by fmpfmpf on 2008-07-02
```
java -version
```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode)

---

### Post by tinny on 2008-07-02
Have you got compiz running?

Also can you post workspace/.metadata/.log if it exists?

---

### Post by fmpfmpf on 2008-07-02
> **tinny said:**
> Have you got compiz running?
what is compiz?

> **tinny said:**
> Also can you post workspace/.metadata/.log if it exists?
doesnt exist

---

### Post by tinny on 2008-07-02
> **fmpfmpf said:**
> what is compiz?


doesnt exist

[Compiz]("http://en.wikipedia.org/wiki/Compiz"), long story

That .log file will be a hidden file if it exists.

can you run eclipse from the bash (command line).

```

cd <path to eclipse>
./eclipse -consoleLog

```

This will print any errors to the console.

---

### Post by tinny on 2008-07-02
Also...

Sometimes the log is stored too, configuration/<timestamp>.log

Actually it would be better to run this from the command line.

```

./eclipse -debug

```

You will get alot more info

---

### Post by fmpfmpf on 2008-07-02
i downloaded eclipse again, but this time using synaptic
it works fine now
tq very much

---

### Post by tinny on 2008-07-02
> **fmpfmpf said:**
> i downloaded eclipse again, but this time using synaptic
it works fine now
tq very much

WOW, really interesting.

What version of Eclipse is it?

---

