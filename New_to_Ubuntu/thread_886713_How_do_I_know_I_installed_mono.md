---
title: "How do I know I installed mono?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Beezgetz on 2008-08-11
How do I know I installed mono?

I migrated to linux last week, and I am having hard time installing and finding programs

How can I check if Mono is installed? I tried couple of times, but i am not sure in success..
Shouldn't it be displayed in applications/Programming/Mono? where can I run it from (visualy)?

Kind regards, Beezgetz

---

### Post by unoodles on 2008-08-11
You mean monodevelop? The IDE? Go into synaptic and search for mono and check if it is installed.

---

### Post by Joeb454 on 2008-08-11
Mono is installed by default :)

If you want the [monodevelop]("apt://monodevelop"), as suggested above, search synaptic or click that link ;)

---

### Post by Beezgetz on 2008-08-11
Hello guys,

thank you for REALLY quick reply!

oh, mono is installed by default? great! 

Yes, I also installed Monodevelop. Thanks!

How can I install gtk#, it is giving me trouble. It should also be shown in Aplications/Programming as MonoDevelop is now? 

...and where is Mono shown?

Kind regards, Beezgetz

---

### Post by Nepherte on 2008-08-11
A quick search on my computer lists these packages to be installed on my system (don't think I installed something extra to get mono):
```
bart@Athena:~$ aptitude search mono | grep ^i
i   libmono-addins-gui0.2-cil       - GTK# frontend library for Mono.Addins     
i   libmono-addins0.2-cil           - addin framework for extensible CLI applica
i   libmono-cairo1.0-cil            - Mono Cairo library                        
i A libmono-cairo2.0-cil            - Mono Cairo library                        
i   libmono-corlib1.0-cil           - Mono core library (1.0)                   
i   libmono-corlib2.0-cil           - Mono core library (2.0)                   
i   libmono-data-tds1.0-cil         - Mono Data library                         
i   libmono-data-tds2.0-cil         - Mono Data Library                         
i   libmono-dev                     - libraries for the Mono JIT - Development f
i A libmono-peapi1.0-cil            - Mono PEAPI library                        
i A libmono-peapi2.0-cil            - Mono PEAPI library                        
i A libmono-relaxng1.0-cil          - Mono Relaxng library                      
i   libmono-security1.0-cil         - Mono Security library                     
i   libmono-security2.0-cil         - Mono Security library                     
i   libmono-sharpzip0.84-cil        - Mono SharpZipLib library                  
i   libmono-sharpzip2.84-cil        - Mono SharpZipLib library                  
i   libmono-sqlite2.0-cil           - Mono Sqlite library                       
i   libmono-system-data1.0-cil      - Mono System.Data library                  
i   libmono-system-data2.0-cil      - Mono System.Data Library                  
i A libmono-system-runtime1.0-cil   - Mono System.Runtime library               
i   libmono-system-web1.0-cil       - Mono System.Web library                   
i   libmono-system-web2.0-cil       - Mono System.Web Library                   
i   libmono-system1.0-cil           - Mono System libraries (1.0)               
i   libmono-system2.0-cil           - Mono System libraries (2.0)               
i A libmono-zeroconf1.0-cil         - CLI library for multicast DNS service disc
i   libmono0                        - libraries for the Mono JIT                
i   libmono1.0-cil                  - Mono libraries (1.0)                      
i   libmono2.0-cil                  - Mono libraries (2.0)                      
i   mono-1.0-devel                  - Mono development tools for CLI 1.0        
i   mono-2.0-devel                  - Mono development tools for CLI 2.0        
i   mono-common                     - common files for Mono                     
i   mono-gac                        - Mono GAC tool                             
i   mono-jit                        - fast CLI JIT/AOT compiler for Mono        
i   mono-runtime                    - Mono runtime 
```
You could search for packages in Synaptics if Remove/install software does't give you anything.

---

### Post by Beezgetz on 2008-08-11
Hey,

Ok, I have those files, thank you very much!

How about gtk#, I get nothing - does that mean it is not installed? How can I install gtk#?

Kind regards, Beezgetz

---

