---
title: "Eclipse - Exception Occured executing command line"
date: 2005-12-01
forum: Programming Talk
---

### Post by ninocass on 2005-12-01
hi all

im getting this error at random times:

```

Exception Occured executing command line

```

when i exit out of eclipse and reload it the code compiles/executes with no problems, and maybe about 20 minutes later i get the Exception error

Thanks

Nino

---

### Post by lisje on 2005-12-02
is your eclipse running on native java??? (gjc)
because I had errors using eclipse when it was running on gjc .. when I changed it to my java from sun the problem was solved.

check your default java with:
```
sudo update-alternatives --config java
```

---

### Post by ninocass on 2005-12-02
i think im running on Sun downloaded Java:

```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

```

---

### Post by arpunk on 2005-12-02
You can also remove the *java-gcj-compat* package installed by default in ubuntu if you have the Sun downloaded java:
```
sudo apt-get remove java-gcj-compat
```
And:
```
sudo update-alternatives --config java
```
That worked for me, and even eclipse runs faster now, no errors until now.

---

### Post by ninocass on 2005-12-02
ill try that now, have a blackjack progam to write for university and the error was starting to get on me nerves


cheers

nino

---

### Post by ninocass on 2005-12-02
my config java thing looks like:
```

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/j2re1.5-sun/bin/java

```

Eclipse is now throwing the toys out of the pram and saying:

a suitable Java Virtual Machine for running eclipse could not be located

am i missing something?

Nino

---

### Post by arpunk on 2005-12-02
Check out if you have the correct locations in */etc/eclipse/java_home*, heres mine:
```

/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/sablevm
/usr/lib/fjsdk
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

```
And this is what eclipse says when i run it in console:
```

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/sablevm...not found
  testing /usr/lib/fjsdk...not found
  testing /usr/lib/j2se/1.5...not found
  testing /usr/lib/j2se/1.4...not found
  testing /usr/lib/j2sdk1.5-ibm...not found
  testing /usr/lib/j2sdk1.4-ibm...not found
  testing /usr/lib/j2sdk1.5-sun...found

```
It runs alright, also check out my java config:
```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/j2sdk1.5-sun/bin/java

```

---

### Post by ninocass on 2005-12-02
working a treat many thanks!!!
eclipse is a good deal faster too!!!!
Nino

---

### Post by arpunk on 2005-12-02
[QUOTE=ninocass]working a treat many thanks!!!
eclipse is a good deal faster too!!!!
Nino[/QUOTE]
;) anytime dude.

---

### Post by Alex Smirnov on 2008-01-10
I've got this error after upgrade from feisty to gutsy.
After removing ~/.eclipse error has gone.

---

