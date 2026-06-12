---
title: "Safely adding dirs in /opt to PATH variable"
date: 2013-04-07
forum: Programming Talk
---

### Post by WebDrake on 2013-04-07
Hello all,

I have various programs that are installed in subdirs of /opt.  In order to allow them to run, I obviously need to add the appropriate dirs to PATH.

My "solution" was to add a little script, opt.sh to /etc/profile.d/ containing the following code:
```

for d in /opt/*/bin; do
        PATH="$PATH:$d"
done

``` ... but this has at least 2 problems: first, it means that if I ever rerun the profile script while logged in, $PATH winds up containing multiple entries; and in any case I believe it's not considered very safe.

Can anyone advise at least how to get rid of the multiple entries, and (better) on any superior solutions for packages installed in subdirs of /opt ... ?

Thanks & best wishes,

     -- Joe

---

### Post by schragge on 2013-04-07
Provided that you don't have several versions of same applications co-installed under /opt I'd try something like
```

mkdir /opt/bin
ln -s /opt/*/bin/* /opt/bin
PATH="$PATH:/opt/bin"

``` and maybe using [stow]("http://manpages.ubuntu.com/manpages/precise/en/man8/stow.8.html") to maintain the link farm.

---

### Post by dwhitney67 on 2013-04-07
> **schragge said:**
> Provided that you don't have several versions of same applications co-installed under /opt I'd try something like
```

mkdir /opt/bin
ln -s /opt/*/bin/* /opt/bin
PATH="$PATH:/opt/bin"

``` and maybe using [stow]("http://manpages.ubuntu.com/manpages/precise/en/man8/stow.8.html") to maintain the link farm.

This is a really, really, bad idea.  It's possible that one may have multiple versions of a toolkit installed in /opt, so for obvious reasons, there will be file name clashes.

---

### Post by dwhitney67 on 2013-04-07
> **WebDrake said:**
> Hello all,

I have various programs that are installed in subdirs of /opt.  In order to allow them to run, I obviously need to add the appropriate dirs to PATH.

My "solution" was to add a little script, opt.sh to /etc/profile.d/ containing the following code:
```

for d in /opt/*/bin; do
        PATH="$PATH:$d"
done

``` ... but this has at least 2 problems: first, it means that if I ever rerun the profile script while logged in, $PATH winds up containing multiple entries; and in any case I believe it's not considered very safe.

Can anyone advise at least how to get rid of the multiple entries, and (better) on any superior solutions for packages installed in subdirs of /opt ... ?

Thanks & best wishes,

     -- Joe

Just check for the existence of the directory 'd' in PATH before attempting to augment PATH variable.  Perhaps:
```

for d in /opt/*/bin; do
        echo $PATH | grep "$d" > /dev/null
        if [ $? -ne 0 ]; then
                PATH="$PATH:$d"
        fi
done

```
I'm not an expert Bash script developer, so perhaps the above can be condensed for efficiency purposes.

---

### Post by schragge on 2013-04-07
Inspired by [this]("http://superuser.com/a/39995").

Since */etc/profile.d/* is not only for bash, I tried to keep it POSIXly correct:
```

for d in /opt/*/bin; do
  test -d "$d" || continue
  case :$PATH: in
  *:"$d":*);;
  *) PATH=${PATH:+$PATH:}$d;;
  esac
done

```

---

### Post by WebDrake on 2013-04-09
Thanks to all of you for the thoughts and replies :-)

@schragge -- forgive me, my shell scripting is not too great -- can you explain the use of case etc. in that script?

It's not clear to me whether that script will handle the case of $d$ being at the beginning or the end of $PATH (i.e. not surrounded on both sides by : ).  I also don't understand the double-semicolons ;; at the end of lines.

---

### Post by schragge on 2013-04-09
Double-semicolons are just part of syntax for the [case construct]("http://www.gnu.org/software/bash/manual/html_node/Conditional-Constructs.html#index-case"), they terminate command list for particular case branch.

Note that the case parameter I'm matching against is not $PATH, but [COLOR=red]:[/COLOR]$PATH[COLOR=red]:[/COLOR]. This is to ensure that > $d$ being at the beginning or the end of $PATH (i.e. not surrounded on both sides by : ) also gets matched.

The logic of the case statement is following:
If the first case pattern is matched, i.e. $d is already in $PATH then do nothing, otherwise add $d to the end of $PATH value.
*${PATH:+$PATH:}* means substitute $PATH with the part after **:+** only if $PATH is set and not empty, otherwise just do *PATH=$d*

---

### Post by WebDrake on 2013-08-20
@schragge: It's a bit late coming, but just to say a big thank you for the case-based script.  For whatever reason I didn't get it to work at the time (probably a typo :-) ) but with a fresh install of 13.10 I had another look, and it's working nicely. :-)

---

