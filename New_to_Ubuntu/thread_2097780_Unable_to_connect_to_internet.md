---
title: "Unable to connect to internet"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by hiranyaroma on 2012-12-24
Hi,
I am using Ubuntu 12.04. I connect to the internet using a proxy. I have put the settings in the network settings of ubuntu. I have also edited the /etc/apt/apt.conf.d/ file as suggested [here]("http://ubuntuforums.org/superuser.com/questions/417903/where-is-proxy-setting-saved-on-ubuntu-12-04"). But still unable to connect to internet. This is the error i get while trying to update system.
> chandu@ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                              
  Something wicked happened resolving 'netmon.iitb.ac.in:80' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                         
  Something wicked happened resolving 'netmon.iitb.ac.in:80' (-5 - No address associated with hostname)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                     
  Something wicked happened resolving 'netmon.iitb.ac.in:80' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                                             
  Something wicked happened resolving 'netmon.iitb.ac.in:80' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                           
  Something wicked happened resolving 'netmon.iitb.ac.in:80' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                
22% [Connecting to netmon.iitb.ac.in] [Connecting to netmon.iitb.ac.in] [Connecting to netmon.iitb.ac.in]^Cchandu@ubuntu:~$ 



Please help me out.

---

### Post by s1baker on 2012-12-24
is your firewall set "off"?

---

### Post by s1baker on 2012-12-24
I mean "sudo ufw disable"

---

