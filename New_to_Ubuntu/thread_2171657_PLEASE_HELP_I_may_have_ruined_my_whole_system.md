---
title: "PLEASE HELP I may have ruined my whole system"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by jack17 on 2013-08-31
Okay I will start from the beginning. I needed to gain access to my /usr/ folder so I ran the command 

sudo chmod 600 /usr/ 

This is where everything messed up. I now cannot run any programs because I get an error saying 

"Failed to execute child process "exo-open" (Permission denied)""

---

### Post by Crusty Old Fart on 2013-09-01
Maybe putting the permission settings back to what they were originally would fix the problem.
On my system, /usr looks like this:
```

drwxr-xr-x  10 root root  4096 2011-02-04 19:26 usr

```
So, that would be:
```

sudo chmod 755 usr

```
I hope the solution is that simple.

---

### Post by jack17 on 2013-09-01
I am now unable to boot Ubuntu. Plus when I was booted into it I couldn't even open terminal it would return the "Failed to execute child process "exo-open" (Permission denied)"" error

---

### Post by Petro Dawg on 2013-09-01
You may need to live boot using a DVD/USB, mount the hard-drive, and fix the permissions from there.

---

### Post by jack17 on 2013-09-01
How would I go about doing this? I am a newbie

---

### Post by Crusty Old Fart on 2013-09-01
There's something else I didn't notice earlier.
You wrote that you used the command:
```

sudo chmod 600 /usr/

```
When I ran a similar command on my system, on a directory I named: x, I got an error:
```

chmod 600 /x/

[COLOR=#008000]**~~~ Output ~~~**[/COLOR]

chmod: cannot access `/x/': No such file or directory

```
I'm surprised the command you entered did anything at all.
So  I have no idea what happened to your system when you tried to chmod on  /usr/ instead of usr without being embedded in slashes.

> **jack17 said:**
> How would I go about doing this? I am a newbie
Did you install Ubuntu using a CD/DVD disk, or did you use a thumb drive?

---

