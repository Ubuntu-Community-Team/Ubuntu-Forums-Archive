---
title: "Bash Scripting Help, how to use external file for variables"
date: 2013-09-10
forum: Programming Talk
---

### Post by greavette on 2013-09-10
This probably isn't the correct forum for this but these Forums have a lot of knowledge so I thought I would give this a shot.

I'm working on a bash script for a linux thin client where the script will check if the Thin Client is connected to the Virtual Machine.  If it's not the script will reconnect to the VM.  I know I can load up the script (like I've done so far) with the various IP addresses.  What I'd like to do instead is list my variables of Hostname and their IP Address in a config file and then have my script check the hostname of the current computer, and find the hostname in the config file and use the IP Address. So far I've got it working where it reads the hostname and finds the IP to use based on the case statement without using a config file. This is what I have so far. 


```
#!/bin/sh
# Check if rdesktop is running
LOGFILE=/home/rpitc/scripts/check.log
read var < ipfile
THISHOST=$(hostname)
if pgrep rdesktop > /dev/null
then
        echo "$(date "+%m%d%Y %T") : rdesktop is already running." >> $LOGFILE$
        exit 0
else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        case $THISHOST in
          (rpiA) rdesktop -z -u user -p password 10.100.100.10;;
          (rpiB) rdesktop -z -u user -p password 10.100.100.11;;
          (rpiC) rdesktop -z -u user -p password 10.100.100.12;;
        esac
        exit 0
fi
```


Right now my code is not using the line: read var < ipfile

So I would like list all my server IP's in the ipfile like this:


```
rpiA="10.100.100.10"
rpiB="10.100.100.11"
rpiC="10.100.100.12"
```


And then modify my code to reference the variables in ipfile in my script. I'm assuming I wouldn't use a case statement any longer, probably a for loop.

Any assistance you can give me on how best to accomplish this task would be greatly appreciated.

Thank you.

---

### Post by scbingham on 2013-09-10
I haven't scripted for years but something like this might work:

If your ipfile was a CSV (Comma Separated Value) file like: 

rpiA,10.100.100.10
rpiB,10.100.100.11
rpiC,10.100.100.12

Test script:

#!/bin/bash
while IFS="," read host ip
do
         echo "Host: $host has address: $ip"
done < ipfile

Output would be:

Host: rpiA has address: 10.100.100.11
Host: rpiB has address: 10.100.100.12
Host: rpiC has address: 10.100.100.13

IFS means Internal Field Separator, in this case a comma. Choose your own variable names after the 'read' command.

Obviously in the 'while' loop you would do your testing.

It would be interesting if this is of any help to you.

---

### Post by Crusty Old Fart on 2013-09-10
You have this:
```

else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        [B][COLOR=red]case $THISHOST in
          (rpiA) rdesktop -z -u user -p password 10.100.100.10;;
          (rpiB) rdesktop -z -u user -p password 10.100.100.11;;
          (rpiC) rdesktop -z -u user -p password 10.100.100.12;;
        esac[/COLOR][/B]
        exit 0
fi

```
You could replace the **[COLOR=red]red[/COLOR]** lines above with the **[COLOR=blue]blue[/COLOR]** lines below as follows:
```

else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        [B][COLOR=blue]ip_string=$(grep $THISHOST ipfile)
        ip_addr=${ip_string#* }
        rdesktop -z -u user -p password ${ip_addr};;[/COLOR][/B]
        exit 0
fi

```
In order for this to work, your ipfile must be formatted like this:
```

rpiA 10.100.100.10
rpiB 10.100.100.11
rpiC 10.100.100.12

```
NOTE: All bash global environment variables are named using ALL UPPERCASE CHARACTERS. In order to prevent modifying the value of one or more of these important variables unintentionally, local variables within scripts should not be named using all uppercase characters. For example: THISHOST should be named ThisHost, thishost, this_host, or something similar, likewise for: LOGFILE.
Have Fun,

Crusty

---

### Post by mörgæs on 2013-09-10
> **greavette said:**
> This probably isn't the correct forum for this...

... so moved to Programming Talk.

---

### Post by btindie on 2013-09-10
With a config file containing something like
```

MY_HOST="1.2.3.4"

```
you can then use the following to get the variable if the output from "hostname -s" was "my-host".
```

#!/bin/bash

[ -f config ] && . ./config

# need to convert - to _ as you can't have it in variable names
THISHOST=$(hostname -s | sed -e 's/-/_/g' | tr '[:lower:]' '[:upper:]')

if [[ -n ${!THISHOST} ]]; then
  echo ${!THISHOST}
fi

```

It uses [bash indirect variables]("http://tldp.org/LDP/abs/html/ivr.html").

---

### Post by greavette on 2013-09-21
Hello,

Thank you all for the replies.  I've successfully been able to connect to the virtual machine of my choice using the code:

```
else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        ip_string=$(grep $THISHOST ipfile)
        ip_addr=${ip_string#* }
        rdesktop -z -u user -p password ${ip_addr};;
        exit 0
fi
```

I will test the other suggestions and reply back with my results as well.

But I do have a further question for this forum.  What if I wanted to add in more variables, like the Userid.  How would I change this bash script to read in two variables to assign and IP Address and Userid to the rdesktop instruction?

And what does my ipfile need to look like to set these two variables by hostname?

Thank you.

---

### Post by Vaphell on 2013-09-21
I'd go with something like this, using sourcing. Each server cfg is in a separate file, script finds all cfgs and creates convenient menu for bonus points.

cfg.sh: 
```
#!/bin/bash

cfg_files=( *.cfg )  # create array of all *.cfg files
select h in "${cfg_files[@]%.cfg}"; do break; done  # menu consists of cfg names with extension stripped
source "$h.cfg"   # load variables from selected cfg file

echo "${user}:${password}@${host}"
```
server1.cfg
```
host=heaven
user=god
password=amen
```
server2.cfg
```
host=rome
user=caesar
password=ave
```

how it works
```
$ ./cfg.sh 
1) server1
2) server2
#? 1
god:amen@heaven
$ ./cfg.sh 
1) server1
2) server2
#? 2
caesar:ave@rome
```

and if you want to stay with a single flat file that looks like this
```
heaven god amen
rome caesar ave
```

```
$ read h; read -r host user pw < <( grep "$h" servers.txt ); echo "$host / $user / $pw"
rome
rome / caesar / ave
```

---

### Post by Crusty Old Fart on 2013-09-21
[COLOR=red][s][COLOR=black]Hmmm...Since this thread has become somewhat of a contest to see how many different ways we can write this script, I thought this was a good time bring in some awkological awkumen...sorry, couldn't resist.[/COLOR][/s]** <-- Edit: Pretty bad idea on my part. I should have paid more attention to what Vaphell was doing with the read command at the bottom of his post directly above.**[/COLOR]

Also, in this post, pursuant to good programming practices, I'm changing the variable name: THISHOST to: ThisHost...couldn't resist that either.
> **greavette said:**
> ...What if I wanted to  add in more variables, like the Userid.  How would I change this bash  script to read in two variables to assign and IP Address and Userid to  the rdesktop instruction?
```
else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        [B][COLOR=red]ip_string=$(grep $THISHOST ipfile)
        ip_addr=${ip_string#* }[/COLOR][/B]
        rdesktop -z -u user -p password ${ip_addr};;
        exit 0
fi
```

You could replace the **[COLOR=red]red[/COLOR]** lines in the code box above, with the **[COLOR=blue]blue[/COLOR]** lines in the code box below.
The **[COLOR=green]green[/COLOR]** lines are included for your testing enjoyment. :cool:
```
else
        echo "$(date "+%m%d%Y %T") : rdesktop has Stopped. Attempting to resta$
        [B][COLOR=red][s][COLOR=blue]string=$(grep $ThisHost ipfile)[/COLOR][/s]
        [s][COLOR=blue]host=$(echo $string | awk  '{ print $1 }')[/COLOR][/s]
        [s][COLOR=blue]ip_addr=$(echo $string | awk '{ print $2 }')[/COLOR][/s]
        [s][COLOR=blue]userid=$(echo $string | awk '{ print $3 }')[/COLOR][/s]
        [s][COLOR=blue]var_1=$(echo $string | awk '{ print $4 }')[/COLOR][/s]
        [s][COLOR=blue]var_2=$(echo $string | awk '{ print $5 }')[/COLOR][/s] <-- Edit replace all the struck out lines above with the following single line. Hat tip to Vaphell for setting me straight here.[/COLOR]
        [COLOR=blue]read -r host ip_addr userid var_1 var_2 < <( grep "$ThisHost" ipfile )[/COLOR]

[COLOR=green]# ~~~ And now, for your testing pleasure: ~~~
        echo "Host = $host"
        echo "IP Addr = $ip_addr"
        echo "User ID = $userid"
        echo "Variable One = $var_1"
        echo "Variable Two = $var_2"[/COLOR][/B]

        rdesktop -z -u user -p password ${ip_addr};;
        exit 0
fi
```


> **greavette said:**
> ...And what does my ipfile need to look like to set these two variables by hostname?

Thank you.
It needs to look something like this:
```

rpiA 10.100.100.10 UseridA VariableOneA VariableTwoA
rpiB 10.100.100.11 UseridB VariableOneB VariableTwoB
rpiC 10.100.100.12 UseridC VariableOneC VariableTwoC

```
...and you're mighty welcome.
> **Vaphell said:**
> I'd go with something like this, using sourcing. Each server cfg is in a separate file, script finds all cfgs and creates convenient menu for bonus points...

Pretty sexy, Vap.
You never disappoint, Sir. :cool:

---

### Post by Vaphell on 2013-09-21
thanks ;-)

as I mentioned earlier *read *is all you need.
wasteful this
```
string=$(grep $ThisHost ipfile)
host=$(echo $string | awk  '{ print $1 }')
ip_addr=$(echo $string | awk '{ print $2 }')
userid=$(echo $string | awk '{ print $3 }')
var_1=$(echo $string | awk '{ print $4 }')
var_2=$(echo $string | awk '{ print $5 }')
```
becomes this
```
$ choice=rpiB
$ **read -r host ip user var1 var2 < <( grep "$choice" servers.txt )**
$ echo [$host][$ip][$user][$var1][$var2]
[rpiB][10.100.100.11][UseridB][VariableOneB][VariableTwoB]

```

---

### Post by Crusty Old Fart on 2013-09-21
> **Vaphell said:**
> thanks ;-)
as I mentioned earlier *read *is all you need.
wasteful this...

As I was preparing my last post, my inner child had this funny feeling that you would show up and change his diaper. :D
Thanks.

Crusty

---

### Post by greavette on 2013-09-25
Wow! This works great guys. Thanks very much for all your help with this script.  Very much appreciated.

---

