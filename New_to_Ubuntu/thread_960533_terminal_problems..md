---
title: "terminal problems."
date: 2008-10-27
forum: New to Ubuntu
---

### Post by AerosolSP on 2008-10-27
everytime i open a terminal, i get:
```

bash: c:command not found
bash: c:command not found
username@groupname:-$
```

the last line is normal, but the first two lines...aren't. In addition to this, I can't run sudo. The instructions im following said to type this:
```

export PSPDEV="/usr/local/pspdev"
export PSPSDK="$PSPDEV/psp/sdk"
export PSPPATH="$PSPDEV/bin:$PSPDEV/psp/bin:$PSPSDK/bin"
export PATH="$PATH:$PSPPATH"
```

which I did. Then I'm supposed to type this

```
sudo chmod 777 -R /usr/

```
but when I do that, I get this:

```
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
bash: sudo: command not found
```

I'm trying to install the psp tool chain, and i this is hindering doing so! Help'd be much appreciated, thanks.

---

### Post by maybeway36 on 2008-10-27
Type:
```
dash
```
It should give you a $ prompt. See if you can run your commands from here.

---

### Post by dracayr on 2008-10-27
type
```
echo $PATH
```

and paste the output here

dracayr

---

### Post by AerosolSP on 2008-10-27
There's no output. Just a blank line

---

### Post by AerosolSP on 2008-10-27
small bump, as the database hiccup seems to have knocked this topic clear over the horizon.

---

### Post by scorchgeek on 2008-10-27
Your path is messed up. I don't know all the directories included in the default path, so I can't tell you how to get it back to normal, but for now you can run sudo by typing
```
/usr/bin/sudo [command]
```.

---

### Post by AerosolSP on 2008-10-27
i was informed that by running chmod 777, i screwed up the permissions of my /usr/ folder, thereby ruining my entire installation. Is that right?

---

### Post by Xiong Chiamiov on 2008-10-27
> **scorchgeek said:**
> Your path is messed up. I don't know all the directories included in the default path, so I can't tell you how to get it back to normal, but for now you can run sudo by typing
```
/usr/bin/sudo [command]
```.
Yes, something went wrong here:
```

export PATH="$PATH:$PSPPATH"

```

If this is still an issue on reboot, then you need to export the proper PATH in your ~/.bashrc.  You can do that by just adding the line
```

export PATH="/bin:/usr/bin:/sbin:/usr/sbin"

```
or whatever.  You'll want more directories than that, but I'm not sure which ones specifically you'll need.  Here's mine:
```

/bin:/usr/bin:/sbin:/usr/sbin:/opt/kde/bin:/usr/bin/perlbin/site:/usr/bin/perlbin/vendor:/usr/bin/perlbin/core:/opt/qt/bin

```

---

### Post by Xiong Chiamiov on 2008-10-27
> **AerosolSP said:**
> i was informed that by running chmod 777, i screwed up the permissions of my /usr/ folder, thereby ruining my entire installation. Is that right?
/usr should be 755, and owned by root.  Almost everything inside of it should be 755 as well, but there may be some exceptions.  Did you chmod with the recursive flag (-R)?  If not, then only that folder was changed, and not everything inside of it, which will make fixing it rather easy.

---

### Post by AerosolSP on 2008-10-28
nope...the instructions i was following said chmod 777 -R /usr/

damnit.

---

