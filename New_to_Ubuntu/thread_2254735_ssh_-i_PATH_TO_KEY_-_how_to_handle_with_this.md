---
title: "ssh -i PATH_TO_KEY - how to handle with this ?"
date: 2014-11-29
forum: New to Ubuntu
---

### Post by dilbert_one on 2014-11-29
hello 

i have to run a tunneling process 

therefore in need to add ssh credentials .... 

so that i can find it and call it to start a port forwarding process with this line .


i have this 
```

linux-70ce:/home/martin # ssh -p525 -L 7799:127.0.0.1:7799 vhost@www2.myhost.org
The authenticity of host '[www2.myhost.org]:525 ([xxx.yy.zz.www]:525)' can't be established.
ECDSA key fingerprint is 33:1e:c5:d7:22:11:7c:aa:46:be:83:dc:eb:ee:13:00.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '[www2.myhost.org]:525,[xxx.yy.zz.www]:525' (ECDSA) to the list of known hosts.
Permission denied (publickey).
linux-70ce:/home/martin # ssh -p525 -L 7799:127.0.0.1:7799 vhost@www2.myhost.org
Permission denied (publickey).                                                

```

can i use this command 

martin@linux-70ce:~> ssh -i PATH_TO_KEY

and add the path to key 

/home/martin/all_safings/my_backups and so forth

---

### Post by mcduck on 2014-11-29
yes, that's pretty much how you'd do it.

Or you can configure the server, path to key etc  in ~/.ssh/config

[http://nerderati.com/2011/03/17/simplify-your-life-with-an-ssh-config-file/]("http://nerderati.com/2011/03/17/simplify-your-life-with-an-ssh-config-file/")
[http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/]("http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/")

---

### Post by Lars Noodén on 2014-11-29
The full line would be something like this:

ssh -i /some/path/to/some/key -p525 -L 7799:127.0.0.1:7799  vhost****@****www2.myhost.org

Though sometimes Ubuntu will choke if you have more than a few keys in ~/.ssh/ even if you are trying to use just one, so you have to tell ssh to ignore the ones in the keyring.

ssh -i /some/path/to/some/key -o IdentitiesOnly=yes -p525 -L 7799:127.0.0.1:7799 vhost****@****www2.myhost.org

Then once you can log in, I too would recommend looking at the two links that mcduck posted about using ~/.ssh/config
If you would like to see all the options, check the manual page for [ssh_config](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) to see the full range of options.

---

### Post by dilbert_one on 2014-11-29
hello you both 
many many thanks - overwhelming 

you are so supportive and helpful 

many many 
greetings

---

