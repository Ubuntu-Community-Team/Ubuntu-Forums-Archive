---
title: "Bash script issues."
date: 2015-05-08
forum: New to Ubuntu
---

### Post by CrewDK on 2015-05-08
I need to send message to all desktop users. Now I wrote bash script like this: 

```
#!/bin/bash

for i in $(who -u | grep tty | awk '{print $1}');
    do
        echo "username check $i";
        export  XAUTHORITY=/home/$i/.Xauthority
        export DISPLAY='127.0.0.1:0.0'
        zenity --info --title="title" --text="msg" &
    done

```

All works fine only if there is only 1 active members. But if last user didn't logout from his session and new user just switched users we has minimum 2 active user. 
For example:

```
who -u | grep tty
test1    tty7         2015-05-08 21:18  &#1076;&#1072;&#928;      2828
teacher  tty8         2015-05-08 21:18  &#1076;&#1072;&#928;      3246
```

And in this case, when i running my script - only 1st user will see my msg. Is there any way i can fix that?

---

### Post by CrewDK on 2015-05-09
OK. Now i know what is my problem. 

```
export DISPLAY='127.0.0.1:0.0' 
```

works fine if there is only one logged in user or only for 1st logged in user if there are many. 

But if there are many users each of them has his own DISPLAY:
```
crew@vbox:~$ echo $DISPLAY
:0.0

test@vbox:~$ echo $DISPLAY
:1

test2@vbox:~$ echo $DISPLAY
:2
```

So if i manualy editing my script and changing "export DISPLAY" like
```
export DISPLAY='127.0.0.1:1'
 
export DISPLAY='127.0.0.1:2'
```

etc. This way all works fine for 2nd, 3rd etc users. But I have to change script for each logged in users. Is there any wau I can set it automaticly trough same script?

---

### Post by sandyd on 2015-05-09
Does this help?
```

ps aux | grep -v grep | grep -i "/usr/bin/X :" | awk -F " " '{ print "127.0.0.1"$12 }'

```

Edit: Fixed

If that doesn't work, please post output of
```

ps aux | grep -v grep | grep -i "/usr/bin/X :"
```

---

### Post by Lars Noodén on 2015-05-09
How about something like this?  Though I'm getting a bit different output from 'who' ...

```

while read user display; 
 do echo $user=$display;
        export  XAUTHORITY=/home/$user/.Xauthority
        export DISPLAY="$display"
        zenity --info --title="title" --text="msg" &
done < <(/usr/bin/who -u | /usr/bin/awk '/tty/ { print $1 " " $2}');

```

(The grep is redundant if awk is being used.)

---

### Post by CrewDK on 2015-05-09
I'm affraid that this didnt help at all. This just gives back my own IP address.

```
$ who | awk -F "(" '{ print $2}' | awk '!x[$0]++' |  rev| cut -c 2- | rev

192.168.1.33
```


Well, maybe my English it too bad. I'll try to explain more. 

Let's imagine that we have one PC in local net. We have 3 local users on this PC: crew, test1, test2. 3 lazy and dumb users, which even can't logout normal from their session. So in one moment we have 2-3 logged in users. 

```
who -u | grep tty
crew     tty9         2015-05-08 21:18  &#1076;&#1072;&#928;      2814
test1    tty7         2015-05-08 21:18  &#1076;&#1072;&#928;      2828
test2    tty8         2015-05-08 21:18  &#1076;&#1072;&#928;      3246
```

Let's imagine that I need to update software on that PC. So I logging in on that PC through ssh and make "sudo blah-blah-blah....". At this moment one of the user want to reboot or shutdown PC. But are you remember, that they are lazy and dumb?  System won't let them turn off system normally (there are other logged in user with higher privileges etc), but instead of call me and ask what to do they just push the button on case :(

And to prevent that I want to create universal script with notification. Something like that: 


[ATTACH=CONFIG]261859[/ATTACH][ATTACH=CONFIG]261860[/ATTACH]

The problem, as I understand, is that every user has his own DISPLAY set. 

```
crew@vbox:~$ echo $DISPLAY
:0.0

test@vbox:~$ echo $DISPLAY
:1

test2@vbox:~$ echo $DISPLAY
:2
```

And I cant understand how I must add this set into my script.

---

### Post by CrewDK on 2015-05-09
> **Lars Noodén said:**
> How about something like this?  Though I'm getting a bit different output from 'who' ...

```

while read user display; 
 do echo $user=$display;
        export  XAUTHORITY=/home/$user/.Xauthority
        export DISPLAY="$display"
        zenity --info --title="title" --text="msg" &
done < <(/usr/bin/who -u | /usr/bin/awk '/tty/ { print $1 " " $2}');

```

(The grep is redundant if awk is being used.)




Thnx, i'll try it tomorrow morning :)

---

### Post by sandyd on 2015-05-09
> **CrewDK said:**
> I'm affraid that this didnt help at all. This just gives back my own IP address.

```
$ who | awk -F "(" '{ print $2}' | awk '!x[$0]++' |  rev| cut -c 2- | rev

192.168.1.33
```


Well, maybe my English it too bad. I'll try to explain more. 

Let's imagine that we have one PC in local net. We have 3 local users on this PC: crew, test1, test2. 3 lazy and dumb users, which even can't logout normal from their session. So in one moment we have 2-3 logged in users. 

```
who -u | grep tty
crew     tty9         2015-05-08 21:18  &#1076;&#1072;&#928;      2814
test1    tty7         2015-05-08 21:18  &#1076;&#1072;&#928;      2828
test2    tty8         2015-05-08 21:18  &#1076;&#1072;&#928;      3246
```

Let's imagine that I need to update software on that PC. So I logging in on that PC through ssh and make "sudo blah-blah-blah....". At this moment one of the user want to reboot or shutdown PC. But are you remember, that they are lazy and dumb?  System won't let them turn off system normally (there are other logged in user with higher privileges etc), but instead of call me and ask what to do they just push the button on case :(

And to prevent that I want to create universal script with notification. Something like that: 


[ATTACH=CONFIG]261859[/ATTACH][ATTACH=CONFIG]261860[/ATTACH]

The problem, as I understand, is that every user has his own DISPLAY set. 

```
crew@vbox:~$ echo $DISPLAY
:0.0

test@vbox:~$ echo $DISPLAY
:1

test2@vbox:~$ echo $DISPLAY
:2
```

And I cant understand how I must add this set into my script.

Fixed - your who format is different because you have an IP in the second column

---

### Post by CrewDK on 2015-05-09
> **sandyd said:**
> Does this help?
```

ps aux | grep -v grep | grep -i "/usr/bin/X :" | awk -F " " '{ print "127.0.0.1"$12 }'

```

Edit: Fixed

If that doesn't work, please post output of
```

ps aux | grep -v grep | grep -i "/usr/bin/X :"
```

Yes, that's works. 

```
crew@VBox:~$ ps aux | grep -v grep | grep -i "/usr/bin/X :" | awk -F " " '{ print "127.0.0.1"$12 }'
127.0.0.1:0
127.0.0.1:1
127.0.0.1:2
crew@VBox:~$
```

But can you help me a little bit more? How can I insert this into my script? 

```
for i in $(who -u | awk '/tty/ { print $1 }');
    do
                echo "username check $i";
                export  XAUTHORITY=/home/$i/.Xauthority
                export DISPLAY='127.0.0.1:0.0'
                zenity --info --title="title" --text="msg" &
    done
```

---

### Post by CrewDK on 2015-05-10
In the end I got something like this: 

```
#!/bin/bash

for i in $(who -u | grep tty | awk '{print $1}');
    do
        T=`who -u | grep tty | grep $i | awk '{print $2}'`
        D=`ps aux | grep -v grep | grep -i "/usr/bin/X :" | grep $T | awk -F " " '{ print "127.0.0.1"$12 }'`

        echo "&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1100; $i - $T - $D"
        export XAUTHORITY=/home/$i/.Xauthority
        export DISPLAY=$D
        zenity --info --title="title" --text="msg" &
    done
```


Looks like working solutions for me. But maybe you can add something? 
Thank you for your help.

---

### Post by Lars Noodén on 2015-05-10
With the script as it is there are just some small things that I would propose changing.  One stylistic change would be to [url=http://mywiki.wooledge.org/BashFAQ/082]use **$( ... )** instead of backticks.  (A performance change would be to roll the greps into awk because awk includes the ability to pattern match, at least for the first one.  But are you familiar with awk's syntax for the second and third?  It's just a bunch of implied if-then statements.)  Then it's a good idea to either explicitly set $PATH or else use absolute paths for the programs.  

My guess:

```
#!/bin/bash

PATH=/usr/sbin:/usr/bin:/sbin:/bin;

for i in $(who -u | awk '/tty/ {print $1}');
    do
        T=$(who -u | awk -v i=$i '/tty/ && $0 ~ i {print $2}')
        D=$(ps aux | awk -F " " -v t=$T '!/awk/ && /\/usr\/bin\/X/ && $0 ~ t { print "127.0.0.1"$12 }')

        echo "&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1100; $i - $T - $D"
        export XAUTHORITY=/home/$i/.Xauthority
        export DISPLAY=$D
        zenity --info --title="title" --text="msg" &
    done
```

However, it is theoretically possible for people to log in or out during the time between when $i, $T and $D are collected.  Can you show some output of
```

ps aux | grep -v grep | grep -i "/usr/bin/X :"

```

where two or more users are logged in?  There might be a way to collect all three variables at once.

---

### Post by CrewDK on 2015-05-10
> **Lars Noodén said:**
> With the script as it is there are just some small things that I would propose changing.  One stylistic change would be to [url=http://mywiki.wooledge.org/BashFAQ/082]use **$( ... )** instead of backticks.  (A performance change would be to roll the greps into awk because awk includes the ability to pattern match, at least for the first one.  But are you familiar with awk's syntax for the second and third?  It's just a bunch of implied if-then statements.)  Then it's a good idea to either explicitly set $PATH or else use absolute paths for the programs.  

My guess:

```
#!/bin/bash

PATH=/usr/sbin:/usr/bin:/sbin:/bin;

for i in $(who -u | awk '/tty/ {print $1}');
    do
        T=$(who -u | awk -v i=$i '/tty/ && $0 ~ i {print $2}')
        D=$(ps aux | awk -F " " -v t=$T '!/awk/ && /\/usr\/bin\/X/ && $0 ~ t { print "127.0.0.1"$12 }')

        echo "&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1077;&#1083;&#1100; $i - $T - $D"
        export XAUTHORITY=/home/$i/.Xauthority
        export DISPLAY=$D
        zenity --info --title="title" --text="msg" &
    done
```

Thank you for the tips.

> **Lars Noodén said:**
> 
However, it is theoretically possible for people to log in or out during the time between when $i, $T and $D are collected.  Can you show some output of
```

ps aux | grep -v grep | grep -i "/usr/bin/X :"

```

where two or more users are logged in?  There might be a way to collect all three variables at once.

No problem. Here it is. 

```
root      1246  0.0  3.7 129172 78084 tty7     Ss+  15:03   0:01 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 vt7 -novtswitch -background none
root      2471 16.4  1.3  78864 27688 tty8     Ss+  15:06  19:54 /usr/bin/X :1 -auth /var/run/lightdm/root/:1 vt8 -novtswitch
root      2945 14.7  1.3  78556 27312 tty9     Ss+  15:06  17:51 /usr/bin/X :2 -auth /var/run/lightdm/root/:2 vt9 -novtswitch

```

---

### Post by Lars Noodén on 2015-05-10
Ok.  That's what I thought.  If your output from [w](http://linux.die.net/man/1/w) is something like this,

```
$ w -s
 18:03:01 up  6:27,  4 users,  load average: 0,09, 0,12, 0,11
USER     TTY      FROM              IDLE WHAT
user1     :0       :0               11:35   ?xdm?   6:21   0.11s init --user
user2     :1       :1               12:54   ?xdm?   6:21   0.07s init --user

```

then maybe the following might be of use

```

#!/bin/bash

while read user display;
 do echo $user=$display;
        export  XAUTHORITY=/home/$user/.Xauthority
        export DISPLAY="$display"
        /usr/bin/zenity --info --title="title" --text="msg" &
done < <(/usr/bin/w -s | /usr/bin/awk '$2 ~ /^:/ { print $1 " " $2}');

```

You might need to tune the regular expression there in awk /^:/   As it is, it looks for lines where the second column starts with a colon.  The caret means start looking only at the start of the column.  The [process substitution](http://tldp.org/LDP/abs/html/process-sub.html) <( ... ) takes the output and lets it be treated as if it were a file that could be read.  The redirect ... < ... before it does, just that, read it as a file and feeds it into the while loop.  

And it is possible to put the environment variables on the same line as zenity, if it is the only program that needs it.  

```

        XAUTHORITY=/home/$user/.Xauthority  DISPLAY="$display"  /usr/bin/zenity --info --title="title" --text="msg" &

```

---

### Post by CrewDK on 2015-05-10
Looks like this is not my warriant. :)

```
w -s
 18:14:46 up  3:11,  6 users,  load average: 0.13, 0.31, 0.35
USER     TTY      FROM               IDLE WHAT
crew     tty7                      17:34m gnome-session --session=ubuntu
crew     pts/0    192.168.1.33      6:35m sshd: crew [priv]   
test1    tty8                      17:34m /usr/bin/lxsession -s LXDE -e LXDE
test2    tty9                      17:34m /usr/bin/lxsession -s LXDE -e LXDE
crew     pts/6    192.168.1.33      7:31m sshd: crew [priv]   
crew     pts/7    192.168.1.33      6.00s sshd: crew [priv]
```

But thnx anyway for your proposal :)

---

### Post by Lars Noodén on 2015-05-10
Ok.  Out of curiosity, which version of Ubuntu are you running?  I've got 14.04 LTS 64-bit.

---

### Post by CrewDK on 2015-05-10
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
```

---

### Post by Lars Noodén on 2015-05-10
Ok.  With 12.04 LTS, the following might work for you:

```

#!/bin/bash

while read user display;
 do echo $user=$display;
        export  XAUTHORITY=/home/$user/.Xauthority
        export DISPLAY="$display"
        /usr/bin/zenity --info --title="title" --text="msg" &
done < <(/usr/bin/w | /usr/bin/awk '$2 ~ /^tty/ { sub(/tty/, "", $2); $2=$2-7; print $1 " :" $2 }');

```

I'm not sure how many users it can tolerate.  It just takes the number from the tty number and subtracts 7 from it to guess the display number.

---

### Post by sandyd on 2015-05-10
try
```
#!/bin/bash

# Print users
for user in $(who | grep ":" | awk -F " " '!x[$1]++ { print $1 }');
        do
                # Get user disp, print value may change according to distro
                user_xdisp=`w -h $user | awk -F" " '!x[$1]++ {print $3}'`
                echo "Username of the user is $user, and their display is $user_xdisp"
        done
```
might work or not depending on ubuntu version

---

### Post by CrewDK on 2015-05-11
Thank you. I already have at least one working solution but i'll try this too. :)

---

