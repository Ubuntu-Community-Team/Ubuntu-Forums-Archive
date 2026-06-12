---
title: "How do you make 'electron app' Cerebro work?"
date: 2020-09-04
forum: New to Ubuntu
---

### Post by nginmu on 2020-09-04
NB I retitled this post after numerous edits to reflect the change in content. I figured out my initial problem (pango libraries incompatible) on my own but then started running into difficulty with how to get an 'Electron app' working. 


OS:
Lubuntu 20.04 (amd64)

Software version tried:
cerebro_0.2.6_amd64.deb from [https://github.com/KELiON/cerebro/releases/download/0.2.6/cerebro_0.2.6_amd64.deb](https://github.com/KELiON/cerebro/releases/download/0.2.6/cerebro_0.2.6_amd64.deb)
cerebro_0.3.0_amd64.deb from [https://github.com/KELiON/cerebro/releases/download/v0.3.0/cerebro_0.3.0_amd64.deb](https://github.com/KELiON/cerebro/releases/download/v0.3.0/cerebro_0.3.0_amd64.deb)

Cerebro installs ok to /opt/Cerebro but will not launch from the Lubuntu main GUI menu. In terminal, it raises the error 'Pango-ERROR' 'Harfbuzz version too old'


Trying to follow the instructions here, which seem to describe the problem exactly:

[https://unix.stackexchange.com/questions/589993/pango-error-harfbuzz-version-too-old](https://unix.stackexchange.com/questions/589993/pango-error-harfbuzz-version-too-old)

I've looked into the dependencies of in my case, cerebro, as instructed & my results are matching exactly the same as what he posted.

I figured rather than downgrade the dependency I would do as he does in his first solution and try to place older versions of the required libraries in with the cerebro executable, just for it's exclusive use?

Trouble is, when I try the follow his links they don't seem to work & give an error, at which point I'm stuck:

libpango-1.0-0 (1.42.4-7):
[https://packages.ubuntu.com/eoan/libs/libpango-1.0-0](https://packages.ubuntu.com/eoan/libs/libpango-1.0-0)

libpangocairo-1.0-0 (1.42.4-7):
[https://packages.ubuntu.com/eoan/libpangocairo-1.0-0](https://packages.ubuntu.com/eoan/libpangocairo-1.0-0)

libpangoft2-1.0-0 (1.42.4-7):
[https://packages.ubuntu.com/eoan/libpangoft2-1.0-0](https://packages.ubuntu.com/eoan/libpangoft2-1.0-0)

How can I obtain the required files?

EDIT//

I just tried replacing 'eoan' with 'focal' in the above URLs and that seems to be giving more sensible results.. if anyone can confirm this is right I'll mark thread solved.

EDIT 2//

obtained, extracted into ~/Desktop/New foldere/, copied the files into Cerebro's root directory:

```

me@me-pc:~/Desktop/New foldere/usr/lib/x86_64-linux-gnu$ sudo cp * /opt/Cerebro/
[sudo] password for me: 
me@me-pc:~/Desktop/New foldere/usr/lib/x86_64-linux-gnu$ cd /opt/Cerebro
me@me-pc:/opt/Cerebro$ ls
blink_image_resources_200_percent.pak  libnode.so                     libpangoft2-1.0.so.0.4400.7  resources
cerebro                                libpango-1.0.so.0              LICENSE.electron.txt         snapshot_blob.bin
content_resources_200_percent.pak      libpango-1.0.so.0.4400.7       LICENSES.chromium.html       ui_resources_200_percent.pak
content_shell.pak                      libpangocairo-1.0.so.0         locales                      views_resources_200_percent.pak
icudtl.dat                             libpangocairo-1.0.so.0.4400.7  natives_blob.bin
libffmpeg.so                           libpangoft2-1.0.so.0           pdf_viewer_resources.pak


```

No joy. All the libraries are showing a higher version number than he was referring to in his example. His were 1.42.4-7; these I obtained were 1.44.7-2

Any help still appreciated. Perhaps instead of 'focal' I'll try using 'bionic-updates' or 'bionic' in the URLs...

... yes that gave me a full set of 1.40.14-1 pango files.

```

me@me-pc:/opt/Cerebro$ sudo rm libpango*
[sudo] password for me: 
me@me-pc:/opt/Cerebro$ ls
blink_image_resources_200_percent.pak  icudtl.dat            LICENSES.chromium.html    resources
cerebro                                libffmpeg.so          locales                   snapshot_blob.bin
content_resources_200_percent.pak      libnode.so            natives_blob.bin          ui_resources_200_percent.pak
content_shell.pak                      LICENSE.electron.txt  pdf_viewer_resources.pak  views_resources_200_percent.pak
me@me-pc:/opt/Cerebro$ sudo cp ~/Desktop/1.40.14-1/* /opt/Cerebro
me@me-pc:/opt/Cerebro$ ls
blink_image_resources_200_percent.pak  libnode.so                      libpangoft2-1.0.so.0.4000.14  resources
cerebro                                libpango-1.0.so.0               LICENSE.electron.txt          snapshot_blob.bin
content_resources_200_percent.pak      libpango-1.0.so.0.4000.14       LICENSES.chromium.html        ui_resources_200_percent.pak
content_shell.pak                      libpangocairo-1.0.so.0          locales                       views_resources_200_percent.pak
icudtl.dat                             libpangocairo-1.0.so.0.4000.14  natives_blob.bin
libffmpeg.so                           libpangoft2-1.0.so.0            pdf_viewer_resources.pak
me@me-pc:/opt/Cerebro$ 


```

I try to start Cerebro now;

```

me@me-pc:~$ cerebro
/opt/Cerebro/resources/electron.asar/common/reset-search-paths.js:0



Error: Cannot find module '../dialog'
    at Module._resolveFilename (module.js:470:15)
    at Function.Module._resolveFilename (/opt/Cerebro/resources/electron.asar/common/reset-search-paths.js:35:12)
    at Function.Module._load (module.js:418:25)
    at Module.require (module.js:498:17)
    at require (internal/module.js:20:19)
    at Object.get [as dialog] (/opt/Cerebro/resources/electron.asar/browser/api/exports/electron.js:11:16)
    at process.<anonymous> (/opt/Cerebro/resources/electron.asar/browser/init.js:54:31)
    at emitOne (events.js:96:13)
    at process.emit (events.js:188:7)
    at process._fatalException (bootstrap_node.js:300:26)
me@me-pc:~$ 


```

I guess I cured the first problem only to run into another :-(

Only thing I can figure here is /opt/Cerebro/resources/electron.asar/ is a discrete file at the end of the path on my install, not a directory

I wondered if maybe I should have explicitly installed 'electron'.. but that didn't seem to go to well..

[https://www.electronjs.org/docs/tutorial/installation](https://www.electronjs.org/docs/tutorial/installation)

```

me@me-pc:~$ sudo npm install electron

> core-js@3.6.5 postinstall /home/me/node_modules/core-js                                                                                                                   
> node -e "try{require('./postinstall')}catch(e){}"                                                                                                                         
                                                                                                                                                                            
Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!                                                            
                                                                                                                                                                            
The project needs your help! Please consider supporting of core-js on Open Collective or Patreon:                                                                           
> https://opencollective.com/core-js                                                                                                                                        
> https://www.patreon.com/zloirock                                                                                                                                          
                                                                                                                                                                            
Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)                                                                                    
                                                                                                                                                                            
                                                                                                                                                                            
> electron@10.1.1 postinstall /home/me/node_modules/electron                                                                                                                
> node install.js                                                                                                                                                           
                                                                                                                                                                            
Downloading electron-v10.1.1-linux-x64.zip: [====================================================================================================] 100% ETA: 0.0 seconds 
Error: EACCES: permission denied, stat '/root/.cache/electron/httpsgithub.comelectronelectronreleasesdownloadv10.1.1SHASUMS256.txt/SHASUMS256.txt'
npm WARN enoent ENOENT: no such file or directory, open '/home/me/package.json'
npm WARN me No description
npm WARN me No repository field.
npm WARN me No README data
npm WARN me No license field.

npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! electron@10.1.1 postinstall: `node install.js`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the electron@10.1.1 postinstall script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     /root/.npm/_logs/2020-09-04T13_26_07_545Z-debug.log
me@me-pc:~$ 


```

The line 

```

 '/root/.cache/electron/httpsgithub.comelectronelectronreleasesdownloadv10.1.1SHASUMS256.txt/SHASUMS256.txt'

```

looks a bit suspicious? I can't seem to gain access to  /root/.npm/ to have a look at the log it's referring to despite trying 'sudo cd root'..

I'm pretty lost now.

---

### Post by wildmanne39 on 2020-09-07
Bump.

---

### Post by Holger_Gehrke on 2020-09-07
Have you taken a look at the issues on [https://github.com/KELiON/cerebro/](https://github.com/KELiON/cerebro/) ? Multiple people have the exact same problem, and not only on Ubuntu. The Project seems dead - or at the very least stalled. The last commit was almost 3 years ago.

One comment in the issues mentions a fork ([https://github.com/oguhpereira/cerebro/tree/499-electron-version-update](https://github.com/oguhpereira/cerebro/tree/499-electron-version-update)) which solved the problem by updating electron so that it works with current harfbuzz instead of looking for an old version, but you'd have to know your way around node.js and electron and the used build system (yarn ?) to use that.

Holger

---

### Post by nginmu on 2020-09-08
Thanks - no I hadn't looked below the surface there.

My main aim is to find a good, trouble-free, system-wide file search tool, Cerebro looked like what I was searching for, but now getting it working seems more involved than I'd hoped 

Maybe there is a better approach to file searching I should look into & I should change course.

---

### Post by tea for one on 2020-09-08
> **nginmu said:**
> Maybe there is a better approach to file searching I should look into & I should change course.

Catfish is worth a look.

```
sudo apt install catfish
```

---

### Post by nginmu on 2020-09-08
Trying it out now. Good first impressions. Thanks!

---

