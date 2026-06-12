---
title: "un-routing ports"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by Hkon_Ingi on 2015-04-23
Hi, few days ago I put up a unbuntu server and apache2, redmine, postgresql and tomcat7 installed on it, when i went to the ip address/redmine I would get up redmine login, okay, but when I entered my ip address:8080 I got tomcat because of its default settings to listen to port 8080, changing it to listen to 80 didnt quite work, even with the auth yes (dont remember the whole line), so I redirected everything on port 80 to go to port 8080 with iptaples, I put in three iptaples lines, but I dont remember them, it was reject and accept and redirect or something, but anyway after that, I got tomcat to work without having to put :8080 at the back of the address, but now redmine doesn't work and i think its because of the rerouting of porst, because it worked before I changed that. So my question is, how do I remove the redirect of ports and get it to be normal again. Hope this is readable as english is not my first language. Any suggestions are appreciated, even if they are about how I can get redmine working again with the routed ports. Thank you!

---

### Post by nerdtron on 2015-04-23
Since you are not also sure on the iptables you have inputted, you list it by the following commands.
```
sudo iptables -L
sudo iptables -L -t nat
```

If you want to reset iptables to default:
```
sudo iptables -F
```

output should be like this: (empty)

```

sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination       
```

---

### Post by Hkon_Ingi on 2015-04-23
sudo iptables -L -t nat

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             anywhere             tcp dpt:http redir ports 8080

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
```

And if I try the sudo iptables -F

```
sudo iptables -F iptables v1.4.12: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
iptables v1.4.12: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
```

I dont get the error message if I enter the command as root, but nothing changes

---

