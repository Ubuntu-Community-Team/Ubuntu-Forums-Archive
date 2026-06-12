---
title: "Setting Python2.5 to Run From The Command Line"
date: 2006-12-09
forum: Programming Talk
---

### Post by cyberslayer on 2006-12-09
I have installed the python2.5 package on my system and I would like to know how to configure my system so that it will run the python2.5 interpreter when I type 'python' on the command line.  Currently it seems to be set to run Python2.4 instead when I type 'python'.  I noticed that there are python2.4 and python2.5 executables in /usr/bin and there is also a file named python which is a link to an executable.  When I look under properties I can see that it is linked to python2.4 so I can see why typing python from the command line runs python2.4 and not python2.5 but I don't know how to change this.  Could someone please tell me how to change the target of the python file?

Thanks

---

### Post by jan247 on 2006-12-09
```

sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python

```

---

### Post by asimon on 2006-12-09
> **jan247 said:**
> ```

sudo rm /usr/bin/python
sudo ln -s /usr/bin/python2.5 /usr/bin/python

```
The debian way to do this is
```

$ sudo update-alternatives --config python

```

---

### Post by cyberslayer on 2006-12-09
Ok.  Thanks for your help.  It works now.

---

### Post by kperkins on 2006-12-09
> **asimon said:**
> The debian way to do this is
```

$ sudo update-alternatives --config python

```

Except when I try this, it says there are no alternatives for python--which I know is false, since I have 2.4 and 2.5 on my system.

---

### Post by Wybiral on 2006-12-09
Same here, I have 2.4 and 2.5 and it told me there were no alternatives either. I don't really mind as I rarely use python in the terminal, just thought I would point that out.

---

### Post by po0f on 2006-12-10
cyberslayer,

If you want to set it up for just one user, you can set an alias for it in ~/.bashrc:
```
[FONT="Courier New"]alias python='/usr/bin/python2.5'[/FONT]
```

I really don't suggest changing /usr/bin/python to point to /usr/bin/python2.5, because I'm sure there's more than a couple of applications that will break if you do so.

---

### Post by cyberslayer on 2006-12-12
> I really don't suggest changing /usr/bin/python to point to /usr/bin/python2.5, because I'm sure there's more than a couple of applications that will break if you do so.

Yes, I just found out that was a really bad idea.  I thought that since I just wanted to use it to run my own programs in python2.5 it wouldn't be a problem but it turns out that if you change the symbolic link to python2.5 Add/Remove programs will not run correctly because it does not work with python2.5!  It looks like this is because there is no AppInstall package in /usr/lib/python2.5/site-packages but there is in /usr/lib/python2.4/site-packages so python doesn't find the required AppInstall package when you try to run Add/Remove programs (probably could have just copied the required packages to /usr/lib/python2.5/site-packages from /usr/lib/python2.4/site-packages but I didn't try it).  Anyway, I changed the symbolic link back to python2.4 and added the alias as po0f suggested and it works fine now.  

Thanks

---

### Post by dthury on 2007-02-11
I think I've figured out how to get python2.5 "fully functional.  Using the update-alternatives "hint" from an earlier response, I did a little research, and learned that "update-alternatives" for python MUST be configured (which it apparently is not, out of the box).

Like others above mentioned, I too experienced  "update-alternatives --config python" returned "no alternatives".   I then did the following (after su root;  sudo before each command may work too):
```

update-alternatives --install /usr/lib/python  python /usr/lib/python2.4  10
update-alternatives --install /usr/lib/python  python /usr/lib/python2.5 1
```

I chose priorities 10 and 1 rather arbitrarily, thinking that Python 2.4 should be the higher/preferred version.

I now get the list of alternatives when I issue the ```
update-alternatives --config python,  or
update-alternatives --set python /usr/lib/python2.5
``` I make my preferred selection. invoke python, and get the selected version.  This about the only tests I've done so far, so I don't yet know if there are any gotchas yet!!

Any comments?

---

### Post by Tyler Oderkirk on 2007-02-25
> **dthury said:**
> 
```

update-alternatives --install /usr/lib/python  python /usr/lib/python2.4  10
update-alternatives --install /usr/lib/python  python /usr/lib/python2.5 1
```

Hi dthury,

Did you mean to say this instead?
```

update-alternatives --install /usr/**bin**/python  python /usr/lib/python2.4  10
update-alternatives --install /usr/**bin**/python  python /usr/lib/python2.5 1
```

/usr/lib/python is a directory of python libraries. /urs/bin/python is the symlink that we want the debian alternatives system to maintain for us I think.

-Tyler

---

