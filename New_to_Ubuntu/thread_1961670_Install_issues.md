---
title: "Install issues"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by xworld on 2012-04-19
I am trying to install ccsm and I get this error ```
sudo apt-get install compizconfig-settings-manager compiz-plugins-extra
[sudo] password for x0110: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Also when I try to uninstall software center I get a message like this ```
 intellectual property laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.                                                                
 &#9474;                                                                                                                                                     
 &#9474; 1. GRANT OF LICENSE. This EULA grants you the following rights:                                                                                     
 &#9474;                                                                                                                                                     
 &#9474;                                                                                                                                                     
 &#9474; 4. U.S. GOVERNMENT RESTRICTED RIGHTS. The SOFTWARE PRODUCT and documentation are provided with RESTRICTED RIGHTS. Use, duplication, or              
 &#9474; disclosure by the Government is subject to restrictions as set forth in subparagraph (c)(1)(ii) of the Rights in Technical Data and Computer        
 &#9474; Software clause at DFARS 252.227-7013 or subparagraphs (c) (1) and (2) of the Commercial Computer Software - Restricted Rights at 48 CFR            
 &#9474; 52.227-19, as applicable. Manufacturer is Microsoft Corporation/One Microsoft Way/Redmond, WA 98052-6399.                                           
 &#9474;                                                                                                                                                     
 &#9474; LIMITED WARRANTY                                                                                                                                    
 &#9474;                                                                                                                                                     
 &#9474; NO WARRANTIES. Microsoft expressly disclaims any warranty for the SOFTWARE PRODUCT. The SOFTWARE PRODUCT and any related documentation is           
 &#9474; provided "as is" without warranty of any kind, either express or implied, including, without limitation, the implied warranties or                  
 &#9474; merchantability, fitness for a particular purpose, or noninfringement. The entire risk arising out of use or performance of the SOFTWARE            
 &#9474; PRODUCT remains with you.                                                                                                                           
 &#9474;                                                                                                                                                     
 &#9474; NO LIABILITY FOR CONSEQUENTIAL DAMAGES. In no event shall Microsoft or its suppliers be liable for any damages whatsoever (including, without       
 &#9474; limitation, damages for loss of business profits, business interruption, loss of business information, or any other pecuniary loss) arising out     
 &#9474; of the use of or inability to use this Microsoft product, even if Microsoft has been advised of the possibility of such damages. Because some       
 &#9474; states/jurisdictions do not allow the exclusion or limitation of liability for consequential or incidental damages, the above limitation may        
 &#9474; not apply to you.                                                                                                                                   
 &#9474;                                                                                                                                                     
 &#9474; MISCELLANEOUS                                                                                                                                       
 &#9474;                                                                                                                                                     
 &#9474; If you acquired this product in the United States, this EULA is governed by the laws of the State of Washington.                                    
 &#9474;                                                                                                                                                     
 &#9474; If this product was acquired outside the United States, then local laws may apply.                                                                  
 &#9474;                                                                                                                                                     
 &#9474; Should you have any questions concerning this EULA, or if you desire to contact Microsoft for any reason, please contact the Microsoft              
 &#9474; subsidiary serving your country, or write: Microsoft Sales Information Center/One Microsoft Way/Redmond, WA 98052-6399.                             


```

in a different color than the terminal and then nothing happens

What is going on?

---

### Post by NikTh on 2012-04-19
> **xworld said:**
> ```
you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Did you try the suggestion ? 
```
sudo dpkg --configure -a
```

---

### Post by audiomick on 2012-04-19
> **xworld said:**
> ...Also when I try to uninstall software center...

Do you really mean "uninstall" there, or do you perhaps mean "close"?

If you mean "uninstall", I would suggest that you don't. I suspect that the software center is quite tightly bound up with some other things in the OS. If you don't want to use it, the just don't use it. I wouldn't try to uninstall it.

Be that as it may, the message that you quote as coming up after trying to "uninstall" the software center is a licensing agreement that comes up when a particular package is installed. If you look closely at the text, you will see that microsoft comes up as the licenser. I believe the package is one that includes microsoft fonts. Anyway, you need to either agree with the licensing agreement or not, in which case the package in question will not be installed. This wont kill you. It may mean that some fonts don't show up properly or something like that. I know that this agreement turns up at times, but I haven't seen it myself, so I don't know exactly which package it is associated with.

So, to get back to the error that you mentioned first:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

dpkg is associated with the installation process. I rather suspect that the interuption was cause by dpkg having been in the process of installing the package associated with that microsoft licensing agreement, and that it was interrupted by having to wait for you to agree or not agree to that.

Anyway, the solution to that is in the error message. In a terminal, run
```
sudo dpkg --configure -a
```
then try to install CSSM again.

---

