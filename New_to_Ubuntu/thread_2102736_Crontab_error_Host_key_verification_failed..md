---
title: "Crontab error: Host key verification failed."
date: 2013-01-08
forum: New to Ubuntu
---

### Post by venkia9 on 2013-01-08
Hi,

when i try to run a crontab to reboot remote machine i am getting error : [COLOR=#222222][FONT=arial]Host key verification failed.

i have 2 machines machine1 , machine 2
currently i am login to machine1 and add a crontab in machine1 as 
10 * * * *  ssh machine2 "sudo -S reboot < password.txt "
i got this error

anyone suggest me about this error    
[/FONT][/COLOR]

---

### Post by Cheesemill on 2013-01-08
Have you set up key authentication?
What is the output of:
```
ssh -vvv machine2
sudo ssh -vvv machine2
```
I'm guessing that as you are using the root crontab ssh is looking for keys in /root/.ssh/ whereas you actually want it to look in your users ~/.ssh/ directory

---

### Post by Lars Noodén on 2013-01-08
It's because you do not have the remote host's key in that user's [known_hosts](http://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files) file.  You could also put the remote host's key in the global known_hosts file, /etc/ssh/ssh_known_hosts, but the easy way would be to just run the login script manually as that user and let ssh create the file automatically.  

If that user is root, you can do it this way:

```

sudo -u root ssh machine2 

```

That will work for other users, too.  Just subsitute in the right user.  When the connection is made for the first time, ssh will create the ~/.ssh/known_hosts file for you and add the host key.  From then on any time you connect to a new host, you have the option of adding the key automatically to the file.

---

