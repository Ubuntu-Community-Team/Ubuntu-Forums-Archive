---
title: "Simple Bash Script Needs tweeking"
date: 2008-08-05
forum: Programming Talk
---

### Post by Tobywuk on 2008-08-05
Hello, I have this bash script that I am running from my terminal. It is a script that sends updates to twitter.

```

#!/bin/bash
#

USERNAME=xxxx
PASSWORD=xxxx

if [ $# != 1 ]
then
echo “Usage: ${0##*/} your tweet as you would like it to read”
exit 1
fi
tweet=$1
curl -u $USERNAME:$PASSWORD -d status=”$1&#8243; http://twitter.com/statuses/update.xml


```

The script works fine if im sending a single word to twitter, but as soon as i try and send a few words it is outputing the text "your tweet as you would like it to read".

how can i fix this? thanks.

---

### Post by geirha on 2008-08-05
You are only accepting one argument [ $# != 1 ]. If you run the script with ```
./script hello world
```, you are sending two arguments; $1 == "hello" and $2 == "world". If you quote them, it will send both words in one argument.
```
./script "hello world"
```

It might be better to check for 0 arguments ( [ $# == 0 ] ), and then use ... -d status="$*" ... to send all arguments. That would make both of the ways I mentioned above, of running the script, work.

---

### Post by mynamewastaken on 2008-08-05
> **geirha said:**
> You are only accepting one argument [ $# != 1 ]. If you run the script with ```
./script hello world
```, you are sending two arguments; $1 == "hello" and $2 == "world". If you quote them, it will send both words in one argument.
```
./script "hello world"
```

It might be better to check for 0 arguments ( [ $# == 0 ] ), and then use ... -d status="$*" ... to send all arguments. That would make both of the ways I mentioned above, of running the script, work.

I dont know anything about twitter, but I would just like to add that if you send anything in quotes such as a newline or tab character \n, \t, you will need to escape them out, else bash will interpret them as meant for the shell and not twitter.

---

### Post by Tobywuk on 2008-08-06
I made the changes you guys suggested, but im still having the same problem, it will only send the first word.

terminal throws out this, the words after the first word.:

```

url: (6) Couldn't resolve host 'all'
curl: (6) Couldn't resolve host 'my'
curl: (6) Couldn't resolve host 'followers'
curl: (6) Couldn't resolve host 'again'

```

The code im using now is:

```

#!/bin/bash
#

USERNAME=tobywuk
PASSWORD=xxxxx

if [ $# == 0 ]
then
echo &#8220;Usage: ${0##*/} your tweet as you would like it to read&#8221;
exit 1
fi
tweet=$#
curl -u $USERNAME:$PASSWORD -d status=&#8221;$*&#8243; http://twitter.com/statuses/update.xml

```

Any more idea's?

thanks :)

---

### Post by geirha on 2008-08-06
```

curl -u $USERNAME:$PASSWORD -d status=[COLOR="Red"]”[/COLOR]$*[COLOR="Red"]&#8243;[/COLOR] http://twitter.com/statuses/update.xml

```

The quotes I've marked in red above are unicode symbols. They are not quotes that bash will accept as quotes. Make sure you use proper ascii quotes

```

curl -u $USERNAME:$PASSWORD -d status=[COLOR="Blue"]"[/COLOR]$*[COLOR="Blue"]"[/COLOR] http://twitter.com/statuses/update.xml

```

---

### Post by Tobywuk on 2008-08-06
thanks very much, banged it on the head! all working as it should now,

thanks all :)

---

### Post by cong06 on 2010-01-05
And thank you for your script. I can't find any other tools that will let me just post. Everything else is there for posting and viewing it seems.

---

