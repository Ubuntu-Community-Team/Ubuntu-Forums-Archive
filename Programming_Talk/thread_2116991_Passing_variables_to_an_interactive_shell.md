---
title: "Passing variables to an interactive shell"
date: 2013-02-17
forum: Programming Talk
---

### Post by CaptainMark on 2013-02-17
At work I must now use ssh tunneling for all my internet traffic because the boss has stupidly decided to make the wifi public, (idiot). I have setup passwordless login to my raspberry pi at home and I want to keep my rsa keys password protected

I set a script up on the laptop that makes a ssh tunnel on login and I wanted to use zenity to capture a password from the user, then store it as a variable and pass it to the shell but I dont know if it can be done, I could of course have a terminal open up and request the password but i thought a gui box would look nicer, heres what I have so far```
#!/bin/bash

# wait for wireless connection to be established
while true ; do
    ping -c 1 www.google.com && break
    sleep 2
    done

# get rsa  key password from user
pass=$(zenity --password)

# make tunnel
ssh -D 1999 raspberrypi
# get totally stuck and give up!!
((( use $pass as user input )))
```Obviously I'm stuck on the last line here, can this be done, or is it impossible?

Regards

Mark

---

### Post by steeldriver on 2013-02-17
You could maybe do it with 'expect'? the basic idea would be something like

```

# make tunnel
/usr/bin/expect -c "
spawn *your ssh tunnel command here*
expect \"assword: \"
send \"$pass\r\"
interact"

```Obviously you'd want to put some error traps / cleanup around that - tbh I don't use expect often enough to advise the 'right' way to do it - hope this is enough to get you started though

---

### Post by ofnuts on 2013-02-17
> **steeldriver said:**
> You could maybe do it with 'expect'? the basic idea would be something like

```

# make tunnel
/usr/bin/expect -c "
spawn *your ssh tunnel command here*
expect \"assword: \"
send \"$pass\r\"
interact"

```Obviously you'd want to put some error traps / cleanup around that - tbh I don't use expect often enough to advise the 'right' way to do it - hope this is enough to get you started though
The right way would be to use certificates and just avoid the passwords.

---

### Post by erind on 2013-02-17
> **CaptainMark said:**
> [...]

I set a script up on the laptop that makes a ssh tunnel on login and I wanted to use zenity to capture a password from the user, then store it as a variable and pass it to the shell but I dont know if it can be done

[...]


If I correctly understand your problem, another way would be using *sshpass*:
 
```
pass="$(zenity --password)"

sshpass -p "$pass" ssh user@remote.machine


## To disable host key checking, if needed, use:
sshpass -p "$pass" ssh -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null user@remote.machine

```Note that the above code is the least secure, and as already suggested the best way is to use ssh authentication keys for a passwordless ssh connection.

---

### Post by CaptainMark on 2013-02-18
> **ofnuts said:**
> The right way would be to use certificates and just avoid the passwords.

I don't mean a login password, I have set up password-less authentication but the rsa key is password protected, I don't want people to be easily able to get the laptops private key and use it to login from elsewhere, I have my home partition encrypted using the built in ecryptfs tool during installation, is this sufficient to keep my private key safe then?

---

### Post by ofnuts on 2013-02-18
> **CaptainMark said:**
> I don't mean a login password, I have set up password-less authentication but the rsa key is password protected, I don't want people to be easily able to get the laptops private key and use it to login from elsewhere, I have my home partition encrypted using the built in ecryptfs tool during installation, is this sufficient to keep my private key safe then?
Thats should be enough... unless you are the target of professional spies, I doubt that the random laptop thief would know how to crack your machine or how to use SSH... and if the laptop is stolen you just remove the key from the ~/.ssh/authorized_keys on your Raspberry.

I would be worrying more about other stuff like email and stored ids/passwords in the browser...

---

