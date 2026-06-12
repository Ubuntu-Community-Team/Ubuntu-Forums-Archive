---
title: "Newbie= Bash / expect Script Issues For Firmware Update Script"
date: 2013-08-17
forum: Programming Talk
---

### Post by dale2 on 2013-08-17
I'm running Ubuntu 9.10 Karmic and am having issues writing a script to pass a password and a http link for the update file. I installed the following packages to add the expect command:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]expect_5.44.1.14-5_i386.deb 
tcl8.5_8.5.8-2_i386.deb
[/SIZE][/FONT][/SIZE][/FONT]
My script looks like the following:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]# this script works to update Firmware
#
# command line format:
#
# sh rcatup [FILE1] 
# 
# where FILE1 is an input file containing a single list of hostnames
#
LOGIN=update
PASSWORD=update
UPDATE=http://xx.xx.xx.xx/update_file.txt 
date 2>&1
for i in `cat $1`
do
if ping $i -c 1 | grep -s "100% packet loss"; 
then echo $i": not on the Network!" >> REDO_RCATUP
else ssh $LOGIN@$i 
expect "$LOGIN@$i" password: 
send "$PASSWORD" 
fi
done


The script stops at the password prompt and when I manually put in the password it logs into the probe correctly but I want the script to put in the password and then send a link to grab the update.
Here is what the output looks like (-x):

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]
# sh -x rcatup file1
+ LOGIN=update
+ PASSWORD=update
+ date
Fri Aug 16 21:54:57 PDT 2013
++ cat file1
+ for i in '`cat $1`'
+ ping xx.xx.xx.xx -c 1
+ grep -s '100% packet loss'
+ ssh [EMAIL="update@xx.xx.xx.xx"]update@xx.xx.xx.xx[/EMAIL]
[email]update@xx.xx.xx.xx[/email]'s password: 
Last login: Sat Aug 17 01:05:54 2013 from xx.xx.xx.xx
CATS 1.0.1.1 (build 1)
CATS-BASE 1.0.1.1
****** Adjusting Alarm Time

<<<<< I hit control C and then get the following >>>>>>>

Update server or http server: Connection to xx.x.xx.xx closed.
+ expect [EMAIL="update@xx.xx.xx.xx"]update@xx.xx.xx.xx[/EMAIL] password:
couldn't read file [EMAIL="update@xx.xx.xx.xx"]update@xx.xx.xx.xx[/EMAIL]: no such file or directory
+ send update
rcatup: line 22: send: command not found

ANY HELP APPRECIATED WITH THIS. I wonder if I need other packages to make this work and I know my code needs help. 

Thanks.

Dale

[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by hakermania on 2013-08-17
Welcome to the forums :)

Ok, I am not an expect expert but I've used it a couple of times.

Just let me point out to you that 9.10 is a very old version of Ubuntu (not supported anymore) and you should totally upgrade to something newer if you want to be and feel secure and use the latest tools.

To the point now, as pointed here: [http://stackoverflow.com/questions/4780893/use-expect-in-bash-script-to-provide-password-to-ssh-command](http://stackoverflow.com/questions/4780893/use-expect-in-bash-script-to-provide-password-to-ssh-command) it is not a good idea to mix up bash and expect. I think that using a different script for the expect part should be a good idea in your case.

This is what I think:

 main_script.sh:

```

LOGIN="update"
PASSWORD="update"


UPDATE=http://xx.xx.xx.xx/update_file.txt 
date 2>&1


while read i; do
    if ping $i -c 1 | grep -s "100% packet loss"; then
        echo " "$i": not on the Network!" >> REDO_RCATUP
    else
        ./do_ip_actions.sh "$LOGIN" "$i" "$PASSWORD" "$UPDATE"
    fi
done < "$1"

```

This reads line by line the file provided by the first argument ($1). Every line is assigned to the $i variable. Then it does to the $i variable what you did.

Please mention that this will work only if there is one IP/server name per line inside the $1 file

Now, when it is the time to login, the script do_ip_actions.sh is called:

```

#!/bin/bash


login="$1"
ip="$2"
pass="$3"
update_file="$4"


/usr/bin/expect <<EOD
set timeout -1


spawn ssh $login@$ip
expect "password: "
send "$pass\n"
expect ":~"
send "ls\n"
expect ":~"
EOD
exit

```

Inside this script you can do whatever you like with the $update_file variable.

Please notice the line **expect ":~"**. It is because in my remote server the prompt looks like this: *alex@alekospi**:~**$ *so the :~ string is in there. I don't know if this is the best way to make this work, but it works just fine in my case.

Tested it on my local network using a raspberry pi as remote server.

---

### Post by localhost8080 on 2013-08-17
I see that you are trying to login using ssh.
you would be safer to setup key based authentication.

I have a tutorial on my blog about how to setup key based auth
[URL="http://jonathansblog.co.uk/ssh-with-keys-forauthentication"]http://jonathansblog.co.uk/ssh-with-keys-forauthentication
[/URL]

once you have the key based auth setup you can skip the 'expect' parts

---

### Post by dale2 on 2013-08-19
Can't thank you enough for your help! The script now stops at the point where it needs the http file for the update so the login works great. Here is my output:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]prompt[EMAIL="t@mpt1a02:/home/gbxfan"]:/home/gbxfan[/EMAIL]# sh -x rcatup file1
+ LOGIN=update
+ PASSWORD=update
+ UPDATE=http://xx.xx.xx.xx/8.0.15.11.inc.txt
+ date
Mon Aug 19 11:52:23 PDT 2013
+ read i
+ ping xx.xx.xx.xx -c 1
+ grep -s '100% packet loss'
+ ./do_ip_actions.sh update xx.xx.xx.xx update [http://xx.xx.xx.xx/cts-8.0t](http://xx.xx.xx.xx/cts-8.0t)
spawn ssh [EMAIL="update@xx.xx.xx.xx"]update@xx.xx.xx.xx[/EMAIL]
[EMAIL="update@xx.xx.xx.xx's"]update@xx.xx.xx.xx's[/EMAIL] password: 
Last login: Mon Aug 19 15:06:32 2013 from xx.xx.xx.xx
CATS 8.0.14.22 (build 1)
CATS-BASE 8.0.14.22
****** Adjusting Alarm Time
Update server or http server:

and then it stops waiting for the update file.
Here is my do_ip_actions file:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]
#!/bin/bash
login="$1"
ip="$2"
pass="$3"
update_file="$4"
&#12288;
/usr/bin/expect <<EOD
set timeout -1
&#12288;
spawn ssh $login@$ip
expect "password: "
send "$pass\n"
expect ":~"
send "ls\n"
expect ":~"
send $update_file
EOD
exit
[/SIZE][/FONT][/SIZE][/FONT]
I tried to using the $update_file with quotes and without quotes but can't seem to get the script to send it.
 

any ideas?

Thanks!!
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by hakermania on 2013-08-19
Please use the ```
 tags for your files or terminal output so as to be formatted correctly in the forums (Automatically placed with the # symbol).

The expect command *send *just sends a command. It is like typing a command with your keyboard.

Example,
[code]
send "ls\n"

```
will send the 'ls' command to the system and thus it will list the files of the home folder of the logged in user.

I don't know what the $update_file variable holds or what exactly you're trying to accomplish there. I guess that the update file is on a remote server but what has to be done with it?

Please give me more information so as to help you.

If $update_file holds an executable command, then I think that you should add
```

expect ":~"

```
exactly after the *send $update_file* command.

---

### Post by dale2 on 2013-08-19
The prompt on the system is waiting for the [http://update_file](http://update_file) name. I just need the send command using the variable to send the update file name ([http://the_update_file](http://the_update_file)) and then hit enter and then the probe will run the update. I wonder after its done and the probe reboots what will happen to the script - does this make sense? Thank you very much. Dale

---

### Post by hakermania on 2013-08-19
Nope, this doesn't make much sense to me.

Is the $update_file some file in a remote server? Does the variable contain a remote file that needs to be downloaded and executed locally (on the corresponding server?). if this is the case, then you could use wget to get the file and then execute it. But I really cannot understand what you're trying to do.

Giving the prompt a remote address that starts with http:// will result in a no such file or directory error. The prompt takes in commands. A remote address alone is not a command.
[I]
Help me to help you :)

 [/I]

---

### Post by dale2 on 2013-08-19
I tried something like this but it didn't work:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2][spawn ssh $login@$ip
expect "password: "
send "$pass\n"
expect ":~"
send "ls\n"
expect ":~"
send "echo $update_file\n"
expect ":~"
EOD
exit]
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by dale2 on 2013-08-19
okay. Thanks for your patience. I believe the [http://update_file](http://update_file) we type in is actually downloading that file and then running it. if that's the case does that make sense?

---

### Post by dale2 on 2013-08-19
Also, if this makes any sense, this is a probe running a version of Unix and when you login as update its running a routine that's expecting a location where it can get the file so its not like a system where you will get errors if you typed in a file location and hit enter because the prompt where the script stops is waiting for the server location where it can get the file it needs for the upgrade.  I think if I can get just (like the echo command) send what's in the update_file variable and hit enter I think I'll be good unless after the upgrade and reboot the script errors out. so is it possible just to send a file location? I think were very close.

---

### Post by hakermania on 2013-08-19
If it really is expecting you the file location exactly after you login, then the following should work:
```

#!/bin/bash

login="$1"
ip="$2"
pass="$3"
update_file="$4"

/usr/bin/expect <<EOD
set timeout -1

spawn ssh $login@$ip
expect "password: "
send "$pass\n"
expect ":~"
send "$update_file\n"
expect ":~"
EOD
exit

```
If it asks you something like this after you login:
"Please give me update file:"
then you should specify it at the expect, something like this, instead:
```

#!/bin/bash

login="$1"
ip="$2"
pass="$3"
update_file="$4"

/usr/bin/expect <<EOD
set timeout -1

spawn ssh $login@$ip
expect "password: "
send "$pass\n"
expect "Please give me update file"
send "$update_file\n"
expect ":~"
EOD
exit

```

---

### Post by dale2 on 2013-08-19
You are a genius! It works.
I am having one small issue with some of the clients giving me the following when it logins in:

[FONT=r_ansi][SIZE=2][FONT=r_ansi][SIZE=2]spawn ssh [EMAIL="update@xx.xx.xx.xx"]update@xx.xx.xx.xx[/EMAIL]
The authenticity of host 'xx.xx.xx.xx (xx.xx.xx.xx)' can't be establish.
RSA key fingerprint is xx:xx:xx:xx:xx:xx:xx:xx:ea.
Are you sure you want to continue connecting (yes/no)? yes

The "yes" you see above is manually typed and it just hangs at that point I would think because the script doesn't know how to handle that BUT it doesn't happen on all clients just a few.

Not sure if you encounted anything like that before but, wow, nice. I appreciate your help! 

Dale
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by hakermania on 2013-08-19
The first time that you ssh at a server it asks you for a yes/no. But ONLY the first time. Once you've done it at least once to each server there shouldn't be any problem if I recall correctly.

A good idea would be to setup key based authentication, as user localhost8080 said at post #3, so as to completely avoid the login part. The whole process will be done faster.

[SIZE=1]Having worked once at the past with expect doesn't make me a genius :P[/SIZE]

---

### Post by dale2 on 2013-08-19
Looks like if I manually SSH into my probe and answer the YES question and it adds it into the known hosts then the script will work so were good unless you have another solution.

---

### Post by dale2 on 2013-08-19
Yes, correct again! Your the best. Thanks so much!! Dale

---

### Post by dale2 on 2013-08-19
Solved!!

---

