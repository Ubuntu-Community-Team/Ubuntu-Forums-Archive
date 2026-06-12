---
title: "ssh support script with bash"
date: 2009-11-05
forum: Programming Talk
---

### Post by junke1990 on 2009-11-05
Hey guys

I'm working on a little support script so users can run the script and wait for me to connect to them remotely. This so I don't have to edit there router configs to port forwarding or stuff like that which makes them more vulnerable for attacks. 

couple of questions:
Is it possible to show my MOTD even with the -N option added to the ssh command?

I've set the shell of the support account to noshell is this advice in this case?

and last, any nice tips from people who are doing the same?

```
#!/bin/bash
#
# made by Junke1990
# for supporting the users
#

### connecting to ssh ###
function connect {
  echo "Zorg dat u contact heeft met de beheerder"
  echo "SSH tunnel word opgebouwd"
  ssh server.junke.nl -l support -R 2222:localhost:22 -N -X -Y
}  

if which sshd > /dev/null; then connect
else
  echo "SSH server niet gevonden, nu installeren? [Y/n]"
  read item
  case "$item" in
   y|Y|*) sudo apt-get install openssh-server
        connect;;
   n|N) echo "Zonder kunnen we je niet helpen, Bye Bye";;
  esac 
fi


```

---

