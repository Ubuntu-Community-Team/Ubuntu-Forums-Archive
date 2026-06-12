---
title: "autostart bash script calling up JAVA"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by chris262 on 2014-07-26
Hello all,

Description: Ubuntu 12.04 LTS (server x64)



I am trying to get the shell script ([http://pastebin.ubuntu.com/7869104/](http://pastebin.ubuntu.com/7869104/)) that starts my program, to autostart with my server startup (no login required)

I created a hard symlink with full directory paths as root:
```
ln /path/to/original/program.sh /etc/init.d/program
```

Then added it to autostart:
```
update-rc.d /etc/init.d/program defaults
```

With root ownership and full execution rights on program.sh

But I get the following error when executing the script from /etc.init.d/program:
```
./opmanager: line 22: bin/JREMigration.sh: No such file or directory
./opmanager: line 26: ./setEnv.sh: No such file or directory
Java Home 
cp: cannot stat `/conf/backup/server.xml': No such file or directory
cp: cannot stat `/conf/backup/workers.properties': No such file or directory
./opmanager: line 69: /bin/java: No such file or directory

```
When executing the script from /path/to/original/program.sh the program runs fine.

How can I get my program to autostart?

Thank you.

---

### Post by sandyd on 2014-07-26
Few issues - your using relative paths, and that script isnt in the propper init.d format.
Since Ubuntu has upstart, I would reccomend using upstart to start scripts instead.

For example,
```

description "yourapp"

start on started mountall
stop on shutdown

setuid useruid
setgid usergid

# Automatically Respawn:
respawn
respawn limit 99 5

script
   #call program script here
end script

post-start script
   # Optionally put a script here that will notifiy you program has restarted
end script
```

---

### Post by chris262 on 2014-07-27
Hello there [COLOR=#C61919][B]sandyd
[/B][/COLOR]Thank you for your input, much appreciated.

I managed to get it all working by using the preconfigured script, linkAsService.sh (and editing it as it did not work out of the box) provided by the original developers > [http://paste.ubuntu.com/7873348/](http://paste.ubuntu.com/7873348/)
Which calls for this script > [http://paste.ubuntu.com/7873375/](http://paste.ubuntu.com/7873375/)
That finally creates the startup service under /etc/init.d

Cheers!

---

