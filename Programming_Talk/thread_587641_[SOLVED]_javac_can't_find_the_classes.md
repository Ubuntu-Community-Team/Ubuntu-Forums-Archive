---
title: "[SOLVED] javac can't find the classes"
date: 2007-10-22
forum: Programming Talk
---

### Post by Nergar on 2007-10-22
Im having a problem with javac, it isn't using . as the classpath when not supplying   one. why is that happening?

for example:

```
nergar@nergar-lap:class$ javac Catfish.java 
Catfish.java:14: cannot find symbol
symbol: class LivingBeing
public class Catfish extends LivingBeing {
                             ^
Catfish.java:206: cannot find symbol
symbol  : method getRand()
location: class Simulation
                row = simulation.getRand().nextInt(10);
                                ^
Catfish.java:208: cannot find symbol
symbol  : method getRand()
location: class Simulation
                column = simulation.getRand().nextInt(10);
                                   ^
3 errors
nergar@nergar-lap:class$ 

``` 

and 

```
nergar@nergar-lap:class$ javac -cp . Catfish.java 
nergar@nergar-lap:class$ 

```

Works fine

---

### Post by germania on 2007-10-22
'.' isn't in the classpath by default -- I can't remember a Sun JVM where it was by default... if you want it to, I think it honours the environment variable $CLASSPATH... you could add

```

export CLASSPATH=$CLASSPATH:.

```

to your ~/.bash_profile to do this.

---

### Post by Nergar on 2007-10-22
hmm, you are so right! y totally forgot! Thanx!!

---

