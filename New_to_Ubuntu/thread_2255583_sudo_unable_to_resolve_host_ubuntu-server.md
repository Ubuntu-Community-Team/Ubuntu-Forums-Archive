---
title: "sudo: unable to resolve host ubuntu-server"
date: 2014-12-06
forum: New to Ubuntu
---

### Post by himayloco on 2014-12-06
Hi All,

I am having the "sudo: unable to resolve host <hostname>" issue that some others have reported over the years.  This is a fresh install of 14.04LTS that is up to date.

When I use the command 

```
cat /etc/hostname
```

I get back:
<hostname>

Likewise when I use:

```
cat /etc/hosts
```

I get back:
127.0.0.1    localhost
127.0.1.1    <hostname>

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I am not really sure what to try next, the hostname and hosts file both contain the same hostname....any ideas?

Cheers!

---

### Post by Gone fishing on 2014-12-06
I think you just need to give your system a host name

Open a terminal and run ```
sudo gedit /etc/hostname
``` and add something to the file for example > himayloco then ```
sudo gedit /etc/hosts
``` amd modify it so that it looks like

```
127.0.0.1       localhost
127.0.1.1       himayloco

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Then reboot and all should be well

---

### Post by himayloco on 2014-12-06
Hi GoneFishing, thanks for the reply!

Thats the weird thing.  I do have a hostname in both places. When this problem first appeared, I had a different hostname with a capital letter in it, so I changed it to something simpler with no special characters or capitals.  I used ```
sudo gedit /etc/hostname
``` to change the hostname file and ```
sudo gedit /etc/hosts
``` to change the hosts file to be that new host name.  I then restarted the machine and nothing....the problem is still there.

Since you took the time to reply, and so that we can be precise, I have changed my hostname to "himayloco" for the time being.  I have edited both the /etc/hostname and /etc/hosts files to reflect this hostname.  I then restarted the machine and I still have the problem.

---

### Post by matt_symes on 2014-12-06
Hi

Does you hostname contain spaces or other unusual characters ?

EDIT: we were cross posting so I guess not ?

Kind regards

---

### Post by matt_symes on 2014-12-06
Hi

Can you post the output of this command.

```
hostname
```

and

```
grep $(hostname) /etc/hosts
```

Kind regards

---

### Post by nerdtron on 2014-12-06
> I am having the "sudo: unable to resolve host <hostname>" issue  that some others have reported over the years.  This is a fresh install  of 14.04LTS that is up to date.

OK. So this is the error you are getting? But the hostname and hosts file are correct already?

What terminal commands shows that error?

---

### Post by himayloco on 2014-12-06
For matt_symes:

```
hostname
```

output:
himayloco

```
grep $(hostname) /etc/hosts
```

output:
127.0.1.1    himayloco


For nerdtron:
Any terminal command that contains "sudo"

Thanks to both of you!

---

### Post by nerdtron on 2014-12-06
HHmmm this is plain weird. I remember this happening to me once and I just corrected the entry on the /etc/hosts. Yours is correct already, well, there's no typo.

Have you tried suggestions here: [http://askubuntu.com/questions/59458/error-message-when-i-run-sudo-unable-to-resolve-host-none](http://askubuntu.com/questions/59458/error-message-when-i-run-sudo-unable-to-resolve-host-none)

---

### Post by matt_symes on 2014-12-06
Hi

That is odd. Can we also check your sudoers files.

boot into the recovery terminal and type 

```
grep -nH "^[^#]" /etc/sudoers{,.d/*}
```

Capital H above. Maybe easier to copy and paste it into the terminal.

Kind regards

---

### Post by nerdtron on 2014-12-06
After the fresh install what else did you do? any changes on system files? What else did you install?

---

### Post by steeldriver on 2014-12-06
Anything non-standard in your /etc/nsswitch.conf file (specifically the hosts line)?

---

### Post by himayloco on 2014-12-06
I figured it out.

It was a 32-bit install problem. I installed the 64-bit version of Ubuntu and the problem was resolved.

Thank you matt_symes, nertdtron, steeldriver, and Gone fishing for your help.  This was my first experience on the the forums, it was amazing to see how quickly the community responds.

---

