---
title: "'package operations failed' issue / ubuntu 14.04 lts"
date: 2015-04-13
forum: New to Ubuntu
---

### Post by kubasienczyk on 2015-04-13
Hello everyone, I am fairly new to Ubuntu. My wives machine suddenly refuses to update and chokes on "Ubuntu main components". Downloading and updating process starts, but after it reaches "installing" part it suddenly ends returning following message"

"Package operations failed. Unable to install or remove package".

A few months ago with the help of forum members I've been able to clear broken repositories using the console, however I am not able to redo that on my own and I need help again.

Ubuntu version is 14.04 LTS, machine is 64-bit Intel Pentium Dual Core T2390, 1.86 Ghz.

Thanks!

---

### Post by slickymaster on 2015-04-13
Can you please post back here in the thread the full output you get from```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by kubasienczyk on 2015-04-13
Here:

```
Ign.  [http://dl.google.com](http://dl.google.com) stable InRelease
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty InRelease                            
Ign.  [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                
Ign.  [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                
Stary [http://dl.google.com](http://dl.google.com) stable Release.gpg                                  
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security InRelease                   
Ign.  [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                            
Ign.  [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates InRelease                    
Stary [http://dl.google.com](http://dl.google.com) stable Release                                      
Ign.  [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                          
Pobieranie:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports InRelease                  
Ign.  [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty Release.gpg                          
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security Release.gpg                 
Ign.  [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                
Stary [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                          
Stary [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                  
Stary [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                          
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates Release.gpg                  
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                              
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports Release.gpg                
Stary [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                        
Stary [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                      
Stary [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                           
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty Release                              
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                              
Stary [http://archive.canonical.com](http://archive.canonical.com) trusty Release                              
Stary [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                       
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security Release                     
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates Release                      
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                              
Stary [http://archive.canonical.com](http://archive.canonical.com) maverick Release                            
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports Release                    
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                              
Stary [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/restricted amd64 Packages            
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/main amd64 Packages                  
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                  
Stary [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages               
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/multiverse amd64 Packages            
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                  
Stary [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/universe amd64 Packages              
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/restricted i386 Packages             
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                  
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/main i386 Packages                   
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                  
Stary [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                    
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/multiverse i386 Packages             
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                      
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                       
Ign.  [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en               
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/universe i386 Packages               
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/main Translation-pl                  
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/main Translation-en                  
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                      
Ign.  [http://dl.google.com](http://dl.google.com) stable/main Translation-pl_PL                       
Ign.  [http://dl.google.com](http://dl.google.com) stable/main Translation-pl                          
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                       
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/multiverse Translation-pl            
Ign.  [http://dl.google.com](http://dl.google.com) stable/main Translation-en                          
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/multiverse Translation-en            
Ign.  [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-pl_PL                   
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/restricted Translation-pl            
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/restricted Translation-en            
Ign.  [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-pl                      
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                      
Ign.  [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/universe Translation-pl              
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                       
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/universe Translation-en              
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/restricted amd64 Packages   
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/universe amd64 Packages     
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                      
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/multiverse amd64 Packages   
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/main amd64 Packages         
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                       
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/restricted i386 Packages    
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/universe i386 Packages      
Stary [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                     
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/multiverse i386 Packages   
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/main i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/main Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/multiverse Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/restricted Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-security/universe Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/restricted amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/universe amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/main amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/universe i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/main i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/main Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/restricted Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-updates/universe Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/main amd64 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/universe i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/main i386 Packages
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/main Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/restricted Translation-en
Stary [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/main Translation-pl_PL
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/multiverse Translation-pl_PL         
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/restricted Translation-pl_PL         
Ign.  [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) trusty/universe Translation-pl_PL           
Pobrano 72 B w 6s (10 B/s)                                                     
Czytanie list pakietów... Gotowe
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: Nale&#380;y uruchomi&#263; apt-get update aby naprawi&#263; te problemy.
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Obliczanie aktualizacji...Gotowe
Nast&#281;puj&#261;ce pakiety zostan&#261; zaktualizowane:
  compiz compiz-core compiz-gnome compiz-plugins-default gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs libcompizconfig0
  libdecoration0 libunity-core-6.0-9 ubuntu-docs unity unity-services
17 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
Konieczne pobranie 4,046 kB/5,241 kB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 947 kB miejsca na dysku.
Kontynuowa&#263;? [T/n] t
Pobieranie:1 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main libcompizconfig0 amd64 1:0.9.11.3+14.04.20150122-0ubuntu1 [117 kB]
Pobieranie:2 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main compiz-gnome amd64 1:0.9.11.3+14.04.20150122-0ubuntu1 [156 kB]
Pobieranie:3 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main compiz-plugins-default amd64 1:0.9.11.3+14.04.20150122-0ubuntu1 [770 kB]
Pobieranie:4 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main libdecoration0 amd64 1:0.9.11.3+14.04.20150122-0ubuntu1 [49.3 kB]
Pobieranie:5 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main compiz-core amd64 1:0.9.11.3+14.04.20150122-0ubuntu1 [296 kB]
Pobieranie:6 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main compiz all 1:0.9.11.3+14.04.20150122-0ubuntu1 [4,044 B]
Pobieranie:7 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-bin amd64 1.20.3-0ubuntu1 [50.8 kB]
Pobieranie:8 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-backends amd64 1.20.3-0ubuntu1 [271 kB]
Pobieranie:9 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-fuse amd64 1.20.3-0ubuntu1 [13.2 kB]
Pobieranie:10 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs amd64 1.20.3-0ubuntu1 [89.5 kB]
Pobieranie:11 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-daemons amd64 1.20.3-0ubuntu1 [109 kB]
Pobieranie:12 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-libs amd64 1.20.3-0ubuntu1 [106 kB]
Pobieranie:13 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main gvfs-common all 1.20.3-0ubuntu1 [42.4 kB]
Pobieranie:14 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main unity amd64 7.2.4+14.04.20141217-0ubuntu1 [1,508 kB]
Pobieranie:15 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main libunity-core-6.0-9 amd64 7.2.4+14.04.20141217-0ubuntu1 [433 kB]
Pobieranie:16 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates/main unity-services amd64 7.2.4+14.04.20141217-0ubuntu1 [31.8 kB]
Pobrano 4,046 kB w 1min 44s (38.6 kB/s)                                        
(Odczytywanie bazy danych ... 216658 plików i katalogów obecnie zainstalowanych.)
Preparing to unpack .../libcompizconfig0_1%3a0.9.11.3+14.04.20150122-0ubuntu1_amd64.deb ...
Unpacking libcompizconfig0 (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-gnome_1%3a0.9.11.3+14.04.20150122-0ubuntu1_amd64.deb ...
Unpacking compiz-gnome (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-plugins-default_1%3a0.9.11.3+14.04.20150122-0ubuntu1_amd64.deb ...
Unpacking compiz-plugins-default (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../libdecoration0_1%3a0.9.11.3+14.04.20150122-0ubuntu1_amd64.deb ...
Unpacking libdecoration0 (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-core_1%3a0.9.11.3+14.04.20150122-0ubuntu1_amd64.deb ...
Unpacking compiz-core (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz_1%3a0.9.11.3+14.04.20150122-0ubuntu1_all.deb ...
Unpacking compiz (1:0.9.11.3+14.04.20150122-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../gvfs-bin_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-bin (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-backends_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-backends (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-fuse_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-fuse (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-daemons_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-daemons (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-libs_1.20.3-0ubuntu1_amd64.deb ...
Unpacking gvfs-libs:amd64 (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../gvfs-common_1.20.3-0ubuntu1_all.deb ...
Unpacking gvfs-common (1.20.3-0ubuntu1) over (1.20.1-1ubuntu1) ...
Preparing to unpack .../unity_7.2.4+14.04.20141217-0ubuntu1_amd64.deb ...
Unpacking unity (7.2.4+14.04.20141217-0ubuntu1) over (7.2.3+14.04.20140826-0ubuntu1) ...
Preparing to unpack .../libunity-core-6.0-9_7.2.4+14.04.20141217-0ubuntu1_amd64.deb ...
Unpacking libunity-core-6.0-9 (7.2.4+14.04.20141217-0ubuntu1) over (7.2.3+14.04.20140826-0ubuntu1) ...
Preparing to unpack .../unity-services_7.2.4+14.04.20141217-0ubuntu1_amd64.deb ...
Unpacking unity-services (7.2.4+14.04.20141217-0ubuntu1) over (7.2.3+14.04.20140826-0ubuntu1) ...
Preparing to unpack .../ubuntu-docs_14.04.5_all.deb ...
Unpacking ubuntu-docs (14.04.5) over (14.04.4) ...
Brak raportu programu apport, poniewa&#380; komunikat b&#322;&#281;du wskazuje na przepe&#322;nienie dysku
      dpkg: error processing archive /var/cache/apt/archives/ubuntu-docs_14.04.5_all.deb (--unpack):
 nie mo&#380;na utworzy&#263; dowi&#261;zania symbolicznego "./usr/share/help/fr/ubuntu-help/sound-broken.page": Brak miejsca na urz&#261;dzeniu
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 /var/cache/apt/archives/ubuntu-docs_14.04.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by slickymaster on 2015-04-13
> **kubasienczyk said:**
> Here:

```
<---snip--->
[COLOR=#ff0000]W: Duplicate sources.list entry [/COLOR][[COLOR=#ff0000]http://archive.canonical.com/ubuntu/[/COLOR]]("http://archive.canonical.com/ubuntu/")[COLOR=#ff0000] trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [/COLOR][[COLOR=#ff0000]http://archive.canonical.com/ubuntu/[/COLOR]]("http://archive.canonical.com/ubuntu/")[COLOR=#ff0000] trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)[/COLOR]
W: Nale&#380;y uruchomi&#263; apt-get update aby naprawi&#263; te problemy.<---snip--->
```
I'm can't speak Polish, but I think that these two lines are indicating us the culprit. Your **sources.list** file has duplicate entries.
Open a terminal and first rename the existing sources.list file to sources.list.bak```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
```Afterwards run```
software-properties-gtk
```After the window is open, select all four categories in the Ubuntu Software tab. Once that done, run again```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by kubasienczyk on 2015-04-13
Doesn't work. I get the message:

"list.bak is not a catalogue"

---

### Post by ian-weisser on 2015-04-13
> **kubasienczyk said:**
> 
Unpacking ubuntu-docs (14.04.5) over (14.04.4) ...
Brak raportu programu apport, poniewa&#380; komunikat b&#322;&#281;du wskazuje na przepe&#322;nienie dysku
      dpkg: error processing archive /var/cache/apt/archives/ubuntu-docs_14.04.5_all.deb (--unpack):
 nie mo&#380;na utworzy&#263; dowi&#261;zania symbolicznego "./usr/share/help/fr/ubuntu-help/sound-broken.page": **Brak miejsca na urz&#261;dzeniu**

Looks like your have TWO problems. You have a malformed source (Slickymaster's help is addressing that), *and* your partition is full.
Please post the output of:
```
df
df -i
```

For example, here's what mine looks like:
```
$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      714871336 98189904 580345048  15% /
none                   4        0         4   0% /sys/fs/cgroup
udev             2985640        4   2985636   1% /dev
tmpfs             599352     1260    598092   1% /run
none                5120        4      5116   1% /run/lock
none             2996752      200   2996552   1% /run/shm
none              102400       96    102304   1% /run/user

$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1      45400064 789112 44610952    2% /
none             749188      4   749184    1% /sys/fs/cgroup
udev             746410    488   745922    1% /dev
tmpfs            749188    576   748612    1% /run
none             749188     15   749173    1% /run/lock
none             749188     11   749177    1% /run/shm
none             749188     53   749135    1% /run/user

```You can see that my system (/) is only 15% full, I have lots of space. Yours should look different.

---

### Post by slickymaster on 2015-04-13
Can you post the output of```
cat /etc/apt/sources.list
```and```
ls /etc/apt/sources.list.d/
```

---

### Post by kubasienczyk on 2015-04-14
Thank you for your input.
My results after typing in your commands:

command: df

System plików  1K-blocks    u&#380;yte  dost&#281;pne %u&#380;. zamont. na
/dev/sda1        9711136  8205720    989064  90% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1525364        4   1525360   1% /dev
tmpfs             307232     1316    305916   1% /run
none                5120        0      5120   0% /run/lock
none             1536152       76   1536076   1% /run/shm
none              102400       32    102368   1% /run/user
/dev/sda5      229412012 81941712 135794116  38% /home



command: df -i

System plików    iw&#281;z&#322;y u&#380;yteI   wolneI %u&#380;.I zamont. na
/dev/sda1        625856 595358    30498   96% /
none             384038      2   384036    1% /sys/fs/cgroup
udev             381341    520   380821    1% /dev
tmpfs            384038    549   383489    1% /run
none             384038      3   384035    1% /run/lock
none             384038      5   384033    1% /run/shm
none             384038     24   384014    1% /run/user
/dev/sda5      14553280  69923 14483357    1% /home



command: cat /etc/apt/sources.list


# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security restricted main universe
# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates restricted main universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-security main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-proposed main restricted universe
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-security restricted universe multiverse main
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates restricted universe multiverse main
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-backports restricted universe multiverse main
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main


command: ls /etc/apt/sources.list.d/

caffeine-developers-ppa-trusty.list
caffeine-developers-ppa-trusty.list.save
google-chrome.list
google-chrome.list.save
linrunner-tlp-trusty.list
linrunner-tlp-trusty.list.save
skunk-pepper-flash-trusty.list
webupd8team-popcorntime-trusty.list
webupd8team-popcorntime-trusty.list.save

---

### Post by ian-weisser on 2015-04-14
> **kubasienczyk said:**
> System plików  1K-blocks    u&#380;yte  dost&#281;pne %u&#380;. zamont. na
/dev/sda1        9711136  8205720    989064  90% /

System plików    iw&#281;z&#322;y u&#380;yteI   wolneI %u&#380;.I zamont. na
/dev/sda1        625856 595358    30498   96% /


Yes, your system partition (/) is full. 90% space, 96% inodes.

Try the following commands:
```
sudo apt-get autoremove
sudo apt-get autoclean
```

Does that free up significant space?


Your sources.list could use a bit of cleanup.
Delete the CD-ROM entries, unless you really intend to use the CD ROM again.
You have lots of duplicate lines, some enabled, others commented out.


> **kubasienczyk said:**
> "list.bak is not a catalogue"
That's right, it's not. It's a backup. Move it out of that directory. You created it just-in-case you needed to restore your sources.

---

### Post by kubasienczyk on 2015-04-14
I run both commands and they did delete some entries, but only a few. Apparently not enough, as problem is still on.
Is "New to Ubuntu" section too advanced to ask how exactly and technically do I perform these operations? Meaning - deleting entries and moving .bak file out of ill directory? :)
I'll get better.

---

### Post by Bashing-om on 2015-04-14
kubasienczyk; Hello;

I'll see what I can do to move this along. As you know there are several issues at play here.
Let's back up and regroup - see what the situation is presently:
and:
> 
Is "New to Ubuntu" section too advanced to ask how exactly and technically do I perform these operations?

Not at all, we will meet with you at your level.
Show us what now we are working with: Post back -Between Code Tags, PLEASE - the outputs of terminal commands:
```

df -h
dpkg -l | grep linux-
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to keep outputs formatted and readable.

[INDENT][INDENT][INDENT]here we go again
[/INDENT][/INDENT][/INDENT]

---

### Post by kubasienczyk on 2015-04-14
Bashing-om, thank you. I appreciate it.
OK then - outputs:

```

System plików  rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sda1       9.3G  7.7G  1.1G  88% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           301M  1.3M  299M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G   76K  1.5G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda5       219G   79G  129G  38% /home


```

```

ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-36                               3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                       3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-38-generic                         3.13.0-38.65                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-38-generic                   3.13.0-38.65                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                  3.13.0-49.83                                        amd64        Linux Kernel Headers for development
ii  linux-lts-utopic-tools-3.16.0-31                      3.16.0-31.43~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-31
ii  linux-lts-utopic-tools-3.16.0-33                      3.16.0-33.44~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-33
ii  linux-lts-utopic-tools-3.16.0-34                      3.16.0-34.47~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-34
ii  linux-lts-utopic-tools-common                         3.16.0-34.47~14.04.1                                all          Linux kernel version specific tools for version 3.16.0
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  linux-tools-3.13.0-45                                 3.13.0-45.74                                        amd64        Linux kernel version specific tools for version 3.13.0-45
ii  linux-tools-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel version specific tools for version 3.13.0-45
ii  linux-tools-3.13.0-46                                 3.13.0-46.79                                        amd64        Linux kernel version specific tools for version 3.13.0-46
ii  linux-tools-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel version specific tools for version 3.13.0-46
ii  linux-tools-3.13.0-48                                 3.13.0-48.80                                        amd64        Linux kernel version specific tools for version 3.13.0-48
ii  linux-tools-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel version specific tools for version 3.13.0-48
ii  linux-tools-3.13.0-49                                 3.13.0-49.83                                        amd64        Linux kernel version specific tools for version 3.13.0-49
ii  linux-tools-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel version specific tools for version 3.13.0-49
ii  linux-tools-3.16.0-31-generic                         3.16.0-31.43~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-31
ii  linux-tools-3.16.0-33-generic                         3.16.0-33.44~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-33
ii  linux-tools-3.16.0-34-generic                         3.16.0-34.47~14.04.1                                amd64        Linux kernel version specific tools for version 3.16.0-34
ii  linux-tools-common                                    3.13.0-49.83                                        all          Linux kernel version specific tools for version 3.13.0
ii  linux-tools-generic                                   3.13.0.49.56                                        amd64        Generic Linux kernel tools
ii  linux-tools-virtual-lts-utopic                        3.16.0.34.27                                        amd64        This package will always depend on the latest minimal generic kernel tools.
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

```

     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    
     6    # deb http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe
     7    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    17    ## team, and may not be under a free licence. Please satisfy yourself as to 
    18    ## your rights to use the software. Also, please note that software in 
    19    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    20    ## security team.
    21    
    22    ## Uncomment the following two lines to add software from the 'backports'
    23    ## repository.
    24    ## N.B. software from this repository may not have been tested as
    25    ## extensively as that contained in the main release, although it includes
    26    ## newer versions of some applications which may provide useful features.
    27    ## Also, please note that software in backports WILL NOT receive any review
    28    ## or updates from the Ubuntu security team.
    29    # deb http://pl.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
    30    # deb-src http://pl.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
    31    
    32    ## Uncomment the following two lines to add software from Canonical's
    33    ## 'partner' repository.
    34    ## This software is not part of Ubuntu, but is offered by Canonical and the
    35    ## respective vendors as a service to Ubuntu users.
    36    deb http://archive.canonical.com/ubuntu trusty partner
    37    deb-src http://archive.canonical.com/ubuntu maverick partner
    38    
    39    ## This software is not part of Ubuntu, but is offered by third-party
    40    ## developers who want to ship their latest software.
    41    # deb http://extras.ubuntu.com/ubuntu maverick main
    42    # deb-src http://extras.ubuntu.com/ubuntu maverick main
    43    # deb http://security.ubuntu.com/ubuntu/ trusty-security restricted main universe
    44    # deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates restricted main universe
    45    
    46    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    47    # newer versions of the distribution.
    48    
    49    ## Major bug fix updates produced after the final release of the
    50    ## distribution.
    51    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe
    52    
    53    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    54    ## team. Also, please note that software in universe WILL NOT receive any
    55    ## review or updates from the Ubuntu security team.
    56    
    57    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    58    ## team, and may not be under a free licence. Please satisfy yourself as to 
    59    ## your rights to use the software. Also, please note that software in 
    60    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    61    ## security team.
    62    
    63    ## N.B. software from this repository may not have been tested as
    64    ## extensively as that contained in the main release, although it includes
    65    ## newer versions of some applications which may provide useful features.
    66    ## Also, please note that software in backports WILL NOT receive any review
    67    ## or updates from the Ubuntu security team.
    68    
    69    # deb http://pl.archive.ubuntu.com/ubuntu/ trusty-security main restricted
    70    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe
    71    
    72    ## Uncomment the following two lines to add software from Canonical's
    73    ## 'partner' repository.
    74    ## This software is not part of Ubuntu, but is offered by Canonical and the
    75    ## respective vendors as a service to Ubuntu users.
    76    deb http://archive.canonical.com/ubuntu trusty partner
    77    deb-src http://archive.canonical.com/ubuntu trusty partner
    78    
    79    ## This software is not part of Ubuntu, but is offered by third-party
    80    ## developers who want to ship their latest software.
    81    deb http://extras.ubuntu.com/ubuntu trusty main
    82    # deb-src http://extras.ubuntu.com/ubuntu trusty main
    83    # deb http://pl.archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe
    84    deb http://pl.archive.ubuntu.com/ubuntu/ trusty restricted main multiverse universe
    85    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
    86    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
    87    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
    88    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-security restricted universe multiverse main
    89    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
    90    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates restricted universe multiverse main
    91    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
    92    deb http://pl.archive.ubuntu.com/ubuntu/ trusty-backports restricted universe multiverse main
    93    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    94    # deb-src http://archive.canonical.com/ubuntu trusty partner
    95    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
    96    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
    97    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
    98    # deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    99    
   100    # deb-src http://archive.canonical.com/ubuntu trusty partner
   101    # deb-src http://extras.ubuntu.com/ubuntu trusty main


```

```


==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <==
deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main

==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list.save <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main

==> /etc/apt/sources.list.d/skunk-pepper-flash-trusty.list <==
deb http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main
# deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-popcorntime-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu trusty main


```

Thanks!

---

### Post by Bashing-om on 2015-04-14
kubasienczyk; Yikes !

Source list is "something else" .. getting it straight is the 1st thing,
Then we look at why "autoremove" did not remove the old kernels.

focus on the sources.list file; you have made a back up right ?
ok:
line 6, - place it back in service  - remove the '#' character at the start of the line. gets the main, restricted and universe repositories available.
line 43 - trusty-security - place back in service . restricted main universe
LineXX add multiverse to - trusty-security 

line 37 - maverick- That release is End_Of_Life ; the repository no longer exists. Comment it out.

line 44, - trusty-updates - place it back in service . restricted main universe
line XX, (none) - trusty-updates - add the multiverse repository. 

Line XX, (none) - trusty multiverse -.. no provision made for trusty multiverse repository. ->
( deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) trusty multiverse )

line 76 - duplicate of line 37
line 77 comment it out, as it is 'source' and you do not need it.
line 88 - duplicate of line 43

line92, is there a good reason to enable this repository ? comment it out otherwise.

---------------
I have checked 3 times, this is all i presently see to change. - Not to say I have not missed something -
when the changes are made, and the file is saved; see now what the package manager thinks:
```

sudo apt-get update
sudo apt-get upgrade

```
if these do not run clean, provide that complete output . We will then see where we jump to.
--------------------

I have chores to take care of, will be a while before I return .
In that mean while,
[INDENT][INDENT][INDENT][INDENT]have fun
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-04-14
I would open the Dash and look for 'Disk Usage Analyzer' to show what is filling that partition.
If not installed, it's available in Software Center.

---

