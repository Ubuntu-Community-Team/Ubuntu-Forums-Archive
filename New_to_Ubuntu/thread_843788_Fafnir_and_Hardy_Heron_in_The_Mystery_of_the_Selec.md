---
title: "Fafnir and Hardy Heron in: The Mystery of the Selective Apt-Get"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Fafnir on 2008-06-28
OK, I'm more or less flummoxed here. My essential problem is that apt-get - and, by extension, Synaptic - can't seem to get access to a few key repositories. Here's the output of a sudo apt-get update, for example:

```
Ign http://packages.medibuntu.org hardy Release.gpg                                                                                                  
Ign http://security.ubuntu.com hardy-security Release.gpg           
Ign http://gb.archive.ubuntu.com hardy Release.gpg                                                                        
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                                                                                       
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy/main Translation-en_GB                                                              
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB                                                                                    
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB       
Ign http://packages.medibuntu.org hardy Release                                                                                                       
Ign http://gb.archive.ubuntu.com hardy/universe Translation-en_GB    
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB  
Ign http://packages.medibuntu.org hardy/free Packages                                                                                                 
Ign http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB  
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Ign http://packages.medibuntu.org hardy/non-free Packages                                                                                             
Ign http://gb.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://security.ubuntu.com hardy-security Release                     
Err http://packages.medibuntu.org hardy/free Packages                                           
  403 Forbidden
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB                           
Ign http://security.ubuntu.com hardy-security/main Packages                                                                
Err http://packages.medibuntu.org hardy/non-free Packages                                       
  403 Forbidden
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB                     
Ign http://security.ubuntu.com hardy-security/restricted Packages         
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB 
Ign http://security.ubuntu.com hardy-security/main Sources                
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Sources          
Ign http://gb.archive.ubuntu.com hardy Release                            
Ign http://security.ubuntu.com hardy-security/universe Packages                                      
Ign http://gb.archive.ubuntu.com hardy-updates Release                                               
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://gb.archive.ubuntu.com hardy/main Packages
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://gb.archive.ubuntu.com hardy/restricted Packages                
Ign http://security.ubuntu.com hardy-security/multiverse Sources          
Ign http://gb.archive.ubuntu.com hardy/main Sources 
Err http://security.ubuntu.com hardy-security/main Packages
  403 Forbidden
Ign http://gb.archive.ubuntu.com hardy/restricted Sources
Ign http://gb.archive.ubuntu.com hardy/universe Packages
Ign http://gb.archive.ubuntu.com hardy/universe Sources
Ign http://gb.archive.ubuntu.com hardy/multiverse Packages
Ign http://gb.archive.ubuntu.com hardy/multiverse Sources
Ign http://gb.archive.ubuntu.com hardy-updates/main Packages
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://gb.archive.ubuntu.com hardy-updates/main Sources
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://gb.archive.ubuntu.com hardy-updates/universe Packages
Ign http://gb.archive.ubuntu.com hardy-updates/universe Sources
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://gb.archive.ubuntu.com hardy/main Packages                      
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/restricted Packages                                           
  403 Forbidden
Err http://security.ubuntu.com hardy-security/restricted Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/main Sources                                                  
  403 Forbidden
Err http://security.ubuntu.com hardy-security/main Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/restricted Sources
  403 Forbidden
Err http://security.ubuntu.com hardy-security/restricted Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/universe Packages
  403 Forbidden
Err http://security.ubuntu.com hardy-security/universe Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/universe Sources
  403 Forbidden
Err http://security.ubuntu.com hardy-security/universe Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/multiverse Packages
  403 Forbidden
Err http://security.ubuntu.com hardy-security/multiverse Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy/multiverse Sources
  403 Forbidden
Err http://security.ubuntu.com hardy-security/multiverse Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/main Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/restricted Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/main Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/restricted Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/universe Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/universe Sources
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
  403 Forbidden
Err http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
  403 Forbidden

[snip looong list of the individual files that couldn't be retrieved]

```

Attempting to install anything is likewise a long list of 403 Forbidden errors. The inaccessible files remain inaccessible between attempts - it's not a random thing. I have a completely healthy Internet connection as far as I can tell, and I seem to have access to the files apt-get complains about from within Firefox so it probably isn't a server-side problem.

My one possible lead on what's going on here is something that as far as I can tell shouldn't be happening. Going by the "progress bar" at the bottom of the xterm, apt-get seems to be connecting through wwwcache.cam.ac.uk, my university proxy. Since I'm at home now, though,  I've set things up to connect to the Internet directly. I've changed the settings back in System->Preferences->Network Proxy and in the Synaptic GUI, and I've commented out the export http_proxy line I added to .bashrc (and an export verifies that http_proxy is indeed unset), so I don't see where apt-get could be getting this from. Could this be related?

This started as soon as I got home, so it's almost certainly caused /somehow/ by the change in network environments. I don't see why it would have such a selective effect though. I have a static IP for both networks as well, so it's not as though there's even a major structural difference... :confused:

So that's the mystery. Any ideas as to what can be causing it, or am I going to be downloading packages with Firefox until next term? Thanks in advance!

---

### Post by Efros on 2008-06-28
Have you tried changing your server on the first tab of the sofware sources applet. I used to use the virgin one in the UK because it seemed to respond faster than the one in the US.

---

### Post by adamogardner on 2008-06-28
this is the funniest thread title I ever read.  there should be a prize.

---

### Post by Fafnir on 2008-07-01
Sorry for the late reply here - changing the repositories doesn't help at all. After a little more research, I *think* I know what the problem is. Here's what I've found:

1. The "Ign" lines in the output of sudo apt-get update actually stand for "Ignore" - apt-get knows the files haven't changed, so it's not even trying to re-download them. That means apt-get is failing for all files in all repositories, rather than just a few select files. That makes things a lot less mysterious.

2. I was suffering from the hostname bug ([link](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)), which greatly reduces responsiveness in some applications. That resulted in each attempt to get a file (i.e. each line of the apt-get output) taking five seconds or so, in a manner consistent with dropped packets or something similar. Applying the workaround for that bug reduced the failure time for each file to something on the order of a tenth of a second, which narrows down the possible causes considerably.

3. Other console commands, like ping, have no trouble accessing the Internet - this seems to be unique to apt-get.

4. I've confirmed that I can't use wwwcache.cam.ac.uk as a proxy from outside the university. Further, attempting to use it results in instant failures (which is why I originally didn't think it would be related).

It therefore seems highly likely that the cause of the problem is apt-get trying to use my university proxy. The question now becomes: how? As far as I know, I've purged all mention of it from my configuration - it's not set in System->Preferences->Network Proxy, it's not set in the Synaptic GUI, and http_proxy isn't declared...

Oh, **that's a bug!** :mad: :wherestheswearingsmileywhenyouneedit:

Yeah. Just as I finished writing this post, on a whim I tried hitting "Apply" in the Synaptic Preferences->Network dialog. The one that was set to "Direct Internet Connection" when I opened it. The one I hadn't changed at all since opening it. And now everything works.

A responsiveness bug affecting the symptoms of a misconfigured proxy that appeared to be correctly configured due to a Synaptic bug - not to mention apt-get giving me 403 Forbidden errors but not indicating they were from the proxy rather than the repository. I'll dine out on this one... Ah well - all's well that ends well, right? :)

---

