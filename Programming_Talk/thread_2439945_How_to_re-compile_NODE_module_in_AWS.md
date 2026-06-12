---
title: "How to re-compile NODE module in AWS?"
date: 2020-04-03
forum: Programming Talk
---

### Post by susja on 2020-04-03
Hello. 
I am trying to build a skill for Alexa using 'Google Assistant' following some tutorial/instructions on AWS.
I was able to build a Skill but I can't initiate it and in AWS I see the following error:
```
——
a different Node.js version using\nNODE_MODULE_VERSION 48. This version of Node.js requires\nNODE_MODULE_VERSION 72. Please try re-compiling or re-installing\nthe module (for instance, using npm rebuild or npm install).","stack":}
2020-04-01T18:56:23.306Z undefined INFO Uncaught exception: Error: The module '/var/task/lib/node_modules/lame/build/Release/bindings.node'
was compiled against a different Node.js version using
NODE_MODULE_VERSION 48. This version of Node.js requires
NODE_MODULE_VERSION 72. Please try re-compiling or re-installing
the module (for instance, using npm rebuild or npm install).
Error: The module '/var/task/lib/node_modules/lame/build/Release/bindings.node'
was compiled against a different Node.js version using
NODE_MODULE_VERSION 48. This version of Node.js requires
NODE_MODULE_VERSION 72. Please try re-compiling or re-installing
the module (for instance, using npm rebuild or npm install).
at Object.Module._extensions..node (internal/modules/cjs/loader.js:1208:18)
at Module.load (internal/modules/cjs/loader.js:1002:32)
at Function.Module._load (internal/modules/cjs/loader.js:901:14)
at Module.require (internal/modules/cjs/loader.js:1044:19)
at require (internal/modules/cjs/helpers.js:77:18)
at bindings (/var/task/lib/node_modules/lame/node_modules/bindings/bindings.js:76:44)
at Object. (/var/task/lib/node_modules/lame/lib/bindings.js:1:37)
at Module._compile (internal/modules/cjs/loader.js:1158:30)
at Object.Module._extensions..js (internal/modules/cjs/loader.js:1178:10)
at Module.load (internal/modules/cjs/loader.js:1002:32)
/var/task/node_modules/alexa-sdk/lib/alexa.js:300
throw err;
^
```

```
Error: The module '/var/task/lib/node_modules/lame/build/Release/bindings.node'
was compiled against a different Node.js version using
NODE_MODULE_VERSION 48. This version of Node.js requires
NODE_MODULE_VERSION 72. Please try re-compiling or re-installing
the module (for instance, using npm rebuild or npm install).
at Object.Module._extensions..node (internal/modules/cjs/loader.js:1208:18)
at Module.load (internal/modules/cjs/loader.js:1002:32)
at Function.Module._load (internal/modules/cjs/loader.js:901:14)
at Module.require (internal/modules/cjs/loader.js:1044:19)
at require (internal/modules/cjs/helpers.js:77:18)
at bindings (/var/task/lib/node_modules/lame/node_modules/bindings/bindings.js:76:44)
at Object. (/var/task/lib/node_modules/lame/lib/bindings.js:1:37)
at Module._compile (internal/modules/cjs/loader.js:1158:30)
at Object.Module._extensions..js (internal/modules/cjs/loader.js:1178:10)
at Module.load (internal/modules/cjs/loader.js:1002:32)
END RequestId: 56fbf218-2bd2-440e-9b90-3b6ffed32af2
REPORT RequestId: 56fbf218-2bd2-440e-9b90-3b6ffed32af2 Duration: 560.79 ms Billed Duration: 600 ms Memory Size: 1344 MB Max Memory Used: 36 MB
RequestId: 56fbf218-2bd2-440e-9b90-3b6ffed32af2 Error: Runtime exited with error: exit status 7
Runtime.ExitError
--
```
My question: how could I fix it? I am not much familiar with AWS hence I would appreciate if someone could help me with it ..
Thanks

---

### Post by QIII on 2020-04-03
Moved to ***Programming Talk***

---

