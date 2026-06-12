---
title: "openssh-server fails to startup"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by bobjohnbowles on 2012-07-03
I have 2 Ubuntu (64-bit) laptops and an Ubuntu lan server (32-bit) all running openssh-server. All 3 machines are running 12.04 LTS and are regularly kept up to date.
Until a couple of weeks ago everything worked fine, all the machines could talk to each other. Then, the two laptops just stopped talking to each other. Having done a lot of homework and browsing the web for answers, so far all I have achieved is a more accurate idea of the problem.
The ssh servers on both the laptops fail to startup, either at boot time or manually, but there is no error message. I can manually start, and immediately check the ports with netstat, and port 22 is empty.
The server's ssh server continues to function happily, and both the laptops can ssh to it, but I really need to be able to transfer files etc between the two laptops.
I have tried all the obvious things like checking the configuration, re-installing... If anyone has any ideas I would be grateful for some inspiration. TIA.

Here is a sample terminal session indicating the problem:

```
bob@bobInspiron:~$ sudo service ssh restart
stop: Unknown instance: 
ssh start/running, process 3971
bob@bobInspiron:~$ sudo netstat -tulpn | grep :22
bob@bobInspiron:~$ ps aux | grep sshd
bob       4538  0.0  0.0  13164   956 pts/0    S+   08:35   0:00 grep --color=auto sshd
bob@bobInspiron:~$
```

---

### Post by ajgreeny on 2012-07-03
> The ssh servers on both the laptops fail to startup, either at boot time  or manually, but there is no error message. I can manually start, and  immediately check the ports with netstat, and port 22 is empty.What do you mean by this?
You say ssh fails to start at boot or manually, then say you can manually start ssh, so I don't follow your arguments or sequence of events.

What is the output of ```
sudo service ssh start
``` on the machines when ssh is not running?

What does ```
ps aux | grep sshd
```show, again on machine, first when ssh is, and then is not running?

And finally, what is the content of **/etc/init/ssh.conf**;  has the "start on filesystem - -" line been commented out for some strange reason you are not aware of?

---

### Post by Lars Noodén on 2012-07-03
When you try to start the server manually, you can keep it from dropping in to the background with -D

```

/usr/sbin/sshd -D

```

You can also increase the verbosity of the messaging by adding up to three -d 

```

/usr/sbin/sshd -Ddd

```

You can also look in the log files to see what errors have been collected so far.  The log file to look at is /var/log/auth.log

---

### Post by bobjohnbowles on 2012-07-03
Thanks for this, Lars. I found an interesting message when ssh stayed in the foreground. Not sure what it means, but here is the output:


```
bob@bobInspiron:~$ sudo /usr/sbin/sshd -D
*** glibc detected *** /usr/sbin/sshd: double free or corruption (out): 0x00007fed29f50870 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7e626)[0x7fed27aa1626]
/lib/x86_64-linux-gnu/liblsp.so(freeaddrinfo+0x13a)[0x7fed29760da2]
/usr/sbin/sshd(main+0x1777)[0x7fed29b96967]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7fed27a4476d]
/usr/sbin/sshd(+0xfe89)[0x7fed29b97e89]
======= Memory map: ========
7fed2657d000-7fed26592000 r-xp 00000000 08:01 524292                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fed26592000-7fed26791000 ---p 00015000 08:01 524292                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fed26791000-7fed26792000 r--p 00014000 08:01 524292                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fed26792000-7fed26793000 rw-p 00015000 08:01 524292                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fed26793000-7fed2679f000 r-xp 00000000 08:01 538365                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7fed2679f000-7fed2699e000 ---p 0000c000 08:01 538365                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7fed2699e000-7fed2699f000 r--p 0000b000 08:01 538365                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7fed2699f000-7fed269a0000 rw-p 0000c000 08:01 538365                     /lib/x86_64-linux-gnu/libnss_files-2.15.so
7fed269a0000-7fed269aa000 r-xp 00000000 08:01 538366                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7fed269aa000-7fed26baa000 ---p 0000a000 08:01 538366                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7fed26baa000-7fed26bab000 r--p 0000a000 08:01 538366                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7fed26bab000-7fed26bac000 rw-p 0000b000 08:01 538366                     /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7fed26bac000-7fed26bb4000 r-xp 00000000 08:01 538368                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7fed26bb4000-7fed26db3000 ---p 00008000 08:01 538368                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7fed26db3000-7fed26db4000 r--p 00007000 08:01 538368                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7fed26db4000-7fed26db5000 rw-p 00008000 08:01 538368                     /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7fed26db5000-7fed26dcd000 r-xp 00000000 08:01 536995                     /lib/x86_64-linux-gnu/libresolv-2.15.so
7fed26dcd000-7fed26fcd000 ---p 00018000 08:01 536995                     /lib/x86_64-linux-gnu/libresolv-2.15.so
7fed26fcd000-7fed26fce000 r--p 00018000 08:01 536995                     /lib/x86_64-linux-gnu/libresolv-2.15.so
7fed26fce000-7fed26fcf000 rw-p 00019000 08:01 536995                     /lib/x86_64-linux-gnu/libresolv-2.15.so
7fed26fcf000-7fed26fd1000 rw-p 00000000 00:00 0 
7fed26fd1000-7fed26fd4000 r-xp 00000000 08:01 524362                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7fed26fd4000-7fed271d3000 ---p 00003000 08:01 524362                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7fed271d3000-7fed271d4000 r--p 00002000 08:01 524362                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7fed271d4000-7fed271d5000 rw-p 00003000 08:01 524362                     /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7fed271d5000-7fed271dc000 r-xp 00000000 08:01 396203                     /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7fed271dc000-7fed273db000 ---p 00007000 08:01 396203                     /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7fed273db000-7fed273dc000 r--p 00006000 08:01 396203                     /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7fed273dc000-7fed273dd000 rw-p 00007000 08:01 396203                     /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7fed273dd000-7fed27402000 r-xp 00000000 08:01 393830                     /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7fed27402000-7fed27602000 ---p 00025000 08:01 393830                     /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7fed27602000-7fed27603000 r--p 00025000 08:01 393830                     /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7fed27603000-7fed27604000 rw-p 00026000 08:01 393830                     /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7fed27604000-7fed27605000 rw-p 00000000 00:00 0 
7fed27605000-7fed2761c000 r-xp 00000000 08:01 536996                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7fed2761c000-7fed2781b000 ---p 00017000 08:01 536996                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7fed2781b000-7fed2781c000 r--p 00016000 08:01 536996                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7fed2781c000-7fed2781d000 rw-p 00017000 08:01 536996                     /lib/x86_64-linux-gnu/libnsl-2.15.so
7fed2781d000-7fed2781f000 rw-p 00000000 00:00 0 
7fed2781f000-7fed27821000 r-xp 00000000 08:01 538372                     /lib/x86_64-linux-gnu/libdl-2.15.so
7fed27821000-7fed27a21000 ---p 00002000 08:01 538372                     /lib/x86_64-linux-gnu/libdl-2.15.so
7fed27a21000-7fed27a22000 r--p 00002000 08:01 538372                     /lib/x86_64-linux-gnu/libdl-2.15.so
7fed27a22000-7fed27a23000 rw-p 00003000 08:01 538372                     /lib/x86_64-linux-gnu/libdl-2.15.so
7fed27a23000-7fed27bd6000 r-xp 00000000 08:01 528225                     /lib/x86_64-linux-gnu/libc-2.15.so
7fed27bd6000-7fed27dd5000 ---p 001b3000 08:01 528225                     /lib/x86_64-linux-gnu/libc-2.15.so
7fed27dd5000-7fed27dd9000 r--p 001b2000 08:01 528225                     /lib/x86_64-linux-gnu/libc-2.15.so
7fed27dd9000-7fed27ddb000 rw-p 001b6000 08:01 528225                     /lib/x86_64-linux-gnu/libc-2.15.so
7fed27ddb000-7fed27de0000 rw-p 00000000 00:00 0 
7fed27de0000-7fed27de3000 r-xp 00000000 08:01 528760                     /lib/x86_64-linux-gnu/libcom_err.so.2.1
7fed27de3000-7fed27fe2000 ---p 00003000 08:01 528760                     /lib/x86_64-linux-gnu/libcom_err.so.2.1
7fed27fe2000-7fed27fe3000 r--p 00002000 08:01 528760                     /lib/x86_64-linux-gnu/libcom_err.so.2.1
7fed27fe3000-7fed27fe4000 rw-p 00003000 08:01 528760                     /lib/x86_64-linux-gnu/libcom_err.so.2.1
7fed27fe4000-7fed280a8000 r-xp 00000000 08:01 396196                     /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7fed280a8000-7fed282a7000 ---p 000c4000 08:01 396196                     /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7fed282a7000-7fed282b1000 r--p 000c3000 08:01 396196                     /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7fed282b1000-7fed282b2000 rw-p 000cd000 08:01 396196                     /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7fed282b2000-7fed282ed000 r-xp 00000000 08:01 393808                     /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7fed282ed000-7fed284ed000 ---p 0003b000 08:01 393808                     /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7fed284ed000-7fed284ee000 r--p 0003b000 08:01 393808                     /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7fed284ee000-7fed284f0000 rw-p 0003c000 08:01 393808                     /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7fed284f0000-7fed284f9000 r-xp 00000000 08:01 538367                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7fed284f9000-7fed286f9000 ---p 00009000 08:01 538367                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7fed286f9000-7fed286fa000 r--p 00009000 08:01 538367                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7fed286fa000-7fed286fb000 rw-p 0000a000 08:01 538367                     /lib/x86_64-linux-gnu/libcrypt-2.15.so
7fed286fb000-7fed28729000 rw-p 00000000 00:00 0 
7fed28729000-7fed2873f000 r-xp 00000000 08:01 528882                     /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fed2873f000-7fed2893e000 ---p 00016000 08:01 528882                     /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fed2893e000-7fed2893f000 r--p 00015000 08:01 528882                     /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fed2893f000-7fed28940000 rw-p 00016000 08:01 528882                     /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7fed28940000-7fed28942000 r-xp 00000000 08:01 538369                     /lib/x86_64-linux-gnu/libutil-2.15.so
7fed28942000-7fed28b41000 ---p 00002000 08:01 538369                     /lib/x86_64-linux-gnu/libutil-2.15.so
7fed28b41000-7fed28b42000 r--p 00001000 08:01 538369                     /lib/x86_64-linux-gnu/libutil-2.15.so
7fed28b42000-7fed28b43000 rw-p 00002000 08:01 538369                     /lib/x86_64-linux-gnu/libutil-2.15.so
7fed28b43000-7fed28ce2000 r-xp 00000000 08:01 524393                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7fed28ce2000-7fed28ee1000 ---p 0019f000 08:01 524393                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7fed28ee1000-7fed28efc000 r--p 0019e000 08:01 524393                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7fed28efc000-7fed28f07000 rw-p 001b9000 08:01 524393                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7fed28f07000-7fed28f0b000 rw-p 00000000 00:00 0 
7fed28f0b000-7fed28f23000 r-xp 00000000 08:01 538378                     /lib/x86_64-linux-gnu/libpthread-2.15.so
7fed28f23000-7fed29122000 ---p 00018000 08:01 538378                     /lib/x86_64-linux-gnu/libpthread-2.15.so
7fed29122000-7fed29123000 r--p 00017000 08:01 538378                     /lib/x86_64-linux-gnu/libpthread-2.15.so
7fed29123000-7fed29124000 rw-p 00018000 08:01 538378                     /lib/x86_64-linux-gnu/libpthread-2.15.so
7fed29124000-7fed29128000 rw-p 00000000 00:00 0 
7fed29128000-7fed29145000 r-xp 00000000 08:01 533600                     /lib/x86_64-linux-gnu/libselinux.so.1
7fed29145000-7fed29344000 ---p 0001d000 08:01 533600                     /lib/x86_64-linux-gnu/libselinux.so.1
7fed29344000-7fed29345000 r--p 0001c000 08:01 533600                     /lib/x86_64-linux-gnu/libselinux.so.1
7fed29345000-7fed29346000 rw-p 0001d000 08:01 533600                     /lib/x86_64-linux-gnu/libselinux.so.1
7fed29346000-7fed29347000 rw-p 00000000 00:00 0 
7fed29347000-7fed29353000 r-xp 00000000 08:01 533680                     /lib/x86_64-linux-gnu/libpam.so.0.83.0
7fed29353000-7fed29553000 ---p 0000c000 08:01 533680                     /lib/x86_64-linux-gnu/libpam.so.0.83.0
7fed29553000-7fed29554000 r--p 0000c000 08:01 533680                     /lib/x86_64-linux-gnu/libpam.so.0.83.0
7fed29554000-7fed29555000 rw-p 0000d000 08:01 533680                     /lib/x86_64-linux-gnu/libpam.so.0.83.0
7fed29555000-7fed2955d000 r-xp 00000000 08:01 528368                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fed2955d000-7fed2975c000 ---p 00008000 08:01 528368                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fed2975c000-7fed2975d000 r--p 00007000 08:01 528368                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fed2975d000-7fed2975e000 rw-p 00008000 08:01 528368                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fed2975e000-7fed29762000 r-xp 00000000 08:01 525141                     /lib/x86_64-linux-gnu/liblsp.so
7fed29762000-7fed29961000 ---p 00004000 08:01 525141                     /lib/x86_64-linux-gnu/liblsp.so
7fed29961000-7fed29962000 r--p 00003000 08:01 525141                     /lib/x86_64-linux-gnu/liblsp.so
7fed29962000-7fed29963000 rw-p 00004000 08:01 525141                     /lib/x86_64-linux-gnu/liblsp.so
7fed29963000-7fed29985000 r-xp 00000000 08:01 534542                     /lib/x86_64-linux-gnu/ld-2.15.so
7fed29b59000-7fed29b63000 rw-p 00000000 00:00 0 
7fed29b7e000-7fed29b7f000 rw-p 00000000 00:00 0 
7fed29b7f000-7fed29b83000 rw-s 00000000 00:04 0                          /SYSVa5723213 (deleted)
7fed29b83000-7fed29b85000 rw-p 00000000 00:00 0 
7fed29b85000-7fed29b86000 r--p 00022000 08:01 534542                     /lib/x86_64-linux-gnu/ld-2.15.so
7fed29b86000-7fed29b88000 rw-p 00023000 08:01 534542                     /lib/x86_64-linux-gnu/ld-2.15.so
7fed29b88000-7fed29c02000 r-xp 00000000 08:01 394433                     /usr/sbin/sshd
7fed29e02000-7fed29e05000 r--p 0007a000 08:01 394433                     /usr/sbin/sshd
7fed29e05000-7fed29e06000 rw-p 0007d000 08:01 394433                     /usr/sbin/sshd
7fed29e06000-7fed29e0f000 rw-p 00000000 00:00 0 
7fed29f4b000-7fed29f6c000 rw-p 00000000 00:00 0                          [heap]
7fff69d73000-7fff69d94000 rw-p 00000000 00:00 0                          [stack]
7fff69dff000-7fff69e00000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
bob@bobInspiron:~$
```

---

### Post by bobjohnbowles on 2012-07-03
The /var/log/auth.log file contains no useful information. It records sshd listening on port 22, but there is nothing to indicate the daemon has aborted.

---

### Post by CharlesA on 2012-07-03
Have you already purged and reinstalled openssh-server?

My guess is a botched sshd_config file.

---

### Post by bobjohnbowles on 2012-07-03
Hi Charles, the example here is from a purged and re-installed openssh-server. BTW thx for adding the code tags, I am still finding my way round the editor :/

---

### Post by CharlesA on 2012-07-03
Try this sshd_config file:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

It is the stock one from 12.04.

---

### Post by bobjohnbowles on 2012-07-03
Hi Charles, the above file made no difference at all. Checking in a file comparison tool it was identical to the existing one except for some white-space characters in a comment line.
Looking at the output from Lars' suggestion running sshd in the foreground, does this mean some of the core libraries may have been corrupted? If so, can these files be safely reinstalled?

---

### Post by CharlesA on 2012-07-03
I guess you could try reinstalling glibc. I dunno tho, as I've never run into that problem and the only [thread I found]("http://ubuntuforums.org/showthread.php?t=2013205") was solved via reinstall.

See here also:
[http://serverfault.com/questions/169829/what-does-glibc-detected-httpd-double-free-or-corruption-mean](http://serverfault.com/questions/169829/what-does-glibc-detected-httpd-double-free-or-corruption-mean)

---

### Post by bobjohnbowles on 2012-07-04
Ouch!

---

### Post by CharlesA on 2012-07-04
Try starting ssh again and then check dmesg. That might have a different error message.

---

### Post by bobjohnbowles on 2012-07-04
Is there a way I could use something like md5sum to check the integrity of the libraries before I start randomly reinstalling them? Like, is there a published list somewhere of what the checksums should be for the different libraries?

---

### Post by bobjohnbowles on 2012-07-04
Here is the tail of the dmesg output from the manual restart using the service command: 


```
[ 5084.883354] init: ssh main process (5488) killed by ABRT signal
[ 5084.883479] init: ssh main process ended, respawning
[ 5084.929928] init: ssh main process (5491) killed by ABRT signal
[ 5084.930056] init: ssh main process ended, respawning
[ 5084.972247] init: ssh main process (5494) killed by ABRT signal
[ 5084.972371] init: ssh main process ended, respawning
[ 5085.018568] init: ssh main process (5497) killed by ABRT signal
[ 5085.018705] init: ssh main process ended, respawning
[ 5085.067189] init: ssh main process (5500) killed by ABRT signal
[ 5085.067331] init: ssh main process ended, respawning
[ 5085.113011] init: ssh main process (5503) killed by ABRT signal
[ 5085.113133] init: ssh main process ended, respawning
[ 5085.154011] init: ssh main process (5506) killed by ABRT signal
[ 5085.154133] init: ssh main process ended, respawning
[ 5085.192997] init: ssh main process (5509) killed by ABRT signal
[ 5085.193152] init: ssh main process ended, respawning
[ 5085.233641] init: ssh main process (5512) killed by ABRT signal
[ 5085.233765] init: ssh main process ended, respawning
[ 5085.275687] init: ssh main process (5515) killed by ABRT signal
[ 5085.275818] init: ssh main process ended, respawning
[ 5085.313677] init: ssh main process (5518) killed by ABRT signal
[ 5085.313796] init: ssh respawning too fast, stopped
bob@bobInspiron:~$
```

I am not sure this really tells us much more than we already know, except that ssh attempts to restart several times before dying.

---

### Post by CharlesA on 2012-07-04
I had sshd do the same thing when I messed up the config file. If the one you have there now is the same as the default, that shouldn't be a problem.

Try this:

```
sudo apt-get purge openssh-server
```

Then check to see if there is anything is /etc/ssh/
If there is, rename it to something else like /etc/sshold

Then reinstall openssh-server

---

### Post by bobjohnbowles on 2012-07-06
I have just completed a total reinstall of 12.04 on one of my laptops, and the problem with sshd remains. The daemon fails to start.

I don't know what has happened, but it used to work fine, and now it does not. I am at a loss what to do. 

I just tried dropbear, and exactly the same thing happens, crash on startup. The stack trace even listed the same libraries...

---

### Post by CharlesA on 2012-07-06
Huh. Have you submitted a bug report to launchpad? Maybe there is something wrong with that library.

---

### Post by bobjohnbowles on 2012-07-08
I guess I kind of assumed that, being a bit of a newbie on the forums, someone else would already have been there, done that. It is hard to imagine someone not noticing sshd not working.

Filed a new bug report in Launchpad, cross-referencing this thread:
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1022434]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1022434")

---

### Post by Conzar on 2012-07-09
I have the same problem both with sshd and samba server.  I have tried this with both a fresh install of 11.10 and an upgrade from 11.04 to 11.10.

Here is the gist of the samba segfault from glibc
```
*** glibc detected *** smbd: free(): invalid pointer: 0x00007f67057cb750 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7a6e6)[0x7f66fff446e6]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f66fff489cc]
/lib/x86_64-linux-gnu/liblsp.so(freeaddrinfo+0x13a)[0x7f6702b03da2]
smbd(+0x3498eb)[0x7f67032728eb]
smbd(main+0x985)[0x7f6703014085]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f66ffeeb30d]
smbd(+0xeb6dd)[0x7f67030146dd]

```

SSHD segfault
```
*** glibc detected *** /usr/sbin/sshd: double free or corruption (out): 0x00007f8b84edd840 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7a6e6)[0x7f8b81ca86e6]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f8b81cac9cc]
/lib/x86_64-linux-gnu/liblsp.so(freeaddrinfo+0x13a)[0x7f8b83931da2]
/usr/sbin/sshd(main+0x1777)[0x7f8b83d654c7]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f8b81c4f30d]
/usr/sbin/sshd(+0xf919)[0x7f8b83d66919]
```

[Update] added to bug report

---

### Post by CharlesA on 2012-07-09
Conzar, please add a comment to the but report in the above post and click on the pen next to "This bug affects 1 person. Does this bug affect you?" You will need an OpenID (launchpad) account to comment.

---

### Post by bobjohnbowles on 2012-07-10
Conzar, that looks a lot like the kind of thing I am seeing. If you can, see if you can add a crash report to the Launchpad bug, I think the moderator was not happy about my original post there because the crash report was missing. It is kind of reassuring this isn't just me it is happening to.

And yes, I have noticed Samba mis-behaving on the same machine, but I am not sure if this is related.

---

### Post by Conzar on 2012-07-10
> **bobjohnbowles said:**
> If you can, see if you can add a crash report to the Launchpad bug,.
Will do.  I'll do that when I get home from work.  I also found a nice [guide]("https://help.ubuntu.com/community/ReportingBugs") on how to do this.

[Updated] Added a crash report - well I think I did but I don't see it.  How does it work submitting a crash report to an existing bug report?  Does the admin need to approve it before it shows up?

---

### Post by bobjohnbowles on 2012-07-17
After a couple of IRC chats with Robie Basak at Canonical and a couple of experiments I have found a solution.

It turns out the liblsp.so library belongs to my vpn software package. I had been given a beta version, and it was this that was causing the problems.

Solution is simple, I uninstalled the beta version and re-installed the older stable version of the vpn client. sshd worked straight away.

This is NOT a problem with the provider's mainstream software, this was a beta client I was using.

I have marked the bug as 'invalid' since it does not fit with any Launchpad project, but I will take this up with the vpn provider, as I am sure they will want to resolve the issue on their own behalf before main release of their software.

---

### Post by CharlesA on 2012-07-17
Glad you were able to figure out what was causing the issue. Hopefully the VPN vendor gets the issues fixed with their beta (cuz it's beta software, afterall. :p)

---

