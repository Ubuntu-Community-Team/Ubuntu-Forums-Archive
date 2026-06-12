---
title: "Cannot install Node.js on Ubuntu 18.14 in a Docker container."
date: 2018-11-12
forum: New to Ubuntu
---

### Post by dmitriano on 2018-11-12
If I start Ubuntu 18.04 in a Docker container (see the [docker file]("https://github.com/dmitriano/DockerLemp/blob/master/u1804/Dockerfile")) and then try to install nodejs and npm I get this:

```
root@ecfd8901d25f:/# apt-get install nodejs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 nodejs : Depends: libc-ares2 (>= 1.11.0~rc1) but it is not installable
          Depends: libhttp-parser2.7.1 (>= 2.7.1) but it is not installable
          Recommends: nodejs-doc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
root@ecfd8901d25f:/# apt install npm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 npm : Depends: nodejs but it is not going to be installed
       Depends: node-abbrev (>= 1.0.4) but it is not going to be installed
       Depends: node-ansi (>= 0.3.0-2) but it is not going to be installed
       Depends: node-ansi-color-table but it is not going to be installed
       Depends: node-archy but it is not going to be installed
       Depends: node-block-stream but it is not going to be installed
       Depends: node-fstream (>= 0.1.22) but it is not going to be installed
       Depends: node-fstream-ignore but it is not going to be installed
       Depends: node-github-url-from-git but it is not going to be installed
       Depends: node-glob (>= 3.1.21) but it is not going to be installed
       Depends: node-graceful-fs (>= 2.0.0) but it is not going to be installed
       Depends: node-inherits but it is not going to be installed
       Depends: node-ini (>= 1.1.0) but it is not going to be installed
       Depends: node-lockfile but it is not going to be installed
       Depends: node-lru-cache (>= 2.3.0) but it is not going to be installed
       Depends: node-minimatch (>= 0.2.11) but it is not going to be installed
       Depends: node-mkdirp (>= 0.3.3) but it is not going to be installed
       Depends: node-gyp (>= 0.10.9) but it is not going to be installed
       Depends: node-nopt (>= 3.0.1) but it is not going to be installed
       Depends: node-npmlog but it is not going to be installed
       Depends: node-once but it is not going to be installed
       Depends: node-osenv but it is not going to be installed
       Depends: node-read but it is not going to be installed
       Depends: node-read-package-json (>= 1.1.0) but it is not going to be installed
       Depends: node-request (>= 2.25.0) but it is not going to be installed
       Depends: node-retry but it is not going to be installed
       Depends: node-rimraf (>= 2.2.2) but it is not going to be installed
       Depends: node-semver (>= 2.1.0) but it is not going to be installed
       Depends: node-sha but it is not going to be installed
       Depends: node-slide but it is not going to be installed
       Depends: node-tar (>= 0.1.18) but it is not going to be installed
       Depends: node-underscore but it is not going to be installed
       Depends: node-which but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

what is it?

On a regular Ubuntu 18.04 installation Node.js installs successfully with these commands.

---

