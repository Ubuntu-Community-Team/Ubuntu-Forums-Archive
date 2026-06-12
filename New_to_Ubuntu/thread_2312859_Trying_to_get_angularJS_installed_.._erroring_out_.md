---
title: "Trying to get angularJS installed .. erroring out installing YO"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by JoGotta on 2016-02-07
Everything I have read indicates that I really need to get yeoman installed in order to set up all of the nodes correctly for AngularJS.  I can complete all of the other steps but when I try to run the yo install command I get the following error

~/workspace/web$ sudo n stable
sudo: n: command not found
jogotta@jogotta-70A4000HUX:~/workspace/web$ sudo npm install -g yo
npm WARN engine yo@1.6.0: wanted: {"node":">=0.12.0"} (current: {"node":"0.10.37","npm":"1.4.28"})
npm WARN deprecated npmconf@2.1.2: this package has been reintegrated into npm and is now out of date with respect to npm
npm WARN engine deep-extend@0.4.1: wanted: {"node":">=0.12.0","iojs":">=1.0.0"} (current: {"node":"0.10.37","npm":"1.4.28"})
npm WARN engine deep-extend@0.4.1: wanted: {"node":">=0.12.0","iojs":">=1.0.0"} (current: {"node":"0.10.37","npm":"1.4.28"})
npm WARN engine cryptiles@2.0.5: wanted: {"node":">=0.10.40"} (current: {"node":"0.10.37","npm":"1.4.28"})
npm WARN engine hoek@2.16.3: wanted: {"node":">=0.10.40"} (current: {"node":"0.10.37","npm":"1.4.28"})
npm WARN engine boom@2.10.1: wanted: {"node":">=0.10.40"} (current: {"node":"0.10.37","npm":"1.4.28"})
/home/jogotta/.node/bin/yo -> /home/jogotta/.node/lib/node_modules/yo/lib/cli.js


> yo@1.6.0 postinstall /home/jogotta/.node/lib/node_modules/yo
> yodoctor


sh: 1: yodoctor: Permission denied


npm ERR! yo@1.6.0 postinstall: `yodoctor`
npm ERR! Exit status 127
npm ERR! 
npm ERR! Failed at the yo@1.6.0 postinstall script.
npm ERR! This is most likely a problem with the yo package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     yodoctor
npm ERR! You can get their info via:
npm ERR!     npm owner ls yo
npm ERR! There is likely additional logging output above.
npm ERR! System Linux 3.19.0-49-generic
npm ERR! command "/usr/bin/node" "/usr/bin/npm" "install" "-g" "yo"
npm ERR! cwd /home/jogotta/workspace/web
npm ERR! node -v v0.10.37
npm ERR! npm -v 1.4.28
npm ERR! code ELIFECYCLE
npm ERR! not ok code 0

---

### Post by sandyd on 2016-02-08
When I first installed node, I had issues with versioning affecting the entire system.

Over time i've found that installing node in your own home directory is much cleaner.

Add something like
```

export PATH="/home/*username*/.node/bin:$PATH"
export N_PREFIX=$HOME/.node
```

to .profile and install node into /home/*username*/.node

Then, to get the changes immediately, run
```

source /home/*username*/.profile

```
Now the node installation will not have any version or permissions conflicts, and you can create multiple users to house various node installations.

---

