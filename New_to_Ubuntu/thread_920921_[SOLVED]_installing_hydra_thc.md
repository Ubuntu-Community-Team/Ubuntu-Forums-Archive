---
title: "[SOLVED] installing hydra thc"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by mike22 on 2008-09-15
I'm trying to install hydra thc. I did ./configure and it seemed to work. However when I type in make and make install I get these errors:


**make and make install errors**

```
gcc -I. -Wall -O2 -c hydra-sip.c -DLIBPOSTGRES 
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function &#8216;md5_crypt&#8217;:
hydra-sip.c:24: error: &#8216;MD5_DIGEST_LENGTH&#8217; undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
hydra-sip.c:26: error: expected &#8216;;&#8217; before &#8216;c&#8217;
hydra-sip.c:31: warning: implicit declaration of function &#8216;MD5_Init&#8217;
hydra-sip.c:31: error: &#8216;c&#8217; undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function &#8216;MD5_Update&#8217;
hydra-sip.c:33: warning: implicit declaration of function &#8216;MD5_Final&#8217;
hydra-sip.c:24: warning: unused variable &#8216;md5_raw&#8217;
hydra-sip.c: In function &#8216;sip_register&#8217;:
hydra-sip.c:60: error: &#8216;MD5_DIGEST_LENGTH&#8217; undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable &#8216;resp&#8217;
hydra-sip.c:61: warning: unused variable &#8216;mu&#8217;
hydra-sip.c:60: warning: unused variable &#8216;urp&#8217;
make: *** [hydra-sip.o] Error 1

```

---

### Post by houbysoft.xf.cz on 2008-09-15
Do a
```

sudo apt-get install libssl-dev

```
then reconfigure, make, and make install.

---

### Post by gauntface on 2008-09-15
Im assuming you havent got some openssl library installed, so have a look in synaptic package manager for a package like libopenssl or just openssl and see if installing one of those will work - Im just guessing from looking at the error message

Gaunt

---

### Post by gauntface on 2008-09-15
Was beaten to it lol

---

### Post by mike22 on 2008-09-15
thanks it worked! how do you run hydra now?

---

### Post by houbysoft.xf.cz on 2008-09-15
Run
```

./hydra

```
or run
```

sudo make install

```
. If you run sudo make install, you will be able to run hydra more easily, like this :
```

hydra

```
;)

---

### Post by houbysoft.xf.cz on 2008-09-15
Oh, and, for the GTK version (it is mandatory, you don't need it, it's just a GUI), you can run 
```

./hydra-gtk

```
or something like that. But I recomment the CMD-line, so use the commands I posted in my previous post.

Hope this all helps.

---

### Post by mike22 on 2008-09-15
looks like I need to install gtk 2.0? It does say ignored though.

```
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)


```

---

### Post by naivivvuli on 2008-09-15
i have just done all the steps listed above, but for some strange odd reason hydra wont start up when i type hydra in the terminal

---

### Post by naivivvuli on 2008-09-15
this is the following error i keep getting.


Now type make install
kenny@Hardy:~/Desktop/hydra-5.4-src$ sudo make install
[sudo] password for kenny: 
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)


any help is greatly appreciated.

---

### Post by naivivvuli on 2008-09-15
```

Now type make install
kenny@Hardy:~/Desktop/hydra-5.4-src$ sudo make install
[sudo] password for kenny: 
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
```

---

### Post by houbysoft.xf.cz on 2008-09-16
Does it work when you only type
```

./hydra

```?

---

### Post by mike22 on 2008-09-16
Can someone help me with this error when I type "make."


```
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)
```

---

### Post by houbysoft.xf.cz on 2008-09-16
Ignore that, that's only the GUI version, this won't affect the hydra cmd-line version.

---

### Post by mike22 on 2008-09-16
> **houbysoft.xf.cz said:**
> Ignore that, that's only the GUI version, this won't affect the hydra cmd-line version.

Thanks for the help. Does this code mean anything or should I ignore it?

```

root@ubuntu:/home/michael/hydra-5.4-src# sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
root@ubuntu:/home/michael/hydra-5.4-src# 

```

---

### Post by houbysoft.xf.cz on 2008-09-18
> **mike22 said:**
> Thanks for the help. Does this code mean anything or should I ignore it?

```

root@ubuntu:/home/michael/hydra-5.4-src# sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
root@ubuntu:/home/michael/hydra-5.4-src# 

```

I don't know, I am little confused that anything is ".exe". It should not be hydra.exe, only hydra. I see you're on linux from the root@ubuntu thing, but are you sure you selected the makefile that's good for you? You haven't compiled with the Windows makefile?
Also, for making things easier, you can install medusa, which is something like hydra, it's almost the same, some people say that hydra is better, other say that medusa is better. However, medusa is much easier to install, because it's in the repos. Just open a terminal, and type
```

sudo apt-get install medusa

```
.
Hope that helps.

---

### Post by mike22 on 2008-09-18
Thank you for the help. I'll try medusa.

---

### Post by mike22 on 2008-09-18
Is john the ripper similar to medusa or hydra? I want to check how secure my ftp is.

To get back on the topic of hydra, here is what the ./configure looks like for hydra. After installing hydra, the hydra command doesn't work.

```
michael@ubuntu:~$ cd '/home/michael/hydra-5.4-src' 
michael@ubuntu:~/hydra-5.4-src$ ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from http://0xbadc0de.be !

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
michael@ubuntu:~/hydra-5.4-src$ 

```

---

### Post by houbysoft.xf.cz on 2008-09-18
Yes, medusa is almost the same as hydra.
The ./configure output looks correct, I don't understand why ./hydra shouldn't work.
Could you post the complete output of these commands?
```

./configure
make
sudo make install
./hydra

```
?

---

### Post by mike22 on 2008-09-19
Alrighty.


```
michael@ubuntu:~$**sudo su**
[sudo] password for michael: 
root@ubuntu:/home/michael# cd /home/michael/hydra-5.4-src
root@ubuntu:/home/michael/hydra-5.4-src# ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from http://0xbadc0de.be !

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
root@ubuntu:/home/michael/hydra-5.4-src# **make**
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)

Now type make install
root@ubuntu:/home/michael/hydra-5.4-src# **sudo make install**
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
root@ubuntu:/home/michael/hydra-5.4-src# **./hydra**
bash: ./hydra: Permission denied
root@ubuntu:/home/michael/hydra-5.4-src# 

```

---

### Post by houbysoft.xf.cz on 2008-09-19
Ok, so after the ./hydra thing, type (preferably under root)
```

chmod +x hydra
./hydra

```
It should work now, if not, post the output again :)

---

### Post by mike22 on 2008-09-19
> **houbysoft.xf.cz said:**
> Ok, so after the ./hydra thing, type (preferably under root)
```

chmod +x hydra
./hydra

```
It should work now, if not, post the output again :)

I redid the installation, same thing as the previous post. Here is what happened when I followed your directions.

```
michael@ubuntu:~/hydra-5.4-src$ chmod +x hydra
michael@ubuntu:~/hydra-5.4-src$ ./hydra
michael@ubuntu:~/hydra-5.4-src$ hydra
michael@ubuntu:~/hydra-5.4-src$ 

```

---

### Post by houbysoft.xf.cz on 2008-09-19
> **mike22 said:**
> I redid the installation, same thing as the previous post. Here is what happened when I followed your directions.

```
michael@ubuntu:~/hydra-5.4-src$ chmod +x hydra
michael@ubuntu:~/hydra-5.4-src$ ./hydra
michael@ubuntu:~/hydra-5.4-src$ hydra
michael@ubuntu:~/hydra-5.4-src$ 

```

That's strange, there really wasn't any output? And didn't chmod +x hydra without root say something like "permission denied"?

---

### Post by mike22 on 2008-09-20
I had an output before that said "permission denied" before.

---

### Post by houbysoft.xf.cz on 2008-09-20
That's really strange, it should give an output. In this case I'm not able to help, sorry. I recomment you to try medusa.

---

### Post by mike22 on 2008-09-24
Medusa seems to be working fine, but medusa doesn't seem to either recognize my list of usernames and passwords or I don't have them in the proper directory. Here is the input when I start medusa and the error I get at the bottom of the input.


```
michael@ubuntu:~$ medusa
Medusa v1.3 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

ALERT: Host information must be supplied.

Syntax: Medusa [-h host|-H file] [-u username|-U file] [-p password|-P file] [-C file] -M module [OPT]
  -h [TEXT]    : Target hostname or IP address
  -H [FILE]    : File containing target hostnames or IP addresses
  -u [TEXT]    : Username to test
  -U [FILE]    : File containing usernames to test
  -p [TEXT]    : Password to test
  -P [FILE]    : File containing passwords to test
  -C [FILE]    : File containing combo entries. See README for more information.
  -O [FILE]    : File to append log information to
  -e [n/s/ns]  : Additional password checks ([n] No Password, [s] Password = Username)
  -M [TEXT]    : Name of the module to execute (without the .mod extension)
  -m [TEXT]    : Parameter to pass to the module. This can be passed multiple times with a
                 different parameter each time and they will all be sent to the module (i.e.
                 -m Param1 -m Param2, etc.)
  -d           : Dump all known modules
  -n [NUM]     : Use for non-default TCP port number
  -s           : Enable SSL
  -g [NUM]     : Give up after trying to connect for NUM seconds (default 3)
  -r [NUM]     : Sleep NUM seconds between retry attempts (default 3)
  -R [NUM]     : Attempt NUM retries before giving up. The total number of attempts will be NUM + 1.
  -t [NUM]     : Total number of logins to be tested concurrently
  -T [NUM]     : Total number of hosts to be tested concurrently
  -L           : Parallelize logins using one username per thread. The default is to process 
                 the entire username before proceeding.
  -f           : Stop scanning host after first valid username/password found.
  -F           : Stop audit after first valid username/password found on any host.
  -b           : Suppress startup banner
  -q           : Display module's usage information
  -v [NUM]     : Verbose level [0 - 6 (more)]
  -w [NUM]     : Error debug level [0 - 10 (more)]
  -V           : Display version


[B]michael@ubuntu:~$ medusa -h (inserted website/host) -U wordlist -P password wordlist -M (inserted module)

FATAL: Failed to open file wordlist.list - No such file or directory
michael@ubuntu:~$ [/B]


```

---

### Post by houbysoft.xf.cz on 2008-09-24
Try this :
```

mv wordlist wordlist.list

```
and then run medusa again.

---

### Post by mike22 on 2008-09-27
> **houbysoft.xf.cz said:**
> Try this :
```

mv wordlist wordlist.list

```
and then run medusa again.

Hmmm this is the output I get:

```
michael@ubuntu:~$ medusa -h (website/ip) -U mv wordlist wordlist.list -P mv wordlist password wordlist.list -M ssh.mod version 1.0.2
Medusa v1.3 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

FATAL: Failed to open file mv - No such file or directory
michael@ubuntu:~$ 

```

```
michael@ubuntu:~$ mv wordlist wordlist.list
mv: cannot stat `wordlist': No such file or directory
michael@ubuntu:~$ 

```

---

### Post by houbysoft.xf.cz on 2008-09-27
I mean to rename wordlist to wordlist.list, not using the command in medusa.
But if it says mv : cannot stat 'wordlist', it means that your wordlist file probably doesn't exist. Are you sure you have it in the directory from where you are calling medusa? (~/?)

---

### Post by mike22 on 2008-09-28
> **houbysoft.xf.cz said:**
> I mean to rename wordlist to wordlist.list, not using the command in medusa.
But if it says mv : cannot stat 'wordlist', it means that your wordlist file probably doesn't exist. Are you sure you have it in the directory from where you are calling medusa? (~/?)

What folder do I put the wordlists in? Is it the /usr/share/doc/medusa folder or /usr/lib/medusa? For either folder I don't have permission. How do I get permission?

---

### Post by houbysoft.xf.cz on 2008-09-28
That doesn't matter. The only thing that matters is from where you are *calling* medusa. So, I suggest you to put your wordlist file in your home folder, because when you open a shell, you start from your home folder (that's the "~/" thing).
So, for example, if your username is "someone", put your wordlist into /home/someone, then open up a shell and when calling medusa it should work.

Hope that helps.

---

### Post by mike22 on 2008-09-29
Got it working thanks. Just had to rename my password wordlist file. How do I thank you?



edit: The only problem I have with medusa, is that my computer freezes when I'm testing. Sorry for the trouble.

---

### Post by houbysoft.xf.cz on 2008-09-29
> **mike22 said:**
> Got it working thanks. Just had to rename my password wordlist file. How do I thank you?



edit: The only problem I have with medusa, is that my computer freezes when I'm testing. Sorry for the trouble.

For the freezing, I really don't know. For thanking me, you have to click the little star in the down right corner of any of my messages :D

---

### Post by sosipator on 2008-10-19
Hello there.

does someone know of some script that generates random combinations from a given list of characters to be used instead of wordlist? 
It would be nice to be added in the crontab to perform password vulnerability assesment once in a while and to create reports.

---

### Post by Yellobes on 2010-06-03
OI! 

```
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ ./hydra
bash: ./hydra: Permission denied
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ make
cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)

Now type make install
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ sudo ./hydra
sudo: ./hydra: command not found
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ chmod +x hydra
chmod: changing permissions of `hydra': Operation not permitted
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ sudo chmod +x hydra
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ ./hydra
zen-master-desu@zen-master-desu-laptop:~/hydra-5.4-src$ 

```

The only reason I was really interested is the password gen, Medusa looks like a dead end if I have to create the keys myself. If anybody has any ideas,

---

### Post by fronow on 2012-01-05
I need help I am new to ubuntu and I am not good with shell code but I would like to install hydra so I could help my brother with something so it said to type ./configure then make then make install ...??? should i have it like hydra or xhydra or hydra-gtk

---

