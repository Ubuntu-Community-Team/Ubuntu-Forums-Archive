---
title: "Test internet connection existence"
date: 2008-03-21
forum: Programming Talk
---

### Post by Mlehliw on 2008-03-21
I'm looking for a standard way to test the existance of an internet connection under Linux. Is anyone aware of any standard methods?

---

### Post by t3hi3x on 2008-03-21
You could always ping a website like google.

---

### Post by LaRoza on 2008-03-21
Usually, I just ping a site. Actually, I use google because it is always there.

---

### Post by Mlehliw on 2008-03-21
Yea, I guess that's an option. I was wondering because I want to pop up a dialog if an internet connection isn't detected.

---

### Post by LaRoza on 2008-03-21
> **Mlehliw said:**
> Yea, I guess that's an option. I was wondering because I want to pop up a dialog if an internet connection isn't detected.

I wrote a program that did exactly that. I'll go look for it.

---

### Post by LaRoza on 2008-03-22
Better solution in Bash (the old program was for Windows)
```

#! /bin/bash

main()
{
    ping -c 64.233.169.103 > /dev/null
    if [ "$?" -eq 0 ] 
    then
        zenity --info --text "Internet Lost";
    else
        sleep 30
        main
    fi
}

main

```

You can tweak this to your liking. It pings google, and if it fails, it will give a popup notifying you, if it suceeds, it waits 30 seconds and does it again.

---

### Post by alex_o on 2009-12-31
> **LaRoza said:**
> Better solution in Bash (the old program was for Windows)
```

#! /bin/bash

main()
{
    ping -c 64.233.169.103 > /dev/null
    if [ "$?" -eq 0 ] 
    then
        zenity --info --text "Internet Lost";
    else
        sleep 30
        main
    fi
}

main

```

You can tweak this to your liking. It pings google, and if it fails, it will give a popup notifying you, if it suceeds, it waits 30 seconds and does it again.

actually the line ping -c 64.233.169.103

gives you the usage because you need to specify the limit of pings to the -c flag ie:
ping -c **1** 64.233.169.103

so in total it should look like:
```
#! /bin/bash

main()
{
    if ping -c 1 64.233.169.103 > /dev/null;then
        zenity --info --text "Internet Lost";
    else
        sleep 30
        main
    fi
}

main
```

---

### Post by fax8 on 2010-06-12
@[alex_o]("http://ubuntuforums.org/member.php?u=805208") actually your code above does alert the user when the connection is working! The instructions in the if and else statements should be switched.

Fabio Varesano

---

### Post by rnerwein on 2010-06-14
hi
you have to use: netstat -punt | grep -i VERBUNDEN ( in english i think it is CONNECTED ) in a selfmade script.
and then, if $? is zero -->  do your stuff  ( 0 == VERBUNDEN || CONNECTED  - depends on your language)
--> -punt will give you the name and the process-id of the process.
ciao

---

### Post by Zugzwang on 2010-06-14
> **rnerwein said:**
> you have to use: netstat -punt | grep -i 

Uuuh, I don't think that this is a good idea. First of all, even if there is a connection, if there is no process at the point of time of checking this, you will receive a false negative. Then, intranet connections are also taken into account. Finally, there are pay-per-use internet connection providers which simply reroute all port-80 traffic through the connection to their payment site and block all other connections until you have bought some connectivity. Here, you get a false positive with your approach.

Finally, for getting rid of the language problem, you can always set "LANG=C" before calling the tool to make sure that the result is in english: "LANG=C netstat -punt"

---

### Post by rnerwein on 2010-06-14
> **Zugzwang said:**
> Uuuh, I don't think that this is a good idea. First of all, even if there is a connection, if there is no process at the point of time of checking this, you will receive a false negative. Then, intranet connections are also taken into account. Finally, there are pay-per-use internet connection providers which simply reroute all port-80 traffic through the connection to their payment site and block all other connections until you have bought some connectivity. Here, you get a false positive with your approach.

Finally, for getting rid of the language problem, you can always set "LANG=C" before calling the tool to make sure that the result is in english: "LANG=C netstat -punt"
hi
sorry 
first of all ---> linux ( i bet you have never heard about tannenbaum ) is not a standard of internet - the roots are comes from ARPANET ( 1969 uuuuups -- the answer [www.google.xxx]("http://www.google.xxx"))
sooooooory - i ain't read this post correct - excuse me
ciao

---

### Post by Zugzwang on 2010-06-15
> **rnerwein said:**
> first of all ---> linux ( i bet you have never heard about tannenbaum ) is not a standard of internet - the roots are 

Actually, I've read enough of the Tanenbaum book to know that his name is not "Tannenbaum". Also, it is non-obvious how your statement that I quoted above relates to the rest of this (necromanced) thread.

---

