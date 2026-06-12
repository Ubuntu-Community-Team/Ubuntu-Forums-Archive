---
title: "[SOLVED] Update manager not responding."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mart478 on 2008-07-29
Hi all.

I recently installed ubuntu and everything seems great, but I can't get update manager to work.  When I log on a notice appears saying "There are 2 updates available".  Clicking on this opens a window listing the 2 upates, however when I click "install" nothing happens.  No error message, no time out, it just sits there.

I have internet access (I'm posting this via ubuntu). The same problem occurs with "add/remove applications", when I try to reload the list.

Any ideas?
thanks
martyn.

---

### Post by iaculallad on 2008-07-29
> **mart478 said:**
> Hi all.

I recently installed ubuntu and everything seems great, but I can't get update manager to work.  When I log on a notice appears saying "There are 2 updates available".  Clicking on this opens a window listing the 2 upates, however when I click "install" nothing happens.  No error message, no time out, it just sits there.

I have internet access (I'm posting this via ubuntu). The same problem occurs with "add/remove applications", when I try to reload the list.

Any ideas?
thanks
martyn.

Post the content of your /etc/hosts file.

```
cat /etc/hosts
```

---

### Post by mart478 on 2008-07-29
Here it is:

martyn@martyn-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 martyn-desktop.martyn's

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
martyn@martyn-desktop:~$

---

### Post by iaculallad on 2008-07-29
> **mart478 said:**
> Here it is:

martyn@martyn-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 martyn-desktop.martyn's

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
martyn@martyn-desktop:~$

Open and Edit your /etc/hosts file:

```
gksudo gedit /etc/hosts
```

and replace the content with:
> 
127.0.0.1 localhost
127.0.1.1 martyn-desktop

Save and Clost the file. Do logoff on your account then log back in.

---

### Post by tinny on 2008-07-29
If the above suggestion doesn't work...

Open a terminal and run the following... (make sure the update manager is closed)

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

Post back the output.

---

### Post by mart478 on 2008-07-29
after entering the code:

gksudo gedit /etc/hosts

I get no response, just a flashing cursor.  This is in Terminal, right?

---

### Post by iaculallad on 2008-07-29
> **mart478 said:**
> after entering the code:

gksudo gedit /etc/hosts

I get no response, just a flashing cursor.  This is in Terminal, right?

It should ask you to enter your password. You just have to enter it even without being echoed. It's just normal.

---

### Post by tinny on 2008-07-29
> **tinny said:**
> If the above suggestion doesn't work...

Open a terminal and run the following... (make sure the update manager is closed)

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

Post back the output.

I really think you should do these command ASAP. This will at the very least give us more info to work with

---

### Post by mart478 on 2008-07-30
I entered this code in terminal:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Sorry, I was unable to copy the resulting text.  It ran to pages and pages, and took quite long to finish.  At the end I was asked to restart my computer.  The result of this is that "add/remove" applications now seems to work.  However update manager still freezes when I try to install the now 7 updates that are available.

Shall I run the code again?

thanks
martyn

---

### Post by tinny on 2008-07-30
> **mart478 said:**
> I entered this code in terminal:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Sorry, I was unable to copy the resulting text.  It ran to pages and pages, and took quite long to finish.  At the end I was asked to restart my computer.  The result of this is that "add/remove" applications now seems to work.  However update manager still freezes when I try to install the now 7 updates that are available.

Shall I run the code again?

thanks
martyn

Really need to see that output, sorry...

---

### Post by mart478 on 2008-07-30
> **iaculallad said:**
> Open and Edit your /etc/hosts file:

```
gksudo gedit /etc/hosts
```

and replace the content with:


Save and Clost the file. Do logoff on your account then log back in.

Thanks- this worked straight away.  What I should have tried first

---

### Post by steveneddy on 2008-07-30
> **mart478 said:**
> Thanks- this worked straight away.  What I should have tried first

Good - now lets mark this as solved please.

---

