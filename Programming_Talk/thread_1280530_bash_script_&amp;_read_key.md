---
title: "bash script &amp; read key"
date: 2009-10-02
forum: Programming Talk
---

### Post by cyrus_the_virus on 2009-10-02
Hi,

I'm trying to write a script which opens a mms stream in vlc media player.
The scripts prompts for a 2 digit number (01, 02 etc) and then opens a mms stream according to that number.

I'm using the code below to obtain the two digit number.
```
read -n 2 KEY
``` 
*"-n 2"* means the input is 2 characters (so no ENTER is needed) and *KEY* is the variable in which the number will be stored.

This works fine when I execute that command directly from a terminal. However when I put it in a script file it throws an error:
*read: 9: Illegal option -n 2*
When I use *"read KEY"* it does work in a script.

Does somebody know why this is? It is quite important that no ENTER is needed because the script is for a remote control which doesn't have a ENTER key.

This is the a part of the script
```

KEY="EMPTY"
while [ "$KEY" != "" ]
do
read -s -p KEY "Password"
if [ "$KEY" = "01" ];
then
	vlc "mms://channel1" -f -R -q
fi
done

```

Thanks

---

### Post by Arndt on 2009-10-02
> **cyrus_the_virus said:**
> Hi,

I'm trying to write a script which opens a mms stream in vlc media player.
The scripts prompts for a 2 digit number (01, 02 etc) and then opens a mms stream according to that number.

I'm using the code below to obtain the two digit number.
```
read -n 2 KEY
``` 
*"-n 2"* means the input is 2 characters (so no ENTER is needed) and *KEY* is the variable in which the number will be stored.

This works fine when I execute that command directly from a terminal. However when I put it in a script file it throws an error:
*read: 9: Illegal option -n 2*
When I use *"read KEY"* it does work in a script.

Does somebody know why this is? It is quite important that no ENTER is needed because the script is for a remote control which doesn't have a ENTER key.

This is the a part of the script
```

KEY="EMPTY"
while [ "$KEY" != "" ]
do
read -s -p KEY "Password"
if [ "$KEY" = "01" ];
then
	vlc "mms://channel1" -f -R -q
fi
done

```

Thanks

Does the script begin with #!/bin/bash? bash knows about the -n option; sh doesn't.

---

### Post by cyrus_the_virus on 2009-10-02
Thanks for your reply.

The doesn't begin with #!/bin/bash. However when I add it, I still get the same error.

---

### Post by Arndt on 2009-10-02
> **cyrus_the_virus said:**
> Thanks for your reply.

The doesn't begin with #!/bin/bash. However when I add it, I still get the same error.

It works when I run it. Maybe your script is given to plain 'sh' anyway for some reason. Did you do "chmod +x" on it? How do you get it invoked?

---

### Post by cyrus_the_virus on 2009-10-02
I've got it working :)

First I invoked the script with *sh tv.sh*
Your comment gave me the idea of doing it this way *./tv.sh* and that worked. 

What is the difference between these two anyway? I'm new to linux scripting so I don't know.

Thanks again

---

### Post by Arndt on 2009-10-02
> **cyrus_the_virus said:**
> I've got it working :)

First I invoked the script with *sh tv.sh*
Your comment gave me the idea of doing it this way *./tv.sh* and that worked. 

What is the difference between these two anyway? I'm new to linux scripting so I don't know.

Thanks again

When you write "sh script.sh", or "bash script.sh" or "python script.sh", or whatever, you are starting a language interpreter and handing it a script as input. sh and bash, and also python, as it happens, treat # as a comment, so then the first line with #! will be ignored. If you run it as ./script.sh, it's the Linux kernel that takes care of it, sees that it's not an executable binary program, and then starts the language interpreter named in the #! line.

sh and bash are mostly compatible (bash builds on the older sh), so you can often run scripts meant for one using the other. I mentioned python just as an example - of course mixing sh and python scripts won't work.

I think sh and bash are actually the same program, it looks at how it's invoked and decides which one it is going to be. But it doesn't look at the #! line.

---

### Post by diesch on 2009-10-02
> **Arndt said:**
> 
I think sh and bash are actually the same program, 

No. In Ubuntu /bin/sh is dash as dash is much faster than bash (but has much less features).

---

### Post by falconindy on 2009-10-02
> **Arndt said:**
> I think sh and bash are actually the same program...
Well, not really, but they are related. The original Unix shell dates back to 1977 whereas Bash is just a little over 20 years old. However, in Jaunty, the default is for /bin/sh to point to /bin/dash, which is the Debian Almquist shell -- a direct descendent of ash (out of freeBSD). Dash is **not** entirely POSIX compliant, so `sh` and `bash` can behave differently.

---

### Post by cyrus_the_virus on 2009-10-04
Thankyou all for the explanation :) I understand the difference now.

---

### Post by A_Fiachra on 2009-10-04
> **falconindy said:**
> Well, not really, but they are related. The original Unix shell dates back to 1977 whereas Bash is just a little over 20 years old. However, in Jaunty, the default is for /bin/sh to point to /bin/dash, which is the Debian Almquist shell -- a direct descendent of ash (out of freeBSD). Dash is **not** entirely POSIX compliant, so `sh` and `bash` can behave differently.

Oy!

Can't we all agree on what a Bourne shell is?

On AIX (if memory serves), the default shell is Korn ... that threw me for a loop.

For a while Slowlaris used C-shell as a default ... Bad!!

Tom Christiansen wrote a funny [rant ]("http://www.ooblick.com/text/CshProgrammingConsideredHarmful.html")about C-shell, worth reading.

---

### Post by diesch on 2009-10-06
> **A_Fiachra said:**
> Oy!

Can't we all agree on what a Bourne shell is?

On AIX (if memory serves), the default shell is Korn ... that threw me for a loop.


Is this related to [this Korn]("http://en.wikipedia.org/wiki/Korn_%28liquor%29")? ;-)

---

