---
title: "Basic zenity+sqlite sintax"
date: 2008-12-03
forum: Programming Talk
---

### Post by lovinglinux on 2008-12-03
I want to make a script with zenity, so it prompts for an action where the options are retrieved from a sqlite database.

The standalone zenity code should be something like this:

```
zenity --list --height=360 --width=300 --text "Select an option" --radiolist  --column "Pick" --column "Options" 1 'Option 1' 2 'Option 2'
```

Here is the script integrated with the database:
```

#!/bin/bash

[COLOR="Red"]**OPTIONS**[/COLOR]=$(sqlite3 ~/mydatabase.sqlite "select [string] from selector")

CAT=$(zenity --list --height=360 --width=300 --text "Select an option" --radiolist  --column "Pick" --column "Options"[COLOR="Red"]** ${OPTIONS}**[/COLOR])

echo "$CAT"
```

Where the database entries are:

```
**rowid                      string**
1                        1 Option1
2                        2 Option2

```

The resulting options prompt looks fine like this:

[[IMG]http://img142.imageshack.us/img142/917/screenshotselectitemsfrpr4.th.png[/IMG]](http://img142.imageshack.us/img142/917/screenshotselectitemsfrpr4.png)

and the result of 

```
echo "$CAT"
```

is also correct

```
Option1
```

The problem is when I use values with spaces in the database string column like this:

```
**rowid                      string**
1                        1 [COLOR="Red"]**Option 1**[/COLOR]
2                        2 [COLOR="Red"]**Option 2**[/COLOR]

```

The prompt will be completely messed up like this:

[[IMG]http://img139.imageshack.us/img139/3250/screenshotselectitemsfrwp0.th.png[/IMG]](http://img139.imageshack.us/img139/3250/screenshotselectitemsfrwp0.png)

So how do I fix this? Or should I use another method?

---

