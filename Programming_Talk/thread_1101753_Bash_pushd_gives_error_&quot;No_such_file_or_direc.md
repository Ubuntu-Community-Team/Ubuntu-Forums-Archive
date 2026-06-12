---
title: "Bash pushd gives error &quot;No such file or directory&quot;"
date: 2009-03-20
forum: Programming Talk
---

### Post by bostonaholic on 2009-03-20
I've got a bash script that tries to *pushd* a directory onto the stack.  Yesterday and earlier today it was working fine, now I'm getting the error "No such file or directory *directory*".  Sometimes it is working, sometimes it does not?  Explanation?

Yes, all my permissions are ok and yes the script is executable.

Here is the script
[PHP]#!/bin/bash

CACHE_PATH=/home/mboston/.java/.deployment/javaws/cache

E_DIR=${CACHE_PATH}/.ext/E1237558777008

pushd ${E_DIR}
echo "do something"
popd

pushd ${CACHE_PATH}/.ext/E1237558777008
echo "so something"
popd[/PHP]

Here is the output
```
~/.java/.deployment/javaws/cache/.ext/E1237558777008 /temp/files
do something
/temp/files
./test.sh: line 11: pushd: /home/mboston/.java/.deployment/javaws/cache/.ext/E1237558777008: No such file or directory
so something
./test.sh: line 13: popd: directory stack empty

```

Any help is greatly appreciated, thanks!

I am using Ubuntu 8.10 64-bit.

---

### Post by bostonaholic on 2009-03-20
Ok, that one above is now working again.  Sometimes it works sometimes it does not.  Now I have another script, not even using *pushd* and I'm getting the same error message

the script
[PHP]#!/bin/bash

DEPLOY_PATH=/temp/deploy
${FILES_PATH}=${DEPLOY_PATH}/files

cp --verbose ${FILES_PATH}/install.properties ${DEPLOY_PATH}/thh/
cp --verbose ${FILES_PATH}/install-thh.opt ${DEPLOY_PATH}/thh/
cp --verbose ${FILES_PATH}/server.properties ${DEPLOY_PATH}/thh/props/properties/[/PHP]

the output
```
./3_copyFiles.sh: line 5: =/temp/deploy/files: No such file or directory
cp: cannot stat `/install.properties': No such file or directory
cp: cannot stat `/install-thh.opt': No such file or directory
cp: cannot stat `/server.properties': No such file or directory

```

---

### Post by ghostdog74 on 2009-03-20
what are you actually wanting to do?

---

### Post by bostonaholic on 2009-03-20
> **ghostdog74 said:**
> what are you actually wanting to do?

The first script is used to run an 'ant' (build/run java code) within the java cache directory.  I use the script so I don't have to manually cd into so many directories and then type a long 'ant -Djava.library.path etc. etc.' everytime.  I can just run this script (from a dir that contains my other helpful scripts) so I don't have to type as much.

The second script is similar to the first but is just copying 3 files into a new directory.

I just need to be able to get inside a directory and run a command from inside it.  When I try to 'pushd' into said directory (and even cd) from the bash, it's telling me "No such file or directory" (but only sometimes).

Does it really matter what I'm trying to accomplish inside the directory?  Black box programming!  That's why I put "#do something".  You need not that piece of information in order to solve my issue.

---

### Post by geirha on 2009-03-21
> **bostonaholic said:**
> 
[PHP]
${FILES_PATH}=${DEPLOY_PATH}/files
[/PHP]


You must not use $ when you assign the variable. ```
FILES_PATH=${DEPLOY_PATH}/files
```

As for your initial problem. Are you sure the cache-dir is still there after you've "done something"? cache is typically removed when it is no longer needed...

---

### Post by bostonaholic on 2009-03-21
> **geirha said:**
> You must not use $ when you assign the variable. ```
FILES_PATH=${DEPLOY_PATH}/files
```
Thanks, I didn't catch that.  My actual file has it correct, I just typed it up wrong in the post.

These are not the exact files I'm using, they're modified to make it easier on you guys.

> As for your initial problem. Are you sure the cache-dir is still there after you've "done something"? cache is typically removed when it is no longer needed...

Yes, it is there.  I know it is cause I can manually cd into it.  And this is javaws cache.  i.e.  When you run a java application from the web, it will DL the jars into a misc. directory so the next time you run the same application it doesn't have to re-download the files.

Again, **IT DOESN'T MATTER WHAT I'M TRYING TO DO INSIDE THE DIRECTORY**  The issue isn't "what" I'm doing in the directory, the issue is "why it's giving me the error message.

---

### Post by WW on 2009-03-21
No need to "shout". :)  

So I take it we can ignore the problem reported in post #2, since it looks like those are exactly the errors that you would get if you had used ${FILES_PATH}=... instead of FILES_PATH=...

---

### Post by bostonaholic on 2009-03-23
oddly enough the scripts are working now.  I haven't changed anything so who knows...

---

