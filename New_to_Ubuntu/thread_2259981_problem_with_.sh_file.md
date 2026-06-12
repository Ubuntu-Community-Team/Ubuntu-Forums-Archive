---
title: "problem with .sh file"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by Dasder_Letzte on 2015-01-08
Hello all,

I'm trying to run a file in terminal: 'vpn_install.sh', and although I use sudo command and even entered su, terminal keeps requiring 'super user privileges'. What am I doing wrong?

'Allow to run' box in file properties is checked by default.

Thanks for your help!

D

PS: by the way, I'm also still looking for a way to configure my touchpad (elantech on acer aspire e5-511), cf [thread]("http://ubuntuforums.org/showthread.php?t=2259687")

---

### Post by Holger_Gehrke on 2015-01-08
You should take a look at the contents of the .sh-file; files with this extension are (normally) shell scripts. Could be it's trying to access something that's just not there but assumes instead that it doesn't have the rights it needs.

---

### Post by Dasder_Letzte on 2015-01-08
hmm, could be the solution lies right on top of the whole thing, it reads:

> WHOAMI=`id | sed -e 's/(.*//'`
if [ "$WHOAMI" != "uid=0" ] ; then
    echo "Sorry, you need super user access to run this script."
    exit 1
fi


what is my uid with su/sudo? what do I need to do in order to get into the correct (probably "uid=1") mode?

thanks so far

---

### Post by kerry_s on 2015-01-08
are you doing: **sudo su**
to become root?

---

### Post by Dasder_Letzte on 2015-01-08
I do: even if I see myself working as root@mypc... I still get: "sorry, you need super user access..."

---

### Post by yancek on 2015-01-08
Have you verified the file is executable?  Usually you will just get a Permission Denied in that case.  Use the command below in the directory in which the file resides.

ls -l vpn_install.sh

---

### Post by kpatz on 2015-01-08
I just copied and pasted your script snippet and ran it as my normal user and as sudo and it worked like it's supposed to.  When run as sudo it returns uid=0, so you shouldn't get that message.

Post the output of these commands (copy & paste into your terminal):

```

id | sed -e 's/(.*//'

```
and
```

sudo id | sed -e 's/(.*//'

```

Also, what exactly are you typing into the terminal to run the script?  Assuming you're in the directory that the script is in, you'd want to use:
```

sudo ./vpn_install.sh

```

---

### Post by Dasder_Letzte on 2015-01-08
did that, still same result. note the command only worked without file extension

edit: sorry. wanted to attach img

---

### Post by steeldriver on 2015-01-08
Generally, *nix does not consider the file extension to be separate from the rest of the filename - so "without file extension" you are actually executing a different file

---

