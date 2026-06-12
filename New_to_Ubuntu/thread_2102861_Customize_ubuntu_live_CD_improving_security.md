---
title: "Customize ubuntu live CD improving security"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by savbuntu on 2013-01-08
I'm a beginner of the Unbuntu OS. I'd like to create a live cd to surf in websites like paypal, ebay and keep out malware (in particurally new generation zero day malware that use keylogging and ssl sniffing, often not detected by most av vendors).
For this reason I need help in the creation of live CD: how can I improve security at the highest levels (firewall, read, write, and execute permission)?
Are there security tool Can I add to live CD?

---

### Post by sudodus on 2013-01-08
There are special linux distros targeting hight security. One of them is tails.

[[COLOR="red"]https://tails.boum.org/download/index.en.html[/COLOR]]("https://tails.boum.org/download/index.en.html")

I think it is hard to make it better without a hugh effort. But with a reasonable effort you can make a reasonably safe ubuntu system.

[[COLOR="Red"]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by savbuntu on 2013-01-08
Thanks for reply and thanks to the Ubuntu community.

---

### Post by sudodus on 2013-01-08
You are welcome to the Ubuntu Forums :-)

---

### Post by Derek Karpinski on 2013-01-08
The problem I see with using a Ubuntu live cd is that the ISO gets released once for every version.  There are many security updates that you won't have by running the live cd.  You'll be running outdated/unpatched software.

---

### Post by savbuntu on 2013-01-09
Searching on Google I've found **Lightweight Portable Security (Live CD)** distro  from the US Department of Defense. I've read this distro does not mount to the hard drive of the host computer, then malware in the HDD, even if exist can't interact with linux distro.

 I'd like to know if it was released to the open source development community.

---

### Post by snowpine on 2013-01-09
> **savbuntu said:**
> Searching on Google I've found **Lightweight Portable Security (Live CD)** distro  from the US Department of Defense. I've read this distro does not mount to the hard drive of the host computer, then malware in the HDD, even if exist can't interact with linux distro.

 I'd like to know if it was released to the open source development community.

All Linux live CD's (including Ubuntu) have this feature. I personally would choose Ubuntu over the DOD's distro. Here is a review:

[http://distrowatch.com/weekly.php?issue=20110704#feature](http://distrowatch.com/weekly.php?issue=20110704#feature)

As mentioned above, however, a Live CD will be missing any security updates/patches since the CD was released. Better in my opinion to use an installed system, with all security patches up-to-date, and practice proper security practices as described in this thread:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Ubuntu is quite secure for the typical user out-of-the-box. There is absolutely no need to worry about Windows malware*; Linux is completely immune. :)

* The only concern would be unknowingly passing an infected file from one Windows user to another Windows user. You can use a program such as clam-av to scan the files you forward.

---

### Post by Paqman on 2013-01-09
> **snowpine said:**
> All Linux live CD's (including Ubuntu) have this feature.

I was about to post the same myself, when I remembered that Ubuntu will automatically mount any swap partitions it finds. I suspect other desktop distros may have the same default behaviour.

---

### Post by snowpine on 2013-01-09
> **Paqman said:**
> I was about to post the same myself, when I remembered that Ubuntu will automatically mount any swap partitions it finds. I suspect other desktop distros may have the same default behaviour.

Good point Paqman!

In which case, simply:

```
sudo swapoff -a
```

before beginning your online banking session. :)

---

### Post by Paqman on 2013-01-09
You could also [pass Grub the option]("https://help.ubuntu.com/community/BootOptions"):
```
noswap
```
before booting.

---

### Post by savbuntu on 2013-01-09
I've read the LPS review by distrowatch [http://distrowatch.com/weekly.php?issue=20110704#feature](http://distrowatch.com/weekly.php?issue=20110704#feature)
LPS distro running as root, how can I disable root access after boot CD?
How can I check that distro doesn't mount the hd drive? 
Can I use 
```
sudo swapoff -a
```to disable hard disk mounting?

Are there other security measures that can I apply after boot live CD?

---

### Post by snowpine on 2013-01-09
Linux's 'mount' command is not mysterious. Simply:

```
mount
```

will tell you what is currently mounted. If you see something that is mounted but shouldn't be, you can easily unmount it with 'umount', for example to unmount the 1st partition of the 1st hard drive:

```
sudo umount /dev/sda1
```

But that's kind of tangential to the actual question/issue here. Why do you think that having hard drive partitions mounted (with the possible exception of personal data being temporarily stored in an unencrypted swap partition) will compromise the security of your online banking/shopping?

Also one thing that gets overlooked a lot in these conversations (apologies if I am stating the obvious) is the role of the financial institution. Have you contacted your bank yet to ask what are their policies and procedures with regards to fraud/identity theft? They probably have an entire department of people working on this exact issue who will be glad to discuss and give you some pointers. Because, no matter what software you run or precautions you take or advice we give you here, it is your bank's policies that will determine whether getting hacked is a minor inconvenience or a major life-changing event! :)

---

### Post by savbuntu on 2013-01-09
> **snowpine said:**
> LWhy do you think that having hard drive partitions mounted (with the possible exception of personal data being temporarily stored in an unencrypted swap partition) will compromise the security of your online banking/shopping?


Because if there is resident malware in my hard disk it can compromise live cd security.

---

### Post by snowpine on 2013-01-09
> **savbuntu said:**
> Because if there is resident malware in my hard disk it can compromise live cd security.

Do you have a link or citation to support this statement?

Not saying it is impossible, just that this is the first time I've heard it in my 5 years on these forums. We have pros on these forums who use Linux Live CD's on a daily basis to repair/recover compromised Windows systems. ;)

---

### Post by savbuntu on 2013-01-09
> **snowpine said:**
> Do you have a link or citation to support this statement?

Not saying it is impossible, just that this is the first time I've heard it in my 5 years on these forums. ;)
Unfortunately no. I'm a little bit paranoid penguin ;)

---

