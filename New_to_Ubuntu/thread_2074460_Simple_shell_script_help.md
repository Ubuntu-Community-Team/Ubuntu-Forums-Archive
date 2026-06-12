---
title: "Simple shell script help"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by hookitup on 2012-10-21
Hello so I have two questions. Basically I have an Ubuntu  server set up at home so that when I'm at school in my shell scripting class I can just ssh into it as apposed to setting up virtual box every time which is annoying . 

So here is my question: how would I have a script run as soon as I login to the server via ssh?

Like as soon as I log in I want it to tell me the host name or something like that.


Second question . I have a IF_THEN_ELSE script that I call fakelogon
Basically it ask for username and if it's equal to jake then It says  success u have loggin in but if it doesn't equal jake then It says sorry wrong username. 
Basically I want to add the command EXIT aftet it says sorry wrong username exiting in 5 seconds

What would I add to the end of my script to have it wait 5 seconds then EXIT

This is the script I have 
```
#!/bin/bash
echo "enter your username"

If [ "$username" = "jake" ]
then
Echo 'success you are logged in now'
else
echo 'sorry wrong username exiting in 5 seconds'
fi

```


I typed this on my phone so sorry if I made typos and stuff

---

### Post by Hadaka on 2012-10-21
Hi, here is a link to some good simple bash script examples.

[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

included is an example for the sleep command...

```
 sleep 5
```

have fun !!

---

### Post by cipherboy_loc on 2012-10-21
[http://www.linuxquestions.org/questions/linux-server-73/motd-or-login-banner-per-user-699925/](http://www.linuxquestions.org/questions/linux-server-73/motd-or-login-banner-per-user-699925/)

That should help you answer your first question about running a script on login.

---

### Post by papibe on 2012-10-21
Hi hookitup.

For code to be executed at a per-user-basis look into each individual ~/.bashrc. For code to affect  all users check /etc/bash.bashrc. Check [this tutorial]("https://help.ubuntu.com/community/EnvironmentVariables") for more information about bash specific files.

**Howerver**, if I understood correctly, you are trying to build your own security scripts. I would not recommend doing that. Instead, I would recommend securing your server using proven-standards methods.

For instance, to only allow only your user to ssh to your machine, set an 'AllowUsers' rule in your /etc/sshd_config. For instance:
```
AllowUsers youruser
```
As always, set and test this rules from home, so you avoid locking out yourself out of the server in case of a misspelling.

Hope that helps, and let us know how it goes.
Regards.

---

### Post by hookitup on 2012-10-21
I believe everyone has been misunderstood 

I am not trying to secure this server in any way . I am just playing with shell scripts for my class I am currently taking requires us to write shell scripts a d practice random
Stuff .

So basically any user (there's only one and it's myself) that logs into the server I would like to have a script run . Any script from echoing hello world or displaying memory information. 

What file would I edit  In order to have this happen after I log into the server.

---

### Post by papibe on 2012-10-21
> **papibe said:**
> For code to affect  all users check /etc/bash.bashrc
.

---

### Post by hookitup on 2012-10-21
oh sorry. thanks, that works.

---

