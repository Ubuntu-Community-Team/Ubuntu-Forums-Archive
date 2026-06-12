---
title: "[SOLVED] &amp;quot;Failed to fetch&amp;quot;  in update and synaptic"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Michl on 2008-09-09
When trying to update or install via synaptic, it fails to fetch and
the reason is:

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


What's my problem?

Solution:
```
sudo grep -r 4001 /etc
```

This showed that anon-proxy was using port 4001.  So
remove anon-proxy

```
sudo apt-get --purge remove anon-proxy
```

The mystery for me is how anon-proxy got installed.  I never
heard of it and did not intentionally install it.  Was it
part of an automatic upgrade?  Part of a Firefox add-on?
I don';t know,  But removing anon-proxy did the trick.

---

### Post by bobnutfield on 2008-09-09
127.0.0.1 is the loopback device.  Looks like you do not have a network connection.

---

### Post by Elfy on 2008-09-09
Quick question have you installed anonproxy?

---

### Post by wolfen69 on 2008-09-09
i would just reset (unplug) your modem/router, and reboot the computer. these things happen once in a while.

---

### Post by drs305 on 2008-09-09
Do you know if you use a proxy?

If you dont' know what I'm talking about, just run this command:
```
echo $http_proxy
```
If you get output, run this:
```
unset http_proxy
```

or if you prefer, check System, Preferences, Network Proxy, Proxy Configuration and try Direct Internet Connection .

---

### Post by tadcan on 2008-09-09
I haven't updated in 70 days. Third party apps update fine. I am told to check my network. I have a lan cable running from the wireless router.

Edit: I didn't see you post drs305. Mine is already set to Direct internet connection.

---

### Post by Michl on 2008-09-09
This is at work and I do have a network connection.
I am connected right now.  But I still get this
strange note that it cannot connect to the local
host.


Also, I am set to direct internet connection.

Just wondering if this is related.  I am connected
to the wired network here at work, but I am not
logged on to a protected wired network.  Could that
be the issue?

---

### Post by Michl on 2008-09-11
I need help ... I cannot update ubuntu.  I do not use a
proxy, I am connected to the internet, etc, but fail to
fetch files.  As before the message is:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080805_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080805_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


HELP!

---

### Post by solotransit on 2009-01-02
Hello,

I had a similar problem, after removing anon-proxy. The same error message. anon-proxy is the cause. 
Fix:
Comment out the [appropriate] two lines in /etc/environment
(By inserting a # at the beginning of each line.)

You can do so using

sudo gedit /etc/environment

Original (after anon-proxy):
[...]
# +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
http_proxy=http://localhost:4001 # +ANON_MARK+

Fixed:
[...]
# +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
#HTTP_PROXY=http://localhost:4001 # +ANON_MARK+
#http_proxy=http://localhost:4001 # +ANON_MARK+


Then log out, and in again.


The problem is that anon-proxy assumes it will always be running. There is no problem when it is running, or running in no-proxy mode, it simply passes synaptic/apt-get's traffic from port 4001 to the internet.
However when anon-proxy isn't running, apt-get still connects on port 4001, where anon-proxy should be listening. So apt fails to reach the internet. A cleaner removal would prevent this residual configuration.

Good luck

---

