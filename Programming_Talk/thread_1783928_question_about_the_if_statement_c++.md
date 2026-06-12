---
title: "question about the if statement c++"
date: 2011-06-16
forum: Programming Talk
---

### Post by hakermania on 2011-06-16
Hello, I am trying to do the following:
```

QString arg="X";
int a=1;
if((arg=="X" || arg=="Y) && a==1)
     do_action();

```I want to say:** if arg is (X or Y) and a is 1, then do_action();**
and I get error message:
```

error: no match for &#8216;operator||&#8217; in &#8216;((arg.QString::operator==(((const char*)"X")) || arg.QString::operator==(((const char*)"Y"))) || arg&#8217;

```Is this something Qt-dependent or my code is wrong?

---

### Post by gusnan on 2011-06-16
try adding some parenthesis around the elements in that line:
```
if(((arg=="X") || (arg=="Y)) && (a==1))
```

---

### Post by hakermania on 2011-06-16
No, same problem....
The actual if statement is (modified after your suggestion)
```

if( ((first_argument=="--start") || (first_argument=="--pause") || (first_argument=="--stop") || (first_argument="--next") || (first_argument="--previous")) && (QCoreApplication::arguments().count()>2) )

```

---

### Post by amauk on 2011-06-16
missing double-equals on 2 of the comparisons

```
first_argument=[COLOR="Red"]=[/COLOR]"--next"
first_argument=[COLOR="Red"]=[/COLOR]"--previous"
```

---

### Post by hakermania on 2011-06-16
> **amauk said:**
> missing double-equals on 2 of the comparisons

```
first_argument=[COLOR=Red]=[/COLOR]"--next"
first_argument=[COLOR=Red]=[/COLOR]"--previous"
```

nice thanks :)
I've done this one million times without an error at all :| I assumed they were corert :)

---

### Post by amauk on 2011-06-16
Value assignment & value comparison are fundamentally different, so make sure you're using the correct one

```
// If foo equals 1
if (foo == 1)
```Vs.```
// If it's possible to assign
// the value 1 to variable foo
// (most likely always true,
// unless foo is immutable)
if (foo = 1)
```

---

