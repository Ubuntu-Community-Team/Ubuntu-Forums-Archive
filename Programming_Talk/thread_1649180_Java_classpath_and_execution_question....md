---
title: "Java classpath and execution question..."
date: 2010-12-19
forum: Programming Talk
---

### Post by sefs on 2010-12-19
Hi I have downloaded an application that has a file in it called grendel.sh which contains....

```

java -Xms128M -Xmx256M -XX:+HeapDumpOnOutOfMemoryError -classpath bin.zip com.grendelscan.GrendelScan 

```

I can run the app if i go to the directory the .sh file is in and double click on it or run it from a terminal.

I tried to setup an item for it in the ubuntu menus, but the program would not run.

How can I adjust the command in the .sh file so that I can run the program without being in the same directory as the .sh file?

Thanks in advance.

---

### Post by trent.josephsen on 2010-12-19
Provide the full path to bin.zip.

If that's not possible, I think you're out of luck.

---

### Post by sefs on 2010-12-19
> **trent.josephsen said:**
> Provide the full path to bin.zip.

If that's not possible, I think you're out of luck.

Tried that already but no luck.

---

### Post by r-senior on 2010-12-20
Trent's suggestion should (and does) work and the program runs.

However:

```

log4j:WARN No appenders could be found for logger (org.apache.commons.configuration.ConfigurationUtils).
log4j:WARN Please initialize the log4j system properly.
[COLOR="Red"]Failed to open scanner.conf. Program will now exit: org.apache.commons.configuration.ConfigurationException: Cannot locate configuration source conf/scanner.conf[/COLOR]

```

So it cannot find the config files in the application's install directory.

I think I'd go for a little bash script on your path to run the app from the right directory. You could change the grendel.sh script to switch directory but you'd have to remember what you did if you upgrade. (Maybe you could raise the issue with the developers?).

```

#!/bin/bash

GRENDEL_HOME=$HOME/Downloads/Grendel-Scan-v1.0-linux/

cd $GRENDEL_HOME
./grendel.sh

```

Then it's trivial to add this script to the menu.

---

### Post by lykeion on 2010-12-20
You could add this line before the java command, to set current working directory to the directory of the script:
```
cd "$(dirname "$0")"
```

EDIT r-senior beat me to it :)

---

### Post by sefs on 2010-12-20
> **r-senior said:**
> Trent's suggestion should (and does) work and the program runs.

However:

```

log4j:WARN No appenders could be found for logger (org.apache.commons.configuration.ConfigurationUtils).
log4j:WARN Please initialize the log4j system properly.
[COLOR="Red"]Failed to open scanner.conf. Program will now exit: org.apache.commons.configuration.ConfigurationException: Cannot locate configuration source conf/scanner.conf[/COLOR]

```

So it cannot find the config files in the application's install directory.

I think I'd go for a little bash script on your path to run the app from the right directory. You could change the grendel.sh script to switch directory but you'd have to remember what you did if you upgrade. (Maybe you could raise the issue with the developers?).

```

#!/bin/bash

GRENDEL_HOME=$HOME/Downloads/Grendel-Scan-v1.0-linux/

cd $GRENDEL_HOME
./grendel.sh

```

Then it's trivial to add this script to the menu.

Yes this works.  Thanks.  I sent off a note to the developer.

---

