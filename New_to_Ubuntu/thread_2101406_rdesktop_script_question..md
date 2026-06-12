---
title: "rdesktop script question."
date: 2013-01-04
forum: New to Ubuntu
---

### Post by Kuroda on 2013-01-04
Hi, I have a rdesktop scripting question that will help me out a lot if it is possible.
I work in a company where I monitor and support a lot of servers on 3 different environments.
So, you can imagine what a pain it is to go through each script and change my password in each one. (the three environments are different passwords)
I was wondering if there was a way I could insert a separate `file` to work as my password so I’ll only need to change it once.
For instance
```
rdesktop  -g 1200x850 -d prod.local -u myname -p password1 -T "RSWSVR14.PROD.LOCAL - 10.16.4.63" 10.16.4.63
```
Any help would really be appreciated.

---

### Post by Kuroda on 2013-01-07
Let me try to ask this a different way, maybe I'll get a response.
I have 190 or so separate scripts I use to remote into servers , We change our password every 90 days, I would like to have a "secret file" in place of the -p flag in my script so I'll onlu have to go and change the password once in the file.. making the scripts know where to go look for it.
Does this make any better sense? Any little help would be appreciated.

---

### Post by Stephan H on 2013-01-07
> **Kuroda said:**
> Let me try to ask this a different way, maybe I'll get a response.
I have 190 or so separate scripts I use to remote into servers , We change our password every 90 days, I would like to have a "secret file" in place of the -p flag in my script so I'll onlu have to go and change the password once in the file.. making the scripts know where to go look for it.
Does this make any better sense? Any little help would be appreciated.

Hi,

Not sure if this is what you were looking for but I use Remmina. Comes with a full GUI and I can save several connections with all their details in it.
Password change is easy....

Stephan

---

### Post by HermanAB on 2013-01-07
Howdy,

You need two scripts and a MySQL or PostgresQL database (or just a simple CSV table).

Parameterize the script.  Replace each password and IP address with a Bash variable eg $1 and $2.  This allows you to pass these parameters on the command line.  Then make a database with hostnames, ip addresses and passwords.  Finally, make another little Perl or Bash script that will do a database lookup and call the rdesktop script.  Then you can type something like 'connect server1' and off you go.

---

### Post by Kuroda on 2013-01-07
Stephan, thank you, but Remmina is not what I am looking for, as I run startup scripts embedded in my bash scripts for each server.
Herman has the right idea but I am afraid I will need a little more hand holding as I am not practiced at variables yet. Is there a thread that will explain how to accomplish this, or something very near to it?
Thank you both for responding.

---

### Post by Sean.m on 2013-01-07
Just some quick info on command line arguments and variables. Say I write a script, something similar to your rdesktop example called 'rdpscript.sh':
```

#!/usr/bin/env bash
rdesktop -fz -u username -p $1 $2
```line 2 is the important part here, it basically means 'launch rdesktop in fullscreen (-f) with compression (z) with user (-u) with password (-p) $1 for host $2. This is what [HermanAB]("http://ubuntuforums.org/member.php?u=44990") was talking about. Inside a bash script, variables are substituted for their values when they are prefixed with a '$'. So I write a script called 'myscript.sh' with a variable:
```

#!/usr/bin/env bash
myName=Sean
echo $myName

#call script
$ ./myscript.sh

#output
$ Sean

```The variable 'myName' is substituted for the value 'Sean' when Bash gets to the variable. Bringing that around, the $1 and $2 are argument variables, these are values that are passed into the script at runtime from the command line, ie: 

```
$ ./rdpscript.sh mypassword myhostname
    $0          $1         $2
```When bash executes the script it "tokenizes" (split on the spaces) the commands that you pass to the script and numbers them 1,2,3,4... So inside of the script, $1 corresponds to the value 'mypassword' and $2 corresponds to 'myhostname' because they are the 1st and 2nd arguments passed to the script.

You could have another script that does looks like this. 

```

#!/usr/bin/env bash
password='mypassword'

rdesktop -fz -u username -p $password $1

```This script would take a single argument, which is the hostname of the prospective computer and stores the password in a variable. This way you only have to change the password in one place and can just pass the hostname to the script, like so './myscript myhostname'. Hope this helps. 

If your interested in learning more about bash scripting, take a look at the "Learning Bash by Example" articles here: [http://www.gentoo.org/doc/en/articles/](http://www.gentoo.org/doc/en/articles/) . Hope this helps.[URL="http://www.gentoo.org/doc/en/articles/"]
[/URL]

---

### Post by Kuroda on 2013-01-11
Thank you Sean.m.. it took me a while to figure it out but without your help I would not have.. thanks to everybody.

---

