---
title: "Running a perl script from startup?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by Mex5150 on 2013-03-31
Hi All

I have a perl script (get_iplayer.cgi) I want to run from startup, I have added ```
perl get_iplayer.cgi --port=1935 &
``` to the Startup aplications and tried to add the folder it's in (/home/mex/get-iplayer) to $PATH in ~/.profile but something isn't working right. What **exactly** do I need to add to ~/.profile to get this to work, does the startup command look right?

Thanks

---

### Post by Mex5150 on 2013-04-04
Anybody?

---

### Post by Polydorus on 2013-04-06
I wanted to create some startup scripts also and would like to hear the answer to this.

---

### Post by schragge on 2013-04-06
Take a look at [uhelp]community/AddingProgramToSessionStartup[/uhelp].

---

### Post by Mex5150 on 2013-04-09
Hi

> **schragge said:**
> Take a look at [uhelp]community/AddingProgramToSessionStartup[/uhelp].This all appears to be in order but it still doesn't work. I think this is down to a problem with the $PATH, as it reports the file not found.

This is what I have added to ~/.profile:```
if [ -d "$HOME/get-iplayer" ] ; then
  PATH="$PATH:$HOME/get-iplayer"
fi
```
Does that look right?

-Mex

---

### Post by schragge on 2013-04-10
It does, but bear in mind that 1) *~/.profile* is relevant only for a login shell, and 2) it gets executed only if neither *~/.bash_profile* nor *~/.bash_login* exist. If running the script is a one off task, there's no much point in adding its directory to $PATH anyway, instead you could just specify the full path:
```
perl /home/mex/get-iplayer/get_iplayer.cgi --port=1935 &
```

---

### Post by Mex5150 on 2013-04-11
Hi

> **schragge said:**
> It does, but bear in mind that 1) *~/.profile* is relevant only for a login shell, and 2) it gets executed only if neither *~/.bash_profile* nor *~/.bash_login* exist. If running the script is a one off task, there's no much point in adding its directory to $PATH anyway, instead you could just specify the full path:
```
perl /home/mex/get-iplayer/get_iplayer.cgi --port=1935 &
```

I came up with the full path idea (although I used $HOME/get-iplayer instead of /home/mex/get-iplayer), but it's still not working. It needs to continue running, but I think it stops as soon as it starts. I thought adding the & at the end would allow it to continue, but it doesn't seem to be working, does perl not work with &, or have I got my wires crossed and need to append something other than the &? When I run the comand from the terminal it works fine unless I close the terminal which is why I think that is the problem with start up, I could be wrong though.

-Mex

---

### Post by schragge on 2013-04-11
I don't think this has anything to do with &. Test that *~/.profile* gets executed at all. Add something like
```
echo This is ~/.profile executed by $0
``` to your *~/.profile*, then change to a text console (e.g. **Ctrl**+**Alt**+**F1**) and log in. The message should be displayed. If it doesn't, then *~/.profile* didn't get executed.

BTW, just opening a terminal in GUI doesn't execute *~/.profile* (*~/.bashrc* gets executed instead). Logging in graphically also doesn't (*~/.xsessionrc* gets executed instead). You need to change to a text console to execute it at login.

---

### Post by Mex5150 on 2013-04-11
Hi

After I boot and log in if I run:```
echo $PATH
```I get:```
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/mex/get-iplayer:/home/mex/get-iplayer
```Not sure why the folder I want is there twice, but as it's there at all, I would assume that the Path is not the problem, but something is still broken as the script still wont run ;^/

---

### Post by schragge on 2013-04-11
To prevent the folder from appearing in $PATH twice, check whether it's already in $PATH:
```

d=$HOME/get-iplayer
if test -d "$d"; then
  case :$PATH: in
  *:"$d":*);;
  *) PATH=${PATH:+$PATH:}$d;;
  esac
fi

```

---

### Post by Mex5150 on 2013-04-11
> **schragge said:**
> To prevent the folder from appearing in $PATH twice, check whether it's already in $PATH:
Does it matter if it's in there twice?

---

### Post by Mex5150 on 2013-05-10
Does it matter if it's in there twice?

---

