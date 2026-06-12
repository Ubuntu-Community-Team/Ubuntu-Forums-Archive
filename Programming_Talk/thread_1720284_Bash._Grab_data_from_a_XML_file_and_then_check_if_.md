---
title: "Bash. Grab data from a XML file and then check if that data is less than."
date: 2011-04-03
forum: Programming Talk
---

### Post by LarsKongo on 2011-04-03
Is there any way I can grab some data from a xml file in a bash script and then check if that data (which is a version number) is less than (version number?)

The file is i'm talking about is /usr/share/gtk-engines/murrine.xml

It starts like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<engine schema_version="0.1" module_name="murrine" long_name="Murrine">

	<metainfo>
		<version>0.98.1.1</version>
```
What I want to extract is 0.98.1.1 and then check if the version number (let say 98 ) is lower than 98, and if it is it will echo a message to the user to install the latest murrine engine. Or if 0 is more than 0 then the echo message will be ignored. :) Also, if it can't find /usr/share/gtk-engines/murrine.xml it will display a message to the user to install the murrine engine.

I've been googling forever for something that can check which version of a specific GTK engine someone have installed. Bonus if it works cross-distribution. :P

---

### Post by Phenax on 2011-04-03
Make sure to modify the variable at the top for version to check against.
Only uses stuff that comes on almost every distro by default.

Not tested much. Can be improved. But I think it should be sufficient for your case. If you want a more robust solution you'd need to use an XML parser and a real programming language, methinks.

TESTVER variable should only contain one decimal.
If you want to check if it is version 0.98.55.3 or later, set TESTVER to 0.98553.

```
FILE="/usr/share/gtk-engines/murrine.xml"
TESTVER=1.0

if [ ! -f "$FILE" ]
then
    echo "$FILE not found. Please install."
    exit 1
fi

VERSION=$(grep -m1 '<version>' "$FILE" | sed -e 's/^[ \t]*//' -e 's/<version>\(.*\)<\/version>/\1/g' -e 's/[.]//2g')

echo "You have version: $VERSION"
echo "Version you need: $TESTVER"

if [ `expr $VERSION \>= $TESTVER` -eq 0 ]
then
    echo "You need to upgrade your version"
else
    echo "You are good to go!"
fi

```

---

### Post by LarsKongo on 2011-04-03
Thank you. Seems to work. :D
Just had to change **\>=** to **\<=**. ;)

---

### Post by kurum! on 2011-04-03
```

$ ruby -ne 'puts $_.scan(/<version>(.*?)<\/version>/i)[0][0] if /<version>/' file
0.98.1.1


```

---

