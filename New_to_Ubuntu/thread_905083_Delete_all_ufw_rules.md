---
title: "Delete all ufw rules"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-30
How can I remove all the ufw rules I have created and return to the defaults?

Thanks in advance!

---

### Post by nicedude on 2008-08-30
I like using Guard Dog to manage IP tables as it is pretty strait forword and easy to use. It can reset all your rules and is a nice GUI to let you set all kinds of rules for standard traffic as well as making custom ones. You can also save your setup after you get it the way you like it to a small config file and then on future PC's you can just load that profile with guard dog and have the same rules as your other PC's if you have several boxes :-)

I like it allot better than firestarter, but you could try that as well if you so choose. They are both in the repos by the way.

Hope that helps you get it under control Travis

---

### Post by pi.boy.travis on 2008-08-30
Sorry, I should have clarified, this is on my server.  No GUIs allowed!

Is there a config file I can delete of something like that?

---

### Post by nicedude on 2008-08-30
Oops I must confess I like GUI's especially for some stuff like IP tables since it is pretty complicated and I didn't feel like getting a brain anurism trying to learn it quick. But I do know there are IP tables configuration scripts out there ( I don't know if anything like that is in the repos but I would look there first ). So I would try finding a script to reset them, someone here might know a command to take them back to default but when I looked at IP tables man page I didn't see one ( but the man page is big and I could have missed it )

Sorry I can't be of more help other than to suggest looking for IP table configuration scripts.

---

### Post by Nepherte on 2008-08-30
You will have to delete every rule on its own. For example, if you denied access to port 22:
```
sudo ufw deny 22
```
you can delete the rule with:
```
sudo ufw delete deny 22
```

---

### Post by _sAm_ on 2008-08-30
All rules you set for ufw are stored in /etc/ufw/maps I don't know myself - but perhaps you could just remove them from it??


And when we talk about ufw; I have a Ubuntu fileserver witch also share a printer. If I enable ufw I can no longer use it from my desktop pc - witch port do I need to open in ufw on both?

---

### Post by boof1988 on 2008-10-26
> **_sAm_ said:**
> All rules you set for ufw are stored in /etc/ufw/maps I don't know myself - but perhaps you could just remove them from it??


And when we talk about ufw; I have a Ubuntu fileserver witch also share a printer. If I enable ufw I can no longer use it from my desktop pc - witch port do I need to open in ufw on both?

I searched for "ufw" and "rules" and this thread came up.  I looked through the results of (command input):
```
info ufw
```
and found out that the file that contains the user rules (part of iptables) is
```
/var/lib/ufw/user.rules
```

I believe that ufw is a front-end of iptables so the rules aren't in  /etc/ufw/  ...dunnoh.

Hope this helps someone.

---

### Post by slapper on 2009-04-22
i am testing ufw.. the rules are stored in 
/var/lib/ufw/user.rules
so you can play with that file..
if you are familiar with iptables you mustn't have any problems :P:P

---

### Post by rusty0101 on 2009-07-31
If I were familiar with iptables I wouldn't be looking for a solution to the following problem:

I have a series of rules that when I do a 'ufw stat' come back as:

```
80:tcp                     DENY    74.55.158.66
80:udp                     DENY    74.55.158.66
80:tcp                     DENY    74.55.158.67
80:udp                     DENY    74.55.158.67
```
[INDENT][FONT=Courier New]...
[/FONT][/INDENT]I would like to replace them with the following ufw rule:
```
ufw deny from 74.55.158.0/24
```

Now adding that rule is simple. However deleting the former rules has been nothing but agrivation. ufw on it's own won't take a command such as:
```
ufw delete 80:udp DENY 74.55.158.67
```

So I try the way that I think that rule was built, with the appropriate delete:
```
ufw delete deny proto udp from 74.55.158.66 to any port 80
```

and while ufw responds with:
```
Rules updated
```

The rule is still in the table.

What I am looking for is a function that will give me back the ufw command that was used to generate the iptables deny entry, without having to go through using iptables syntax to modify the tables entry.

I emphaticly don't know the silly syntax for iptables, and since ufw exists and can supposedly modify the commands, it certainly would be nice if it would tell me what the 'ufw' rules were, rather than a dump from iptables.

thanks.

---

### Post by Wizard_Yo on 2009-09-03
slapper, thank you for the file location.  I had somehow added a rule by accident (one that didn't show up at all in my command history) that simply refused to delete.  It would only say "Rule updated" and never deleted.



rusty0101, your trouble should clear up with the following two commands:

sudo ufw delete deny from 74.55.158.66 to any port 80
sudo ufw delete deny from 74.55.158.67 to any port 80


viva la Ubuntu ~!
:popcorn:

---

### Post by kansasnoob on 2009-09-03
```
sudo ufw default deny
```

```
sudo ufw default allow
```

```
sudo ufw enable
```

---

### Post by jasonkf1 on 2009-09-23
Ok, so I was looking to do the same that the original thread mentioned "Delete all ufw rules" and I hadn't seen any clear solution so here goes.  After reading man pages, web pages, and testing this is what I have as a working solution.  This is in the event you don't want to manually delete each rule using ufw.

Tested On: Ubuntu 8.04 LTS Server 

ufw keeps it's user created rules in file /var/lib/ufw/user.rules

open this file with the text editor of your choice 

```
sudo nano -w /var/lib/ufw/user.rules
```the file contents should look similar to below

```
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
### RULES ###

"Your Rules Here"

### END RULES ###
-A ufw-user-input -j RETURN
-A ufw-user-output - j RETURN
-A ufw-user-forward - j RETURN
COMMIT
```the user created rules will be between the "### RULES ###" and "### END RULES ###" comments.  Make sure **NOT** to delete the lines above the "### RULES ###" they are needed. (they refer to the chains created in /etc/ufw/before.rules)  Also, do **NOT** delete the lines under the "END RULES" comment also important.

Now you should have a file like below

```
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
### RULES ###



### END RULES ###
-A ufw-user-input -j RETURN
-A ufw-user-output - j RETURN
-A ufw-user-forward - j RETURN
COMMIT
```The next time you disable/enable ufw it will not load the previous rules, however the rules will still exist in iptables as ufw is only a front-end to iptables.  There is a fair chance you may want to clear this to rebuild your rules.  You can do so with the following commands.

```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X
```what this does is sets the INPUT, OUTPUT, and FORWARD chains to accept (I believe this is default for many installs but correct me if I'm wrong.) Then it flushes all chains and deletes the user-defined chains.

Now if you issue command

```
sudo iptables -L
```you should see the following

```
Chain INPUT (policy ACCEPT)
target        prot   opt   source                    destination

Chain FORWARD (policy ACCEPT)
target        prot   opt   source                    destination

Chain OUTPUT (policy ACCEPT)
target        prot   opt   source                    destination
```enabling ufw after removing the user rules will repopulate iptables because when ufw is run the files are evaluated as such:

[LIST=1]
[*] /etc/ufw/before.rules
[*]/var/lib/ufw/user.rules
[*]/etc/ufw/after.rules
[/LIST]
**ufw** will read in /etc/ufw/sysctl.conf on boot when enabled. To change this behavior, modify /etc/default/ufw.

And remember for best security practice always deny first then allow.. If it were a boat wouldn't you rather start with no holes?

So that concludes my first post in the forum, I hope it is helpful.

---

### Post by tanoloco on 2010-04-15
Hi guys,

for those who can use a gui there's a gui configuration tool named gufw you can download from 

[https://launchpad.net/gui-ufw](https://launchpad.net/gui-ufw)

or by repository but at the moment I write this is older and somehow doesn't work properly on my karmic while the newer one downloaded from the above url does.

Anyhow it has an option under Edit > Reset Configuration which seems to delete all rules and reset the firewall.

Not tested at this time.

I don't know how to do it through a shell but I thought there's must be a command like

```
sudo ufw reset
```so I googled and found this link
[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/436608](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/436608)

but the above command doesn't work here to me.

ufw version: 0.29-4ubuntu1
gufw version: 10.04.3-0ubuntu2
kernel: 2.6.31-20-generic (karmic)

Hope this can help

---

