---
title: "Changing DNS"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by thefoolisme on 2008-05-27
Hi folks, 

I've got Gutsy installed on my laptop, and I've been trying desperately to get the networking working.  Under ifconfig, both the wired and wireless networking have been assigned ip addresses, but neither will work.  I was going through the forums and the Ubuntu docs and came across something about the nameserver in /etc/resolv.conf.  The name server was pointing to my router.  From  troubleshooting another piece of hardware, I learned that the nameserver should be the ones "outside" the network.  So I edited the file with the outside nameserver, but every time I restart, it resets itself to my router's ip address.  I'm pretty sure this is the problem with the networking, so I'd like to try here first.  Like I said, I can't get the wired or wireless to work.  Any suggestions before I go back to edgy eft, which I know worked well?  :-)  Thanks.

---

### Post by tramir on 2008-05-27
You can try [OpenDNS]("http://https://www.opendns.com/start?device=ubuntu"). Read their instructions for Ubuntu, they tell you what to do to keep the settings after reboot.

---

### Post by spiderbatdad on 2008-05-27
Indeed nameservers are used to resolve internet searches, generally provided by your isp.
Have you edited the /etc/hosts file at all?

---

