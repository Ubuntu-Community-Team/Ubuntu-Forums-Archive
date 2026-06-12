---
title: "Git issues"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by lekofraggle on 2012-12-26
Hello,
I have been bulding on 12.04 on an old macbook pro running in a vm. I just recieved a lenovo w500 and tossed 12.04 on it. I was trying to migrate my whole build environment, but I had trouble due to lack of space on the mac. I had issues with 12.04 on the lenovo, So I installed 12.1 instead. It seems to be running smoother, but I am still getting the following error on syncing to git.

fatal: unable to connect to github.com:
github.com[0: 207.97.227.239]: errno=Connection refused


I can ping with no problem, and I did install the sdk and run the first sync fine.

Do you have any advice?

Thanks in advance.
~Leko

---

### Post by ubudog on 2012-12-26
Is the git port (9418) open?

---

### Post by COMECON on 2012-12-26
Have you got any firewall activated?

Catbuntu

---

### Post by lekofraggle on 2012-12-26
I guess this is a stupid question, but how do I check if I have a firewall and if the port is open?

I am running a default install and the only software I added was compiz .

I know I do not have ab external firewall, because my Mac can sync. 
~Leko

---

### Post by ubudog on 2012-12-26
This command should let you know whether the port for Git is open or not:
```
nmap -v -sV localhost -p 9418
```

Also, could you post the Git command you're running that gives the error?

See [here]("https://help.ubuntu.com/12.10/serverguide/firewall.html") for more information on Ubuntu's firewall system.

---

### Post by lekofraggle on 2012-12-26
Thanks a lot.  I had to install nmap, but it does look like the port may be closed.

Here is the readout.

```
Starting Nmap 6.00 ( http://nmap.org ) at 2012-12-26 19:41 EST
NSE: Loaded 17 scripts for scanning.
Initiating Ping Scan at 19:41
Scanning localhost (127.0.0.1) [2 ports]
Completed Ping Scan at 19:41, 0.00s elapsed (1 total hosts)
Initiating Connect Scan at 19:41
Scanning localhost (127.0.0.1) [1 port]
Completed Connect Scan at 19:41, 0.00s elapsed (1 total ports)
Initiating Service scan at 19:41
NSE: Script scanning 127.0.0.1.
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000046s latency).
PORT     STATE  SERVICE VERSION
9418/tcp closed git
```

So, how do I open it?

I am using repo to connect to my and other gits.

the init command is...

$repo init -u git://github.com/CyanogenMod/android.git -b jellybean

This works fine along with an initial sync, then.

I use 
$repo sync -j24

I have changed -j24 to -j1 to see if that was the error.

Thanks again.

~Leko

---

### Post by ubudog on 2012-12-26
Strange.  Let's try opening the port and then see what it does:
```
sudo iptables-save > rules.bak
```
```
sudo iptables -A INPUT -p tcp --dport 9418 -j ACCEPT
```
```
sudo iptables-save
```

---

### Post by lekofraggle on 2012-12-26
I tried to open the port, and got the same result both with Nmap, and repo.

This is so odd. 

I also backed up my android build directory and tried running repo from the usb drive.  I have the same error.

On my virtual machine, I have no sync problems.

~Leko

---

