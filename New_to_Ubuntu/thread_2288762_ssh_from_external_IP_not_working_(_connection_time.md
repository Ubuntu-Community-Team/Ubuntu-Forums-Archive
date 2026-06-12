---
title: "ssh from external IP not working ( connection timed out), internally works"
date: 2015-07-29
forum: New to Ubuntu
---

### Post by romello6543 on 2015-07-29
Hello,
Here is rundown of what happened:
****Before****
-I was able to successfully setup OpenSSH(Ubuntu 15.04). I was able to ssh from within my LAN and externally. This also confirm the port is not blocked on the router.

**After****
I decided to implement SSH Keys so no password is needed. So my Mac Laptop has the private key and my Ubuntu workstation has the public key. I successfully implemented this and I can SSH from my LAN ( on my Mack only), but I cannot SSH from outside of my network ( using my Mac with the public key). The error I get when I try to SSH externally is "connection timed out".  

I revered back by changing "[COLOR=#000000]PasswordAuthentication yes" to "[/COLOR][COLOR=#000000]PasswordAuthentication no" to see if I would be able to SSH from an external IP and be prompted for the password but that also did not work. I am at a lost here. I am thinking there some internal firewall rule is the issue but I do not know enough on how to check this. Any assistance would be appreciated! much thanks[/COLOR]

---

### Post by TheFu on 2015-07-29
Does the Ubuntu machine have a static IP? Is the ssh port forwarded from the router to that static IP?

Had to ask.  I've never seen the issue you are describing.

Did you reboot either the router or the Ubuntu machine?

Did you check the Ubuntu firewall?

---

### Post by romello6543 on 2015-07-30
Thanks for replying. Yes the Ubuntu machine has a static IP. The router is setup to properly forward SSH to the static IP ( going to triple check this again). I will reboot the router and PC again ( wish me luck:) I have not checked the Ubuntu firewall as I never had to make any changes when it was working. I also used an external site to check if my port was open. I will reboot PC and Router tonight and report. thx

---

### Post by TheFu on 2015-07-30
Well ... it is time for the desperate move.

Turn up the ssh verbosity ... **ssh -vvvv userid@server** and see how far the connection gets.
BTW, posting the exact connection AND the exact errors would really be helpful.

---

### Post by romello6543 on 2015-07-30
cool .btw i thought you pull out the stops with the "-vvv" lol

NIKE-Air:~ lando$ ssh -vvv cbr604@9x.2xx.1x.1xx
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.6 [192.168.1.6] port 22.
debug1: connect to address 192.168.1.6 port 22: Operation timed out
ssh: connect to host 192.168.1.6 port 22: Operation timed out
NIKE-Air:~ lando$ 

Note: This is the same Mac Air laptop that I can ssh from on the LAN and it works. Once I tether to my phone to simulate a outside connection this is what i get.

---

### Post by TheFu on 2015-07-31
You cannot ssh to a non-public IP address over the public internet.
192.168.x.x should never work over the internet.
10.x.x.x should never work either and 172.16.x.x-172.32.x.x should never work either.  

You need to know the public IP of your internet connection and ssh into that.

---

### Post by romello6543 on 2015-07-31
yes I agree with you. The first line does show I am entering my public IP ([COLOR=#000000]NIKE-Air:~ lando$ ssh -vvv cbr604@9x.2xx.1x.1xx) . The 6th line shows my internal nat for my Ubuntu. So i may be mistaken but it seem like it -v is showing I am getting to the router via my public IP and the port fowarding rule is correct. I do see an error on line 5 and this may be the issue. I will look into this to see what I can find.
[/COLOR]

---

### Post by TheFu on 2015-07-31
Is 192.168.1.6 really listening on port 22 for ssh?  netstat, nmap, lsof will show.  I'd check the firewall again and double check the /etc/sshd_config on the server   (.6) for any allow/deny entries too).

Could you be doing port translation from some other port than 22?  I like to have the router listen on some strange port, but forward to port 22 internally.

BTW, you can run the sshd server interactively with -vvv options too. If it doesn't see anything, you've just verified the issue is somewhere else.

---

### Post by romello6543 on 2015-07-31
If I can ssh internally from within my network to 192.168.1.6 port 22 and it works so I would assume this box is really listening on that port ( correct me if i am wrong)....I will try to use [COLOR=#000000]netstat, nmap, lsof  to see if it can capture my SSH request externally. If i dont see the attempt then I can narrow it down to the router being issue. How does that sound?[/COLOR]  I will do the port translation to see if that helps( port 9876 ->22).  What do you mean by "[COLOR=#000000]sshd server interactively with -vvv options "[/COLOR]
? Much Thanks

---

### Post by TheFu on 2015-07-31
Thanks for baring with me.  What you say above is normally true, but there are some rare exceptions there the sshd settings will block certain clients from access.  I do as part of my security management for ssh.  For example, I do not allow password authentication from any non-LAN IP. External IPs must use keys, period.  I also like to use different ports for external vs internal connections. That makes it clear which is being used. By using the ~/.ssh/config file, managing my different userids for each different remote system, and different ports isn't something I have to remember.  That file is used by every ssh-compatible tool I know. Basically, I never have to remember my userid or port on any remote box. Very convenient, even only as a documentation thing.

It is possible for sshd_config to block connections from specific locations. Anything funny in there on your sshd server?

It is also possible that your wireless ISP is blocking ssh traffic and/or traffic to the router.  The -vvvv options can be involved on the client and debug data requested on the server.   -d option is useful to troubleshoot the daemon. If you check the manpage for sshd, it is there.  So, stop the normal sshd (service stop) and manually run it - **sudo /usr/sbin/sshd -d ** then watch the debug output as you attempt connections from the other box.  Might want to **tee** the output to a log file - that output is to stderr, not just stdout, so do any redirection desired.

If you don't see any connection ... then check the firewall. If that passes,  start working towards the internet for issues.

---

### Post by romello6543 on 2015-07-31
no worries at all. Thanks so much for the direction. I will try tonite and report back. thx again

---

### Post by TheFu on 2015-07-31
> **romello6543 said:**
> no worries at all. Thanks so much for the direction. I will try tonite and report back. thx again

I find ssh to be one of the easiest network daemons/services to troubleshoot and setup.  

It is the swiss-army-knife of networking. The list of things possible with ssh is amazing - not just remote shells and transferring files.

---

### Post by romello6543 on 2015-07-31
thanks for your insight! As a newbie I will not fail this task :) You change your profile name to "The Fu SSH Guru"

---

### Post by TheFu on 2015-07-31
> **romello6543 said:**
> thanks for your insight! As a newbie I will not fail this task :) You change your profile name to "The Fu SSH Guru"

What else can ssh do? [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

### Post by romello6543 on 2015-08-01
Thanks for the info! Good work! I think I want to try file transfers next . Before I solve this issue. I have been a bit under the weather so i did not get a chance to try the next troubleshooting steps. I appreciate all the information you have provided.

---

### Post by romello6543 on 2015-08-03
So in /var/log I "tail -f auth.log " & "tail -f syslog" I realized that on my windows box and on another Windows laptop i was able to SSH from with my network and outside of the network via proxy. I was able to see activity in the logs. However, Iwas not seeing this when I tried to SSH from the laptop so I narrowed down the issue to the Mac laptop itself. It turns out my
".bash_profile" was somehow corrupted. I had created 2 alias weeks ago so I am not sure how it got corrupted. I removed the entries i entered in ".bash_profile" saved and exited and I can  now SSH from within my network and ouside.

btw I did uninstall OpenSSHServer and re-installed it before the above steps. Now I have to setup SSH keys again.  TY so much "TheFu" aka SSH Guru.

---

