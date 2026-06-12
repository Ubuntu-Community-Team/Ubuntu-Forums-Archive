---
title: "Forward slash delimiter problems with bash and expect."
date: 2014-11-15
forum: Programming Talk
---

### Post by Slatevine on 2014-11-15
I posted a version of this problem in linuxforums, but noone could find the solution. Maybe this is something Ubuntu specific, or maybe there are some experts here can help?

I have a bash script which uses expect to talk to telnet. It calls expect using an inline <<EOF portion for expect. This works fine mostly.
 
But one telnet command must look like this:

```

nvram set filter_rule10=\$STAT:2\$NAME:NoInet\$DENY:1\$

```

Note the slashes which must be sent to telnet as per the above. I know this command syntax is correct because it works when entered manually to telnet exactly as above.

The script portion attempting to do this is :

```
function inetOff {
      expect <<EOF 
      spawn telnet router
      expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         
      expect {
         "Password"                 { send "$pwd\r" }
         timeout                    { exit 2 }
             }
      expect { 
         ":~#"                     { send 'nvram set filter_rule10=\\$STAT:1\\$NAME:NoInet\\$DENY:1\\$$\r' }
         timeout                    { puts "Oh dear" }
             }
       expect {
         "*"                     { send "exit\r" }
             }

EOF

} 

```

The problem is that expect reports the resulting command string to telnet as being incorrect, like this for the above attempt:
```

expect: does " nvram set filter_rule10=:1:NoInet:1\u00a699\r\nroot@Paul:~# " (spawn_id exp6) match glob pattern ":~#"? yes

```


The command string ot sends is completely incorrect. 

But to my thinking to send a slash, I must delimit that slash with another slash to avoid bash and/or expect interpreting it. Hence my command string contains double slashes.

But obviously bash or expect is still interpreting those slashes and translating the following text. This isnt what I want!

The trouble is, after that Im just guessing as to what might cause the slashes not to get interpreted. It's not a good way to solve the problem, and unsurprisingly hasnt worked:

```
{ send "nvram set filter_rule10=\\$STAT:1\\$NAME:NoInet\\$DENY:1\\$$\r" }

expect: does " nvram set filter_rule10=:1:NoInet:1\u009891\r\nroot@Paul:~# " (spawn_id exp6) match glob pattern ":~#"? yes


send "nvram set filter_rule10=\\$STAT:1\\$NAME:NoInet\\$DENY:1\\$$\\r"

expect: set expect_out(buffer) " nvram set filter_rule10=:2:NoInet:1\u008d0\r\nroot@Paul:~#"


send "nvram set filter_rule10=\\\$STAT:1\\\$NAME:NoInet\\\$DENY:1\\\$$\\r"

set expect_out(buffer) " nvram set filter_rule10=$STAT:2$NAME:NoInet$DENY:1$$\r\nroot  @Paul:~#"


```

Are there any bash slash expect experts out there? To solve this I need to understand how to stop the slashes getting interpreted....





[/CODE][/CODE]

---

### Post by ofnuts on 2014-11-16
Put what should be taken verbatim in single quotes. If you need substitutions, you can abut parts in double and single quotes.

---

### Post by Slatevine on 2014-11-18
> **ofnuts said:**
> Put what should be taken verbatim in single quotes. If you need substitutions, you can abut parts in double and single quotes.

Unfortnately that gives the same result. But it does highlight the problem better. If I construct the command like this 

```
cmd="nvram set filter_rule10="'\$'"STAT:2"'\$'"NAME:NoInet"'\$'"DENY:1"'\$$'"\r"

```

and then send it like this

```
      expect { 
         ":~#"                     { send $cmd  }
```

Expect generates the correct sequences of slashes, like this:

```
usage: send [args] string
    while executing
"send nvram set filter_rule10=\$STAT:2\$NAME:NoInet\$DENY:1\$$\r  "
    invoked from within


```

But the problem is that expect send thinks the command string is parameters to the expect send command. As you can see, it thinks there is a syntax error - because nvram is not a valid send parameter, or that's what it looks like to me.

The solution, then, is to quote the command string so that expect send knows it is the command text. But that takes me right back to the beginning. 

Quoting the command string like this 

```
      expect { 
         ":~#"                     { send "$cmd"  }
```

gives this

```
send: sending "nvram set filter_rule10=$STAT:2$NAME:NoInet$DENY:1$$\r" to { exp6 }

```

so while expect is now happy with the syntax, it has removed the slashes just as it was before.

I can even try to put the quotes in before expect gets to them, like this:

```
cmd="\"nvram set filter_rule10="'\$'"STAT:2"'\$'"NAME:NoInet"'\$'"DENY:1"'\$$'"\r\""
```

but that only takes me back to the start with no slashes to be seen:

```
send: sending "nvram set filter_rule10=$STAT:2$NAME:NoInet$DENY:1$$\r" to { exp6 }


```


The problem seems to be that:
[LIST=1]
[*]expect send wants the command string in double quotes. Otherwise it doesnt understand the syntax. 
[*]as soon as I put the command in double quotes, no matter what variations I try, expect send interprets the slashes. 
[*]I know Im sending a valid telnet command via expect because it correctly reflects the intended syntax when it spits the error on the send when using double quotes. 
[/LIST]

 It's a tricky one for sure.

---

### Post by ofnuts on 2014-11-19
$-expansion only happens once. Put the string you want to protect in variables:
```

deny='\\$DENY'

```
then build your command using these variables.

---

### Post by Slatevine on 2014-11-24
Apologies for the delay, been away for the weekend :-)

> **ofnuts said:**
> $-expansion only happens once. Put the string you want to protect in variables:


Im not sure how that's any different from what I constructed before, but Im happy to try. 

you mean like this?

```
a='\\$STAT:2'
b='\\$NAME:NoInet'
c='\\$DENY:1'
d='\\$'
e='$'
f='\r'
cmd='nvram set filter_rule10='"$a$b$c$d$e$f"

      expect { 
         ":~#"                     { send "$cmd" }


```

which gives something similar to previous attempts :

```
send "nvram set filter_rule10=\\$STAT:2\\$NAME:NoInet\\$DENY:1\\$$\r" 

```

Too many slashes again.

---

### Post by ofnuts on 2014-11-24
It produces exactly the slashes you put in...  so why not remove some of the slashes from what you initialize the variables with? I'm not even sure you need any backslashes here:
```

**>echo $$
7242
**>x='$$'
**>echo $x
$$
**>

```

---

### Post by Slatevine on 2014-11-24
> It produces exactly the slashes you put in...

That's my problem - it doesnt produce exactly the slashes I put in. Well, bash might do, but when a bash variable or string containing slashes and/or $ symbols is used within expect, the slashes produced are not exactly as I put in. It doesnt matter if I build the variable up as you have suggested, or type it directly into the expect command sequence. The result is the same.

You can see this in my earlier posts, or like this:
```

a='\$STAT:2'
b='\$NAME:NoInet'
c='\$DENY:1'
d='\$'
e='$'
f='\r'
cmd='nvram set filter_rule10='"$a$b$c$d$e$f"

giving :

0: $cmd = nvram set filter_rule10=\$STAT:2\$NAME:NoInet\$DENY:1\$$

which is correct.

But then executing expect like this:

      expect { 
         ":~#"                     { send "$cmd" }

when expect says this :

send: sending "nvram set filter_rule10=$STAT:2$NAME:NoInet$DENY:1$$\r" to { exp6 }


```



So here I have used only one preceeding slash. The $cmd variable is correct. But expect and/or bash has stripped out some of the slashes by the time expect gets to send the command string to telnet. 

That's not correct and isnt exactly, or even particularly similar to, what I put into the bash variable.

Other  combinations of double slashes also give various incorrect results, none of which reflect what I put into the bash variable (or expect command string) by the time expect sends it to telnet.

> 
I'm not even sure you need any backslashes here:

Im not sure if you mean any at all, or any additional ones? My initial posts explain that single slashes are needed for correct telnet command syntax. But that may not be what you meant.

---

### Post by steeldriver on 2014-11-24
Don't forget there are (potentially) two levels of expansion going on: (1) by the shell and (2) by Tcl. You can prevent (1) by quoting any part of the heredoc delimiter "EOF". For (2) you likely need to escape both the \ and the $.

Here is a minimal script that *seems* to do what you want:

```

#!/bin/bash

function inetOff {
    /usr/bin/expect -d <<- "EOF" 
    spawn ./test_spawn.sh
    expect { 
        ":~#"    { 
            send "nvram set filter_rule10=\\\$STAT:1\\\$NAME:NoInet\\\$DENY:1\\\$\r"
            }
    }
    EOF
}

inetOff

```

where [FONT=courier new]~/.test_spawn.sh[/FONT] is
```

#!/bin/bash

read -p ":~#" cmd

```

Then (run with the -d switch as shown):

```

$ ./test_expect.sh
expect version 5.45
argv[0] = /usr/bin/expect  argv[1] = -d  
set argc 0
set argv0 "/usr/bin/expect"
set argv ""
executing commands from command file
spawn ./test_spawn.sh
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {19024}

expect: does "" (spawn_id exp6) match glob pattern ":~#"? no
:~#
expect: does ":~#" (spawn_id exp6) match glob pattern ":~#"? yes
expect: set expect_out(0,string) ":~#"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) ":~#"
send: sending "**nvram set filter_rule10=\$STAT:1\$NAME:NoInet\$DENY:1\$**\r" to { exp6 }

```

---

### Post by Slatevine on 2014-11-26
Thankyou for that reply. Im impressed/grateful you got expect to reflect the wanted string!

I confess I dont  fully understand what you're doing here, which makes the following questions potentially dumb (sorry). 

You're spawning another bash process, which then handles the string of expect statements right? Somehow because of the spawned process, it prevents double handling of the slashes by expect. Hence your expect send statement looks right?

If im OK so far, the bit Im missing is how do I get expect to talk to telnet, which is where the nvram command needs to go. In my script (first post) I spawn telnet not bash, of course. So how do I send my string of now correct expect commands to telnet?

And I have several other expect commands both preceeding and following that need to go to expect. How does fis fit in with my spawned bash process, that doesnt as far as I can see it know anything about my telnet session?

I told you Id be asking some dumb questions! That's what happens when you dont understand what's gong on :-)

As an aside, I also dont get how the read statement is working. MAN read doesnt tell me too much, but -help tells me -p is prompting for input. So it looks like the spawn prompts the original script which feeds it the expect statements, or something along those lines? Im lost as to what "cmd" refers to in the spawn.sh.

thanks again for coming up with something that looks so close to what I need it's not funny!

---

### Post by steeldriver on 2014-11-26
There's no special significance to the bash script or its read statement - it's just a way of mimicking the same interactive spawned process as yours i.e. it's pretending to be a telnet session to a client that sends a ":~#" string and then waits for interactive input (the "nvram set ... " command) in response  - which gets read into a variable called "cmd"

---

### Post by Slatevine on 2014-11-30
OK, I get it now thanks. Bit slow sorry. It also made me jump to conclusions because Ive tried that string, although I didnt explicitly list it in my earlier posts as I tried several guesses in desperation.

So it seems there is something different in my system than yours. Here's my script following your suggestion:

```
#!/bin/bash

#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/home/colic/scripts:/bin/grep
cd "/home/$(whoami)/scripts"
zzout="/home/$(whoami)/scripts/zzchkInet.dat"
log="/home/$(whoami)/scripts/zzchkInet.log"
chkBb="/home/$(whoami)/scripts/chkBroad.dat"

#
# mailing list and database details
#
uname='root'
pwd='idideditthisbitbutnothingelse'
#useData=""
hour=$(date +"%H")
day=$(date +"%d")
mon=$(date +"%m")
year=$(date +"%Y")
 
function blockInet {
      expect <<EOF 
      exp_internal 1     
      
      spawn telnet wndr3300
      expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         
      expect  {
         "Password"                 { send "$pwd\r" } 
         timeout                    { exit 2 }
             }
      expect { 
      
         ":~#"                     {  send "nvram set filter_rule10=\\\$STAT:\\\$NAME:NoInet\\\$DENY:1\\\$\r"}

             }
       expect {
         "*"                     { send "exit\r" }
             }

EOF

}

blockInet
exit


```

and here's what expect thinks of that:

```
Restarting with: /usr/local/bin/bashdb zzexpect.sh 
bash debugger, bashdb, release 4.2-0.8

Copyright 2002, 2003, 2004, 2006, 2007, 2008, 2009, 2010, 2011 Rocky Bernstein
This is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.

(/home/colic/scripts/zzexpect.sh:4):
4:    cd "/home/$(whoami)/scripts"
bashdb<0> 
bashdb<1> 
bashdb<2> 
bashdb<3> 
bashdb<4> 
bashdb<5> 
bashdb<6> 
bashdb<7> 
bashdb<8> c
Breakpoint 1 hit (1 times).
(/home/colic/scripts/zzexpect.sh:20):
20:    function blockInet {
bashdb<9> s
(/home/colic/scripts/zzexpect.sh:21):
21:          expect <<EOF 
bashdb<10> s
spawn telnet wndr3300
parent: waiting for sync byte
parent: telling child to go ahead
parent: now unsynchronized from child
spawn: returns {7770}

expect: does "" (spawn_id exp6) match glob pattern "login"? no
Trying 192.168.4.1...

expect: does "Trying 192.168.4.1...\r\n" (spawn_id exp6) match glob pattern "login"? no
Connected to WNDR3300.
Escape character is '^]'.

expect: does "Trying 192.168.4.1...\r\nConnected to WNDR3300.\r\nEscape character is '^]'.\r\n" (spawn_id exp6) match glob pattern "login"? no

DD-WRT v24-sp2 std (c) 2010 NewMedia-NET GmbH
Release: 08/12/10 (SVN revision: 14929)

Paul login: 
expect: does "Trying 192.168.4.1...\r\nConnected to WNDR3300.\r\nEscape character is '^]'.\r\n\r\r\nDD-WRT v24-sp2 std (c) 2010 NewMedia-NET GmbH\r\nRelease: 08/12/10 (SVN revision: 14929)\r\n\nPaul login: " (spawn_id exp6) match glob pattern "login"? yes
expect: set expect_out(0,string) "login"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) "Trying 192.168.4.1...\r\nConnected to WNDR3300.\r\nEscape character is '^]'.\r\n\r\r\nDD-WRT v24-sp2 std (c) 2010 NewMedia-NET GmbH\r\nRelease: 08/12/10 (SVN revision: 14929)\r\n\nPaul login"
send: sending "root\r" to { exp6 }

expect: does ": " (spawn_id exp6) match glob pattern "Password"? no
root

expect: does ": root\r\n" (spawn_id exp6) match glob pattern "Password"? no
Password: 
expect: does ": root\r\nPassword: " (spawn_id exp6) match glob pattern "Password"? yes
expect: set expect_out(0,string) "Password"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) ": root\r\nPassword"
send: sending "wiredbum1116130911B^ykrz@\r" to { exp6 }

expect: does ": " (spawn_id exp6) match glob pattern ":~#"? no


expect: does ": \r\n" (spawn_id exp6) match glob pattern ":~#"? no
==========================================================
 
 ____  ___    __        ______ _____         ____  _  _ 
 | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | 
 || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ 
 ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| 
 |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| 
 
                       DD-WRT v24-sp2
                   http://www.dd-wrt.com
 
==========================================================

expect: does ": \r\n==========================================================\r\n \r\n ____  ___    __        ______ _____         ____  _  _ \r\n | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | \r\n || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ \r\n ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| \r\n |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| \r\n \r\n                       DD-WRT v24-sp2\r\n                   http://www.dd-wrt.com\r\n \r\n==========================================================\r\n" (spawn_id exp6) match glob pattern ":~#"? no



expect: does ": \r\n==========================================================\r\n \r\n ____  ___    __        ______ _____         ____  _  _ \r\n | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | \r\n || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ \r\n ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| \r\n |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| \r\n \r\n                       DD-WRT v24-sp2\r\n                   http://www.dd-wrt.com\r\n \r\n==========================================================\r\n\r\n\r\n" (spawn_id exp6) match glob pattern ":~#"? no
BusyBox v1.13.4 (2010-08-12 03:24:38 CEST) built-in shell (ash)
Enter 'help' for a list of built-in commands.


expect: does ": \r\n==========================================================\r\n \r\n ____  ___    __        ______ _____         ____  _  _ \r\n | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | \r\n || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ \r\n ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| \r\n |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| \r\n \r\n                       DD-WRT v24-sp2\r\n                   http://www.dd-wrt.com\r\n \r\n==========================================================\r\n\r\n\r\nBusyBox v1.13.4 (2010-08-12 03:24:38 CEST) built-in shell (ash)\r\nEnter 'help' for a list of built-in commands.\r\n\r\n" (spawn_id exp6) match glob pattern ":~#"? no
root@Paul:~# 
expect: does ": \r\n==========================================================\r\n \r\n ____  ___    __        ______ _____         ____  _  _ \r\n | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | \r\n || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ \r\n ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| \r\n |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| \r\n \r\n                       DD-WRT v24-sp2\r\n                   http://www.dd-wrt.com\r\n \r\n==========================================================\r\n\r\n\r\nBusyBox v1.13.4 (2010-08-12 03:24:38 CEST) built-in shell (ash)\r\nEnter 'help' for a list of built-in commands.\r\n\r\nroot@Paul:~# " (spawn_id exp6) match glob pattern ":~#"? yes
expect: set expect_out(0,string) ":~#"
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) ": \r\n==========================================================\r\n \r\n ____  ___    __        ______ _____         ____  _  _ \r\n | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | \r\n || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ \r\n ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| \r\n |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| \r\n \r\n                       DD-WRT v24-sp2\r\n                   http://www.dd-wrt.com\r\n \r\n==========================================================\r\n\r\n\r\nBusyBox v1.13.4 (2010-08-12 03:24:38 CEST) built-in shell (ash)\r\nEnter 'help' for a list of built-in commands.\r\n\r\nroot@Paul:~#"
send: sending "nvram set filter_rule10=$STAT:$NAME:NoInet$DENY:1$\r" to { exp6 }

expect: does " " (spawn_id exp6) match glob pattern "*"? yes
expect: set expect_out(0,string) " "
expect: set expect_out(spawn_id) "exp6"
expect: set expect_out(buffer) " "
send: sending "exit\r" to { exp6 }
(/home/colic/scripts/zzexpect.sh:49):
49:    exit
bashdb<11> 


```


or in abbreviated form:

```
send: sending "nvram set filter_rule10=$STAT:$NAME:NoInet$DENY:1$\r" to { exp6 }


```

My command string, as far as I can see, is identical to the one you have proposed. Yet the result is very different.

So then I tried your exact test script and got this:

```
colic@Gonzalez:~/scripts$ zzt1.sh
/home/colic/scripts/zzt1.sh: line 14: warning: here-document at line 4 delimited by end-of-file (wanted `EOF')
/home/colic/scripts/zzt1.sh: line 15: syntax error: unexpected end of file
colic@Gonzalez:~/scripts$ zzt1.sh
/home/colic/scripts/zzt1.sh: line 14: warning: here-document at line 4 delimited by end-of-file (wanted `EOF')
/home/colic/scripts/zzt1.sh: line 15: syntax error: unexpected end of file
colic@Gonzalez:~/scripts$ 


```

So now Im suspecting my expect version is perhaps the problem? I cant see a simple syntax error, well the code is just a straight cut and paste.

 My expect is version 5.45 which is the latest synaptic gives me in Ubuntu 12.04.

---

### Post by steeldriver on 2014-11-30
You don't appear to be quoting the EOF like I suggested? 
```

  /usr/bin/expect -d << [COLOR=#0000ff]**"**[/COLOR]EOF[COLOR=#0000ff]**"**[/COLOR] 

```

From [FONT=courier new]man bash[/FONT]
```

   Here Documents
       This  type  of  redirection  instructs the shell to read input from the
       current source until a line containing only delimiter (with no trailing
       blanks)  is seen.  All of the lines read up to that point are then used
       as the standard input for a command.

       The format of here-documents is:

              <<[-]word
                      here-document
              delimiter

       No parameter expansion, command substitution, arithmetic expansion,  or
       pathname expansion is performed on word.  [B]If any characters in word are
       quoted, the delimiter is the result of quote removal on word,  and  the
       lines  in the here-document are not expanded.  If word is unquoted, all
       lines of the here-document are subjected to parameter  expansion,  com&#8208;
       mand  substitution,  and arithmetic expansion. [/B] In the latter case, the
       character sequence \<newline> is ignored, and \ must be used  to  quote
       the characters \, $, and `.

```

---

### Post by Slatevine on 2014-11-30
OK we're getting somewhere (well you are, thanks :-))!

Your basic test script doesnt work on my system and gives the error I listed (yes sorry, I showed my code with the EOF unaltered, failing to realise the significance as expect seemed to read its statements with my EOF syntax).

So if I Use this:

```
#!/bin/bash

function inetOff {
        /usr/bin/expect -d <<- "EOF" 
        spawn ./zztestspawn.sh
        expect { 
            ":~#"    { 
                send "nvram set filter_rule10=\\\$STAT:1\\\$NAME:NoInet\\\$DENY:1\\\$\r"
                }
        }
        EOF
}

```
I get this:

```
colic@Gonzalez:~/scripts$ zzt1.sh
zzt1.sh
/home/colic/scripts/zzt1.sh: line 14: warning: here-document at line 4 delimited by end-of-file (wanted `EOF')
/home/colic/scripts/zzt1.sh: line 15: syntax error: unexpected end of file
colic@Gonzalez:~/scripts$ 


```

But if I make sure the EOF is in the first column, it now works:

```
[CODE]#!/bin/bash

function inetOff {
        /usr/bin/expect -d <<- "EOF" 
        spawn ./zztestspawn.sh
        expect { 
            ":~#"    { 
                send "nvram set filter_rule10=\\\$STAT:1\\\$NAME:NoInet\\\$DENY:1\\\$\r"
                }
        }
EOF
}

```

giving:

```
expect: set expect_out(buffer) ":~#"
send: sending "nvram set filter_rule10=\$STAT:1\$NAME:NoInet\$DENY:1\$\r" to { exp6 }
```

Changing my original code (I hope) to your suggested syntax for both EOF and the command, gives me this:

```
can't read "uname": no such variable
    while executing
"send "$uname\r" "
    invoked from within
"expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         "


```

and my code to produce that error reads :

```
#!/bin/bash

#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/home/colic/scripts:/bin/grep
cd "/home/$(whoami)/scripts"
zzout="/home/$(whoami)/scripts/zzchkInet.dat"
log="/home/$(whoami)/scripts/zzchkInet.log"
chkBb="/home/$(whoami)/scripts/chkBroad.dat"

#
# mailing list and database details
#
uname='root'
pwd='idideditthisbitbutnothingelse'
#useData=""
hour=$(date +"%H")
day=$(date +"%d")
mon=$(date +"%m")
year=$(date +"%Y")
 
function blockInet {
      expect -d <<- "EOF" 
      exp_internal 1     
      
      spawn telnet wndr3300
      expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         
      expect  {
         "Password"                 { send "$pwd\r" } 
         timeout                    { exit 2 }
             }
      expect { 
      
         ":~#"                     {  send "nvram set filter_rule10=\\\$STAT:\\\$NAME:NoInet\\\$DENY:1\\\$\r"}

             }
       expect {
         "*"                     { send "exit\r" }
             }

EOF

}



blockInet
exit
```

So it appears what looks like a simple change to the EOF syntax has now made my variables out of scope. I confess to not having a clue what's happening here.

---

### Post by steeldriver on 2014-11-30
... adding the - character i.e.

```

/usr/bin/expect -d <<[COLOR=#0000ff]**-**[/COLOR] "EOF" 

```

**should** allow you to tab in the closing EOF

```

        }
        EOF
}

```

but the indenting **must** be done with **tabs** - not spaces

---

### Post by Slatevine on 2014-12-05
> but the indenting **must** be done with **tabs** - not spaces

Didnt work for me, but that could be my editor config. Ill leave it in column 1 for now as it's only an aesthetics issue as far as I can see. It doesnt worry me.

With my earlier version Expect understood my variables and read all the expect commands OK. It just didnt format the slashes string properly. Which of course is no use!

With the amended version (thanks :-)) expect still reads the statements correctly, and now correctly formats the correct string to send to telnet. But it loses scope of my variables. It's only a mild improvement as I need to pass variables to the expect handling.  

How do I fix the loss of variable scope? Has expect lost it's marbles because I used a different syntax?

---

### Post by steeldriver on 2014-12-05
Sorry I don't understand what you mean by variable scope in this context

It appeared from your original post that you wanted to escape your variable strings so that they would be passed literally - if that's not what you intend then I'm sorry we have been at cross purposes and you should ignore my previous posts

---

### Post by Slatevine on 2014-12-09
> 
It appeared from your original post that you wanted to escape your variable strings

That's correct - I wanted the specific variable containing the slashes to be passed correctly to telnet by Expect. 

So I pass the string directly without using a variable, like this:

```
     
send "nvram set filter_rule10=\\\$STAT:1\\\$NAME:NoInet\\\$DENY:1\\\$\r" 
```

The above works correctly. All that I have changed to make it work, as per your suggestion, is this syntax :

```
      expect <<EOF 
```

to this

```
/usr/bin/expect -d <<[COLOR=#0000ff]**-**[/COLOR] "EOF"
```

So, as far as i can see, that one change has made the slashes string work as desired. 

However that same change has had the unwanted side effect of making variables within the Expect -d>>EOF loop out of scope. So, see the variables $uname and $pwd in my script here:

```
function blockInet {
      expect -d <<- "EOF" 
      exp_internal 1     
      
      spawn telnet wndr3300
      expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         
      expect  {
         "Password"                 { send "$pwd\r" } 
         timeout                    { exit 2 }
             }
      expect { 
      
         ":~#"                     {  send "nvram set filter_rule10=\\\$STAT:\\\$NAME:NoInet\\\$DENY:1\\\$\r"}

             }
       expect {
         "*"                     { send "exit\r" }
             }

EOF

}
```

Well now they are not recognised, as in :

```
can't read "uname": no such variable
    while executing
"send "$uname\r" "
    invoked from within
"expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         "
```


That is, with the change you suggested, my variables are no longer recognised **"can't read "uname": no such variable"**. Prior to that change, $uname and $pwd were both correctly interpreted to be the values I put in them earlier in the script (which are obviously the telnet username and password). But now they are not recognised as variables - so I cant logon to telnet unless I hard code the string in place of variables (which I cant do as they change).

Not sure if Ive explained well enough? There are more detailed traces of what Im saying a couple of posts back.

---

### Post by steeldriver on 2014-12-09
Oops sorry I missed that you needed to expand the $pwd shell variable - in that case, the solution of using a quoted "EOF" will not work.

Try reverting to the UNquoted EOF and then simply adding additional escaping in the send string:

```

      send "nvram set filter_rule10=**\\\\\**$STAT:1**\\\\\**$NAME:NoInet**\\\\\**$DENY:1**\\\\\**$\r"

```

The first \ escapes the second; the third \ escapes the fourth; the fifth \ escapes the $ so that $STAT, $NAME, $ are treated as literals instead of shell variables.

---

### Post by Slatevine on 2014-12-09
Well that sort of brings me back full circle! OK so now my variables are interpreted, but I get too many slashes. 

My problem with all variants was always either too many or not enough slashes as you'll see from earlier posts.

```
\r\nEnter 'help' for a list of built-in commands.\r\n\r\nroot@Paul:~#"
can't read "STAT": no such variable
    while executing
"send "nvram set filter_rule10=\\$STAT:1\\$NAME:NoInet\\$DENY:1\\$\r""
    invoked from within
"expect { 


```

The above being the output generated by expect resulting from both:

```
function blockInet {
      expect << EOF 
      exp_internal 1     
      
      spawn telnet wndr3300
      expect {
         "login"  { send "$uname\r" }
         timeout                    { exit 1 }
             }         
      expect  {
         "Password"                 { send "$pwd\r" } 
         timeout                    { exit 2 }
             }
      expect { 
      
         ":~#"                     {  send "nvram set filter_rule10=\\\\\$STAT:1\\\\\$NAME:NoInet\\\\\$DENY:1\\\\\$\r"}

             }
       expect {
         "*"                     { send "exit\r" }
             }

EOF

}
```

or the same but using:

```
      expect -d <<- EOF 

```

This is begining to feel like ground hog day!

---

### Post by steeldriver on 2014-12-09
Do either of these work for you

```

      send "nvram set filter_rule10=**\\\\\\\**$STAT:1**\\\\\\\**$NAME:NoInet**\\\\\\\**$DENY:1**\\\\\\\**$\r"

      send "nvram set filter_rule10=**\x5c\\\**$STAT:1**\x5c\\\**$NAME:NoInet**\x5c\\\**$DENY:1**\x5c\\\**$\r"

```

---

### Post by Slatevine on 2014-12-09
```
send "nvram set filter_rule10=**\\\\\\\**$STAT:1**\\\\\\\**$NAME:NoInet**\\\\\\\**$DENY:1**\\\\\\\**$\r"
```

nearly works, although somewhere I lost an extra $ so amended the above to 

```
send "nvram set filter_rule10=\\\\\\\$STAT:2\\\\\\\$NAME:NoInet\\\\\\\$DENY:1\\\\\\\$\\\$\r"
```

which gives 

```
send: sending "nvram set filter_rule10=\$STAT:2\$NAME:NoInet\$DENY:1\$$\r" to { exp6 }

expect: does " " (spawn_id exp6) match glob pattern "*"? yes

```

from expect. The command string now looks correct (thakyou!), but for some reason it has no effect within Telnet. So if I look in telnet after executing the above expect code, I see this:

```
root@Paul:~# nvram get filter_rule10
$STAT:0$NAME:NoInet$DENY:1$$

```

But the code from expect changes $STAT to equal 2. Yet it is still set to 0.

If I simply copy paste the exact string that expect says it generates, less the \r, and hit return I get

```
nvram set filter_rule10=\$STAT:2\$NAME:NoInet\$DENY:1\$$
root@Paul:~# nvram get filter_rule10
$STAT:2$NAME:NoInet$DENY:1$$


```

Now the $STAT value has changed correctly. Yet the apparently same string in expect does nothing. The only difference I can see is the \r which is perhaps not being interpreted correctly. Either that or expect doesnt actually send what it says its sending, or worse still doesnt send anything. Although it does correctly send the username and password.

---

