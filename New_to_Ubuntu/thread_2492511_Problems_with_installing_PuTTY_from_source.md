---
title: "Problems with installing PuTTY from source"
date: 2023-11-13
forum: New to Ubuntu
---

### Post by dsliu on 2023-11-13
I have downloaded the unix source archive [putty-0.79.tar.gz]("https://the.earth.li/~sgtatham/putty/latest/putty-0.79.tar.gz") of PuTTY from it's official website. After unzip the file, I ran those commands in the README file 
> 
PuTTY is built using CMake <https://cmake.org/>. To compile in thesimplest way (on any of Linux, Windows or Mac), run these commands in
the source directory:


  cmake .
  cmake --build .


Then, to install in the simplest way on Linux or Mac:


  cmake --build . --target install


And I think I have successfully installed PuTTY according to the terminal outputs
> 
[  0%] Checking current git commit
[  0%] Built target check_git_commit
[  0%] Updating cmake_commit.c
[  0%] Built target cmake_commit_c
[ 28%] Built target utils
[ 28%] Built target logging
[ 30%] Built target eventloop
[ 31%] Built target console
[ 32%] Built target settings
[ 32%] Built target object_lib_HAVE_CLMUL
[ 32%] Built target object_lib_HAVE_AES_NI
[ 33%] Built target object_lib_HAVE_SHA_NI
[ 45%] Built target crypto
[ 50%] Built target network
[ 53%] Built target keygen
[ 54%] Built target agent
[ 55%] Built target guiterminal
[ 56%] Built target noterminal
[ 56%] Built target all-backends
[ 56%] Built target sftpcommon
[ 57%] Built target sftpclient
[ 59%] Built target otherbackends
[ 60%] Built target testcrypt
[ 61%] Built target test_host_strfoo
[ 62%] Built target test_decode_utf8
[ 62%] Built target test_tree234
[ 63%] Built target test_wildcard
[ 63%] Built target test_cert_expr
[ 64%] Built target bidi_gettype
[ 64%] Built target bidi_test
[ 70%] Built target sshcommon
[ 73%] Built target sshclient
[ 74%] Built target plink-be-list
[ 74%] Built target plink
[ 75%] Built target pscp-be-list
[ 75%] Built target pscp
[ 75%] Built target psftp-be-list
[ 76%] Built target psftp
[ 78%] Built target psocks
[ 78%] Built target manpages
[ 81%] Built target sshserver
[ 82%] Built target puttyxpms
[ 83%] Built target ptermxpms
[ 83%] Updating sbcsdat.c
[ 84%] Built target generated_sbcsdat_c
[ 87%] Built target charset
[ 88%] Updating licence.h
[ 88%] Built target generated_licence_h
[ 88%] Built target fuzzterm-be-list
[ 89%] Built target fuzzterm
[ 89%] Built target osxlaunch
[ 90%] Built target psusan-be-list
[ 91%] Built target psusan
[ 93%] Built target puttygen-common
[ 93%] Built target puttygen
[ 94%] Built target cgtest
[ 94%] Built target testsc
[ 95%] Built target testzlib
[ 95%] Built target uppity-be-list
[ 97%] Built target uppity
[ 98%] Built target pageant-be-list
[100%] Built target pageant
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/plink
-- Installing: /usr/local/share/man/man1/plink.1
-- Installing: /usr/local/bin/pscp
-- Installing: /usr/local/share/man/man1/pscp.1
-- Installing: /usr/local/bin/psftp
-- Installing: /usr/local/share/man/man1/psftp.1
-- Installing: /usr/local/bin/psusan
-- Installing: /usr/local/share/man/man1/psusan.1
-- Installing: /usr/local/bin/puttygen
-- Installing: /usr/local/share/man/man1/puttygen.1
-- Installing: /usr/local/bin/pageant
-- Installing: /usr/local/share/man/man1/pageant.1


However, when I type > $ putty in the terminal, it shows this
> 
Command 'putty' not found, but can be installed with:

sudo apt install putty


Am I missing some steps like adding a softlink?

---

### Post by MAFoElffen on 2023-11-14
Do this...
```

find /usr/local/bin -name putty
printenv PATH

```
I think what your are going to find is that installed it into a subdirectory of /usr/local/bin/ and that it might not be in the path... Is it?

---

### Post by SeijiSensei on 2023-11-14
If you just want an SSH client, you can use the one that is included by default.
```
$ ssh server_name_or_ip
```
Use
```
username@server_name
```
if you are connecting to an account with different credentials from your own.

---

### Post by MAFoElffen on 2023-11-15
^^^ That is what I was wondering. I mean, I answered what you asked... But that brought up so many questions in my head, on the "why's?" behind it. 

Putty is a GUI that adds terminal connections to Windows machines, that are already native to Linux through a terminal or console session.

Learning to use command line = You could just take that as an educational journey. So many things are limited or masked in Windows, that are not in Linux. Then again, there are many things that you can do from an admin cmd or PowerShell session, that most Windows users are not aware of... That is just having to look at things in a different perspective.

If you can't remember, or have problems understanding the options of commands, then I can see using a GUI to make things a bit easier. Also saving connections information as profiles can be handy to keep... But those kinds of things are already in applications such as Remmina, which also have connection types for RDP and VNC. So doing things with Putty, well, I think would be "limitted" and duplications of what you already have. Where other things have so much more to offer you.

Also, "Putty" is in the Ubuntu Repostitories. There is no need to have to compile it on your own, unless you really need some kind of new feature, that isn't in the repo version. I can't think of any with Putty. Putty is very old code. LOL

---

### Post by dsliu on 2023-11-15
It didn't work:
> 
(base) dsliu@dsliu:~$ find /usr/local/bin -name putty
(base) dsliu@dsliu:~$ printenv PATH
/home/dsliu/miniconda3/bin:/home/dsliu/miniconda3/condabin:/usr/local/texlive/2021/bin/x86_64-linux:/usr/local/lib/nodejs/node-v14.16.1-linux-x64/bin:/home/dsliu/.local/bin:/home/dsliu/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/dsliu/.local/bin


---

### Post by The Cog on 2023-11-16
Compiling something for source should be the last resort for fixing a problem.
What's the problem you trying to solve. Why are you trying to install a Linux port of a Windows copy of a Unix program in the first place? Why not just use the native tools that come with Ubuntu? 
If you just want to make an ssh connection, open a terminal and type "ssh <hostname>". If you insist on having a GUI round your command-line ssh connection, both putty and remmina are in the repositories. "sudo apt install remmina" or "sudo apt install putty". 

If the answer is "Well that's what I want to do and I don't want to talk about it", then that's fine. I'm used to that.

---

### Post by MAFoElffen on 2023-11-16
All asked in posts #3 & #4, where he skirted around that and didn't answer any.  

First off, he installed minimal-desktop, which was missing build dependencies. He still has not posted the make log, which would note what it was mssing and where it failed.

Even if he "needs it" for something,it is already built and packaged in the repo's.

---

### Post by TheFu on 2023-11-16
PuTTY was created mainly for the MS-Windows platform.  On Unix/Linux systems, any terminal program (there must be 50 of them) is a terminal and connections via ssh are trivial through them as post #3 above shows.  Pick any terminal program you like and use ssh from it.  This is usually a foreign idea to Windows-people.

If you want a point-n-click program, you can set that up too. Just a 1-line script will do. Here's one that I use, daily, constantly, 
```
xterm -geometry 80x22+0+630 $XTERM_OPTS -e ssh -X deneb &
```
I'm using xterms, which is a bit old-school, but they are very light. I like my terminals for specific systems to be placed in the same location every time I start them.  Upper left is for the local system (I start 4 terminals there). Upper right is for another VM host (2 terminals), lower right (1 terminal) is for a specific project I'm working and lower-left is for my "desktop" system to let me launch desktop programs like browsers, fat email programs, etc.  

Most programs I run actually don't run locally, but I want the window and controls to be on the current workstation I happen to be sitting at.

---

### Post by krants on 2023-12-17
I had the same problem and solved it..

Run before "ReadMe" steps
> ./mkunxarc.sh

---

### Post by ActionParsnip on 2023-12-18
Why use PuTTY at all?

---

### Post by TheFu on 2023-12-18
> **ActionParsnip said:**
> Why use PuTTY at all?

+1?  Why?  It is fairly limiting compared to a normal terminal with ssh connections to other systems.

---

### Post by MAFoElffen on 2023-12-18
+1000 -- Since it can be done (better) from Windows CMD prompt, PowerShell prompt, and now that Windows Terminal is a default install in Win11. 

I guess I just do not understand...

---

### Post by TheFu on 2023-12-18
> **MAFoElffen said:**
> +1000 -- Since it can be done (better) from Windows CMD prompt, PowerShell prompt, and now that Windows Terminal is a default install in Win11. 

I guess I just do not understand...

On MS-Windows, I'd use PuTTY, but I've never seen Win10 or Win11.  PuTTY on Windows provides a nice enough copy/paste - very xterm-like.
But on any Unix with real terminal programs, I can't imagine any good reason, unless the boss mandates it, to have putty on Linux, Unix, BSD.  X/Windows select+paste is so much better and when connected to your favorite shell, even if that is ksh or bash, it is still a great productively environment since tab completion were added in the 1990s.

Every few years, someone screws up X/Windows select paste because they think we want multi-level copy buffers. Takes me about 10 minutes to figure out how to disable that crap.  Recently, bash started preventing multi-line pastes to "protect us".  All they did was **** me off and make me hunt down the ~/.inputrc setting
```
set enable-bracketed-paste off
```
so I could be productive again.  
A) They should have made it available and on the first use, asked if we wanted it or not. Then never ask again. E-V-E-R.
B) At least they included a method to disable it ... unlike some other tools that change a default and don't provide a way back to the old behavior.

Sorry ... stress brings out the rant in me.  This time of year isn't good for that - I have to see family soon. Arrrrg. There's a reason we live 7 hours apart.

---

### Post by bernx01 on 2024-05-23
Install a GTK-dev package like 
sudo apt-get install libgtk-3-dev
otherwise will be compiled only CLI programs

---

### Post by bernx01 on 2024-05-23
Install a GTK-dev package like sudo apt-get install libgtk-3-dev 
otherwise will be compiled only CLI programs

---

### Post by ActionParsnip on 2024-05-24
You can SSH from PowerShell from Windows.....why PuTTY? It's been part of PowerShell for ages now....

---

### Post by TheFu on 2024-05-24
> **ActionParsnip said:**
> You can SSH from PowerShell from Windows.....why PuTTY? It's been part of PowerShell for ages now....

The shells and lack of trivial select/paste on MS-Windows makes PuTTY very useful on that platform.  If you are using any menu system or keyboard shortcuts to select/paste, you are doing it the hard way.  PuTTY select is just using the left mouse button to select, then using the right button to paste.

But all Linux terminal programs support that already, so there's no need for PuTTY on Linux/BSD/Unix.  Terminal selection is just using the left mouse button to select, then using the middle button to paste.  No menus, no keyboard.  Get your single, double, and triple click selections for even more speed/convenience.  

Little things like these are lost when people don't work in teams, in the same room and see how others do it - or when they come from a different OS and simply don't know any better.  Sigh.

---

### Post by him610 on 2024-05-24
Maybe the OP is accustomed to using putty in windows, and is hesitant to learn something new and unfamiliar. 
After all, this sub-forum is titled, "New to Ubuntu."

---

### Post by MAFoElffen on 2024-05-25
> **TheFu said:**
> The shells and lack of trivial select/paste on MS-Windows...

On Windows SSH'ing to Linux via both PowerSheel and CMD: There has been changes to Win10 and inherited by Win11 where you can copy and paste, and a toggle to turn it on as hot-keys, which is more than graphical terminal sessions in Linux...

> **TheFu said:**
> But all Linux terminal programs support that already, so there's no need for PuTTY on Linux/BSD/Unix.  Terminal selection is just using the left mouse button to select, then using the middle button to paste.  No menus, no keyboard.  Get your single, double, and triple click selections for even more speed/convenience.  

+1 = Very true. I think the key point here paralleled with this User, is a Windows User who is using what they know. (Also pointed out by Him610) Not knowing that there are other ways to do that.

I had to use Putty, when I went back to college, because they were Windows based, and that is what they taught. In Putty, once the connection is made, it's just a basic terminal session. The only plus is in the connection part of that, where you can save connection settings for various multiple connections...

But in Linux, you can do the same if you ssh in Remmina. That would give that plus for doing that in Linux, over just using a graphical terminal session or in console.

 My curiosity is still, if you are set on that: Why compile Putty from source, when it is already available and stable as Apt, Snap, and FlatPak packages?Or did I miss something about that?

---

### Post by TheFu on 2024-05-26
No complaints about using PuTTY on Windows, assuming they've upgraded over the decades to use the correct ciphers and protocols. In the early 2000s, they didn't, but the alternatives were worse, so everyone used PuTTY even when commercials terminals were available and BOUGHT by their companies.

But PuTTY is a little non-standard, so it integrates poorly with other ssh-based tools that are now, finally, available 25 yrs late, in Win10.  For example, ssh-keys for PuTTY are special and cannot be used by non-PuTTY ssh-based programs.  That kinda defeats the purpose.  In Win10, I know there is the normal ssh-keygen that creates keys which can be share with rsync, scp, sftp, and ssh (probably 20 other tools), just not PuTTY.  Of course, in all Unix-based systems, those and 50 others integrate and the same keys and config file will be used across all the tools making PuTTY a poor choice for use when not on MS-Windows.

The fact that table completion works across ssh-based connections should be enough reason. But if it hasn't been seen, it is one of those things you don't know you are missing.
That's all I was trying to say.  I hope we've shown the OP sufficient cause to try native tools, see how nice they are compared to PuTTY so he can be more productive AND more secure with very few hassles.

---

