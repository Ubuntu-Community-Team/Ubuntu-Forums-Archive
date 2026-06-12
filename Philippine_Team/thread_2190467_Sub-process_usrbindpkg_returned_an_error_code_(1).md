---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-11-27
forum: Philippine Team
---

### Post by huntinfreak55 on 2013-11-27
I can't install spotify for some reason.  I was working for awhile.  I have heard of Spotify changing their key.  So I am trying to just remove Spotify all together but i can't because apparently it isn't installed correctly.

When I try sudo apt-get update && sudo apt-get install spotify-client-qt   OR      apt-get remove     OR      apt-get autoremove   it gives me this:
Sub-process /usr/bin/dpkg returned an error code (1)[ATTACH=CONFIG]248136[/ATTACH][ATTACH=CONFIG]248137[/ATTACH]

---

### Post by Bashing-om on 2013-11-27
huntinfreak55; Hi ! Welcome to the forum .
This:
"cd: can't cd to /opt/spotify/spotify-client" says this may be a real pain to track down, remove and (re-)install !

But, If you are up to it, I am willing to give it a whirl.
1st, what is the operating system we are "operating" on ?
Post back the outputs of terminal codes: - BETWEEN code tags;
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

lsb_release -a
uname -a

```
And I want to know the state of the package management system:
```

dpkg -C

```
That is an uppercase "c";

And specific to "spotify"
```

dpkg -l spotify
dpkg -l spotify-client
apt-cache policy spotify
ls -la /var/lib/dpkg/info/spotify.list

```
and also, How are you "fetching" spotify ?
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d/

```

Once all this is known, we can see about finding what remains of spotify on your system and how to complete the removal.

[INDENT][INDENT]the longest journey begins with 1 step
[/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-27
I appreciate it!  When I search for spotify by hitting the home button it doesn't even show it as being installed anymore.  I am pretty new to linux so it is possible that I deleted it while playing on Terminal.  I was actually given this laptop.  It had Ubuntu on it but it was version 10 something, so I updated it to the version it is now.[ATTACH=CONFIG]248143[/ATTACH][ATTACH=CONFIG]248144[/ATTACH][ATTACH=CONFIG]248145[/ATTACH][ATTACH=CONFIG]248146[/ATTACH][ATTACH=CONFIG]248147[/ATTACH]

---

### Post by Bashing-om on 2013-11-27
huntinfreak55; Hey ,

Redo that last and place the outputs, per request, between code tags - for readability and access. Please take the time to read the tutorial provided.

I have enough on my desktop as it is, and screen shots are very difficult for me to manage and are not readable in the entirety of the content.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-27
Ok I apologize, is this what you were thinking?

**lsb_release -a**
Ubuntu 12.04.3 LTS
codename: precise

**uname -a**
Linux chester-laptop 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 17:31:43 UTC 2013 i686 i686 i386 GNU/Linux

**dpkg -C**
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 spotify-client-qt    Transitional package for spotify-client


The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 spotify-client       Spotify desktop client

**dpkg -l spotify**
No packages found matching spotify

**dpkg -l spotify-client**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rF  spotify-client 1:0.9.4.183.g6 Spotify desktop client



**apt-cache policy spotify**
N: Unable to locate package spotify



**ls -la /var/lib/dpkg/info/spotify.list**
ls: cannot access /var/lib/dpkg/info/spotify.list: No such file or directory

**cat -n /etc/apt/sources.list**
1    # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     6    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    11    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    17    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    18    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    19    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    27    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    28    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    29    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    30    
    31    ## Uncomment the following two lines to add software from the 'backports'
    32    ## repository.
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    39    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    46    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    47    
    48    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    49    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    50    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    51    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    52    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    53    deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
    54    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    55    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
    56    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
    57    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
    58    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
    59    deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free



**ls -la /etc/apt/sources.list.d/**
total 20drwxr-xr-x 2 root root 4096 Nov 14 10:59 .
drwxr-xr-x 6 root root 4096 Nov 27 09:36 ..
-rw-r--r-- 1 root root  134 Nov 11 19:48 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Nov 11 19:48 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  150 Nov 11 19:48 ubuntu-x-swat-x-updates-precise.list

---

### Post by Bashing-om on 2013-11-27
huntinfreak55; Yes, some what better.
Place the output Between code tags is better yet, really helps for readability.

The good news is that "spotify" is the only fault the system is aware of.
This output says we will do things the hard way.
```

ls -la /var/lib/dpkg/info/spotify.list
ls: cannot access /var/lib/dpkg/info/spotify.list: No such file or directory

```
So, show me the output of terminal code:
```

sudo find / -name "spotify*"

```
Which will take a bit of time to complete as it is searching every file on your system looking for matches; patience,

Are you comfortable editing files ?
there are duplicated sources that must be removed:
> 
55 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
56 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
57 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
58 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
59 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

Now here for your reference is why it is desirable for outputs to be placed between code tags; do you see ?:
```

sysop@1304mini:~$ cat -n /etc/apt/sources.list
     1  # deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
     2
     3  # deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
     4  #following line is a duplicate unknown why/where (24may2013) and commented out.
     5  #deb http://security.ubuntu.com/ubuntu raring-security main restricted
     6
     7  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8  # newer versions of the distribution.
     9  deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
    10  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted
    11
    12  ## Major bug fix updates produced after the final release of the
    13  ## distribution.
    14  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
    15  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
    16
    17  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18  ## team. Also, please note that software in universe WILL NOT receive any
    19  ## review or updates from the Ubuntu security team.
    20  deb http://us.archive.ubuntu.com/ubuntu/ raring universe
    21  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
    22  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
    23  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
    24
    25  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26  ## team, and may not be under a free licence. Please satisfy yourself as to 
    27  ## your rights to use the software. Also, please note that software in 
    28  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    29  ## security team.
    30  deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
    31  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
    32  deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
    33  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
    34
    35  ## N.B. software from this repository may not have been tested as
    36  ## extensively as that contained in the main release, although it includes
    37  ## newer versions of some applications which may provide useful features.
    38  ## Also, please note that software in backports WILL NOT receive any review
    39  ## or updates from the Ubuntu security team.
    40  deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
    41  #(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
    42
    43  deb http://security.ubuntu.com/ubuntu raring-security main restricted
    44  #(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
    45  deb http://security.ubuntu.com/ubuntu raring-security universe
    46  #(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security universe
    47  deb http://security.ubuntu.com/ubuntu raring-security multiverse
    48  #(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security multiverse
    49
    50  ## Uncomment the following two lines to add software from Canonical's
    51  ## 'partner' repository.
    52  ## This software is not part of Ubuntu, but is offered by Canonical and the
    53  ## respective vendors as a service to Ubuntu users.
    54  #uncommented 23may2012
    55  deb http://archive.canonical.com/ubuntu raring partner
    56  # deb-src http://archive.canonical.com/ubuntu raring partner
    57
    58  ## Uncomment the following two lines to add software from Ubuntu's
    59  ## 'extras' repository.
    60  ## This software is not part of Ubuntu, but is offered by third-party
    61  ## developers who want to ship their latest software.
    62  #uncommented 23may2013
    63  deb http://extras.ubuntu.com/ubuntu raring main
    64  # deb-src http://extras.ubuntu.com/ubuntu raring main
sysop@1304mini:~$

```
[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-27
I am comfortable with editing files, but I am not sure how to remove the repository or deb file.  I am not sure what  file type it is.

**sudo find / -name "spotify*"**
/home/chester/.local/share/Trash/info/spotify.trashinfo
/home/chester/.local/share/spotify
/home/chester/.config/spotify
/home/chester/.cache/spotify
/var/crash/spotify-client.0.crash
/var/cache/apt/archives/spotify-client-qt_1%3a0.9.4.183.g644e24e.428-1_all.deb
/var/cache/apt/archives/spotify-client_1%3a0.9.4.183.g644e24e.428-1_i386.deb
/var/lib/dpkg/info/spotify-client-qt.list
/var/lib/dpkg/info/spotify-client.prerm
/var/lib/dpkg/info/spotify-client.postinst
/var/lib/dpkg/info/spotify-client-qt.md5sums
/var/lib/dpkg/info/spotify-client.list
/var/lib/dpkg/info/spotify-client.md5sums
/usr/bin/spotify
/usr/share/applications/spotify.desktop
/usr/share/icons/hicolor/24x24/apps/spotify-client.png
/usr/share/icons/hicolor/128x128/apps/spotify-client.png
/usr/share/icons/hicolor/32x32/apps/spotify-client.png
/usr/share/icons/hicolor/64x64/apps/spotify-client.png
/usr/share/icons/hicolor/512x512/apps/spotify-client.png
/usr/share/icons/hicolor/256x256/apps/spotify-client.png
/usr/share/icons/hicolor/16x16/apps/spotify-client.png
/usr/share/icons/hicolor/48x48/apps/spotify-client.png
/usr/share/icons/hicolor/22x22/apps/spotify-client.png
/usr/share/doc/spotify-client-qt
/usr/share/doc/spotify-client
/usr/share/spotify

---

### Post by Bashing-om on 2013-11-27
huntinfreak55;
Maybe there is enough for the package manager to work with. We will see directly after we get those dup lines removed from the sources list file.

Terminal code:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-orig
gksudo gedit /etc/apt/sources.list

```
Which opens the file for editing with admin privileges,
arrow down to line 56 and delete it and all the lines after it. - the line numbers are not reflected in the file !- 
> 
56 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
57 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
58 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
59 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
 leaving line 55.

Save and exit back to terminal,
Now run terminal command:
```

sudo apt-get update

``` making sure that runs clean prior to proceeding .

[INDENT]progress, one step at a time
[/INDENT]

---

### Post by huntinfreak55 on 2013-11-28
Runs clean, lets do the next step.

---

### Post by Bashing-om on 2013-11-28
huntinfreak55; OK !

As the .deb files still exist on your system, and you want to retain spotify.. let's try this:
```

sudo dpkg-reconfigure spotify-client

```
Which is what the package manager originally advised to try.
We will see what results from this and see what else is to be done.

[INDENT][INDENT]we be stepp'n
[/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-28
**sudo dpkg-reconfigure spotify-client**
/usr/sbin/dpkg-reconfigure: spotify-client is broken or not fully installed

---

### Post by Bashing-om on 2013-11-28
huntinfreak55; Well !

I am not going to give up on the easier approach just yet,
Try:
```

sudo apt-get install --reinstall spotify-client

```
and if that fails:
```

sudo apt-get install --fix-broken spotify-client

```

Trying to avoid the hassle and trials to manually remove spotify and it's dependencies just to turn around and (re-)install.

Let the package manager
[INDENT][INDENT][INDENT]do it's job
[/INDENT][/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-28
[B]sudo apt-get install --reinstall spotify-client
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up spotify-client (1:0.9.4.183.g644e24e.428-1) ...
/var/lib/dpkg/info/spotify-client.postinst: 5: cd: can't cd to /opt/spotify/spotify-client
dpkg: error processing spotify-client (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of spotify-client-qt:
 spotify-client-qt depends on spotify-client; however:
  Package spotify-client is not configured yet.
dpkg: error processing spotify-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                  Errors were encountered while processing:
 spotify-client
 spotify-client-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)

[B]sudo apt-get install --fix-broken spotify-client
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
spotify-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up spotify-client (1:0.9.4.183.g644e24e.428-1) ...
/var/lib/dpkg/info/spotify-client.postinst: 5: cd: can't cd to /opt/spotify/spotify-client
dpkg: error processing spotify-client (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of spotify-client-qt:
 spotify-client-qt depends on spotify-client; however:
  Package spotify-client is not configured yet.
dpkg: error processing spotify-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                  Errors were encountered while processing:
 spotify-client
 spotify-client-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried re installing it like I did the first time

[B]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

[/B]**sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'**

[B]sudo apt-get update && sudo apt-get install spotify-client-qt
[/B]
But it still gave me the error

---

### Post by Bashing-om on 2013-11-28
huntinfreak55; Not all bad.

Let's see if we can determine what dpkg is complaining about:
> 
/var/lib/dpkg/info/spotify-client.postinst: 5: cd: can't cd to /opt/spotify/spotify-client

What returns from terminal commands:
```

ls -la /opt/spotify
ls -la /opt/spotify/spotify-client

```

Perhaps all we have to do is create that directory ??
We are working hard to make this easy !
//
also will have to go back into "/etc/apt/sources.list" and remove the once more duplicated source list "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" .

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by huntinfreak55 on 2013-11-29
Nothing happens when I type:
[B]/var/lib/dpkg/info/spotify-client.postinst: 5: cd: can't cd to /opt/spotify/spotify-client

ls -la /opt/spotify
[/B]ls: cannot access /opt/spotify: No such file or directory

**ls -la /opt/spotify/spotify-client**
ls: cannot access /opt/spotify/spotify-client: No such file or directory

Would it possibly be easier to just remove all of spotify and reinstalling it?
I tried removing it before but it gives me the error code.
I tried **sudo get-apt remove spotify **before contacting you.

---

### Post by Bashing-om on 2013-11-29
huntinfreak55;

Well, we can try. To be honest though, we may have to (un-)install wine too...
But let's see what we can do:
Show me the output - I prefer you use the "code tags (#) - of terminal commands:
```

dpkg -l | grep spotify
dpkg -l | grep spotify-client
dpkg -l | grep spotify-client-qt

```

If we have to remove spotify manually, there are scores of files to hunt down and remove, and then there is the clean up to make sure the package management system is in a consistent state. I am trying not to undertake that action !

[INDENT][INDENT]we do what we have to do
[/INDENT][/INDENT]

---

### Post by AnthonyAlmighty on 2013-11-30
I'm having the exact same issue; although I know EXACTLY how my installation was borked. I installed Spotify during a new sys install, and it wound up causing the UI to freeze--I had forgotten that I had installed it via package manager, and falsely thought I had installed it like sublime (download files, copy to /opt and symlink to /usr/local/bin). 

```
 sudo rm -rf /opt/spotify-client 
```

I can be the dumbest smart guy I know... 

Here's the output you had requested... 

```
 anthony@hodor ~ $ dpkg -l | grep spotify-client
pF  spotify-client                              1:0.9.4.183.g644e24e.428-1             amd64        Spotify desktop client 
```

---

### Post by huntinfreak55 on 2013-11-30
Maybe you could give me an example of what code tags look like.  This is what I interpret it to be...

#dpkg -l | grep
rF  spotify-client                                1:0.9.4.183.g644e24e.428-1                           Spotify desktop client
iU  spotify-client-qt                             1:0.9.4.183.g644e24e.428-1                           Transitional package for spotify-client

#dpkg -l | grep spotify-client
rF  spotify-client                                1:0.9.4.183.g644e24e.428-1                           Spotify desktop client
iU  spotify-client-qt                             1:0.9.4.183.g644e24e.428-1                           Transitional package for spotify-client



#dpkg -l | grep spotify-client-qt
iU  spotify-client-qt                             1:0.9.4.183.g644e24e.428-1                           Transitional package for spotify-client

---

### Post by Bashing-om on 2013-11-30
@huntinfreak55; OK, let's get ready to go to work.
Two more files to look at before we proceed to manually remove a lot of files (hang in there with me).
Post back the outputs of terminal commands:
```

cat /var/lib/dpkg/info/spotify-client.list
cat /var/lib/dpkg/info/spotify-client-qt.list

```
Will compare these list with the output of the find command and start rm'n files.

Code tags: It has dawned on me that you are probably replying with the "Quick Reply" button .. That code tag option [#] is not available there. You want to hit the BIG RED "+Reply to Thread" button at the top and bottom of the thread page. The "#" is in the 2nd row, 3rd from right end - in the tool bars at the top of the post.
Again the tutorial: This link, just click on it to go to it.
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

------------
@AnthonyAlmighty; Hey !
The op, huntinfreak55, and I know now that if one has removed the "/opt/spotify-client" file then you are up that creek and almost without a paddle !
The only thing I know to do is to hunt up all those files and remove them and then fix the package manager.
Let's see what remains on your system:
terminal code:
```

sudo find / -name "spotify*"

```

Your output I do expect to be different than   huntinfreak55's. In your output show me also the contents of any of the .list files found.

hey guys;
[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by eledh on 2013-12-07
I had the same issue.

What I did to solve this:

# sudo dpkg --contents spotify-client_0.9.4.183.g644e24e.428-1_amd64.deb 
drwxr-xr-x root/root         0 2013-10-10 10:29 ./
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/bin/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/share/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/share/spotify/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/share/doc/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./usr/share/doc/spotify-client/
-rw-r--r-- root/root        36 2013-09-30 15:45 ./usr/share/doc/spotify-client/copyright
-rw-r--r-- root/root      1212 2013-10-10 10:22 ./usr/share/doc/spotify-client/changelog.Debian.gz
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/spotify/
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/spotify/spotify-client/
-rw-r--r-- root/root      3915 2013-10-10 10:22 ./opt/spotify/spotify-client/changelog
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/spotify/spotify-client/Data/
-rw-r--r-- root/root   2490094 2013-10-10 10:29 ./opt/spotify/spotify-client/Data/resources.zip
-rw-r--r-- root/root   5402756 2013-10-10 10:26 ./opt/spotify/spotify-client/Data/apps.zip
-rw-r--r-- root/root   2170787 2013-08-23 12:51 ./opt/spotify/spotify-client/Data/cef.pak
-rw-r--r-- root/root   4247292 2013-08-23 12:51 ./opt/spotify/spotify-client/Data/devtools_resources.pak
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/spotify/spotify-client/Data/locales/
-rw-r--r-- root/root      4176 2013-08-23 12:51 ./opt/spotify/spotify-client/Data/locales/en-US.pak
-rw-r--r-- root/root  72545184 2013-10-10 10:29 ./opt/spotify/spotify-client/Data/libcef.so
-rwxr-xr-x root/root   1154464 2013-10-10 10:29 ./opt/spotify/spotify-client/Data/SpotifyHelper
drwxr-xr-x root/root         0 2013-10-10 10:29 ./opt/spotify/spotify-client/Icons/
-rw-r--r-- root/root      1398 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-16.png
-rw-r--r-- root/root     24055 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-256.png
-rw-r--r-- root/root      1991 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-32.png
-rw-r--r-- root/root      3246 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-48.png
-rw-r--r-- root/root      1333 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-22.png
-rw-r--r-- root/root      1451 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-24.png
-rw-r--r-- root/root     54308 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-512.png
-rw-r--r-- root/root      4443 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-64.png
-rw-r--r-- root/root     10425 2013-09-30 15:45 ./opt/spotify/spotify-client/Icons/spotify-linux-128.png
-rw-r--r-- root/root    218801 2013-10-09 18:56 ./opt/spotify/spotify-client/licenses.xhtml
-rwxr-xr-x root/root       927 2013-10-09 18:56 ./opt/spotify/spotify-client/linklibs-fedora.sh
-rwxr-xr-x root/root       863 2013-10-10 10:22 ./opt/spotify/spotify-client/linklibs.sh
-rw-r--r-- root/root      2285 2013-10-09 18:56 ./opt/spotify/spotify-client/readme.fedora
-rwxr-xr-x root/root       980 2013-09-30 15:45 ./opt/spotify/spotify-client/register.sh
-rw-r--r-- root/root       254 2013-09-30 15:45 ./opt/spotify/spotify-client/spotify.desktop
-rwxr-xr-x root/root       883 2013-09-30 15:45 ./opt/spotify/spotify-client/unregister.sh
-rwxr-xr-x root/root  28782832 2013-10-10 10:29 ./opt/spotify/spotify-client/spotify
lrwxrwxrwx root/root         0 2013-10-10 10:29 ./usr/bin/spotify -> /opt/spotify/spotify-client/spotify

# wget [http://repository.spotify.com/pool/non-free/s/spotify/spotify-client_0.9.4.183.g644e24e.428-1_amd64.deb](http://repository.spotify.com/pool/non-free/s/spotify/spotify-client_0.9.4.183.g644e24e.428-1_amd64.deb)
# sudo dpkg --extract spotify-client_0.9.4.183.g644e24e.428-1_amd64.deb /tmp
# mkdir -p /opt/spotify/spotify-client/
# sudo mv /tmp/opt/spotify/spotify-client/* /opt/spotify/spotify-client/
# sudo apt-get install --reinstall spotify-*

And done. Hope this helps.

Cheers,
Marc Caubet

---

### Post by jetaimez on 2014-03-14
hi i'm found a problem pls helps



root@slave:~# sudo apt-get install mariadb-server-5.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mariadb-server-5.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? t^Hy^H^H^Hy^H
Abort.
root@slave:~# sudo apt-get install mariadb-server-5.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mariadb-server-5.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mariadb-server-5.5 (5.5.36+maria-1~precise) ...
 * Stopping MariaDB database server mysqld
   ...done.
 * Starting MariaDB database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mariadb-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-5.5 (= 5.5.36+maria-1~precise); however:
  Package mariadb-server-5.5 is not configured yet.
dpkg: error processing mariadb-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mariadb-test-5.5:
 mariadb-test-5.5 depends on mariadb-server-5.5 (= 5.5.36+maria-1~precise); however:
  Package mariadb-server-5.5 is not configured yet.
dpkg: error processing mariadb-test-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mariadb-test:
 mariadb-test depends on mariadb-test-5.5 (= 5.5.36+maria-1~precise); however:
  Package mariadb-test-5.5 is not configured yet.
dpkg: error processing mariadb-test (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because MaxReports is reached already
                                                  Errors were encountered while processing:
 mariadb-server-5.5
 mariadb-server
 mariadb-test-5.5
 mariadb-test
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2014-03-14
jetaimez; Hi ! A hearty welcome to the forum, but ->

Your server problem has nothing to do with the theme of this thread, and few will even see it buried as it is.

Please start your own thread with a suitable title to gain the broader range and attention of those who can work with you.

even so
[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

