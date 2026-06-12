---
title: "unable to update"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by abhisheksinghrn02 on 2013-02-14
os version = ubuntu 10.04 server edition
apt-get update giving following output

```
Get:1 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid Release.gpg [688B]
Get:2 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN [708B]
98% [2 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN                               
Get:3 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN [714B]                
65% [3 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN                                                         
Get:4 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN [712B]                                                  
49% [4 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN                                                           
Get:5 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN [714B]                                                
39% [5 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN                                                         
Get:6 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates Release.gpg [696B]                                                                 
Get:7 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN [716B]               
42% [7 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN                                                       
Get:8 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN [722B]                                        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [695B]              
43% [8 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN                 
Get:10 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN [715B]              
Get:11 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN [720B]
45% [10 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN                         
35% [11 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN                    
Get:12 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN [721B]         
32% [12 Translation-en_IN bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN                                                
Get:13 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN [722B]                                     
30% [13 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN                                                  
Get:14 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid Release                                                                                    
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [704B]                                           
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid Release                                                                         
Get:16 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN [719B]                             
36% [16 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN                     
Get:17 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates Release [692B]                                     
Get:18 [http://ppa.launchpad.net/freeradius/stable/ubuntu/](http://ppa.launchpad.net/freeradius/stable/ubuntu/) precise/main Translation-en_IN [724B]
38% [17 Release gpgv 692B] [18 Translation-en_IN bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers] [Wabzip2: (stdin) is not a bzip2 file.
Get:19 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN [721B]                                              
Ign [http://ppa.launchpad.net/freeradius/stable/ubuntu/](http://ppa.launchpad.net/freeradius/stable/ubuntu/) precise/main Translation-en_IN                                                     
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates Release                                                                                    
36% [19 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN                   
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                 
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [700B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                          
Get:22 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/main Packages [706B]        
40% [22 Packages bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/main Packages                                        
  Sub-process /bin/bzip2 returned an error code (2)
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                              
42% [23 Packages bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                                              
  Sub-process /bin/bzip2 returned an error code (2)
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Packages [722B]                                                             
45% [24 Packages bzip2 0B] [Waiting for headers] [Waiting for headers] [Connecting to ppa.launchpad.net (91.189.95.83)]bzip2: (stdin) is not a bzip2 file.
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Packages                                                                     
  Sub-process /bin/bzip2 returned an error code (2)
Get:25 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/restricted Packages [712B]                                                   
47% [25 Packages bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/restricted Packages                                  
  Sub-process /bin/bzip2 returned an error code (2)
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                        
49% [26 Packages bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                                        
  Sub-process /bin/bzip2 returned an error code (2)
Get:27 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/main Sources [700B]                                                            
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [716B]          
53% [27 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/main Sources                  
  Sub-process /bin/bzip2 returned an error code (2)
53% [28 Sources bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources        
54% [29 Sources bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                                        
  Sub-process /bin/bzip2 returned an error code (2)
Get:30 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/restricted Sources                                      
56% [30 Sources bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/restricted Sources                                            
  Sub-process /bin/bzip2 returned an error code (2)
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                                  
57% [31 Sources bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                                  
  Sub-process /bin/bzip2 returned an error code (2)
Get:32 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/universe Packages [710B]                                
58% [32 Packages bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/universe Packages              
  Sub-process /bin/bzip2 returned an error code (2)
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [717B]
60% [33 Packages bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:34 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/universe Sources [704B]                                  
61% [34 Sources bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/universe Sources                                              
  Sub-process /bin/bzip2 returned an error code (2)
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [711B]                             
62% [35 Sources bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                              
63% [36 Packages bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.91.13)]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                                  
  Sub-process /bin/bzip2 returned an error code (2)
Get:37 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/multiverse Packages [712B]                               
64% [37 Packages bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/multiverse Packages                                            
  Sub-process /bin/bzip2 returned an error code (2)
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [713B]                            
65% [38 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:39 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/multiverse Sources
66% [39 Sources bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid/multiverse Sources                      
  Sub-process /bin/bzip2 returned an error code (2)
Get:40 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/main Packages [714B]         
67% [40 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:41 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/restricted Packages [720B]
67% [41 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:42 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/main Sources [708B]
68% [42 Sources bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/main Sources                    
  Sub-process /bin/bzip2 returned an error code (2)
Get:43 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/restricted Sources           
69% [43 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:44 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/universe Packages [718B]
70% [44 Packages bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/universe Packages                
  Sub-process /bin/bzip2 returned an error code (2)
Get:45 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/universe Sources [712B]       
70% [45 Sources bzip2 0B] [Connecting to lk.archive.ubuntu.com (91.189.92.200)]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/universe Sources                
  Sub-process /bin/bzip2 returned an error code (2)
Get:46 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/multiverse Packages [720B]   
71% [46 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:47 [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/multiverse Sources [714B]
72% [47 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 33.4kB in 1s (22.2kB/s)
W: GPG error: [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2](http://lk.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://ppa.launchpad.net/freeradius/stable/ubuntu/dists/precise/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/freeradius/stable/ubuntu/dists/precise/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://ppa.launchpad.net/freeradius/stable/ubuntu/dists/precise/main/source/Sources.bz2](http://ppa.launchpad.net/freeradius/stable/ubuntu/dists/precise/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```



nothing is getting updated 
please do help

---

### Post by schragge on 2013-02-14
Try
```

sudo apt-get -o Acquire::CompressionTypes::Order::=gz update

```

---

### Post by abhisheksinghrn02 on 2013-02-14
output of 
```
sudo apt-get -o Acquire::CompressionTypes::Order::=gz update

Ign [http://hobbes](http://hobbes) lucid Release.gpg
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Ign [http://hobbes](http://hobbes) lucid-updates Release.gpg
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Ign [http://hobbes](http://hobbes) lucid-security Release.gpg
Ign [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Ign [http://hobbes](http://hobbes) lucid Release
Ign [http://hobbes](http://hobbes) lucid-updates Release
Ign [http://hobbes](http://hobbes) lucid-security Release
Ign [http://hobbes](http://hobbes) lucid/main Packages
Ign [http://hobbes](http://hobbes) lucid/restricted Packages
Ign [http://hobbes](http://hobbes) lucid/main Sources
Ign [http://hobbes](http://hobbes) lucid/restricted Sources
Ign [http://hobbes](http://hobbes) lucid/universe Packages
Ign [http://hobbes](http://hobbes) lucid/universe Sources
Ign [http://hobbes](http://hobbes) lucid/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid/multiverse Sources
Ign [http://hobbes](http://hobbes) lucid-updates/main Packages
Ign [http://hobbes](http://hobbes) lucid-updates/restricted Packages
Ign [http://hobbes](http://hobbes) lucid-updates/main Sources
Ign [http://hobbes](http://hobbes) lucid-updates/restricted Sources
Ign [http://hobbes](http://hobbes) lucid-updates/universe Packages
Ign [http://hobbes](http://hobbes) lucid-updates/universe Sources
Ign [http://hobbes](http://hobbes) lucid-updates/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid-updates/multiverse Sources
Ign [http://hobbes](http://hobbes) lucid-security/main Packages
Ign [http://hobbes](http://hobbes) lucid-security/restricted Packages
Ign [http://hobbes](http://hobbes) lucid-security/main Sources
Ign [http://hobbes](http://hobbes) lucid-security/restricted Sources
Ign [http://hobbes](http://hobbes) lucid-security/universe Packages
Ign [http://hobbes](http://hobbes) lucid-security/universe Sources
Ign [http://hobbes](http://hobbes) lucid-security/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid-security/multiverse Sources
Ign [http://hobbes](http://hobbes) lucid/main Packages
Ign [http://hobbes](http://hobbes) lucid/restricted Packages
Ign [http://hobbes](http://hobbes) lucid/main Sources
Ign [http://hobbes](http://hobbes) lucid/restricted Sources
Ign [http://hobbes](http://hobbes) lucid/universe Packages
Ign [http://hobbes](http://hobbes) lucid/universe Sources
Ign [http://hobbes](http://hobbes) lucid/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid/multiverse Sources
Ign [http://hobbes](http://hobbes) lucid-updates/main Packages
Ign [http://hobbes](http://hobbes) lucid-updates/restricted Packages
Ign [http://hobbes](http://hobbes) lucid-updates/main Sources
Ign [http://hobbes](http://hobbes) lucid-updates/restricted Sources
Ign [http://hobbes](http://hobbes) lucid-updates/universe Packages
Ign [http://hobbes](http://hobbes) lucid-updates/universe Sources
Ign [http://hobbes](http://hobbes) lucid-updates/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid-updates/multiverse Sources
Ign [http://hobbes](http://hobbes) lucid-security/main Packages
Ign [http://hobbes](http://hobbes) lucid-security/restricted Packages
Ign [http://hobbes](http://hobbes) lucid-security/main Sources
Ign [http://hobbes](http://hobbes) lucid-security/restricted Sources
Ign [http://hobbes](http://hobbes) lucid-security/universe Packages
Ign [http://hobbes](http://hobbes) lucid-security/universe Sources
Ign [http://hobbes](http://hobbes) lucid-security/multiverse Packages
Ign [http://hobbes](http://hobbes) lucid-security/multiverse Sources
Err [http://hobbes](http://hobbes) lucid/main Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/restricted Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/main Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/restricted Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/universe Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/universe Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/multiverse Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid/multiverse Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/main Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/restricted Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/main Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/restricted Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/universe Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/universe Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/multiverse Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-updates/multiverse Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/main Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/restricted Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/main Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/restricted Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/universe Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/universe Sources
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/multiverse Packages
  401  Unauthorized
Err [http://hobbes](http://hobbes) lucid-security/multiverse Sources
  401  Unauthorized
W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.lzma](http://hobbes/apt-cacher/in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.lzma)  401  Unauthorized

W: Failed to fetch [http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.lzma](http://hobbes/apt-cacher/security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.lzma)  401  Unauthorized

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by schragge on 2013-02-14
Wow, what a spectacular failure. Is it *apt-cacher* or *apt-cacher-ng* that you're using? Ok, try this
```

(GLOBIGNORE=lock;cd /var/lib/apt/lists; sudo rm *)
sudo apt-get update

```

---

### Post by abhisheksinghrn02 on 2013-02-15
sudo: unable to resolve host enpaq
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by schragge on 2013-02-15
```

sudo mkdir /var/lib/apt/lists/partial

```

> sudo: unable to resolve host enpaqWas that message coming from *apt-get update*? To troubleshoot it, please post the output of
```

grep enpaq /etc/apt/sources.list{,.d/*}

```

---

### Post by abhisheksinghrn02 on 2013-02-15
grep: /etc/apt/sources.list.d/*: No such file or directory

---

### Post by Silent Warrior on 2013-02-15
Hm... Wasn't the sources.list.d directory taken into use later than 10.04?

Well, see what this altered command does, then:
```
grep enpaq /etc/apt/sources.list
```
(It turns out I don't have enpaq installed, so I can't tell you how it should look.)
But why is APT looking for 'http://hobbes'? That doesn't look a valid package repository... You didn't let a hamster eat a hole through the source list, did you?

I for one don't really have any idea besides that. Have you tried downloading from another package mirror?

---

### Post by schragge on 2013-02-15
I guess the OP uses either [apt-cacher](http://manpages.ubuntu.com/manpages/lucid/en/man1/apt-cacher.1.html), or [apt-cacher-ng](http://manpages.ubuntu.com/manpages/lucid/en/man8/apt-cacher-ng.8.html). I have zero experience with APT caching proxies, and don't know what *apt-get update* should show on such systems.

---

### Post by anbar on 2013-02-15
I've a similar problem, executing
sudo apt-get -o Acquire::CompressionTypes::Order::=gz update

gives
E: The method driver /usr/lib/apt/methods/cdrom could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/http could not be found.
E: The method driver /usr/lib/apt/methods/cdrom could not be found.
E: The method driver /usr/lib/apt/methods/cdrom could not be found.

and I, alas, have no clue what to do

---

### Post by schragge on 2013-02-15
@**anbar**. Pleas start your own thread instead of hijacking this one.

---

### Post by abhisheksinghrn02 on 2013-02-18
hobbes is the update server

---

### Post by abhisheksinghrn02 on 2013-02-18
hobbes is the update server

---

### Post by abhisheksinghrn02 on 2013-02-18
sudo apt-get -o Acquire::CompressionTypes::Order::=gz update


[email]elina@hq.yourdomain.com[/email]:/opt/virtualbox$ sudo apt-get -o Acquire::CompressionTypes::Order::=gz update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [685B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN [710B]
99% [2 Translation-en_IN gzip 0B] [Waiting for headers]
gzip: stdin: not in gzip format
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
66% [3 Translation-en_IN gzip 0B] [Waiting for headers]
gzip: stdin: not in gzip format
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [693B]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN [712B]
59% [5 Translation-en_IN gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN          
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN  
49% [6 Translation-en_IN gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [681B]                                
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [689B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [702B]                  
54% [9 Packages gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                          
  Sub-process gzip returned an error code (1)
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [708B]          
59% [10 Packages gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                     
  Sub-process gzip returned an error code (1)
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [696B]                  
63% [11 Sources gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                           
  Sub-process gzip returned an error code (1)
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [702B]           
66% [12 Sources gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                     
  Sub-process gzip returned an error code (1)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [710B]        
68% [13 Packages gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages                   
  Sub-process gzip returned an error code (1)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [716B]   
71% [14 Packages gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages             
  Sub-process gzip returned an error code (1)
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [704B]          
72% [15 Sources gzip 0B] [Connecting to archive.ubuntu.com (91.189.92.201)]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources                   
  Sub-process gzip returned an error code (1)
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [710B]   
74% [16 Sources gzip 0B] 
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
  Sub-process gzip returned an error code (1)
Fetched 11.2kB in 0s (17.7kB/s)
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

