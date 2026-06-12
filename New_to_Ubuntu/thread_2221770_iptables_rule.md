---
title: "iptables rule"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-05-03
I have a rule that looks like this:
ACCEPT     TCP     --     ANYWHERE       ANYWHERE     tcp dpt:discard

while all of my other rules looks like this:
```
[FONT=Verdana]tcp dpt:p[/FONT][FONT=Verdana]ort#[/FONT]
```

What does this "discard" mean?

---

### Post by SeijiSensei on 2014-05-03
I have no idea.  The word "discard" does not appear in the [manual page for iptables]("http://linux.die.net/man/8/iptables").

By the way, you might want to edit that post with the Advanced editor and tell it not to use smilies.  Also it helps a lot to see the complete rule with interfaces and other items clearly identified. Try using this to display your ruleset:
```
sudo iptables -L -nv
```
The "-n" switch tells iptables not to bother resolving IP addresses to names; the -v switch makes it verbose so the entire rule is displayed like this:
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  14M   13G ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
8038K 6411M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

```
The first rule applies to packets on the "lo" ("localhost") interface.  The next accepts all RELATED,ESTABLISHED replies on any interface.

---

### Post by Doug S on 2014-05-03
Doesn't it just mean port number 9? Meaning, I think the listing was done with port to name conversion, and "discard" maps to port 9, similar to the more familiar ports such as "ssh" mapping to port 22.

---

### Post by Lars Noodén on 2014-05-04
You can see the port mappings in /etc/services or at one of the links listed at the head of that file.  Then if you really want to you can use that to track down the corresponding RFC.  [http://tools.ietf.org/html/rfc863](http://tools.ietf.org/html/rfc863)  But as mentioned, the -n option with iptables will identify the port number explicitly.

---

### Post by sniper8752 on 2014-05-05
So I forgot to save the table, and it seems that it is no longer there when I go to re-create my iptables again.  Another question, though.  How would I add this rule to the beginning:
```
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```
I know you have to do 
```
[COLOR=#333333][FONT=UbuntuMono]-I INPUT ##[/FONT][/COLOR]
```
But I get an error.  Where do I have to place it?  Here is what I do:
```
sudo iptables -A -I INPUT 1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by Doug S on 2014-05-06
You have both the append (-A) and insert (-I) commands on the same line. Just do the insert command:```
sudo iptables -I INPUT 1 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

---

