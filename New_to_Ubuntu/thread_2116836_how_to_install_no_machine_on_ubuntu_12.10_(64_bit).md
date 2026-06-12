---
title: "how to install no machine on ubuntu 12.10 (64 bit) to remotely log in to unix like en"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by cutSn8 on 2013-02-16
Hi new to linux, wanting to install no machine client on my ubuntu 12.10 64 bit environment (to use no machine to remotely log in to a unix like environment, a uni a/c).

A few issues: 
1. When I look at the no machine client download list ([http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)) I don't see a 12.10 option, so which should I use?  
2. Is downloading from the above site the best way to go, or is there a sudo apt-get alternative that is a better way to go?
3. When I searched this issue, I found discussions of problems some more advanced users had (on ubuntu help and elsewhere), and workarounds - will I have these problems? Is there a newbie summary of the workarounds?  (I think some of the problems arise when people are trying to use nx to log in to there 12.10 machine remotely from a windows client - not what I'm wanting to do.)
4. Is there a better way for me to go (to remotely log in to an account in a unix like system from my 12.10 pc)?

Thanks muchly for any help.

---

### Post by Ms. Daisy on 2013-02-18
I haven't used nomachine, but it looks like it's designed for enterprise environments.  Are you deploying this in an enterprise or at home?

If all you're trying to accomplish is to remotely log into to a unix-like (server?) system from your ubuntu 12.10 workstation, then [ssh ]("https://help.ubuntu.com/community/SSH")would do what you need.

---

### Post by cutSn8 on 2013-02-18
Thanks Ms. Daisy
yes SSH does log me on.  The uni has set up a no machine ?server however (which, when I log on with ac. no machine client, gives me remote access to various useful programs - not sure if I can launch all of these from bash).  Anyway, I thought about the choice between 12.04 and 12.10 and decided 12.04 was fine, so I downgraded and am now running no machine from there fine.

Kind regards

---

