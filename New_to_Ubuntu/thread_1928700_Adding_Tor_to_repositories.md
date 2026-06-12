---
title: "Adding Tor to repositories"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by oscillator on 2012-02-20
I'm trying to follow the instructions @ [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en) and this includes setting up their package repository (they advise against using packages in the Ubuntu universe).

First, I've tried this in the terminal : 
'Then add this line to your /etc/apt/sources.list file:[FONT=monospace]

[/FONT]deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main' [FONT=monospace]

[/FONT]Which does nothing but tell me deb is not a command.
So I've gone to System > Administration > Software Sources and added it through that, which works although this message then appears: 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B6C6326781C0BE11
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810

Which I've assumed is fine as the next few steps on the website are about verification.
So then the result of the next step :
gpg --keyserver keys.gnupg.net --recv 886DDD89

Output: gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Soooo how on earth am I meant to add the gpg key to verify packages???

Help please!

---

### Post by Rodney9 on 2012-02-20
Then add the gpg key used to sign the packages by running the following commands at your command prompt ***in the TERMINAL***:

> gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

Now refresh your sources, running the following command (as root) at your command prompt:

> apt-get update

If there are no errors you're good to continue.
We provide a Debian package to help you keep our signing key current. It is recommended you use it. Install it using

> apt-get install deb.torproject.org-keyring

To finally install Tor just run:

> apt-get install tor


Rodney

---

### Post by oscillator on 2012-02-20
I have run those commands in the terminal, the output given is in the last part of my post.

---

### Post by sanderj on 2012-02-20
> **oscillator said:**
> 
Output: gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Are you behind a firewall or proxy? What does "wget keys.gnupg.net" say to you.

Here's mine:

```
sander@xubuntu:~$ wget keys.gnupg.net
--2012-02-20 22:08:21--  http://keys.gnupg.net/
Resolving keys.gnupg.net... 209.234.253.170, 195.113.19.83, 188.40.65.201, ...
Connecting to keys.gnupg.net|209.234.253.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                                                                                         ] 4,521       --.-K/s   in 0.09s   

2012-02-20 22:08:24 (48.9 KB/s) - `index.html' saved [4521]

sander@xubuntu:~$

```

---

### Post by oscillator on 2012-02-21
I've got some firewall rules down yeh, I get the following with 'wget keys.gnupg.net'

user@cipher-desktop:~$ wget keys.gnupg.net
--2012-02-21 07:41:41--  [http://keys.gnupg.net/](http://keys.gnupg.net/)
Resolving keys.gnupg.net... 188.40.65.201, 195.113.19.83, 209.234.253.170, ...
Connecting to keys.gnupg.net|188.40.65.201|:80... failed: Connection refused.
Connecting to keys.gnupg.net|195.113.19.83|:80... failed: Connection refused.
Connecting to keys.gnupg.net|209.234.253.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 4,521       --.-K/s   in 0.1s    

2012-02-21 07:41:41 (45.6 KB/s) - `index.html' saved [4521]

I'm guessing connection refused is due to my firewall?

---

