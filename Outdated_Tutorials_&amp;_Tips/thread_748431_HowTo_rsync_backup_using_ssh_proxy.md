---
title: "HowTo: rsync backup using ssh proxy"
date: 2008-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by slightcrazed on 2008-04-07
OK - so the first thing that I'm going to be criticized for is using the term 'proxy'. Yes, technically what I'm about to describe does not involve a true 'proxy' in normal terms, but this was the best title I could come up with. 

About 2 months ago I ran into a situation where I had to set up a mirror between 2 machines that, as luck would have it, couldn't directly talk to each other. The problem was that the data I was trying to mirror was on a box at a site that did not allow direct outside access; everything was funneled through a squid proxy.

I spent about 2 weeks trying to find a solution, which mainly involved goog'ling until my eyes bled, but I ended up with the following as a workable solution, and thought it might help someone else in the same place, so here it is:
```

rsync -vcrtI file -e "ssh -l user_on_proxy -i /proxy_private_key proxy_ip_address ssh -i /destination_key" destination_user@destination_IP_address:/path/to/mirror/dir/

```

OK, for some explanation:

We need to establish a connection between 2 machines over ssh using a third machine as a 'go between'. In my case machine 3 was the aforementioned squid proxy box. ssh allows you to send a command automatically following your login, so 
```
ssh user@machine pwd
```
 would log you in as **user** to **machine** and run the command **pwd**. What I did was to pass to my first ssh command a *second* ssh command. In essence I did 2 ssh logins, the first to the proxy box, and the second to my destination. rsync was more than happy to establish and use this connection, and I've been getting my mirror ever since.

Please note the double-quotes, as placement of these is critical so that flags are passed properly between commands. 

The command above assumes that you are using automatic log-in through the use of priv/pub keys. There are other HowTos describing how to set those up, and for brevity's sake I won't repeat them. Needless to say you need 2 sets of keys for this method to work. The source machine will have a private key, with a matching public on the proxy. The proxy will have a private key as well, with its matching public on the destination machine. Thus both connections happen automatically and the rsync push is done.

There are probably variations to this method, and comments are welcome. For all I know there is a simpler, less painful way to do what I did, but this was the best I could come up with at a time when google held no answers for me. 

Enjoy!

---

### Post by say2sky on 2008-04-08
It's very useful. 

Now you sync local file "file" to dest directory "destination_user@destination_IP_address:/path/to/mirror/dir/".

How about sync file from machine 2 to/from machine 3?

---

### Post by slightcrazed on 2008-04-08
You certainly could rsync between machine 2 (proxy) and 3 (destination), the only stipulation being that rsync would have to be installed on both machines. That is how rsync through ssh is normally done, between 2 machines that *can* talk to each other. My dilemma was to get 2 machines that *couldn't* talk to each other to be able to sync. 

In the end, the above method is most useful in getting through to a nat'd/firewalled machine that doesn't allow direct ssh connections. As long as you can get to a machine via ssh that can talk to the destination machine via ssh then this will work. In theory you could chain together as many ssh pass-throughs as you wanted to, connecting between 2 machines with as many 'hops' in between as you needed.

---

### Post by Gimly on 2009-03-16
Thank you for solution.
Multiple SSH proxy chains can also be used.
Syncing files from br4 to local using ssh with chain scheme:
local -> br1 -> br2 -> br3 -> br4

Simple solution:
rsync -avz -e "ssh -A user1@br1 ssh -A user2@br2 ssh -A user3@br3 ssh" user4@br4:/source destination

"-A" - ssh option, that enables "authentication agent forwarding".
"ssh-add" console command can cache all RSA/DSA authentication keys used on br1-br4 hosts (~/.ssh/authorized_keys auth).
No passwords or knowledge which keys on which host is needed.

Or even (usernames on all hosts br1-br4 are same as current user and put files back from local to br4):
rsync -avz -e "ssh -A br1 ssh -A br2 ssh -A br3 ssh" src br4:/dest

For cron job or service auth-agent must be run:
```
#!/bin/bash
eval `ssh-agent`
ssh-add [key-files or empty for default keys]
rsync [....]
eval `ssh-agent -k`

```

---

