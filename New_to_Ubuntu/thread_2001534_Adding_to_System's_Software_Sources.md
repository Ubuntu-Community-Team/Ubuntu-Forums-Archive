---
title: "Adding to System's Software Sources"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by kjbox on 2012-06-11
I purchased Full Circle Magazine from the software centre and nothing seemed to happen. I did get an e-mail from Full Circle saying that if I had any difficulties then visit [https://software-center.ubuntu.com/subscription/203723/](https://software-center.ubuntu.com/subscription/203723/) where I got the following instruction:


To install packages from this archive you need to copy the line below and add it to your system's software sources.

"Deb line for Full Circle Magazine #61 for Ubuntu 12.04:
```

deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main

```
This repository is signed with OpenPGP key 1024R/75254D99."

Please can somebody tell me the correct command(S) to use in a terminal to dd this line to my system's software sources.

Thanks

---

### Post by roelforg on 2012-06-11
```

sudo echo deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main >> /etc/apt/sources.list

```

---

### Post by kjbox on 2012-06-11
Thanks for the quick reply.

Tried that and got:

```
charles@charles-UX31E:~$ sudo echo deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied 
```

There was no request for authentication password.

Any ideas?

---

### Post by roelforg on 2012-06-11
> **kjbox said:**
> Thanks for the quick reply.
 
Tried that and got:
 
```
charles@charles-UX31E:~$ sudo echo deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied 
```
 
There was no request for authentication password.
 
Any ideas?
 
Woops, made a mistake. This should work:
```

sudo bash -c 'echo deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main >> /etc/apt/sources.list'

```
Or you could do:
```

sudo -i
echo deb https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu precise main >> /etc/apt/sources.list
exit

```
The exit at the end of that on is important because we need to exit the root shell.
 
Another option would be:
```

sudo add-apt-repository [https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu](https://charles18954:Vddl2Zl16P9K3RRPb153@private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu)

```
But i'm not sure if that is the correct syntax.

---

### Post by sanderj on 2012-06-11
This is what worked for me:

gksudo gedit /etc/apt/sources.list &

... and add the line "deb https://..." to the end. Save & Exit.

Then:

sudo apt-get update

which will give an error. Solve that by:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  E131728675254D99
sudo apt-get update


BTW: the URL looks to contain your personal info. Is that OK?

---

### Post by kjbox on 2012-06-11
Thanks for replies,

I tried the first alternate solution suggested by roelfrog and then ran sanderj's command and sure enough the new URL was added to the list.

I did get the error when updating (I got the same error earlier during routine auto-update.)

I entered your fix and got the same error (pasted below). I did also try purchasing issue 61 just to see if that worked but getting the same error. I note that the URL is specific for the issue number, would relacing the number with * work? If not then it better be a very good magazine to go through this for each issue! 

There also appear to be 2 other failed updates not associated with this URL, any ideas regarding those?

```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/my.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-53/ubuntu/dists/precise/main/binary-i386/Packages  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-i386/Packages  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-i386/Packages  gnutls_handshake() failed: A TLS packet with unexpected length was received.

E: Some index files failed to download. They have been ignored, or old ones used instead.
charles@charles-UX31E:~$ 

```

The personal info is just e-mail address which they have anyway.

---

### Post by mastablasta on 2012-06-11
why not just add the deb line to software soources in software center?

---

