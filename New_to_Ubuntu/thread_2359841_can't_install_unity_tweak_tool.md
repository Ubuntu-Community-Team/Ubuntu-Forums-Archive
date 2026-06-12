---
title: "can't install unity tweak tool"
date: 2017-04-28
forum: New to Ubuntu
---

### Post by ib.tabun on 2017-04-28
ubuntu 16.4 lts

---

### Post by QIII on 2017-04-28
Hello!

It is difficult to tell from just that image what the problem may be.

If you could attempt to install from the command line and paste back the results, it would be very helpful!

```
sudo apt install unity-tweak-tool
``` should do it.

When you post the results back, please use code tags to contain the text.  This will preserve any formatting and make your response much easier to read. You may do one of the following:

1.  Click the # sign in the toolbar above the text entry box, place your cursor between the code tags that appear and paste your text.

2.  Paste your text, highlight it and then click the # sign.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo apt install unity-tweak-tool[sudo] password for ibtabun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-tweak-tool : Depends: unity-webapps-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ 



```

thank you for your reply

---

### Post by Perfect Storm on 2017-04-28
It's aknown problem, do:

```
sudo apt install liboxideqt-qmlplugin
sudo apt install qml-module-ubuntu-web
sudo apt install webbrowser-app
sudo apt install webapp-container
sudo apt install unity-webapps-common
sudo apt install unity-webapps-service
```

I have splitted the commands as to resolved the dependencies problem. You should now be able to install unity tweak.

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo apt install liboxideqt-qmlplugin[sudo] password for ibtabun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 liboxideqt-qmlplugin : Depends: liboxideqtcore0 (= 1.21.5-0ubuntu0.16.04.1) but it is not going to be installed
                        Depends: liboxideqtquick0 (= 1.21.5-0ubuntu0.16.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ sudo apt install qml-module-ubuntu-web
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 qml-module-ubuntu-web : Depends: liboxideqt-qmlplugin (>= 1.15) but it is not going to be installed
                         Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) or
                                  qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ sudo apt install webbrowser-app
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 webbrowser-app : Depends: qtbase-abi-5-5-1
                  Depends: qtdeclarative-abi-5-5-0
                  Depends: liboxideqt-qmlplugin (>= 1.9) but it is not going to be installed
                  Depends: qml-module-ubuntu-web (= 0.23+16.04.20161028-0ubuntu2) but it is not going to be installed
                  Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) or
                           qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ sudo apt install webapp-container
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 webapp-container : Depends: qtbase-abi-5-5-1
                    Depends: qtdeclarative-abi-5-5-0
                    Depends: liboxideqt-qmlplugin (>= 1.8) but it is not going to be installed
                    Depends: qml-module-ubuntu-web (= 0.23+16.04.20161028-0ubuntu2) but it is not going to be installed
                    Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) or
                             qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) but it is not going to be installed
                    Depends: unity-webapps-qml but it is not going to be installed
                    Depends: webbrowser-app (= 0.23+16.04.20161028-0ubuntu2)
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ sudo apt install unity-webapps-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-common : Depends: unity-webapps-service (>= 2.3.8-0ubuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ sudo apt install unity-webapps-service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-webapps-service : Depends: webapp-container
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ 



```

non of the above worked

---

### Post by Perfect Storm on 2017-04-28
So it runs deeper;
```
sudo apt install liboxideqtcore0 liboxideqtquick0
```

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ ibtabun@ibtabun-PC:~$ sudo apt install liboxideqtcore0 liboxideqtquick0ibtabun@ibtabun-PC:~$: command not found
ibtabun@ibtabun-PC:~$ [sudo] password for ibtabun: 
[sudo]: command not found
ibtabun@ibtabun-PC:~$ Reading package lists... Done
Reading: command not found
ibtabun@ibtabun-PC:~$ Building dependency tree       
Building: command not found
ibtabun@ibtabun-PC:~$ Reading state information... Done
Reading: command not found
ibtabun@ibtabun-PC:~$ Some packages could not be installed. This may mean that you have
No command 'Some' found, did you mean:
 Command 'tome' from package 'tome' (multiverse)
Some: command not found
ibtabun@ibtabun-PC:~$ requested an impossible situation or if you are using the unstable
requested: command not found
ibtabun@ibtabun-PC:~$ distribution that some required packages have not yet been created
distribution: command not found
ibtabun@ibtabun-PC:~$ or been moved out of Incoming.
or: command not found
ibtabun@ibtabun-PC:~$ The following information may help to resolve the situation:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
ibtabun@ibtabun-PC:~$ 
ibtabun@ibtabun-PC:~$ The following packages have unmet dependencies:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
ibtabun@ibtabun-PC:~$  liboxideqtcore0 : Depends: qtbase-abi-5-5-1
liboxideqtcore0: command not found
ibtabun@ibtabun-PC:~$ E: Unable to correct problems, you have held broken packages.
E:: command not found
ibtabun@ibtabun-PC:~$ ibtabun@ibtabun-PC:~$ 
ibtabun@ibtabun-PC:~$: command not found
ibtabun@ibtabun-PC:~$ 



```

the second try 

```
ibtabun@ibtabun-PC:~$ sudo apt install liboxideqtcore0 liboxideqtquick0[sudo] password for ibtabun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 liboxideqtcore0 : Depends: qtbase-abi-5-5-1
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ 



```

---

### Post by Perfect Storm on 2017-04-28
```
sudo apt install qtbase-abi-5-5-1
```

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo apt install qtbase-abi-5-5-1[sudo] password for ibtabun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.2 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate
ibtabun@ibtabun-PC:~$ 



```

---

### Post by Perfect Storm on 2017-04-28
```
sudo apt install libqt5core5a

```

If this continue it's going to be a loooong thread. When it complains about dependency try to install it, it may run deep.

---

### Post by ib.tabun on 2017-04-28
this one

 libqt5core5a is already the newest version (5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1).

---

### Post by Perfect Storm on 2017-04-28
> **ib.tabun said:**
> this one

 libqt5core5a is already the newest version (5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1).

Try reinstall it.
```
sudo apt install --reinstall libqt5core5a
sudo apt install -f qtbase-abi-5-5-1
```

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo apt install -f qtbase-abi-5-5-1Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.2 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate
ibtabun@ibtabun-PC:~$ 



```

---

### Post by Perfect Storm on 2017-04-28
Try download it fromm here: [https://pkgs.org/download/qtbase-abi-5-5-1](https://pkgs.org/download/qtbase-abi-5-5-1)

Then:
```
sudo dpkg --force-all -i ~/Downloads/libqt5core5a_5.5.1*
```

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo dpkg --force-all -i ~/Downloads/libqt5core5a_5.5.1*dpkg: warning: downgrading libqt5core5a:amd64 from 5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 to 5.5.1+dfsg-16ubuntu7.4
(Reading database ... 233405 files and directories currently installed.)
Preparing to unpack .../libqt5core5a_5.5.1+dfsg-16ubuntu7.4_amd64.deb ...
Unpacking libqt5core5a:amd64 (5.5.1+dfsg-16ubuntu7.4) over (5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1) ...
Setting up libqt5core5a:amd64 (5.5.1+dfsg-16ubuntu7.4) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
ibtabun@ibtabun-PC:~$ 



```
i don't know what this means but i think it worked
still can't install unity tweak tool.

---

### Post by Perfect Storm on 2017-04-28
Aye, now:
```
sudo apt install liboxideqtcore0 liboxideqtquick0
```

Then try install unity tweak tool.

---

### Post by ib.tabun on 2017-04-28
```
ibtabun@ibtabun-PC:~$ sudo apt install liboxideqtcore0 liboxideqtquick0Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 liboxideqtcore0 : Depends: qtbase-abi-5-5-1
E: Unable to correct problems, you have held broken packages.
ibtabun@ibtabun-PC:~$ 



```

and it won't install

---

### Post by cariboo on 2017-04-28
Click the Status button in the lower left of Synaptic, it should have a broken package entry. Remove the broken package, and you should be good to go.

---

### Post by ib.tabun on 2017-04-28
i don't have that

---

### Post by #&amp;thj^% on 2017-04-28
Post any errors from the terminal with:
```
sudo apt install -f
```

---

### Post by ib.tabun on 2017-04-29
```
ibtabun@ibtabun-PC:~$ sudo apt install -f[sudo] password for ibtabun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 138 not upgraded.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:43 and /etc/apt/sources.list.d/xenial-partner.list:4



```

---

