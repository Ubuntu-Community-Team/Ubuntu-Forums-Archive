---
title: "Noob help, dpkg not installing dependecies, apt -f install removes deb package"
date: 2020-04-01
forum: New to Ubuntu
---

### Post by aglyons on 2020-04-01
Hey guys & gals, I'm trying to install Seedsync ([https://github.com/ipsingh06/seedsync](https://github.com/ipsingh06/seedsync)) on an Ubuntu container in a Synology NAS. I've tried the docker Seedsync container but there are DIR permissions problems so I thought let's just install Ubuntu and install Seedsync that way.

Running this image [https://registry.hub.docker.com/_/ubuntu/](https://registry.hub.docker.com/_/ubuntu/)

I've run 'apt-get update && apt-get upgrade' on the install.

running the command dpkg -i <package name> returns missing dependencies. Everything I've read says to run apt -f install after which is supposed to install those missing dependencies but instead, it removed the Seedsync install.

```
root@Seedsync_Ubuntu:/# dpkg -i /nas/feral/seedsync_0.7-0_amd64.deb                                
Selecting previously unselected package seedsync.                                                  
(Reading database ... 4101 files and directories currently installed.)                             
Preparing to unpack .../feral/seedsync_0.7-0_amd64.deb ...                                         
Unpacking seedsync (0.7-0) ...                                                                     
dpkg: dependency problems prevent configuration of seedsync:                                       
 seedsync depends on libexpat1 (>= 2.1~beta3); however:                                            
  Package libexpat1 is not installed.                                                              
 seedsync depends on libreadline6 (>= 6.0); however:                                               
  Package libreadline6 is not installed.                                                           
 seedsync depends on libssl1.0.0 (>= 1.0.2~beta3); however:                                        
  Package libssl1.0.0 is not installed.                                                            
 seedsync depends on lftp; however:                                                                
  Package lftp is not installed.                                                                   
 seedsync depends on openssh-client; however:                                                      
  Package openssh-client is not installed.                                                         
                                                                                                   
dpkg: error processing package seedsync (--install):                                               
 dependency problems - leaving unconfigured                                                        
Processing triggers for libc-bin (2.27-3ubuntu1) ...                                               
Errors were encountered while processing:                                                          
 seedsync
                                                                                          
root@Seedsync_Ubuntu:/# apt -f install
                                                            
Reading package lists... Done                                                                      
Building dependency tree                                                                           
Reading state information... Done                                                                  
Correcting dependencies... Done                                                                    
The following packages will be REMOVED:                                                            
  seedsync                                                                                         
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.                                     
1 not fully installed or removed.                                                                  
After this operation, 21.3 MB disk space will be freed.                                            
Do you want to continue? [Y/n] y                                                                   
(Reading database ... 4197 files and directories currently installed.)                             
Removing seedsync (0.7-0) ...                                                                      
Processing triggers for libc-bin (2.27-3ubuntu1) ...                                               
root@Seedsync_Ubuntu:/#
```


Any ideas on getting this running??

Thanks in advance.

---

### Post by Holger_Gehrke on 2020-04-01
'dpkg' is for installing local packages for which all dependencies have been installed already. It can also serve as a front end to some other low-level tools in the package management (dpkg-build, dpkg-query ...). In theory you can try to install something, see what packages it needs, download those, install them (possibly finding out that those packages have dependencies themselves ...) and then install the package you actually want. In practice using 'apt install' with a path and filename is simpler, since apt will download and install dependencies automatically. So a simple 'sudo apt install /nas/feral/seedsync_0.7-0_amd64.deb' should do it (if you don't give apt a path to the file it assumes you want to download the package from the repositories ...).

I see one potential problem: libreadline6 is not really available for any version of Ubuntu past 16.04. In all later versions it's a purely virtual package. You'd need to install libreadline-dev which provides that virtual package.

Holger

---

### Post by aglyons on 2020-04-01
Hey @Holger_Gehrke, You were right about libreadline6 being a problem. The apt install did get things going but it crapped out because of that missing dep.

I'll have to think of another approach.

Thanks for pointing me in the right direction.

---

### Post by Holger_Gehrke on 2020-04-01
And I also said to try and install libreadline-dev ('sudo apt install libreadline-dev') because that will provide the virtual package. Have you tried that ?

Holger

---

