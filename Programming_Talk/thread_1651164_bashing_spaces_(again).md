---
title: "bashing spaces (again)"
date: 2010-12-22
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-22
I seem to always be having problems with spaces in scripts. This time I want to call xgettext with a space in one of it's paramaters so I do this:
[php]
#!/bin/bash
XGETFLAGS="--copyright-holder=\"Chris Scaife\" --package-name=$1 --package-version=0.0 --keyword=translatable"

if [ -z $1 ]
then
	echo "use: updatepo exename"
	exit 1
fi

echo "creating first $1.pot message template"
xgettext $XGETFLAGS -o $1.pot *.cpp *.glade

[/php]

IDK why, but xgettext is still getting my name as two separate command line parameters and complains it doesn't know the file extension ". Naturally I tried it with single quotes and I tried escaping the space... but all to no avail :(

what am I missing here ? ](*,)

---

### Post by dwhitney67 on 2010-12-22
Maybe quotes around XGETFLAGS.
```

...
xgettext "$XGETFLAGS" -o $1.pot *.cpp *.glade

```

---

### Post by worksofcraft on 2010-12-22
> **dwhitney67 said:**
> Maybe quotes around XGETFLAGS.
```

...
xgettext "$XGETFLAGS" -o $1.pot *.cpp *.glade

```

Thanks for that idea :)
Alas it looks like the documented xgettext options have not been implemented :(
... but I found a work around using the msgmerge facility :)

Now I'm trying to decide if translatable strings from a library should simply be presented along with those of the application or if they be better off with their own translation domain. 

The advantage would be that they then only need to be translated once for each language, but OTOH there isn't much point translating the library strings when the main app is still in C localeze. :confused:

---

