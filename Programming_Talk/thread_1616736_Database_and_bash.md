---
title: "Database and bash"
date: 2010-11-08
forum: Programming Talk
---

### Post by cazz on 2010-11-08
Hi
I was thinking about create a restore station on a old computer.

That I was thinking is I start a script, it read the computer name and then read a database/list to see what image it going to use. I was thinking about use clonezilla

I know how I can get the computer name that the script is running but I have no idea how to get the computer name on that computer that I plugin to make a recovery.

That is maybe not so easy but I also thinking about what I can use as a database in bash?
is it a textfile I can use (it going to be a big textfile)
or MySQL maybe or something else?

---

### Post by HarrisonNapper on 2010-11-08
If you have to use a database (and it sounds like there are easier ways to accomplish this), probably best to use an established database like one of the squirrels. MySQL would be fine if you're just trying to store and retrieve images.

---

### Post by amauk on 2010-11-08
Not quite sure I understand what you're trying to do WRT computer names, if you could explain a bit more, or maybe post some pseudo-code?

As for MySQL from Bash,
You'll need the mysql client installed in the machine running the bash script,
then it's just simply a case of

```
#!/bin/bash

DB_HOST="domain.com"
DB_USERNAME="my_username"
DB_PASSWORD="my_password"
DB_NAME="my_database"

QUERY="SELECT foo FROM bar WHERE baz = 1"

echo "$QUERY" | mysql --host="$DB_HOST" --user="$DB_USERNAME" --password="$DB_PASSWORD" --batch --silent "$DB_NAME"
```

---

### Post by cazz on 2010-11-08
Thanks for the code

Well I have not so many code right now but I can tell my idea.

A person go to a computer station with his laptop.
He connect a network cable and use a USB/CD to boot the linux that read the computer name of the laptop and use MySQL to send the right image to the laptop.
After that he just unplug the computer and remove the USB/CD and walk away


I know Clonezilla have PXE but not all laptop work with it and I think it need the MAC address. I have not work with the PXE so much so that is a little new to me.

---

