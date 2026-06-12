---
title: "Additional Drivers will not start ( Ubuntu 11.10 )"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Jakobskadkaer on 2012-03-21
I have this exact same problem in the 11.10 version.
[http://ubuntuforums.org/showthread.php?t=1693778](http://ubuntuforums.org/showthread.php?t=1693778)

I get this after running 'sudo apt-get update && sudo apt-get upgrade'

```
[COLOR=#000000][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security InRelease
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric InRelease                            
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates InRelease                    
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports InRelease
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric InRelease 
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security Release.gpg
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric Release.gpg
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates Release.gpg         
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports Release.gpg       
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security Release              
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric Release.gpg                     
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric Release                      
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates Release                       
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric Release                                   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports Release            
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/main Sources                   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/universe i386 Packages                
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/multiverse i386 Packages     
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/main TranslationIndex        
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/multiverse TranslationIndex           
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/restricted TranslationIndex 
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/universe TranslationIndex   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/main Sources        
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/restricted Sources  
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/universe Sources    
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/multiverse Sources  
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/main i386 Packages  
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/restricted i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/universe i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric/main Sources                    
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/restricted Sources   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/universe Sources
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/multiverse Sources   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/main i386 Packages   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/restricted i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/main TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/universe TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/universe i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/multiverse i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/main TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/multiverse TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/restricted TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric/main i386 Packages              
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric/main TranslationIndex           
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/universe TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/main Translation-en  
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/multiverse Translation-en
[/COLOR][COLOR=#0000BB]Get[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]1 http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/main Sources [1,095 kB]   
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/restricted Sources                    
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/restricted Translation-en      
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//security.ubuntu.com oneiric-security/universe Translation-en        
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric/main Translation-en_US                    
[/COLOR][COLOR=#0000BB]Ign http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//extras.ubuntu.com oneiric/main Translation-en
[/COLOR][COLOR=#0000BB]Get[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]2 http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/universe Sources [5,792 kB]
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/multiverse Sources
[/COLOR][COLOR=#0000BB]Get[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]3 http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/main i386 Packages [1,583 kB]
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/restricted i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/restricted Sources
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/universe Sources
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/multiverse Sources
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/main i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/restricted i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/universe i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/main TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/universe TranslationIndex
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/multiverse Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/restricted Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/multiverse Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/restricted Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/universe Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/main Sources
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/main Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/multiverse Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/restricted Translation-en
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-backports/universe Translation-en
[/COLOR][COLOR=#0000BB]Get[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]4 http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/main Translation-en [861 kB]
[/COLOR][COLOR=#0000BB]Get[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]5 http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric/universe Translation-en [3,919 kB]
[/COLOR][COLOR=#0000BB]Hit http[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//dk.archive.ubuntu.com oneiric-updates/main Translation-en
[/COLOR][COLOR=#0000BB]Fetched 5 B in 1s [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]2 B[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]s[/COLOR][COLOR=#007700])      
[/COLOR][COLOR=#0000BB]W[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Failed to fetch gzip[/COLOR][COLOR=#007700]:/var/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lists[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]partial[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dk[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]archive[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ubuntu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Failed to fetch gzip[/COLOR][COLOR=#007700]:/var/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lists[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]partial[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dk[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]archive[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ubuntu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch

W[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Failed to fetch gzip[/COLOR][COLOR=#007700]:/var/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lists[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]partial[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dk[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]archive[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ubuntu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]com_ubuntu_dists_oneiric_main_binary[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]i386_Packages  Hash Sum mismatch

W[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Failed to fetch gzip[/COLOR][COLOR=#007700]:/var/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lists[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]partial[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dk[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]archive[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ubuntu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]com_ubuntu_dists_oneiric_main_i18n_Translation[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]en  Encountered a section with no Package[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]header

W[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Failed to fetch gzip[/COLOR][COLOR=#007700]:/var/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lists[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]partial[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]dk[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]archive[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]ubuntu[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]com_ubuntu_dists_oneiric_universe_i18n_Translation[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]en  Encountered a section with no Package[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]header

E[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]Some index files failed to download[/COLOR][COLOR=#007700]. [/COLOR][COLOR=#0000BB]They have been ignored[/COLOR][COLOR=#007700], or [/COLOR][COLOR=#0000BB]old ones used instead[/COLOR][COLOR=#007700].  [/COLOR][/COLOR]
```What should i do about it ?

Jakob

---

### Post by HiImTye on 2012-03-21
try switching your download server (software sources) and issuing the command again

---

### Post by Jakobskadkaer on 2012-03-21
That Solved it

Thank you !

---

