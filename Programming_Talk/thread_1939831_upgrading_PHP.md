---
title: "upgrading PHP"
date: 2012-03-12
forum: Programming Talk
---

### Post by 1cookie on 2012-03-12
hi

I'm currently using PHP 5.3.x. With the release of 5.4.x, Is there a simple command line way of upgrading from 5.3 to 5.4? Ive tried:

```

andy@andy-R519-R719:~$ php -v
PHP 5.3.6-13ubuntu3.6 with Suhosin-Patch (cli) (built: Feb 11 2012 02:17:16) 
Copyright (c) 1997-2011 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2011 Zend Technologies
andy@andy-R519-R719:~$ sudo add-apt-repository ppa:nginx/php5.4
[sudo] password for andy: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 83, in get_ppa_info_from_lp
    return json.loads(lp_page)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded
andy@andy-R519-R719:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://gb.archive.ubuntu.com oneiric InRelease                                     
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                           
Ign http://archive.canonical.com oneiric InRelease                                     
Ign http://extras.ubuntu.com oneiric InRelease                                         
Hit http://security.ubuntu.com oneiric-security Release.gpg                            
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                                   
Hit http://extras.ubuntu.com oneiric Release.gpg                                       
Hit http://archive.canonical.com oneiric Release.gpg                                   
Hit http://security.ubuntu.com oneiric-security Release                                
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release                                           
Hit http://archive.canonical.com oneiric Release                                       
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                         
Hit http://security.ubuntu.com oneiric-security/main Sources                           
Hit http://gb.archive.ubuntu.com oneiric Release                                       
Hit http://extras.ubuntu.com oneiric/main Sources                                      
Hit http://security.ubuntu.com oneiric-security/restricted Sources                     
Hit http://security.ubuntu.com oneiric-security/universe Sources                       
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                     
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                     
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com oneiric-updates Release                               
Hit http://archive.canonical.com oneiric/partner i386 Packages                         
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                             
Hit http://gb.archive.ubuntu.com oneiric-backports Release                             
Hit http://gb.archive.ubuntu.com oneiric/main Sources                                  
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                            
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                              
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                            
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                 
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages               
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                  
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex            
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex            
Ign http://archive.canonical.com oneiric/partner TranslationIndex                      
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                            
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages                      
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                        
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages                      
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                         
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex              
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex                   
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex                   
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex                     
Hit http://gb.archive.ubuntu.com oneiric-updates/main Sources                          
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Sources                    
Hit http://security.ubuntu.com oneiric-security/main Translation-en                    
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Sources                      
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources                    
Hit http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages                
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en              
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex             
Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources                        
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources                  
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources                    
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources                  
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages                  
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages            
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages            
Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex               
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex         
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex         
Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                        
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                           
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB                  
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en                     
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB                  
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en                     
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB                    
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en                       
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en                   
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en             
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en               
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en                 
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en             
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                            
Ign http://archive.canonical.com oneiric/partner Translation-en_GB   
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://linux.avasys.jp lsb3.2 InRelease    
Hit http://linux.avasys.jp lsb3.2 Release.gpg
Hit http://linux.avasys.jp lsb3.2 Release
Hit http://linux.avasys.jp lsb3.2/main i386 Packages
Ign http://linux.avasys.jp lsb3.2/main TranslationIndex
Ign http://linux.avasys.jp lsb3.2/main Translation-en_GB
Ign http://linux.avasys.jp lsb3.2/main Translation-en
Reading package lists... Done
andy@andy-R519-R719:~$ sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
The following packages were automatically installed and are no longer required:
  dia-libs libboost-program-options1.42.0 virtualbox-ose libgcj11 libjs-mootools
  virtualbox-ose-dkms gcj-4.5-jre-lib dia-common libreadline5 gcj-4.5-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

I'm still on 5.3 though...

---

### Post by Bachstelze on 2012-03-12
> **1cookie said:**
> Is there a simple command line way of upgrading from 5.3 to 5.4?

Depends how you define "simple". If you mean something as simple as [font=monospace]apt-get update && apt-get upgrade[/font], the answer is no, not in Ubuntu.

If you really want PHP 5.4, you can either search for a third-party repository with Ubuntu packages of it, or get it from Debian Sid.

---

### Post by 1cookie on 2012-03-13
> **Bachstelze said:**
> Depends how you define "simple". If you mean something as simple as [FONT=monospace]apt-get update && apt-get upgrade[/FONT], the answer is no, not in Ubuntu.
 
If you really want PHP 5.4, you can either search for a third-party repository with Ubuntu packages of it, or get it from Debian Sid.
 
thanks
 
Ive never had the need to upgrade in Ubuntu before. So from the package manager do i have to uninstall then reinstall php? Is that the normal way to upgrade?

---

### Post by Bachstelze on 2012-03-13
> **1cookie said:**
> thanks
 
Ive never had the need to upgrade in Ubuntu before. So from the package manager do i have to uninstall then reinstall php? Is that the normal way to upgrade?

There is no "normal" way to upgrade a package that is not in the repositories. If you get an updated version form somewhere else as a DEB package, then it depends. If it was built properly, like if you get it from Debian, then there is no need to uninstall, the package manager will recognize it as an update, and will update your existing packages when you install the new ones.

If you install directly from the source code, then yes, you have to uninstall the packages first. But since there are packages in Debian, you shouldn't need to go that way.

---

### Post by dharmavir on 2012-03-24
I think this might not be as simple as apt-get update/upgrade because 5.4 is new and have not been added to official repos yet.

So I would suggest you to go with separate setup by downloading complete bunch from the [bitnami lampstack]("http://bitnami.org/stack/lampstack").

Though as of today they are not production ready as they are apache2.4+php5.4 combo which is yet less explored.

[http://bitnami.org/stack/lampstack](http://bitnami.org/stack/lampstack)

Good luck.
[Dharmavirsinh Jhala]("http://www.dharmavir.com")

---

### Post by SeijiSensei on 2012-03-24
Is there some specific functionality in 5.4 that you need that isn't available in 5.3?  Upgrading just because there's a new release available isn't always the best idea, especially on a production server.

Security threats are usually handled quickly by the developers via an update to the current release version, so security is generally not a strong reason to change versions.

---

### Post by garak on 2012-04-01
> **SeijiSensei said:**
> Is there some specific functionality in 5.4 that you need that isn't available in 5.3?  Upgrading just because there's a new release available isn't always the best idea, especially on a production server.

Security threats are usually handled quickly by the developers via an update to the current release version, so security is generally not a strong reason to change versions.

Most notable difference in 5.4 is support for traits.
Anyway, 5.4 is still not stable and should not be used, unless you want to try traits.

---

### Post by dharmavir on 2012-04-02
Hi Cookie,

You should give try to bitnami lampstack ([LAMPStack 5.4.0-0 dev]("http://bitnami.org/stack/lampstack")), which is not production ready but I am hoping that you're not trying to upgrade 5.4 on your production server because that's too fresh for now and in that case you should wait till it become available on public repos.

---

### Post by 1cookie on 2012-04-09
hi

And thanks for all the tips. Apologies for a late response. Mon Amie...

---

