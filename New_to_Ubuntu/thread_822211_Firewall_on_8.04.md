---
title: "Firewall on 8.04?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-08
Is there somekind of firewall built in in Hardy 8.04? I've been stuck a few days on this problem. I've upgraded to Hardy 8.04 and now can't access gmail. I'm browsing the web (this site for instance) and google sites too. But I can't get gmail to come up. I've even tried ip 64.233.185.106 in the addressbar but still no go. :confused:

---

### Post by Kronie on 2008-06-08
weird... i am on ubuntu 8.04 with latest updates ff3rc2 and i can go to my gmailinbox.. i also tried it on ff3b5 and it worked too.. i didnt mess around with any security settings and all that..

---

### Post by avtolle on 2008-06-08
> **niceguy123 said:**
> Is there somekind of firewall built in in Hardy 8.04? I've been stuck a few days on this problem. I've upgraded to Hardy 8.04 and now can't access gmail. I'm browsing the web (this site for instance) and google sites too. But I can't get gmail to come up. I've even tried ip 64.233.185.106 in the addressbar but still no go. :confused:
Yes, it is called (as I recall) iptables. Firestarter, which may be installed from the repositories, is a GUI to manage this. 

There are some other threads around about difficulties in getting gmail to come up, have you seen them?

---

### Post by niceguy123 on 2008-06-08
> **avtolle said:**
> Yes, it is called (as I recall) iptables. Firestarter, which may be installed from the repositories, is a GUI to manage this. 

There are some other threads around about difficulties in getting gmail to come up, have you seen them?

Actually I saw very few threads almost none dealing with this problem, which is even more furstating. Why is this happending only to me? 


iptables - How do I run it? 

```
nice@nice-desktop:~$ iptables
iptables v1.3.8: no command specified
Try `iptables -h' or 'iptables --help' for more information.

```

---

### Post by hovzio on 2008-06-08
I wouldnt mess with iptables. (i mean you can.. but in my opinion its easier to use a gui) Try using firestarter, its just a graphical front-end to iptables. You will have to install firestarter.

Are you accessing gmail via Evolution (imaps). If so you will have to allowthe ports associated with imaps.(forgot what they are and cannot access firewall at the moment) 
If you are having problems reaching gmail from your browser; I doubt that it is an issue concerning your firewall. Check all you browser settings. (cookies, scripts etc??)
Maybe try doing a complete reinstall of your browser. Just to test the theory you could try a different browser. (epiphany or so)

---

### Post by Butthead on 2008-06-08
Yes, Hardy does have a firewall built in.

Type in "sudo ufw status" to find out if it's currently loaded or not.

You can also type in "sudo ufw enable" to turn it on, and (consequently?) "sudo ufw disable" turns it off.

---

### Post by bruce928 on 2008-06-09
Hello new to all this ubuntu, tring it out is their a way to have this fire stater thing start on it own?:confused:

---

### Post by hovzio on 2008-06-10
Firestarter does not need to start on its own.. iptables is always running and firesatarter is just a front end to make "adjustments/configurations" to the iptables since doing this manually is rather difficult. Firestarter does the same thing uwf does, personally I prefer firestarter. Try googling iptables. There  is quite a bit on it.

---

### Post by hyper_ch on 2008-06-10
(1) Firestarter is merely a graphical frontend for configuring iptables

(2) Iptables is integrated into the kernel and runs all the time

(3) Very likely you don't need to bother with iptables and firestarter and ufw at all... there's very little reason for altering the default configuration.

(4) with regard to your problem, can you ping the according domain? Can you access other stuff?

---

### Post by bryncoles on 2008-06-10
for bruce928 - i found the following quite useful

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

also there are lots of threads about firewalls and firestarter on ubuntu. i like to read them, they can be quite entertaining, not to mention informative and heated!

---

### Post by The Cog on 2008-06-10
To find out if you have any firewall runnin, use this command:
**sudo iptables -L**
and if you have no firewall rules, you just get three headings with nothing listed under them like this:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

and in this case, a firewall is not the cause of your problems. If you do see rules listed, then a firewall has configured them somewhere. You should find the configuration program that made the rules, but you can clear all the rules with these commands just to prove whether or not those rules are the cause of your problems:
sudo iptables -F
sudo iptables -S
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTOUT ACCEPT
sudo iptables -P FORWARD ACCEPT
Of course I have no idea how to reinstate the rules.

---

### Post by the_doc on 2008-06-10
I didn't find iptables all that difficult to get to grips with, and you only have to write it once as a script or whatever.

---

