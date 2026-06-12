---
title: "ssh stopped working"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by tmcmulli on 2008-04-29
I'm running 7.10 desktop, and have been connecting to this machine via ssh for over a year.  Last week, ssh stopped working.  I can connect to the machine, but when I enter a password, the window closes when using Putty, but I get "connection refused" when trying to connect from my other Ubuntu box (which works fine).

This is my mail server, and it is connected directly to the Internet...

I can connect fine with VNC, everything else seems fine...

Any ideas?  At least I need to know where the logs are to check out the errors.

Thanks!

---

### Post by Xiong Chiamiov on 2008-04-29
Did the machine update or anything?  It's possible that the key you have stored for it has changed.  I'm not familiar with putty, but can you get access to a Linux machine and connect through the terminal?

---

### Post by Sjovan on 2008-04-29
It could be your router that have restarted or something. go to [_http://www.canyouseeme.org_]("http://www.canyouseeme.org") and check that the port you are running ssh on is open.

---

### Post by ironwolfe on 2008-04-29
Since you can VNC - it is safe to say that networking is set up properly.  Are you ssh tunneling ssh or vpn?

I got a connection refused when I accidently closed the ssh port.  check your /etc/ssh/ssh_config and /etc/ssh/sshd_config file and ensure that you have the correct port open.  Test a new port - other than 22.

If you use authorization keys, you might want to blow them away and start again...

check you IP's as well - I use dyndns.org to update my IP to a host name.  

Lastly turn of ssh-agent - this usually messes me up... remember you passphrase ;)

Good luck

---

### Post by tmcmulli on 2008-04-29
Thanks, guys, I did check the config files, and both are set to the same port.  Again, this has been running for quite some time.  I cannot connect from my other Ubuntu machine at all... and this machine is connected to the T1 router, so all traffic is hitting it.  I use Firestarter for the firewall and most ports are blocked.  I've shut down ssh for now, will rebuild keys when I get home tomorrow (currently on the road, of course).

As for updates, I keep it updated, but there hasn't been one in a week or so, and the same updates are applied to my samba box which is still working great.

Oh, I just connect using Putty or ssh directly from the terminal.  No other programs tunneling over ssh.

Thanks again!

---

### Post by tmcmulli on 2008-04-29
Ok, deleted the key from the registry for Putty, and I can connect from Putty.  But my other linux machine will not connect still.  I removed the keys from the known_hosts file in .ssh, but it still gets "connection refused" from the ssh prompt.  Are the client-side keys stored somewhere besides .ssh?

Thanks!

---

### Post by ironwolfe on 2008-04-29
Did you turn off ssh-agent?

the keys are stored in /etc/ssh/

you will need to sudo

---

### Post by tmcmulli on 2008-04-30
> **ironwolfe said:**
> Did you turn off ssh-agent?

the keys are stored in /etc/ssh/

you will need to sudo

I didn't intentionally turn off anything on either side... but I had to delete the keys from my client on Windows to get that machine to connect.  I thought clearing out the known_hosts file woudl work... checkign in /etc/ssh/ now...

---

### Post by tmcmulli on 2008-04-30
> **ironwolfe said:**
> Did you turn off ssh-agent?

the keys are stored in /etc/ssh/

you will need to sudo

Now I'm confused... which keys are stored in /etc/ssh/?  The client-side or the server side?  I want to clear the client-side known host keys for this client...

---

### Post by ironwolfe on 2008-05-01
The way I understand it is that the keys are put in both locations, private and public.

I think you have to delete them from both locations:

~/.ssh/
and
/etc/ssh/

Since you will be remaking your keys, you might as well make a new key for the Putty machine and add it to the ~/.ssh/authorized_keys file

I looked up your error as well
> 10.13 "Network error: Connection refused"

This error means that the network connection PuTTY tried to make to your server was rejected by the server. Usually this happens because the server does not provide the service which PuTTY is trying to access.

Check that you are connecting with the correct protocol (SSH, Telnet or Rlogin), and check that the port number is correct. If that fails, consult the administrator of your server.

you may want to reinstall openssh-server on the server machine.

```
sudo apt-get install openssh-server
```

good luck.

---

### Post by tmcmulli on 2008-05-01
Ok, so putty started working again once I removed the keys from the registry on the machine running Putty and reconnected.

The ubuntu-ubuntu problem was a bonehead on my side.

A few weeks ago, I was worried about security and some issues...and I turned firestarter on for all outbound communications...

System is acting like I told it to...:lolflag:

Thanks, guys!

---

### Post by ironwolfe on 2008-05-08
I am glad that you got it working.  Don't be shy with the "Thanks" button ;)

---

