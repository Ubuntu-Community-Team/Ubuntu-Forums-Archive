---
title: "ssh error: &quot;shift: 28: can't shift that many&quot; - ssh'ing to my ubuntu box times out"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by fattykins on 2012-03-11
Hello, I have openssh installed on my ubuntu box.  

I've suddenly come across a problem recently (no change was made to the box before this happened), where I can't ssh into the ubuntu box.  I get "Operation timed out."  

When I go to the ubuntu box, I run 'ps -ef |grep "sshd"' and I run 'ps -A | grep sshd' to check if ssh is running, and it's indeed running.  But when I try "sudo /etc/init.d/ssh" to check the status of ssh, I get the error "shift: 28: can't shift that many."  

I can ssh to localhost fine on that box.  And from another computer on the network, I can ssh to the ubuntu box's 192.168... address just fine.  And when I ping the ubuntu box IP address from another computer (my router is set to port forward to the ubuntu box on the ssh port), I get packets received no problem.  

But if I ssh from another computer to my ubuntu box, I get a timeout error.

Does anyone have any idea why I may be getting a timeout error?  The only error I can find that's happening on my ssh is the "shift: 28: can't shift that many," but I can't find what that means.  

Help?  Thank you!

---

