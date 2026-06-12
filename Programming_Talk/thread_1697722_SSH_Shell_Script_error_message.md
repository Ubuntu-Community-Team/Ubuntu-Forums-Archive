---
title: "SSH Shell Script error message"
date: 2011-03-01
forum: Programming Talk
---

### Post by theDaveTheRave on 2011-03-01
Hi all,

First off the description of this thread is not good, but I can't think of a better one... so appologies.

I'm writing a pair of shell scripts to ease my wake on lan and SSH process.

The wake on lan script works fine, so now I'm having a go at my SSH script.

here is my code
```

#!/bin/bash
#options to log into server via ssh if required

#first check server is running...

ping -c 3 MyServer
#catch the ping exit code, code = 1 on error, 0 on success
if [[ $? != 0 ]];then #the spaces in the clause are required
	echo WachabeServer not online
	end
#if online give options...
	else
		login #call the login function
fi
exit

#function to login to server
function login(){
				local Options="SSH to Server" "Quit"
				select opt in $Options:do
				#the first option
					if[$opt="Quit"];then 
						echo done
						exit
				#will now exit from script
				#second option to SSH to server
						elif ["$opt="SSH to Server"];then
							ssh -X davem@MyServer
				#catch any erroneous entries
							else
								clear
								echo bad options
							fi	
					}#end

```
I'm going to leave in my comments for good measure.

So I run this script and I get the following output

> 
 ./sshToServer.sh 
PING MyServer.lan (192.168.1.6) 56(84) bytes of data.
64 bytes from MyServer.lan (192.168.1.6): icmp_seq=1 ttl=64 time=0.840 ms
64 bytes from MyServer.lan (192.168.1.6): icmp_seq=2 ttl=64 time=34.1 ms
64 bytes from MyServer.lan (192.168.1.6): icmp_seq=3 ttl=64 time=6.16 ms

--- WachabeServer.lan ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.840/13.712/34.132/14.601 ms

login: Cannot possibly work without effective root


Can someone enlighten me as to what that error message means?

I'm guessing also that I need to run the SSH part of the script (line 31) in another terminal, is that my problem? However I can't find how to do this :confused:

I assume this as otherwise the command to ssh to my server will run in the current terminal and then the script will terminate, which obviously isn't what I want, so how do I get it to do that?

Your help is appreciated.

David

---

### Post by Arndt on 2011-03-01
> **theDaveTheRave said:**
> Hi all,

First off the description of this thread is not good, but I can't think of a better one... so appologies.

I'm writing a pair of shell scripts to ease my wake on lan and SSH process.

The wake on lan script works fine, so now I'm having a go at my SSH script.

here is my code
```

#!/bin/bash
#options to log into server via ssh if required

#first check server is running...

ping -c 3 MyServer
#catch the ping exit code, code = 1 on error, 0 on success
if [[ $? != 0 ]];then #the spaces in the clause are required
	echo WachabeServer not online
	end
#if online give options...
	else
		login #call the login function
fi
exit

#function to login to server
function login(){
				local Options="SSH to Server" "Quit"
				select opt in $Options:do
				#the first option
					if[$opt="Quit"];then 
						echo done
						exit
				#will now exit from script
				#second option to SSH to server
						elif ["$opt="SSH to Server"];then
							ssh -X davem@MyServer
				#catch any erroneous entries
							else
								clear
								echo bad options
							fi	
					}#end

```
I'm going to leave in my comments for good measure.

So I run this script and I get the following output



Can someone enlighten me as to what that error message means?

I'm guessing also that I need to run the SSH part of the script (line 31) in another terminal, is that my problem? However I can't find how to do this :confused:

I assume this as otherwise the command to ssh to my server will run in the current terminal and then the script will terminate, which obviously isn't what I want, so how do I get it to do that?

Your help is appreciated.

David

I think what happens is that the program 'login' is called, and not the function you defined in the script.

---

### Post by theDaveTheRave on 2011-03-01
arndt

Thanks for that.... I didn't realise that there was a command called 'login' :guitar:

In hindsight however it would seem fairly obvious :lolflag:

So a quick change to call the function < MyLogin> and calling it with parentheses after 
```

if [[ $? != 0 ]];then #the spaces in the clause are required
	echo WachabeServer not online
	end
#if online give options...
	else
		MyLogin() #call the MyLogin function
fi
exit

```
has solved that problem,
now I get a different error message

> 
./sshToServer.sh: line 17: syntax error near unexpected token `fi'
./sshToServer.sh: line 17: `fi'


which seems strange!?

and debugging the code would suggest I'm not even getting into the if condition?

so from one problem to the next!

David

---

### Post by Arndt on 2011-03-01
> **theDaveTheRave said:**
> arndt

Thanks for that.... I didn't realise that there was a command called 'login' :guitar:

In hindsight however it would seem fairly obvious :lolflag:

So a quick change to call the function < MyLogin> and calling it with parentheses after 
```

if [[ $? != 0 ]];then #the spaces in the clause are required
	echo WachabeServer not online
	end
#if online give options...
	else
		MyLogin() #call the MyLogin function
fi
exit

```
has solved that problem,
now I get a different error message



which seems strange!?

and debugging the code would suggest I'm not even getting into the if condition?

so from one problem to the next!

David

Some semicolon syntax problem, probably. But I don't get an error when I try your snippet, except that 'end' is not defined.

---

