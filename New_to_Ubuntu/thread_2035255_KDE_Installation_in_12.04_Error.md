---
title: "KDE Installation in 12.04 Error"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by Farvez Afridi on 2012-07-30
Recently I installed KDE Plasma Desktop through Synaptics package manager and It failed to run.
It gives the following error: > call to lnusertemp failed (temporary directories full ?).Check your installation

Any Solutions for it?:confused:

---

### Post by uzumakifahim on 2012-07-30
Please describe your problem more briefly. Is the installation successful? When you are getting this message? Before logging into your Ubuntu account have you getting the options for multiple Desktop Environments including KDE?

---

### Post by Farvez Afridi on 2012-07-30
> **uzumakifahim said:**
> Please describe your problem more briefly. Is the installation successful? When you are getting this message? Before logging into your Ubuntu account have you getting the options for multiple Desktop Environments including KDE?
The installation was successful, The error message was shown after logging in to my user account.

---

### Post by drmrgd on 2012-07-30
Would you mind posting the output of these two commands (please use the "Code" tags above to make it a little easier to read):

```
df -h
```

```
ll /var/
```

I suspect that either your filesystem (especially the partition where /tmp resides) is full, or /tmp has improper permissions and can't be written to.

---

### Post by Farvez Afridi on 2012-07-30
> **drmrgd said:**
> Would you mind posting the output of these two commands (please use the "Code" tags above to make it a little easier to read):

```
df -h
``````
ll /var/
```I suspect that either your filesystem (especially the partition where /tmp resides) is full, or /tmp has improper permissions and can't be written to.

The Output of:

1.```
df -h
```
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       116G   26G   85G  23% /
udev            997M  4.0K  997M   1% /dev
tmpfs           402M  876K  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1004M   57M  948M   6% /run/shm

```
2.```
 ll /var/
```
```
total 52
drwxr-xr-x 13 root root     4096 Jul 31 03:25 ./
drwxr-xr-x 24 root root     4096 Jul 30 22:01 ../
drwxr-xr-x  2 root root     4096 Jul 31 01:37 backups/
drwxr-xr-x 20 root root     4096 Jul 26 15:48 cache/
drwxrwsrwt  2 root whoopsie 4096 Jul 31 02:20 crash/
drwxr-xr-x  3 root root     4096 Jul 28 21:11 games/
drwxr-xr-x 78 root root     4096 Jul 30 21:50 lib/
drwxrwsr-x  2 root staff    4096 Apr 19 13:32 local/
lrwxrwxrwx  1 root root        9 Jul 31 03:25 lock -> /run/lock/
drwxr-xr-x 16 root root     4096 Jul 31 04:22 log/
drwxrwsr-x  2 root mail     4096 Apr 23 15:34 mail/
drwxr-xr-x  2 root root     4096 Apr 23 15:34 opt/
lrwxrwxrwx  1 root root        4 Jul 31 03:25 run -> /run/
drwxr-xr-x  9 root root     4096 Jul 27 02:25 spool/
drwxrwxrwt  2 root root     4096 Jul 31 04:25 tmp/

```
These are the outputs.

---

### Post by freesbee on 2012-09-15
> I suspect that either your filesystem (especially the partition where /tmp resides) is full, or /tmp has improper permissions and can't be written to.I have exactly the same problem (I should mention that I am quite new to linux).
I checked my permissions on tmp:

```

$ ls -la
drwxrwxrwt   9 root root       4096 Sep 15 20:39 tmp
drwxr-xr-x  16 root root       4096 Sep 13 16:00 var

```I checked my partitions:
```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        46G  4.6G   39G  11% /
udev            486M  4.0K  486M   1% /dev
tmpfs           199M  848K  198M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M  144K  496M   1% /run/shm
/dev/sda5        28G  886M   26G   4% /home
/dev/sda7        33G  1.5G   30G   5% /var

```The system is a fresh installation, and I have no problems logging in with Unity. This message happens only if I try to login with KDE.

I tried all what I found around (permission on /home, on /tmp, on /var), but no success.

> Is the installation successful? When you are getting this message?  Before logging into your Ubuntu account have you getting the options for  multiple Desktop Environments including KDE?Sorry: I do not really understand this question.
The system is working fine with Unity, but I would like to use KDE. I get the message when I try to login using KDE, and I cannot login.

> I'm just wondering how you installed KDE exactly through synaptic what packages did you install? kubuntu-desktop?I installed KDE via

```
sudo apt-get install kubuntu-desktop
```Any idea?

---

### Post by Epodx64 on 2012-09-15
I'm just wondering how you installed KDE exactly through synaptic what packages did you install? kubuntu-desktop?

---

### Post by Epodx64 on 2012-09-15
Try completely shutting down your computer that will clear the /tmpfs and should allow you to log into KDE if that doesn't work maybe it's eating up to much  memory trying to run Compiz+Kwin? KDE is pretty resource intensive when I had Kubuntu 12.04.1 it would usually idle around 700-800mb right after start-up with just Kwin running how much Ram do you have? 800mb really wasn't a concern for me because I was running on top of 4GiB's of Ram but I'd imagine anything less then 2GiB's would probably struggle with Kubuntu especially if it's trying to run gnomes effects on top of Kwin (/tmpfs is Ram+Swap)

---

