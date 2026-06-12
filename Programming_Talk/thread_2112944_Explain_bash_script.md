---
title: "Explain bash script?"
date: 2013-02-06
forum: Programming Talk
---

### Post by CrewDK on 2013-02-06
There is one bash script. I want to make other scrpt similar to the first one, but do not quite understand some things in this script. Can someone help me with this?


This part of the script in which I want to understand.
```

pfile=/etc/passwd

echo
LOGIN="$1"
needinput=yes
while [ ! -z $needinput ]; do
  if [ -z "$LOGIN" ]; then 
    while [ -z "$LOGIN" ]; do LOGIN="$(get_input "Login name for new user []:")" ; done
  fi
  grep "^${LOGIN}:" $pfile >/dev/null 2>&1  # ensure it's not already used
  if [ $? -eq 0 ]; then
    echo "- User '$LOGIN' already exists; please choose another"
    unset LOGIN
  elif [ ! -z "$( echo $LOGIN | grep "^[0-9]" )" ]; then
    echo "- User names cannot begin with a number; please choose another"
    unset LOGIN
  elif [ ! "$LOGIN" = "`echo $LOGIN | tr A-Z a-z`" ]; then # useradd does not allow uppercase
    echo "- User '$LOGIN' contains illegal characters (uppercase); please choose another"
    unset LOGIN
  elif [ ! -z "$( echo $LOGIN | grep '\.' )" ]; then
    echo "- User '$LOGIN' contains illegal characters (period/dot); please choose another"
    unset LOGIN
  else
    unset needinput
  fi
done

```1. Why firstly variable LOGIN is set to $ 1?
This is in case the script is run with an additional variable in the command line? Like: 

```
somescript.sh username
```2. What does mean options "-z" in 

```
while [ ! -z $needinput ]; do
  if [ -z "$LOGIN" ]; then 
    while [ -z "$LOGIN" ]; do LOGIN="$(get_input "Login name for new user []:")" ; done

```3. I do not quite understand how the script looks for a new login to the already existing list of users. What does it mean?

```
2>&1
```


PS: Thnx for your help for noob like me. :(

---

### Post by iMac71 on 2013-02-06
a) $1 is the first argoment passed to the script: see here:
[http://tldp.org/LDP/abs/html/othertypesv.html](http://tldp.org/LDP/abs/html/othertypesv.html)

b) -z is a comparison operator for verifying if a string is null: see here:
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

c) 2>&1 means that the output is sent to stderr (file descriptor #2) in addition to stdout (file descriptor #1): see here:
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by squakie on 2013-02-06
Perhaps if you could tell us what you are changing it to and why we might be able to help more.

---

### Post by schragge on 2013-02-06
Not that it were important or changed something, but I'd rewrite the code like this
```

echo
LOGIN="$1"
another='please choose another'

while
  while [[ -z $LOGIN ]]
    do LOGIN="$(get_input "Login name for new user []:")"
  done
do
  if getent passwd "$LOGIN" &>/dev/null; then
    echo "- User '$LOGIN' already exists;" $another
  else
    case $LOGIN in
    [0-9]*)
      echo "- User names cannot begin with a number;" $another
      ;;
    *[A-Z]*)
      echo "- User '$LOGIN' contains illegal characters (uppercase);" $another
      ;;
    *.*)
      echo "- User '$LOGIN' contains illegal characters (period/dot);" $another
      ;;
    *) break
    esac
  fi
  unset LOGIN
done

```

---

### Post by CrewDK on 2013-02-06
> **iMac71 said:**
> a) $1 is the first argoment passed to the script: see here:
[http://tldp.org/LDP/abs/html/othertypesv.html](http://tldp.org/LDP/abs/html/othertypesv.html)

b) -z is a comparison operator for verifying if a string is null: see here:
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

c) 2>&1 means that the output is sent to stderr (file descriptor #2) in addition to stdout (file descriptor #1): see here:
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

Thanks. I'll read all this man's.

[QUOTE=squakie]Perhaps if you could tell us what you are changing it to and why we might be able to help more.     [/QUOTE]

Well, I'm working as a sort of administrator in a normal school in Russia.
At the moment I'm trying to reinstall most of the computers in our school from windows to Linux.
The problem is that there is some part of the training programs (on CD or DVD f.x.) that don't work under wine, but only under winxp so I have to install on some machines VirtualBox.

At school, there is not a domain, so I have to setup all the computers separately. 
So I want to write a script that would:

- ask login (username) of the target user and check whether there exist such login on the computer;
- download, install package with VirtualBox (already done);
- download, unpack the archive with VBox HDD (with installed WinXP) and settings to user's home directory and fix the path to user's home directory in the vbox configs. (almost done)

---

### Post by CrewDK on 2013-02-06
> **schragge said:**
> Not that it were important or changed something, but I'd rewrite the code like this
```

echo
LOGIN="$1"
another='please choose another'

while
  while [[ -z $LOGIN ]]
    do LOGIN="$(get_input "Login name for new user []:")"
  done
do
  if getent passwd "$LOGIN" &>/dev/null; then
    echo "- User '$LOGIN' already exists;" $another
  else
    case $LOGIN in
    [0-9]*)
      echo "- User names cannot begin with a number;" $another
      ;;
    *[A-Z]*)
      echo "- User '$LOGIN' contains illegal characters (uppercase);" $another
      ;;
    *.*)
      echo "- User '$LOGIN' contains illegal characters (period/dot);" $another
      ;;
    *) break
    esac
  fi
  unset LOGIN
done

```

Thnx. But this part of script i need only like example for my other script. BTW, initialy this is rather big script for adding user, managing user's groups e.t.c., some sort of adduser\useradd but with advanced features. :)

---

### Post by schragge on 2013-02-06
> **CrewDK said:**
> - ask login (username) of the target user and check whether there exist such login on the computer;If I understand correctly, that's the part you're working on now. You can check for existence of a user with [getent(1)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=getent") like this
```

if getent passwd "$LOGIN" >/dev/null
then
  echo User found
else
  echo User not found
fi

```

---

### Post by CrewDK on 2013-02-06
> **iMac71 said:**
> 

c) 2>&1 means that the output is sent to stderr (file descriptor #2) in addition to stdout (file descriptor #1): see here:
[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

Do I understand right that in this case, I just do not see any messages (about error for example)?

> **schragge said:**
> If I understand correctly, that's the part  you're working on now. You can check for existence of a user with [getent(1)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=getent") like this
```

if getent passwd "$LOGIN" >/dev/null
then
  echo User found
else
  echo User not found
fi

```

Yes, you understand correctly. Thanx for this idea. But I think, that's it'll be better keep some checks for correct username in my script.

---

### Post by iMac71 on 2013-02-06
> **CrewDK said:**
> Do I understand right that in this case, I just do not see any messages (about error for example)?in your script```
>/dev/null 2>&1
```means that error messages are not displayed on the screen, i.e. your script runs quietly.

---

### Post by CrewDK on 2013-02-07
One more question. I want to add another variable to the script, which would mean the amount of RAM for future virtual machine.
How can I set check for the amount of allocated memory, that it's not greater than, for example, 1\2 all your memory?

```

echo
RAM="$2"
needinput=yes
while [ ! -z $needinput ]; do
  if [ -z "$RAM" ]; then
    while [ -z "$RAM" ]; do RAM="$(get_input "RAM size for VBox? []:")" ; done
  fi
  grep "^${RAM}:" $pfile >/dev/null 2>&1  # **<<---------- how can I check correct RAM size **
  if [ $? -ne 0 ]; then
    echo "- '$RAM' size is too big; please choose another"
    unset RAM
  else
    unset needinput
  fi
done


```

---

### Post by schragge on 2013-02-07
if $pfile in your example references */etc/passwd* then it's wrong: */etc/passwd* contains no information about RAM. Instead, you need to evaluate either */proc/meminfo* or the output of [free(1)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=free"). The actual code depends on

[LIST=1]
[*]what units is the RAM size entered in?
[*] do you count only physical RAM or swap space as well?
[/LIST]

To get the physical RAM size in kilobytes try:
```

RAM=`free | awk '/^Mem:/ {print $2}'`

```

---

### Post by CrewDK on 2013-02-07
> **schragge said:**
> if $pfile in your example references */etc/passwd* then it's wrong: */etc/passwd* contains no information about RAM. 


I know. It's just an example of chek from script above. :)

> **schragge said:**
> 
Instead, you need to evaluate either */proc/meminfo* or the output of [free(1)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=free"). The actual code depends on

[LIST=1]
[*]what units is the RAM size entered in?
[*] do you count only physical RAM or swap space as well?
[/LIST]


1. In my variable I want to enter RAM size in Mb (256, 512 e.t.c.)
2. I'm counting only physical RAM

> **schragge said:**
> 
To get the physical RAM size in bytes try:
```

RAM=`free | awk '/^Mem:/ {print $2}'`

```

I've already tried "free", but I don't know how can I transfer RAM size in bytes from output to megabytes and how compare this value with my variable. :(

---

### Post by schragge on 2013-02-07
> **CrewDK said:**
> I've already tried "free", but I don't know how can I transfer RAM size in bytes from output to megabytes and how compare this value with my variable. :(

Try this
```

RAM="$(get_input "RAM size for VirtualBox (MB)? []:")"
if ((RAM > $(free -m | awk '/^Mem:/ {print $2}')/2)); then
  echo RAM size too big
else
  echo OK
fi

```

---

### Post by CrewDK on 2013-02-07
Thank you. It works great.

---

### Post by CrewDK on 2013-02-07
There is no limit to perfection :D

I want to show the total amount of memory on the system in my RAM request, for not to wonder each time how much total RAM have the machine.
So I decided to set one more variable. Something like that: 

```

RAM1="free -m | awk '/^Mem:/ {print $2}'"
echo $RAM1 Mb

```I understand, that it's no wonder that in this case as result i see 

```
free -m | awk '/^Mem:/ {print }' MB
```but how can I should change my variable if I want see result as, for example

```
1024 Mb
```

---

### Post by schragge on 2013-02-07
Use backticks instead of double-quotes.
```

RAM1=`free -m|awk '/^Mem:/{print$2}'`
echo $RAM1 Mb

```

---

### Post by CrewDK on 2013-02-07
I love you guys. :)

---

### Post by Vaphell on 2013-02-07
> Use backticks instead of double-quotes.
don't use backticks, use $() instead.

backtick are on their way out - they have poorer readability (opening and closing ones are not immediately obvious when you have plenty of them + single quotes which are similar) and cause problems when you stack them (require escaping)

---

