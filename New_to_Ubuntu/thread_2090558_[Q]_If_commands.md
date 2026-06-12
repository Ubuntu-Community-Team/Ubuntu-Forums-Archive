---
title: "[Q] If commands"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by Sportsstar99 on 2012-12-02
Hi everyone, 
I'm trying to use an if command to copy some files heres what I'm trying to do
Say i want to copy a file from home just called copyme here's how i think it would work
```
if [ md5sum ~/copyme = dasjfhslakdjh ]
    then
cp ~/copyme ~/Desktop/copyme
fi
```
or i perfer the way below
```
MD5SUM=adsfaslkdjhasdhkjl
if [ md5sum ~/copyme = $MD5SUM ]
    then
cp ~/copyme ~Desktop/copyme
fi
```
unfortunately none of these ways work so if someone could tell me how to do what i want to do that would be great. Thanks. Also one more thing if the md5sum does not match then the script would continue without copying correct?

---

### Post by Krytarik on 2012-12-02
> **Sportsstar99 said:**
> unfortunately none of these ways work so if someone could tell me how to do what i want to do that would be great.
Here you go :-) :
```
MD5SUM=<checksum>

if [[ $(md5sum <file> | awk '{print $1}') = $MD5SUM ]]; then
    cp <file> <target>
fi
```> **Sportsstar99 said:**
> Also one more thing if the md5sum does not match then the script would continue without copying correct?
Yup.

Regards.

---

### Post by Sportsstar99 on 2012-12-02
Thank you very much! Really appreciate it.

---

### Post by Sportsstar99 on 2012-12-03
Sorry one more thing how can i put that in a makefile since makefiles use ifeq and ifneq and endif

---

### Post by Krytarik on 2012-12-03
> **Sportsstar99 said:**
> Sorry one more thing how can i put that in a makefile since makefiles use ifeq and ifneq and endif
Several things reg. that:

[LIST]
[*]you can use shell conditional constructs in makefiles as well;
[/LIST]

[LIST]
[*]you need to 'escape' the variables that need to be expanded by the shell with an additional "$" in front of them;
[/LIST]

[LIST]
[*]by default, makefiles use Dash, ie. "/bin/sh", in Ubuntu, if you want to use Bash instead, you need to specify that.
[/LIST]
So, to use my originally suggested construct in a makefile as well, you'd need to put it like this:
```
SHELL=/bin/bash
MD5SUM=<checksum>

target:

    @if [[ $$(md5sum <file> | awk '{print $$1}') = ${MD5SUM} ]]; then \
        cp <file> <target>; \
    fi
```Or, to just use the default shell, ie. Dash, put it like this:
```
MD5SUM=<checksum>

target:

    @if [ "$$(md5sum <file> | awk '{print $$1}')" = "${MD5SUM}" ]; then \
        cp <file> <target>; \
    fi
```

---

### Post by Sportsstar99 on 2012-12-03
Thanks again man!

---

