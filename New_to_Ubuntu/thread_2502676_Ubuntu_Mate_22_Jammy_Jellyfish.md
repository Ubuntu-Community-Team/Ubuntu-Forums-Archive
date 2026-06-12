---
title: "Ubuntu Mate 22 Jammy Jellyfish"
date: 2024-11-24
forum: New to Ubuntu
---

### Post by colink37 on 2024-11-24
How can I remove dozens of old Linux kernels from Jammy Jellyfish, please?  Synaptic only gives me the option to install, with no opportunity to remove or delete from my nearly full disk.  Simple advice would be truly appreciated.  Thanks.  Colin.

---

### Post by grahammechanical on 2024-11-24
Dozens?

I am unfamiliar with the Mate desktop user interface so I cannot give you directions. On Gnome we have a Software Updater utility. This utility installs new kernels and removes old kernels as part of the update/upgrade process. Are we to assume the Mate does not have a similar utility?

In Gnome I can also update/upgrade using the terminal. When I do I sometimes get notification that there are kernels that are no longer needed and I can remove them using the autoremove command. Are you not able to do this in Mate?

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
```

I do not normally use Synaptic to update/upgrade. I have used it in the past. It is possible to search for Linux kernels and mark some for removal. Be careful not to remove the kernel that you are using. Keep the two newest kernels.

Some commands to identify the kernels you already have

```
uname -r
```

will tell you the present kernel

```
ls -l .boot
```

will list all the kernels. Look for lines with vmlinuz. Search Synaptic for vmlinuz. Make a note of the kernels you have and identify the kernels you need to remove. Keep the two latest kernels. Synaptic will also let you remove files associated with the vmlinuz packages. To be safe remove one kernel and its associated packages at a time.

Regards

---

### Post by colink37 on 2024-11-25
Thank you Grahammechanical. I appreciate your help and will give this a try.  Colin.

---

### Post by ActionParsnip on 2024-11-25
What is the output of:
```

uname -a; echo; dpkg -l | grep linux-image | grep -v head

```

---

### Post by Norm24 on 2024-11-25
```
sudo apt autoremove
```

I've used Mate for many years and this is all I've ever had to do to remove old kernals.The two newest should be left after executing that command.

---

### Post by Quarkrad on 2024-11-26
Interesting.  I'm a Mate user and currently running 22.04.  I run **sudo apt autoremove** (and other 'clean' commands) daily via a script and I too have multiple kernels.  **sudo apt autoremove** is not removing my kernels.  I've just run the command manually as per below.

```
dad@dadubuntu:~$ uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

rc  linux-image-5.19.0-32-generic                 5.19.0-32.33~22.04.1                        amd64        Signed kernel image generic
rc  linux-image-6.2.0-33-generic                  6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-34-generic                  6.2.0-34.34~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-35-generic                  6.2.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-36-generic                  6.2.0-36.37~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-37-generic                  6.2.0-37.38~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-39-generic                  6.2.0-39.40~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-14-generic                  6.5.0-14.14~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-15-generic                  6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-17-generic                  6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-18-generic                  6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-21-generic                  6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-25-generic                  6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-26-generic                  6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-27-generic                  6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-28-generic                  6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-35-generic                  6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-41-generic                  6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-44-generic                  6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-45-generic                  6.5.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-45-generic                  6.8.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-47-generic                  6.8.0-47.47~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-48-generic                  6.8.0-48.48~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image
dad@dadubuntu:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
dad@dadubuntu:~$ uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

rc  linux-image-5.19.0-32-generic                 5.19.0-32.33~22.04.1                        amd64        Signed kernel image generic
rc  linux-image-6.2.0-33-generic                  6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-34-generic                  6.2.0-34.34~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-35-generic                  6.2.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-36-generic                  6.2.0-36.37~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-37-generic                  6.2.0-37.38~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-39-generic                  6.2.0-39.40~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-14-generic                  6.5.0-14.14~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-15-generic                  6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-17-generic                  6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-18-generic                  6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-21-generic                  6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-25-generic                  6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-26-generic                  6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-27-generic                  6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-28-generic                  6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-35-generic                  6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-41-generic                  6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-44-generic                  6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-45-generic                  6.5.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-45-generic                  6.8.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-47-generic                  6.8.0-47.47~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-48-generic                  6.8.0-48.48~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image

```

---

### Post by Quarkrad on 2024-11-26
Hmm.. I did not understand this.  Further reading suggests that the **rc** (release candidate) kernels listed above, for my system, are not actually installed - the only ones installed are the **ii** ones.

---

### Post by ActionParsnip on 2024-11-26
> **Quarkrad said:**
> Interesting.  I'm a Mate user and currently running 22.04.  I run **sudo apt autoremove** (and other 'clean' commands) daily via a script and I too have multiple kernels.  **sudo apt autoremove** is not removing my kernels.  I've just run the command manually as per below.

```
dad@dadubuntu:~$ uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

rc  linux-image-5.19.0-32-generic                 5.19.0-32.33~22.04.1                        amd64        Signed kernel image generic
rc  linux-image-6.2.0-33-generic                  6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-34-generic                  6.2.0-34.34~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-35-generic                  6.2.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-36-generic                  6.2.0-36.37~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-37-generic                  6.2.0-37.38~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-39-generic                  6.2.0-39.40~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-14-generic                  6.5.0-14.14~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-15-generic                  6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-17-generic                  6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-18-generic                  6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-21-generic                  6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-25-generic                  6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-26-generic                  6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-27-generic                  6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-28-generic                  6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-35-generic                  6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-41-generic                  6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-44-generic                  6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-45-generic                  6.5.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-45-generic                  6.8.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-47-generic                  6.8.0-47.47~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-48-generic                  6.8.0-48.48~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image
dad@dadubuntu:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
dad@dadubuntu:~$ uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

rc  linux-image-5.19.0-32-generic                 5.19.0-32.33~22.04.1                        amd64        Signed kernel image generic
rc  linux-image-6.2.0-33-generic                  6.2.0-33.33~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-34-generic                  6.2.0-34.34~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-35-generic                  6.2.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-36-generic                  6.2.0-36.37~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-37-generic                  6.2.0-37.38~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.2.0-39-generic                  6.2.0-39.40~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-14-generic                  6.5.0-14.14~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-15-generic                  6.5.0-15.15~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-17-generic                  6.5.0-17.17~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-18-generic                  6.5.0-18.18~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-21-generic                  6.5.0-21.21~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-25-generic                  6.5.0-25.25~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-26-generic                  6.5.0-26.26~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-27-generic                  6.5.0-27.28~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-28-generic                  6.5.0-28.29~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-35-generic                  6.5.0-35.35~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-41-generic                  6.5.0-41.41~22.04.2                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-44-generic                  6.5.0-44.44~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.5.0-45-generic                  6.5.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-40-generic                  6.8.0-40.40~22.04.3                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-45-generic                  6.8.0-45.45~22.04.1                         amd64        Signed kernel image generic
rc  linux-image-6.8.0-47-generic                  6.8.0-47.47~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-48-generic                  6.8.0-48.48~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image

```

This is super easy
```

sudo dpkg -P `dpkg -l | grep linux-image | grep -v head | grep ^rc | awk {'print $2'}`

```

All those "rc" lines are packages you removed but old configs remain. This cleans them up

---

### Post by ActionParsnip on 2024-11-26
> **Quarkrad said:**
> Hmm.. I did not understand this.  Further reading suggests that the **rc** (release candidate) kernels listed above, for my system, are not actually installed - the only ones installed are the **ii** ones.

Correct

---

### Post by Quarkrad on 2024-11-26
Wow - your command in #8 did the trick.  I now have:

```
 uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image

```

Thank you.  I hopes this sorts out for **colink37**

---

### Post by ActionParsnip on 2024-11-26
> **Quarkrad said:**
> Wow - your command in #8 did the trick.  I now have:

```
 uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image

```

Thank you.  I hopes this sorts out for **colink37**

No worries. If you read the command you can see what's going on

---

### Post by Norm24 on 2024-11-26
> **Quarkrad said:**
> Wow - your command in #8 did the trick.  I now have:

```
 uname -a; echo; dpkg -l | grep linux-image | grep -v head
Linux dadubuntu 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

ii  linux-image-6.8.0-49-generic                  6.8.0-49.49~22.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04                 6.8.0-49.49~22.04.1                         amd64        Generic Linux kernel image

```

Thank you.  I hopes this sorts out for **colink37**

Also if yourself and the OP are so inclined this can also be done through gui using> Ubuntu CleanerJust be aware this is not an officially maintained package,it can be downloaded through Github.

---

### Post by colink37 on 2024-12-01
My thanks to all of you who have been kind enough to suggest solutions.  Please don’t think me rude.  I’ve only had time to check my emails lately because I’m carer for my wife who’s ill.  I’m grateful for all your suggestions and hope to be able to try them soon.  Colin

---

### Post by colink37 on 2024-12-01
To Grahammechanical, thank you.  Sudo apt update, and upgrade, and autoremove caused some actions, but still my disk space was not reduced much.  but afterwards I was able to remove about a dozen, yes, about 12, old generic kernels with Synaptic, however probably 100 old ‘bits’ were still left which couldn’t be marked for removal.  
uname -r showed my latest ‘6.8.0-49-generic’ kernel after running,  
but ls -l .boot returned screen message ‘cannot access ‘.boot’: No such file or directory’ 
Thanks for trying to help me.  If I get a bit of time later, I’ll try ActionParsnips suggestion. Colin

---

### Post by colink37 on 2024-12-02
Thank you ActionParsnip.  Running your code  
uname -a; echo; dpkg -l | grep linux-image | grep -v head  gave me the result

Linux colin-OptiPlex-790 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux 

ii  linux-image-6.8.0-48-generic             6.8.0-48.48~22.04.1                      amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic             6.8.0-49.49~22.04.1                      amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04            6.8.0-49.49~22.04.1                      amd64        Generic Linux kernel image

Is this helpful?  I still have about one hundred left over 'bits' displayed by Synaptic, which I cannot remove or delete using Synaptic.  An example reads

Linux-image-5.15.0-1002-gke   5.15.0-1002.2    signed kernel image gke   It is not installed, but is 11.2 Mb, presumably using **** space.  100 like these  is leaving me with no free and usable dev disk space  Any helpful advice would be appreciated.  Do I have to delete these one by one from a Terminal screen with a 'remove' command?   Colin.

---

### Post by ActionParsnip on 2024-12-03
> **colink37 said:**
> Thank you ActionParsnip.  Running your code  
uname -a; echo; dpkg -l | grep linux-image | grep -v head  gave me the result

Linux colin-OptiPlex-790 6.8.0-49-generic #49~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov  6 17:42:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux 

ii  linux-image-6.8.0-48-generic             6.8.0-48.48~22.04.1                      amd64        Signed kernel image generic
ii  linux-image-6.8.0-49-generic             6.8.0-49.49~22.04.1                      amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04            6.8.0-49.49~22.04.1                      amd64        Generic Linux kernel image

Is this helpful?  I still have about one hundred left over 'bits' displayed by Synaptic, which I cannot remove or delete using Synaptic.  An example reads

Linux-image-5.15.0-1002-gke   5.15.0-1002.2    signed kernel image gke   It is not installed, but is 11.2 Mb, presumably using **** space.  100 like these  is leaving me with no free and usable dev disk space  Any helpful advice would be appreciated.  Do I have to delete these one by one from a Terminal screen with a 'remove' command?   Colin.

You have two kernels. This isn't terrible. You can remove the old one with
```

sudo apt --purge remove linux-image-6.8.0-48-generic
sudo apt autoremove

```

---

### Post by yancek on 2024-12-03
In your initial post, you indicate you have a nearly full disk but have not posted any exact information on it.  Run the df -h command and it will show the size and used for each mounted partition.  Have you checked your log files?  That's often where a disk fills up.  You can get that info with:  sudo du -c -h /var/log.  You can run that command on other directories to see how much data you have.

---

### Post by colink37 on 2024-12-03
Thank you Yancek, I&#8217;ll give that a try tomorrow.  Colin.

---

### Post by colink37 on 2024-12-03
Thank you ActionParsnip.  I&#8217;ll give that a shot tomorrow.  Colin.

---

### Post by colink37 on 2024-12-04
Thank you ActionParsnip.  I&#8217;ll give that a shot tomorrow.  Colin.

---

### Post by colink37 on 2024-12-04
Great, thanks.  Now I&#8217;m getting somewhere.  Appreciated.  Colin37

---

### Post by colink37 on 2024-12-04
Thanks yancek.  That gave me some very useful info.  Colin37

---

