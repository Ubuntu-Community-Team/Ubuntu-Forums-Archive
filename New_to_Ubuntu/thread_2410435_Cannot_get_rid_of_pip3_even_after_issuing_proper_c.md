---
title: "Cannot get rid of pip3 even after issuing proper command"
date: 2019-01-15
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-15
I am trying to uninstall pip3 on my Ubuntu 16.04 system. After issuing the correct command, I check it by typing at the terminal

pip3 

and there st ill seems to be something there.

The copy and paste shows my commands;

```

The following packages will be REMOVED:
  python3-pip* python3-wheel*
0 upgraded, 0 newly installed, 2 to remove and 141 not upgraded.
After this operation, 780 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 337393 files and directories currently installed.)
Removing python3-pip (8.1.1-2ubuntu0.4) ...
Removing python3-wheel (0.29.0-1) ...
Processing triggers for man-db (2.7.5-1) ...
james@james-VirtualBox:~$ pip3

Usage:   
  pip <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  search                      Search PyPI for packages.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to WARNING, ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
  --retries <retries>         Maximum number of retries each connection should attempt (default 5 times).
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup, (a)bort.
  --trusted-host <hostname>   Mark this host as trusted, even though it does not have valid or any HTTPS.
  --cert <path>               Path to alternate CA bundle.
  --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the certificate in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine whether a new version of pip is available for download. Implied with --no-index.
james@james-VirtualBox:~$ sudo apt-get --purge autoremove python3-pip
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package 'python3-pip' is not installed, so not removed
```


As you can see it says that pip3 is removed, yet when I typepip3 something shows up. What is going on?

Did I remove pip3 or not?

Any help appreciated.

Respectfully,

ErnestTBass

---

### Post by Lou Reed on 2019-01-15
I really need an answer to this post. It it confusing that when I remove pip3and the software says it was removed, thta whenI go to check injames@james-VirtualBox:~$ sudo apt-get remove python3-pip
I still get a response like pip3 is still on the Ubuntu system. 

```
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package 'python3-pip' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 141 not upgraded.
james@james-VirtualBox:~$ pip3 -help

Usage:  
  pip <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  search                      Search PyPI for packages.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to WARNING, ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
  --retries <retries>         Maximum number of retries each connection should attempt (default 5 times).
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup, (a)bort.
  --trusted-host <hostname>   Mark this host as trusted, even though it does not have valid or any HTTPS.
  --cert <path>               Path to alternate CA bundle.
  --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the certificate in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine whether a new version of pip is available for download. Implied with --no-index.
james@james-VirtualBox:~$ 
```



Any assistance appreciated.

Respectfully,

ErnestTBass

---

### Post by QIII on 2019-01-15
Hello!

We are quite well aware that you want to solve this issue.  You wouldn't be here if you didn't want to solve it, so that is self evident.  There's no need to state that desire. 

Three hours is precious little time to give the all-volunteer community (including the Staff) -- who have lives outside of the Forums -- a chance to see your post.  Please display a modicum of patience and respect for volunteers.  Impatience is not likely to improve your chances for support.

If a post has not received a response in about 12 hours, feel free to bump it.  Bumping prematurely attracts the attention of the Staff ... and posts such as this one.

Also, please place all commands and results in code tags.  That preserves formatting, keeps certain character strings from turning into smileys, and makes your posts easier to read.

To use code tags, either:

1. Click the # button above the text entry box, place your cursor between the code tags that appear and paste or type your text.  Alternatively, paste or type your text, highlight it and then click the # button.

2. Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following it.  The square brackets are required.

---

### Post by again? on 2019-01-15
Check if installed.
```
apt list --installed | grep '.*-pip'
```
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt list --installed | grep '.*-pip'**

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

python-pip/bionic-updates,bionic-updates,now 9.0.1-2.3~ubuntu1 all [installed]
python-pip-whl/bionic-updates,bionic-updates,now 9.0.1-2.3~ubuntu1 all [installed,automatic]
python3-pip/bionic-updates,bionic-updates,now 9.0.1-2.3~ubuntu1 all [installed]
```

Try to actually search  using pip3...
```
pip3 search something
```

---

### Post by Lou Reed on 2019-01-16
I will give a try this afternoon. I cannot do it now. I am at work. Thanks for your help.

Respectfully,

Ernest-T-Bass

I re-installed both pip and pip3 and then uninstalled them. Now by typing either 
pip  or pip3 I get that screen print that you see in the first post. So I guess this problem is not confined to pip3 only.

I though that pip3 was for python 3 and pip was for python 2. I have been using them that way.

---

### Post by again? on 2019-01-16
FYI I'm on Xubuntu 18.04 and this shows removing python3-pip...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] pip3 --version**
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt remove python3-pip**
[sudo] password for glen:         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  python3-pip
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 599 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 284735 files and directories currently installed.)
Removing python3-pip (9.0.1-2.3~ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] pip3 --version**
bash: /usr/bin/pip3: No such file or directory
```
Maybe somewhere along the way you made a local install in **~/.local/bin**
```
which pip3
```

Try rebooting to see if your results change.

---

