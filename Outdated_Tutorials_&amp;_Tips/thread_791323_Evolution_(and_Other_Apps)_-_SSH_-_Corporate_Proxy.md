---
title: "Evolution (and Other Apps) - SSH - Corporate Proxy"
date: 2008-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by AcidHawk on 2008-05-12
I needed an SSH server as the Corporate proxy does not have socks enabled.  If socks was enabled I would simply have configured tsocks to point to that server.

1.Get access to the ssh server.
2.Login using
```

ssh acidhawk@10.0.0.2

```
3.Test connection to my mail server from the ssh server (if this didn't work I would have asked the sysadmin to enable socks support on the corporate network proxy.... )
```

telnet mail.acme.com 25 (smtp to send)
telnet mail.acme.com 110 (pop3 to receive)

```
4.End ssh session
5.Download tsocks to my local machine
```

sudo apt-get install tsocks

```
6.Change /etc/tsocks.conf to point to my local machine
```

change server = 192.168.0.1 to server = 127.0.0.1

```
6.From a local shell setup ssh tunnel
```

ssh -D 1080 acidhawk@10.0.0.2

```
This opens a shell connection to 10.0.0.2 if you close this shell your ssh tunnel will also close 
7.From a new shell on your local machine run
```

tsocks evolution &

```

I didn't like having to type my password every time I connected so I did the following (which I got from [http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html) ):

1.From a cmd shell on your local machine run
```

ssh-keygen -t rsa 

```
2.Change to your homedir and then go to the .ssh dir (you need to copy the generated key to the ssh server)
3.Copy the id_rsa.pub file to your homedir on the ssh server by typing
```
 
scp id_rsa.pub acidhawk@10.0.0.2:./id_dsa.pub

```
4.Connect to the ssh server 
```

ssh acidhawk@10.0.0.2

```
5.Run the following commands to add your public key to a file that will allow you kay access to the ssh server
```

acidhawk@10.0.0.2:~$ touch authorized_keys2
acidhawk@10.0.0.2:~$ chmod 600 authorized_keys2
acidhawk@10.0.0.2:~$ cat ../id_rsa.pub >> authorized_keys2
acidhawk@10.0.0.2:~$ rm ../id_rsa.pub

```
6.Exit from the ssh server and run the following
```

ssh -l acidhawk 10.0.0.2

```
7.After you have entered your passphrase you will be connected. Next time you run ssh acidhawk@10.0.0.2 you will not be asked for your password.
8.Next I didn't want the ssh shell to be opened (I wanted it to run in background) so now I run the following to setup the tunnel
```

ssh -N -f -D 1080 acidhawk@10.0.0.2

```
9.Check that ssh is still running 
```

ps -ef | grep 10.0.0.2

```
(you should see the command you just ran)

My next trick is to automate the tunnel setup if I am at this particular office.  I don't want to run this when I am at home so I investigated editing my .bashrc as well as looked at setting the tunnel up from a startup script.  Neither of these seemd like a good idea as I would have to still open a shell to run evolution like so (tsocks evolution &).  I decided to create a script to run all the apps I wanted to be able to go through this tunnel (Evolution, RapidSvn, Eclipse etc)  The following is the first attempt at this script.  What I will do now is change all my menu launchers to the following
```

myLauncher evolution      -or -      myLauncher rapidsvn     etc.

```

myLauncher look as follows
**Update:** Now check if my 3G is connected and determine if I need to use tsocks when launching an app
```

#!/bin/sh

MYIP=`ifconfig eth0 | grep 'inet addr:' | cut -d: -f2 | awk '{print $1}'`

if [ "$1" = "" ]; then
	echo "Usage: $0 <ProgramName>"
elif [ "$1" = "stop" ]; then
	pid=`ps -ef | grep 10.0.0.2 | grep -v grep | awk '{print $2}'`
        if [ "$pid" != "" ]; then
	        kill -9 $pid 
        ]
else
        # Check if I am at ClientABC (My Address here is always 192.168.99.10)
	if [ "$MYIP" = "192.168.99.10" ]; then
		pid=`ps -ef | grep 10.0.0.2 | grep -v grep | awk '{print $2}'`
		if [ "$pid" = "" ]; then
			echo "Setting up SSHTunnel for ClientABC..."
			ssh -N -f -D 1080 acidhawk@10.0.0.2
	        fi
                #Chech if my 3G is connected
                PPP=`ifconfig ppp0 >/dev/null 2>&1`
		if [ $? -ne 0 ]; then
			echo "NO 3G detected - Launching $1 with \"tsocks\""
			tsocks $1 >/dev/null 2>&1 &
		else 
			echo "3G detected - Launching $1 without \"tsocks\""
			$1 >/dev/null 2>&1 &
		fi

        #I am not at any client so will not use tsocks
	else 
		$1 >/dev/null 2>&1 &
	fi
fi

```

Basically what I am looking to see if I am at a particular client (I do this by checkin my ip address).  I then check if there is already a PID for my ssh tunnel if there is I will not setup the tunnel again.  However , if I am at ClientABC I will launch my app ($1) with tsocks.  I can use this script at home as my ip address is different and I will then launch my app as simply $1.

Hope this helps
Acidhawk

---

