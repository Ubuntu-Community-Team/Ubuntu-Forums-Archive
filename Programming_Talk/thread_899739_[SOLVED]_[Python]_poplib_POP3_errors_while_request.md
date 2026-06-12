---
title: "[SOLVED] [Python] poplib POP3 errors while requesting inbox; also how to get sender's"
date: 2008-08-24
forum: Programming Talk
---

### Post by MaxIBoy on 2008-08-24
Okay, I'm planning to run a home server with a possibly changing IP address. I'm trying to rig up a combination of scripts that checks my email inbox every five seconds, and if needed, sends me an email with the IP of the server. All I should have to do is send myself an email with the subject line "give me IP," and the script will log into my account, see the email, and send another one with the IP of the server (as if I'd sent it myself.) I'm implementing this with a shell script that runs a Python script every five seconds. Here's the shell script:

```
#! /bin/bash
cd '/home/maxtothemax/Documents/ifconfig_email'


#make sure that ifconfig.out exists, then remove it
ls>ifconfig.out #make sure that the next command won't crash if ifconfig.out
				  #doesn't exist.
rm ifconfig.out 


ls>ip.out
rm ip.out





#main loop

shouldContinue=1
wasConnected=1 #This is an assumption. It's a safe assumption, but if you're not on the Internet 
#when this script is first run, you're going to have to manually ask for the ip address.

while [ $shouldContinue ]; do

	#This section determines if there is an Internet connection. 
	#This is to avoid running the lynx command and the Python script if the connection got interrupted.

	ifconfig | grep "inet addr" > ifconfig.out 
	#If there is an Internet connection, ifconfig.out looks something like this: 
	#           inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
	#          inet addr:127.0.0.1  Mask:255.0.0.0
	#If there is no Internet connection, ifconfig.out looks like this: 
	#          inet addr:127.0.0.1  Mask:255.0.0.0

	wcOutput=$(wc -l ifconfig.out)

	rm ifconfig.out

	isConnected=${wcOutput:0:1} #isConnected will be 1 if there's no Internet, and 2 if there is.
	let isConnected=isConnected-1 #Make isConnected a more traditional boolean



	#This section deals with two different Python scripts, and is the "meat" of the shell script.
	#reply_if_needed.py checks a certain email address to see if the IP address has been requested. 
	#If so, it sends an email to an address containing the contents of ip.out.
	#reply_definitely_needed.py sends the email without checking if it's been requested.
	#reply_definitely_needed.py is used if this shell script determines that it's just had Internet
	#restored after an outage. This works for all situations, because the only time an IP address 
	#changes is during an outage. (NOTE: the accuracy of this depends on whether the length of the outage
	#is less than five seconds, which is how often this loop runs.)
	if [ $isConnected ]; then
		lynx -dump whatismyip.com | grep "Your IP Address Is " > ip.out
		if [ $wasConnected ]; then
			shouldContinue=$(python reply_if_needed.py) #reply_if_needed will print 0 instead of 1 if it is 
			#instructed to cause this shell script to exit.
		else
			python reply_definitely_needed.py
		fi
	fi
	wasConnected=$isConnected

	date #For some reason the script exits if you don't have at least one echo statement

	sleep 5
done

```



Here's reply_if_needed.py:
```
#This python script is called by a shell script to do the following:
# 1. Check an email account
# 2. If there is an email with the subject line "give me IP," and
# 3. If that email is from a specified email address, then
# 4. Reply to that email with a message containing the IP address of the
#    computer.
#This is intended for running a home server with a non-static IP address.
#If an email is sent from only one, trusted email address, with a specific
#subject line requesting the IP address, it will be replied to with the IP
#address as determined from whatismyip.com.

import poplib


#read in the ip address; this text will go verbatim in an email
#ip.out is from the following command in the bash shell:
#    lynx -dump whatismyip.com | grep "Your IP Address Is " > ip.out
f = open("ip.out", 'r')
ip_address = f.read()
f.close()


#get all the information needed to handle the email address from email_info.dat
# 0. inbox server (must be POP3)
# 1. outbox server (must be SMTP)
# 2. username of the email address that this program will use
# 3. password of the email account that this program will use
# 4. email address to look for requests from, and to respond to
f = open("email_info.dat", 'r')
count = 0
info = []
for line in f:
    info.append((line.partition('=')[2]).partition('/n')[0])
    count += 1


# check the email address specified
# adapted from code found at http://www.informit.com/articles/
# article.aspx?p=686162&seqNum=6
needsReply = False
inbox = poplib.POP3(info[0])
inbox.user(info[2])
inbox.pass_(info[3])
numMsgs = len(inbox.list()[1])
for msgNum in range (numMsgs):
    for msg in inbox.retr(msgNum+1)[1]:
        if msg == "Subject: give me IP":
            needsReply = True
            break
    break

print 1

```



The Python script is obviously not done yet, nowhere near, because I've run into two problems:
[LIST]
[*]I can't find any documentation on how to find the email address of the person who sent a given email.
[*]I get the following error when I run this:
```
Traceback (most recent call last):
  File "reply_if_needed.py", line 28, in <module>
    inbox = poplib.POP3(info[0])
  File "/usr/lib/python2.5/poplib.py", line 84, in __init__
    for res in socket.getaddrinfo(self.host, self.port, 0, socket.SOCK_STREAM):
socket.gaierror: (-2, 'Name or service not known')
Sun Aug 24 13:56:53 PDT 2008

```
[/LIST]


Help on both of these problems would be great.

---

### Post by MaxIBoy on 2008-08-24
I also have a thread on this in the Python forums, if it get answered there first I'll mark this thread as solved.

---

### Post by mike_g on 2008-08-24
O_O you must be in a hurry. 30 minutes is not giving people much time to respond; especially considering the size of your post. I guess then theres no point in anyone here spending their time replying to this then as by now its probably plastered all over the interweb.

---

### Post by MaxIBoy on 2008-08-24
And yes, I'm sorry, I actually am in a hurry, because I need to get this running very soon. I just didn't say that in the original post because I thought it might be impolite.


And no, it's not plastered all over the Internet either. It's just here and in the Python Forums.


I'm very grateful to replies to my question in either forum.

---

### Post by MaxIBoy on 2008-08-24
Okay, I fixed up my partition statements and email_info.dat, now I no longer get errors. However, I still don't know how to get the email address of the person who sent a given email.

---

### Post by MaxIBoy on 2008-08-24
Posting in the Python forums paid off, someone helped me out.
[http://python-forum.org/pythonforum/viewtopic.php?f=3&t=9052&sid=48e497e0707f8db690c97d34fd48853e](http://python-forum.org/pythonforum/viewtopic.php?f=3&t=9052&sid=48e497e0707f8db690c97d34fd48853e)

Thread marked as 'solved.' Thanks anyway to anyone who read this thread.

---

