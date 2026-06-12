---
title: "Getting a bunch of npm errors when I attempt to compile the atom editor"
date: 2014-05-20
forum: Packaging and Compiling Programs
---

### Post by sethj3 on 2014-05-20
I am attempting to compile the [Atom editor]("https://github.com/atom/atom/blob/master/README.md#building") from source. 

I installed nodejs, npm and libgnome-keyring-dev as specified in the installation instructions.  

I then told npm to use python 2 as instructed:  

```
npm config set python /usr/bin/python2 -g
``` 

and ran the build script: ```
sudo script/build
```. The build fails with these errors:  

```
Usage: gyp_main.py [options ...] [build_file ...]

gyp_main.py: error: no such option: --no-parallel
gyp ERR! configure error 
gyp ERR! stack Error: `gyp` failed with exit code: 2
gyp ERR! stack     at ChildProcess.onCpExit (/home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/node-gyp/lib/configure.js:340:16)
gyp ERR! stack     at ChildProcess.EventEmitter.emit (events.js:98:17)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (child_process.js:797:12)
gyp ERR! System Linux 3.13.0-24-generic
gyp ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/runas
gyp ERR! node -v v0.10.25
gyp ERR! node-gyp -v v0.13.0
gyp ERR! not ok 








Usage: gyp_main.py [options ...] [build_file ...]

gyp_main.py: error: no such option: --no-parallel
gyp ERR! configure error 
gyp ERR! stack Error: `gyp` failed with exit code: 2
gyp ERR! stack     at ChildProcess.onCpExit (/home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/node-gyp/lib/configure.js:340:16)
gyp ERR! stack     at ChildProcess.EventEmitter.emit (events.js:98:17)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (child_process.js:797:12)
gyp ERR! System Linux 3.13.0-24-generic
gyp ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js" "rebuild"
gyp ERR! cwd /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/keytar
gyp ERR! node -v v0.10.25
gyp ERR! node-gyp -v v0.13.0
gyp ERR! not ok 
npm ERR! EEXIST, mkdir '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/npm/doc/cli'
File exists: /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/npm/doc/cli
Move it away, and try again. 
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/npm/doc/cli
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/npm/doc/cli/npm-whoami.md
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code EEXIST
npm ERR! errno 47
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:171:23
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/mkdirp/index.js:37:53
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/fstream/lib/dir-writer.js'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/fstream/lib/dir-writer.js
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/fstream/lib/dir-writer.js
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/block-stream/test/pause-resume.js'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/block-stream/test/pause-resume.js
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/tar/node_modules/block-stream/test/pause-resume.js
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/season/node_modules/coffee-script/lib/coffee-script/scope.js'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/season/node_modules/coffee-script/lib/coffee-script/scope.js
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/season/node_modules/coffee-script/lib/coffee-script/scope.js
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/git-utils/deps/libgit2/deps/regex/regex_internal.h'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/git-utils/deps/libgit2/deps/regex/regex_internal.h
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/git-utils/deps/libgit2/deps/regex/regex_internal.h
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! runas@0.3.0 install: `node-gyp rebuild`
npm ERR! Exit status 1
npm ERR! 
npm ERR! Failed at the runas@0.3.0 install script.
npm ERR! This is most likely a problem with the runas package,
npm ERR! not with npm itself.
npm ERR! Tell the author that this fails on your system:
npm ERR!     node-gyp rebuild
npm ERR! You can get their info via:
npm ERR!     npm owner ls runas
npm ERR! There is likely additional logging output above.
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! code ELIFECYCLE
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/node-gyp/gyp/pylib/gyp/MSVSSettings_test.py'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/node-gyp/gyp/pylib/gyp/MSVSSettings_test.py
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/node-gyp/gyp/pylib/gyp/MSVSSettings_test.py
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/first-mate/benchmark/bootstrap.min.css'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>
npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/first-mate/benchmark/bootstrap.min.css
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/first-mate/benchmark/bootstrap.min.css
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! Error: ENOENT, lstat '/home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/plist/tests/iTunes-BIG.xml'
npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>

npm ERR! System Linux 3.13.0-24-generic
npm ERR! command "node" "/home/seth/Downloads/atom-0.96.0/build/node_modules/.bin/npm" "--userconfig=/home/seth/Downloads/atom-0.96.0/.npmrc" "install" "--quiet"
npm ERR! cwd /home/seth/Downloads/atom-0.96.0/apm
npm ERR! node -v v0.10.25
npm ERR! npm -v 1.4.10
npm ERR! path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/plist/tests/iTunes-BIG.xml
npm ERR! fstream_path /home/seth/Downloads/atom-0.96.0/apm/node_modules/atom-package-manager/node_modules/plist/tests/iTunes-BIG.xml
npm ERR! fstream_type File
npm ERR! fstream_class FileWriter
npm ERR! code ENOENT
npm ERR! errno 34
npm ERR! fstream_stack /home/seth/Downloads/atom-0.96.0/build/node_modules/npm/node_modules/fstream/lib/writer.js:284:26
npm ERR! fstream_stack Object.oncomplete (fs.js:107:15)
npm ERR! 
npm ERR! Additional logging details can be found in:
npm ERR!     /home/seth/Downloads/atom-0.96.0/apm/npm-debug.log
npm ERR! not ok code 0

```

I looked through the errors but I'm not familiar with npm and can't make much sense of it.

Is this a bug or did I do something wrong? I have attached the build instructions.

---

### Post by sethj3 on 2014-05-22
Upon looking the error over again, I noticed this:  

```

npm ERR! If you need help, you may report this *entire* log,
npm ERR! including the npm and node versions, at:
npm ERR!     <http://github.com/npm/npm/issues>


``` 

Maybe I'll try that, since if anyone knows, the developers ought ;)

---

### Post by sethj3 on 2014-05-22
Someone pointed out that I should have run npm config as root, I did this but am still getting the same errors when I attempt a build. I have pasted the full log file [here]("http://paste.ubuntu.com/7503148/") (I forgot to when I started this thread).

I haven't opened a GitHub issue yet, going to do that now.

---

### Post by sethj3 on 2014-05-23
Well it turns out I just needed a newer version of nodejs than what comes on Trusty be default (0.10.25). I installed nodejs 0.10.28 from Chris Lea's PPA [https://launchpad.net/~chris-lea/+archive/node.js/](https://launchpad.net/~chris-lea/+archive/node.js/) and then rebuilt atom. Everything worked fine.  

I removed the PPA after the build because it caused some dependency errors with other node related packages (not exactly surprising). I haven't seen any bad effects with atom yet so I'm assuming nodejs was only needed for the build. (just confirmed in a VM)

---

### Post by sethj3 on 2014-07-15
Well I started getting node errors as soon as a tried to install any atom plugins. Re-added the PPA and everything worked (for the most part). Still some occasional errors, but those don't come from node/npm as far as I can tell. Guess this is solved.

---

