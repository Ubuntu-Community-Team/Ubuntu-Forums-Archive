---
title: "Using NPM Install"
date: 2017-11-29
forum: New to Ubuntu
---

### Post by marc50 on 2017-11-29
I am fairly new to Ubuntu, and know a little java, but Linux is blowing my mind. I am trying to install this app from github, "https://github.com/colinodell/tunegenie-spotify", and required npm install. Although, how do I install it? 

I was using, "npm install https://github.com/colinodell/tunegenie-spotify" it would do some things, and show a yellow WARN to the left of each command. It would also throw a package.json not in directory error.

Any help?

---

### Post by slickymaster on 2017-11-29
Hello marc50, welcome to the forums.

Try installing it like this, since NodeJs installs node and npm:```
sudo apt update
sudo apt install nodejs  # need it first!
sudo apt install npm
```

---

### Post by marc50 on 2017-11-29
I have tried those commands, and I receive an error saying that "npm is known not to run on Node.js v4.2.6". It continues to inform me that there is a bug that can break npm, and asks me to update to at least 4.7.0 to use this version of npm. Then it gives me the links.

I've also tried to pull the version number, although it gives me the same message.

---

### Post by slickymaster on 2017-11-29
Try this solution over here: [https://stackoverflow.com/questions/46360567/error-npm-is-known-not-to-run-on-node-js-v4-2-6](https://stackoverflow.com/questions/46360567/error-npm-is-known-not-to-run-on-node-js-v4-2-6)

---

