---
title: "Pipe into another script"
date: 2008-04-20
forum: Programming Talk
---

### Post by Dr Small on 2008-04-20
I have written a very short script in haste, and basically I want to pipe other commands into it. Whatever I pipe into it, I want to be able to nab that command and add it as a variable to my script.

Here is the current script:
```
#!/bin/bash

to="drsmall@mycroftserver.homelinux.org"
subject="Server Emergency"

message=$(echo "Mycroft Server Emergency.\n\nLast command:\n"$0 "\n\n\nReason:\n"$1)
echo -e $message | mail -s "$subject" $to

```

I have $0 in there for the script name, but when I get the email, in tells me the location of my mailer script, instead of the command I piped into it.

So the basic question, how can I read the command (not the stdin) in my script that I piped through it?

Dr Small

---

### Post by ghostdog74 on 2008-04-20
```

#!/bin/bash
cat << EOF | mail recipient@email.add.com
 Mycroft Server Emergency.
  Last command:
  $0 
  Reason : $1
EOF

```

---

### Post by Dr Small on 2008-04-20
That has the same effect:
```

 Mycroft Server Emergency.
  Last command:
  /home/drsmall/bin/mailer 
  Reason : 

```

And I ran:
```
free -h | mailer
```

Just for a test. Well, thanks anyhow for trying.

---

### Post by ghostdog74 on 2008-04-20
```

#!/bin/bash
echo "script name: $0"
while read  var
do
    echo "input line: " $var
done

```
output:
```

# df | ./mailer.sh

```

---

