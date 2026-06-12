---
title: "Can not install unity-tweak-tool.......need help"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by hasan5599 on 2016-11-23
Hello helpful guys.....................

I am new ubuntu user and installed ubuntu 16.04 LTS.But now I am facing some problem when I tried to install "unity-tweak-tool by this command but It is not working my terminal reply me something ...............

```
hasan@Anaymous-Pc:~$ sudo su -
[sudo] password for hasan: 
root@Anaymous-Pc:~# apt-get install unity-tweak-tool
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
root@Anaymous-Pc:~#
```



how can I installed this very important software ????? Plz give me suggestion....Thanks

---

### Post by kpatz on 2016-11-23
It's safer to use sudo to run your commands than to open a root shell with sudo su.

The command:```
sudo apt-get install -f
``` should resolve the dependency issue and allow unity-tweak-tools to install.

---

### Post by hasan5599 on 2016-11-23
Thanks for your quick reply but

Problem still remains...................

```
hasan@Anaymous-Pc:~$ sudo apt-get install -f
[sudo] password for hasan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
hasan@Anaymous-Pc:~$ sudo apt-get install unity-tweak-tool
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
hasan@Anaymous-Pc:~$
```

What now ??

---

### Post by kpatz on 2016-11-23
Install unity-webapps-common explicitly:```
sudo apt-get install unity-webapps-common unity-tweak-tool
```

---

### Post by hasan5599 on 2016-11-23
I am sorry to say not working again............

```
hasan@Anaymous-Pc:~$ sudo apt-get install unity-webapps-common unity-tweak-tool
[sudo] password for hasan: 
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
hasan@Anaymous-Pc:~$
```



what now ??

---

### Post by fenrice on 2016-11-23
My guess is you could maybe use these two stackoverflow posts to figure it out. 

[https://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages](https://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages) 

[https://askubuntu.com/questions/164587/how-can-you-unhold-remove-a-hold-on-a-package](https://askubuntu.com/questions/164587/how-can-you-unhold-remove-a-hold-on-a-package)

---

### Post by hasan5599 on 2016-11-23
Sorry guys me again It is not working ..................


```
hasan@Anaymous-Pc:~$ sudo aptitude install unity-tweak-tool
The following NEW packages will be installed:
  libandroid-properties1{a} libhardware2{a} libhud2{a} libhybris{a} 
  libhybris-common1{a} libmedia1{a} liboxideqt-qmlplugin{a} 
  liboxideqtcore0{ab} liboxideqtquick0{a} libqt5feedback5{a} 
  libqt5organizer5{ab} libqt5positioning5{ab} libqt5quicktest5{ab} 
  libqt5test5{a} libubuntugestures5{ab} libubuntutoolkit5{ab} 
  libunity-action-qt1{a} libunity-webapps0{a} 
  qml-module-qt-labs-folderlistmodel{a} qml-module-qt-labs-settings{a} 
  qml-module-qtfeedback{a} qml-module-qtgraphicaleffects{a} 
  qml-module-qtquick-layouts{ab} qml-module-qtquick-window2{ab} 
  qml-module-qtquick2{ab} qml-module-qttest{ab} 
  qml-module-ubuntu-components{ab} qml-module-ubuntu-layouts{ab} 
  qml-module-ubuntu-onlineaccounts{a} 
  qml-module-ubuntu-performancemetrics{a} qml-module-ubuntu-test{ab} 
  qml-module-ubuntu-web{a} qtdeclarative5-accounts-plugin{a} 
  qtdeclarative5-qtquick2-plugin{a} 
  qtdeclarative5-ubuntu-ui-toolkit-plugin{a} 
  qtdeclarative5-unity-action-plugin{a} suru-icon-theme{a} 
  ubuntu-mobile-icons{a} ubuntu-ui-toolkit-theme{a} unity-tweak-tool 
  unity-webapps-common{a} unity-webapps-qml{a} unity-webapps-service{a} 
  webapp-container{ab} webbrowser-app{ab} 
0 packages upgraded, 45 newly installed, 0 to remove and 5 not upgraded.
Need to get 47.3 MB of archives. After unpacking 172 MB will be used.
The following packages have unmet dependencies:
 qml-module-qtquick-window2 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                        - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-test : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                    - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                    - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 liboxideqtcore0 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                             - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                             - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 qml-module-qtquick2 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                 - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5organizer5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 qml-module-qtquick-layouts : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                        - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                        - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                              Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                        - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-qttest : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                               - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5quicktest5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 webapp-container : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                    Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                              - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-layouts : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                       - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-components : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                          - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                          - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                                Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                          - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libubuntutoolkit5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                               - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                               - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 webbrowser-app : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                            - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                            - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                  Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                            - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5positioning5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 libubuntugestures5 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                - libqt5qml5, but 5.7.1~20161021-5 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:    
1)      liboxideqt-qmlplugin [Not Installed]                   
2)      liboxideqtcore0 [Not Installed]                        
3)      liboxideqtquick0 [Not Installed]                       
4)      libqt5organizer5 [Not Installed]                       
5)      libqt5positioning5 [Not Installed]                     
6)      libqt5quicktest5 [Not Installed]                       
7)      libubuntugestures5 [Not Installed]                     
8)      libubuntutoolkit5 [Not Installed]                      
9)      libunity-webapps0 [Not Installed]                      
10)     qml-module-qtgraphicaleffects [Not Installed]          
11)     qml-module-qtquick-layouts [Not Installed]             
12)     qml-module-qtquick-window2 [Not Installed]             
13)     qml-module-qtquick2 [Not Installed]                    
14)     qml-module-qttest [Not Installed]                      
15)     qml-module-ubuntu-components [Not Installed]           
16)     qml-module-ubuntu-layouts [Not Installed]              
17)     qml-module-ubuntu-onlineaccounts [Not Installed]       
18)     qml-module-ubuntu-test [Not Installed]                 
19)     qml-module-ubuntu-web [Not Installed]                  
20)     qtdeclarative5-accounts-plugin [Not Installed]         
21)     qtdeclarative5-qtquick2-plugin [Not Installed]         
22)     qtdeclarative5-ubuntu-ui-toolkit-plugin [Not Installed]
23)     unity-tweak-tool [Not Installed]                       
24)     unity-webapps-common [Not Installed]                   
25)     unity-webapps-qml [Not Installed]                      
26)     unity-webapps-service [Not Installed]                  
27)     webapp-container [Not Installed]                       
28)     webbrowser-app [Not Installed]                         



Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```
                                         
```
hasan@Anaymous-Pc:~$ sudo aptitude install unity-tweak-tool
The following NEW packages will be installed:
  libandroid-properties1{a} libhardware2{a} libhud2{a} libhybris{a} 
  libhybris-common1{a} libmedia1{a} liboxideqt-qmlplugin{a} 
  liboxideqtcore0{ab} liboxideqtquick0{a} libqt5feedback5{a} 
  libqt5organizer5{ab} libqt5positioning5{ab} libqt5quicktest5{ab} 
  libqt5test5{a} libubuntugestures5{ab} libubuntutoolkit5{ab} 
  libunity-action-qt1{a} libunity-webapps0{a} 
  qml-module-qt-labs-folderlistmodel{a} qml-module-qt-labs-settings{a} 
  qml-module-qtfeedback{a} qml-module-qtgraphicaleffects{a} 
  qml-module-qtquick-layouts{ab} qml-module-qtquick-window2{ab} 
  qml-module-qtquick2{ab} qml-module-qttest{ab} 
  qml-module-ubuntu-components{ab} qml-module-ubuntu-layouts{ab} 
  qml-module-ubuntu-onlineaccounts{a} 
  qml-module-ubuntu-performancemetrics{a} qml-module-ubuntu-test{ab} 
  qml-module-ubuntu-web{a} qtdeclarative5-accounts-plugin{a} 
  qtdeclarative5-qtquick2-plugin{a} 
  qtdeclarative5-ubuntu-ui-toolkit-plugin{a} 
  qtdeclarative5-unity-action-plugin{a} suru-icon-theme{a} 
  ubuntu-mobile-icons{a} ubuntu-ui-toolkit-theme{a} unity-tweak-tool 
  unity-webapps-common{a} unity-webapps-qml{a} unity-webapps-service{a} 
  webapp-container{ab} webbrowser-app{ab} 
0 packages upgraded, 45 newly installed, 0 to remove and 5 not upgraded.
Need to get 47.3 MB of archives. After unpacking 172 MB will be used.
The following packages have unmet dependencies:
 qml-module-qtquick-window2 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                        - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-test : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                    - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                    - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 liboxideqtcore0 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                             - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                             - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 qml-module-qtquick2 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                 - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5organizer5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 qml-module-qtquick-layouts : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                        - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                        - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                              Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                        - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-qttest : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                               - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5quicktest5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 webapp-container : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                              - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                    Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                              - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-layouts : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                       - libqt5qml5, but 5.7.1~20161021-5 is installed.
 qml-module-ubuntu-components : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                          - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                          - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                                Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                          - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libubuntutoolkit5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                               - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                               - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 webbrowser-app : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                            - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                            - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
                  Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                            - libqt5qml5, but 5.7.1~20161021-5 is installed.
 libqt5positioning5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                                - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.                                - libqt5core5a, but 5.7.1~20161021+dfsg-5 is installed.
 libubuntugestures5 : Depends: qtdeclarative-abi-5-5-0 which is a virtual package, provided by:
                                - libqt5qml5, but 5.7.1~20161021-5 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:    
1)      liboxideqt-qmlplugin [Not Installed]                   
2)      liboxideqtcore0 [Not Installed]                        
3)      liboxideqtquick0 [Not Installed]                       
4)      libqt5organizer5 [Not Installed]                       
5)      libqt5positioning5 [Not Installed]                     
6)      libqt5quicktest5 [Not Installed]                       
7)      libubuntugestures5 [Not Installed]                     
8)      libubuntutoolkit5 [Not Installed]                      
9)      libunity-webapps0 [Not Installed]                      
10)     qml-module-qtgraphicaleffects [Not Installed]          
11)     qml-module-qtquick-layouts [Not Installed]             
12)     qml-module-qtquick-window2 [Not Installed]             
13)     qml-module-qtquick2 [Not Installed]                    
14)     qml-module-qttest [Not Installed]                      
15)     qml-module-ubuntu-components [Not Installed]           
16)     qml-module-ubuntu-layouts [Not Installed]              
17)     qml-module-ubuntu-onlineaccounts [Not Installed]       
18)     qml-module-ubuntu-test [Not Installed]                 
19)     qml-module-ubuntu-web [Not Installed]                  
20)     qtdeclarative5-accounts-plugin [Not Installed]         
21)     qtdeclarative5-qtquick2-plugin [Not Installed]         
22)     qtdeclarative5-ubuntu-ui-toolkit-plugin [Not Installed]
23)     unity-tweak-tool [Not Installed]                       
24)     unity-webapps-common [Not Installed]                   
25)     unity-webapps-qml [Not Installed]                      
26)     unity-webapps-service [Not Installed]                  
27)     webapp-container [Not Installed]                       
28)     webbrowser-app [Not Installed]                         



Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```
                                         
```
hasan@Anaymous-Pc:~$ sudo apt-get install unity-tweak-tool
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
hasan@Anaymous-Pc:~$ sudo apt-mark unhold unity-tweak-tool
unity-tweak-tool was already not hold.
```


any further suggestion ?????????

---

### Post by slickymaster on 2016-11-23
@hasan5599:

I just edited all your posts in thread, adding [code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to all. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of [code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Frogs Hair on 2016-11-23
These commands will display release and desktop environment.

```
lsb_release -a   
``````
echo $XDG_CURRENT_DESKTOP
```

---

