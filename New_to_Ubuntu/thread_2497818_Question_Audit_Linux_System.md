---
title: "Question Audit Linux System"
date: 2024-05-19
forum: New to Ubuntu
---

### Post by bhubunt on 2024-05-19
Hi,
It was recommended to me that I install audit packages for my ubuntu laptop [no personal server, hooked up to commercial modem via wired connection], based on this webpage: [https://www.cyberciti.biz/tips/howto...ccounting.html](https://www.cyberciti.biz/tips/howto...ccounting.html)

The following commands worked fine:
```

ac
ac -d 

```

For 
```
ac -p 
```
the return was 
```
 me                         11.46
    total       11.46 
```


But when I entered 

```
 lastcomm 
``` with my username 
and the same command with tty2 there were no returns.  

Earlier I entered the following commands into the terminal, "netstat", "last," "ls", so shouldn't they show up in the return for my username?   Since I am new to this feature, I'd appreciate feedback.

---

### Post by MAFoElffen on 2024-05-19
As in my last PM to you on how to install that package and it's use... After that part of my PM, I explained that 'lastcomm' does not capture the session or where the user was from. (Though, it does capture many details on exactly what users were logged in, and everything they do on your computer...)

It captures since the package was installed and the auditing turned on. Does that make sense.

Since it doesn't track sessions and where from... That is why I went on the explain that I setup 'w' as a crontab job creating a log file to capture those further details. I explained how to set that up, and how often you should review that... and what to do with that log after reviewing it.

Re-read that last PM...

---

### Post by bhubunt on 2024-05-19
OK.

Shouldn't there be a root ref in the return for 

```
 ac -p  
```  ?

Or did I get that wrong?

---

### Post by #&amp;thj^% on 2024-05-19
Mine:
```
ac -p
	me                                  37.74
	total       37.74
root@me-Legion-5-zfs:/home/me# ac -a
	total       37.75
root@me-Legion-5-zfs:/home/me# ac -ap
	me                                  37.75
	total       37.75

```
Understanding will become easier as you learn with it. What it does what it can not do....on and on.
```
 ac -d
May  6	total        7.94
May  7	total        5.21
May  8	total        4.96
May 10	total        1.73
May 11	total        7.39
May 12	total        1.07
May 14	total        0.18
May 15	total        4.94
May 17	total        2.52
Today	total        1.81

```
It's a good place to start looking for foul play.

---

### Post by #&amp;thj^% on 2024-05-20
Another tool I use is Lynis : [https://www.howtogeek.com/674288/how-to-audit-your-linux-systems-security-with-lynis/](https://www.howtogeek.com/674288/how-to-audit-your-linux-systems-security-with-lynis/)

Lynis performs a suite of automated tests that thoroughly inspect many system components and settings of your Linux operating system. Please read all the information covered on the page link, also some extra plugins are available.

Also pertaining to your "lastcomm" not showing a return, I'm currently working on a bug I found with it, so give it some time to investigate that.
Currently on 24.10 Testing "lastcomm"
```
lastcomm
*** buffer overflow detected ***: terminated
Aborted (core dumped)

```

Also your query on a tty2 session:
```
last tty2

wtmp begins Mon May  6 10:14:09 2024

```
That is verified by me as my user logged in at that time.
Today's "last"
```
last
me       tty7         :0               Mon May 20 09:57    gone - no logout
reboot   system boot  6.8.0-31-generic Mon May 20 09:57   still running

```

Like I said the more you use these utility's the more will become evident.

---

### Post by bhubunt on 2024-05-20
Thanks for the Lynus tool.

In the return there were a lot of red warnings, for example, under 

Users, Groups and Authentication

```

- Locked accounts                                           [ FOUND ] (in red)
- Permissions for directory: /etc/sudoers.d               [ WARNING ] (in red)  
```

---

### Post by #&amp;thj^% on 2024-05-20
Lynis expects /etc/sudoers.d to be unreadable by &#8220;others&#8221;, i.e. rwx[r-][w-][x-]---. If you run
```
chmod 750 /etc/sudoers.d
```
It should fix that warning.
```
 - Sudoers file(s)                                           [ FOUND ]
    - Permissions for directory: /etc/sudoers.d               [ OK ]
    - Permissions for: /etc/sudoers                           [ OK ]
    - Permissions for: /etc/sudoers.d/README                  [ OK ]

```
The information should have been logged in the Lynis log file... 
As for the Locked Accounts see this: [https://cisofy.com/lynis/controls/AUTH-9218/](https://cisofy.com/lynis/controls/AUTH-9218/)

---

### Post by #&amp;thj^% on 2024-05-20
Some of the first checks I look at to see if any further action is needed by me:
This I consider after running lynis a good thing:
```
[+] Home directories
------------------------------------
  - Permissions of home directories                           [ OK ]
  - Ownership of home directories                             [ OK ]
  - Checking shell history files                              [ OK ]

```
This is key as well:
```
[+] Cryptography
------------------------------------
  - Checking for expired SSL certificates [0/151]             [ NONE ]

  [WARNING]: Test CRYP-7902 had a long execution: 18.630953 seconds

  - Found 1 LUKS encrypted block devices.                     [ OK ]
  - Found 0 encrypted and 1 unencrypted swap devices in use.  [ OK ]
  - Kernel entropy is sufficient                              [ YES ]
  - HW RNG & rngd                                             [ NO ]
  - SW prng                                                   [ NO ]
  MOR-bit set                                                 [ YES ]

```

This part is not to be ignored:
```
- blueman-mechanism.service:                          [ UNSAFE ]
        - bluetooth.service:                                  [ MEDIUM ]
```
```
sudo systemctl disable bluetooth
[sudo] password for me: 
Synchronizing state of bluetooth.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install disable bluetooth
Removed "/etc/systemd/system/bluetooth.target.wants/bluetooth.service".
Removed "/etc/systemd/system/dbus-org.bluez.service".

```
We have a well known user that was hacked through bluetooth, so keep it disabled when not needed.

Security is a Life Long learning process.

---

### Post by bhubunt on 2024-05-21
> **1fallen said:**
> Lynis expects /etc/sudoers.d to be unreadable by “others”, i.e. rwx[r-][w-][x-]---. If you run
```
chmod 750 /etc/sudoers.d
```


This is what I get when entering the command, with and without sudo 

```
 XXX-ThinkPad-X240:~$ chmod 750 /etc/sudoers.d
chmod: changing permissions of '/etc/sudoers.d': Operation not permitted
XXX-ThinkPad-X240:~$ sudo chmod 750 /etc/sudoers.d
[sudo] password for XXX: 
XXX-ThinkPad-X240:~$  
```

---

### Post by bhubunt on 2024-05-21
> **1fallen said:**
> Lynis expects /etc/sudoers.d to be unreadable by &#8220;others&#8221;, i.e. rwx[r-][w-][x-]---. If you run
```
chmod 750 /etc/sudoers.d
```


This is what I get when entering the command, with and without sudo 

```
 XXX-ThinkPad-X240:~$ chmod 750 /etc/sudoers.d
chmod: changing permissions of '/etc/sudoers.d': Operation not permitted
XXX-ThinkPad-X240:~$ sudo chmod 750 /etc/sudoers.d
[sudo] password for XXX: 
XXX-ThinkPad-X240:~$  
```

---

### Post by bhubunt on 2024-05-21
> **1fallen said:**
> Lynis expects /etc/sudoers.d to be unreadable by “others”, i.e. rwx[r-][w-][x-]---. If you run
```
chmod 750 /etc/sudoers.d
```


This is what I get when entering the command, with and without sudo 

```
 XXX-ThinkPad-X240:~$ chmod 750 /etc/sudoers.d
chmod: changing permissions of '/etc/sudoers.d': Operation not permitted
XXX-ThinkPad-X240:~$ sudo chmod 750 /etc/sudoers.d
[sudo] password for XXX: 
XXX-ThinkPad-X240:~$  
```

---

### Post by bhubunt on 2024-05-21
Just did another Lynus scan to compare my results to yours.

How to fix the warning Home Directories?

```
 Home directories
------------------------------------
  - Permissions of home directories                           [ WARNING ]
  - Ownership of home directories                             [ OK ]
  - Checking shell history files                              [ OK ]

```

There was also the following warning. How to take care of it? 

```
   -[ Lynis 3.0.7 Results ]-

  Warnings (1):
  ----------------------------
  ! Found one or more vulnerable packages. [PKGS-7392] 
      https://cisofy.com/lynis/controls/PKGS-7392/

  
```

I had the bluetooth removed on this laptop.

---

### Post by #&amp;thj^% on 2024-05-21
First yes Admin or sudo will always be needed with a "chmod" along with any "/etc" changes.
  Interesting warning "- Permissions of home directories                           [ WARNING ]"
  
  Can you show me this please:
  ```
 stat /home/<your-user-here>
```
  And this:
  ```
ls -al
```
  
  Just a heads up, > I'm going to be on and offline today.
  
  Nice Job on the bluetooth part, one less thing to worry about.

---

### Post by MAFoElffen on 2024-05-21
I have to say something tonight.

You "are" on someone's radar. The way things have gone with your machine with two separate breaches, some one has an interest in that...

You have done that a few times about permissions, from not being tech aware... Which demonstrate and point back to the importance of "you" changing your passwords every so often (because whoever had the old password(s), then that is no good to them any longer), and the importance of creating a few more accounts as non-admin users for anything on the internet, if if breached, cannot do bad things to your computer on those accounts.

That start to make more sense now?

Have you taken those steps yet?

1fallen and I use tools to look for indicators that something might be amiss. But...
We have dealt with Security issues on systems. We have had some experience with what to do to keep ourselves, the systems we have supported, and other Users safe. We have set up best practices to try to ensure they stay safe.
We have some knowledge and experience.

You have things to learn and get in the habit of doing, to try to stay safe...

You can "investigate"... That is good to understand 'what happened'. But that doesn't fix you from what happened and happening again (yet). Now, and in the mean time, you really need to harden your 22.04 system.
 
*** Sidenote: It takes about 2-3 years for those standards to come out, after an LTS is released, for just the standards to release forthat Distro Release... Before a Distro can work on trying to comply to those. So for forget about going to 24.04 for awhile (for you).

You want to get a head start on that? 

You have 5 free machines covered by Ubuntu Pro. I don't usually go around, openly recommending that to people. But in your case, there is a point to me recommending it to you. The [DISA-STIG]("https://ubuntu.com/blog/disa-stig-ubuntu-22-04-lts"). Running one script will automatically harden your machine to Government standards. That is available to you for free under Ubuntu Pro.

That still does not free you from practicing safe habits...

---

### Post by #&amp;thj^% on 2024-05-21
+1 with>>>>You "are" on someone's radar.

---

### Post by bhubunt on 2024-05-24
Sorry for the late reply

> **1fallen said:**
> 
  Interesting warning "- Permissions of home directories                           [ WARNING ]"
  
  Can you show me this please:
  ```
 stat /home/<your-user-here>
```
  And this:
  ```
ls -al
```
  
  


Here are the results. Why does it say modify and change on May 21 2024? Judging from my next post, see below, that change seems to relate to Lynus? Or perhaps not/not only?

```
 me-ThinkPad-X240:~$ stat /home/me
  File: /home/me
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: fc01h/64513d    Inode: 3407874     Links: 19
Access: (0755/drwxr-xr-x)  Uid: ( 1000/me)   Gid: ( 1000/ me)
Access: 2024-05-24 07:46:17.659750132 +0200
Modify: 2024-05-21 19:33:52.889471682 +0200
Change: 2024-05-21 19:33:52.889471682 +0200
 Birth: 2023-08-29 13:59:29.490114563 +0200 
```

---

### Post by bhubunt on 2024-05-24
> **1fallen said:**
> 
  ```
ls -al
```
  
  Just a heads up, > I'm going to be on and offline today.
  
  Nice Job on the bluetooth part, one less thing to worry about.

Here is the result, just the top part and the final part listed. In the in-between part are 9 pdfs, mostly gmail conversations, including 3 about or the lawyer I am consulting about the breaches of my system. The pdfs are all from in between April 11 2024 and May 20 2024. 

In reviewing this output,  keep in mind that I am not a high-tech ubuntu user. So I don't typically make technical changes -- mostly only when I am asked to type in commands by people on the ubuntu forum trying to help me. 


Aug 29 2023 is when I installed my current OS.




```

ls -al
total 9408
drwxr-xr-x 19 me me    4096 Mai 21 19:33  .
drwxr-xr-x  3 root    root       4096 Aug 29  2023  ..
-rw-------  1 me me    4326 Mai 24 10:08  .bash_history
-rw-r--r--  1 me me     220 Aug 29  2023  .bash_logout
-rw-r--r--  1 me me    3771 Aug 29  2023  .bashrc
drwx------ 22 me me    4096 Mär  5 09:35  .cache
drwx------ 21 me me    4096 Feb  9 11:22  .config
drwxr-xr-x  3 me me     4096 Okt 24  2023  Desktop
drwxr-xr-x  4 me me    4096 Mai 24 12:24  Documents
drwxr-xr-x 84 me me   36864 Mai 24 09:13  Downloads

(...) Part skipped with 9 pdfs  but here's a sample: -rw-rw-r--  1 me me  89455 Mai 20 10:51 'Gmail - Name of Lawyer .pdf'


drwx------  3 me me     4096 Mai 14 19:57  .gnupg
(...)
-rw-rw-r--  1 me me     0 Mai 21 15:25  .lesshsQ
drwxr-xr-x  3 me me   4096 Aug 29  2023  .local
-rw-rw-r--  1 me me   1611 Okt 16  2023 'log messages'
-rw-rw-r--  1 me me   111939 Okt 19  2023 'log messages.18.10.2023.hacked.between.12.and.13u'
-rw-r-----  1 me me     169 Mai 21 19:33  lynis.log
-rw-r-----  1 me me       0 Mai 21 19:33  lynis-report.dat
drwx------  4 greener greener    4096 Okt  4  2023  .mozilla
(...)
-rw-r--r--  1 me me  807 Aug 29  2023  .profile
drwx------  8 me me    4096 Nov  7  2023  snap
drwx------  2 me me     4096 Sep  5  2023  .ssh
-rw-r--r--  1 me me       0 Sep  5  2023  .sudo_as_admin_successful

-rw-rw-r--  1 me me     168 Okt 23  2023  .wget-hsts
drwxrwxr-x  4 me me    4096 Okt 29  2023  .wine  
```

---

### Post by bhubunt on 2024-05-24
> **MAFoElffen said:**
> I have to say something tonight.

You "are" on someone's radar. The way things have gone with your machine with two separate breaches, some one has an interest in that...

..

Sorry for the late reply. I will get in touch with you via PM.

---

