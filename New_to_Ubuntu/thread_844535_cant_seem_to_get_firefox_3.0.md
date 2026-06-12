---
title: "cant seem to get firefox 3.0"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by default00 on 2008-06-29
I can't get firefox 3 installed correctly. I've gone through the terminal and tried sudo apt-get install firefox-3.0 and it says that I already have it. When I open up firefox though it is still firefox 2. I've used the Synaptic Package Manager too and have firefox-3.0 and firefox-3.0-gnome-support installed. I previously uninstalled the firefox 3 beta and reverted back to firefox 2, could this be the cause of my problem?

---

### Post by sayakb on 2008-06-29
At a terminal:
```
firefox-3.0
```
Should start FF3. If it doesn't, paste the output of the command here.

---

### Post by default00 on 2008-06-29
this opens firefox 2. Help -> About shows firefox 2.0.0.14

---

### Post by Wobblybob on 2008-06-29
try typing just firefox, I think the version number is not required once updated. If this works it may just be your launcher that needs it's properties updating. You could also open [Synaptic] and remove all the old versions of firefox-2.
Good luck

---

### Post by aysiu on 2008-06-29
Can you paste these commands into the terminal and then post the output back here? ```
ls /usr/bin/firefox -l
ls /usr/bin/firefox-3.0 -l
ls /opt
```

---

### Post by default00 on 2008-06-29
ls /usr/bin/firefox -1 : /usr/bin/firefox

ls /usr/bin/firefox-3.0 -1 : /usr/bin/firefox-3.0

ls /opt : i just get another prompt, nothing is returned

---

### Post by aysiu on 2008-06-29
Paste. Do not retype.

It's a lowercase *L*, not the number one.

---

### Post by default00 on 2008-06-29
```
~$ ls /usr/bin/firefox -1
/usr/bin/firefox
~$ ls /usr/bin/firefox-3.0 -1
/usr/bin/firefox-3.0
~$ ls /opt
~$
```

---

### Post by ercferret18 on 2008-06-29
try "sudo apt-get install firefox"

---

### Post by aysiu on 2008-06-29
Once again, I think you're missing something.

Please **paste** the command I gave you. Do not *retype* the command.

That last bit is *-l* not *-1*, as you keep typing.

---

### Post by default00 on 2008-06-29
Wow sorry about that, heres what i get:

```
~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 11 2008-06-29 16:39 /usr/bin/firefox -> firefox-3.0
~$ ls /usr/bin/firefox-3.0 -l
lrwxrwxrwx 1 root root 29 2008-06-29 16:39 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0/firefox.sh
~$ ls /opt
~$
```

---

### Post by aysiu on 2008-06-29
There's absolutely no reason Firefox 2 should be launched.

You don't have the Mozilla version of Firefox 2 installed to /opt, and your /usr/bin/firefox points to Firefox 3.0

Can you close all instances of Firefox and then press Alt-F2 and type ```
firefox
``` and then see if 2 or 3 launches?

---

### Post by default00 on 2008-06-29
I'm still getting firefox 2

---

### Post by ercferret18 on 2008-06-29
ok, maybe search for firefox 2 in synaptic package manager and uninstall everything that looks like it is firefox 2

---

### Post by aysiu on 2008-06-29
Hm. That's weird. How about the output of this command? ```
cat /usr/lib/firefox-3.0/firefox.sh
```

---

### Post by default00 on 2008-06-29
```
:~$ cat /usr/lib/firefox-3.0/firefox.sh
#!/bin/sh

# Firefox launcher containing a Profile migration helper for
# temporary profiles used during alpha and beta phases.

# Authors:
#  Alexander Sack <asac@jwsdot.com>
#  Fabien Tassin <fta@sofaraway.org>
# License: GPLv2 or later

# if there exists a beta profile (first found: $MOZDIR/firefox-3.0,
# $MOZDIR/firefox-trunk, $MOZDIR/granparadiso) and there is a standard
# firefox profile as well, ask the user what to do. In case he decides to
# import the firefox 2 profile settings, we keep the firefox directory
# untouched, but rename the beta profile by appending the suffix
# |.abandoned|. In case the user decides to keep using the firefox 3
# profile, we will rename the original firefox profile to firefox.2-replaced
# and rename the beta profile to be |.mozilla/firefox|.
#
# as a third option the user can defer his final decision. This will leave the
# directories untouched, thus making the user use the old firefox profile by
# default.
#
# in addition, even older profiles are renamed too, by appending |.abandoned|
# to their name.

APPNAME=firefox
MOZDIR=$HOME/.mozilla
LIBDIR=/usr/lib/firefox-3.0
DROPPED=abandoned

FOUND=""
if [ -d $MOZDIR/firefox ] ; then
  FOUND=firefox
fi

FOUND_BETA=""
BETA_LIST=""
for betaname in granparadiso firefox-trunk firefox-3.0; do
  if [ -d $MOZDIR/$betaname ]; then
    BETA_LIST="$BETA_LIST $betaname"
    FOUND_BETA=$betaname
  fi
done

if [ "$FOUND" != "" -a "$FOUND_BETA" != "" ] ; then
  echo -n "Found Beta Participation ..."
  $LIBDIR/ffox-3-beta-profile-migration-dialog
  result=$?
  if [ $result = 1 ]; then
     mv $MOZDIR/$FOUND $MOZDIR/$FOUND.2-replaced
     mv $MOZDIR/$FOUND_BETA $MOZDIR/$FOUND
     for beta in $BETA_LIST ; do
       if [ $beta != $FOUND_BETA ] ; then
         mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
       fi
     done
     echo " keep beta profile."
  elif [ $result = 2 ]; then
     for beta in $BETA_LIST ; do
       mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
     done
     echo " use firefox 2 profile."
  else
     echo " use firefox 2 profile, but will ask again next time."
  fi
  echo " ... will check again next time."
elif [ "$FOUND_BETA" != "" -a "$FOUND" = "" ]; then
  # in case we only have a beta profile the user most likely wants to use
  # that. just doing, no questions asked.
  mv $MOZDIR/$FOUND_BETA $MOZDIR/firefox
  for beta in $BETA_LIST ; do
    # Move out the older beta profiles
    if [ $beta != $FOUND_BETA ] ; then
      mv $MOZDIR/$beta $MOZDIR/$beta.$DROPPED
    fi
  done
  echo "*NOTICE* Profile $FOUND_BETA found and moved as main profile"
fi

exec $LIBDIR/$APPNAME "$@"

```

---

### Post by neogrammarian on 2008-06-30
Hey all, I've got a nearly identical issue.  The only difference is that I've  uninstalled the "3.0"  I put "3.0" in quotes b/c the files I got via symantec today were labeled "3.0," refused to install, and when I dug around for an executable, I discovered it was 3.0a8, Grand Paradiso- which appears to be what you have, too.  Upon closer inspection, my synaptic labels "3.0" a developer version.  

I'm guessing that the "3.0" we're trying to download isn't the regular release.  Can anyone wiser than I on these matters confirm this based on the log in the post above?

When I downloaded from Firefox's site (trying to workaround what I assume is an old repository for synaptic), I got an archive, w/no installer or instructions as to how to proceed.

[my apologies if I'm not understanding this thread- it's labeled "solved" but I see no solution posted]

---

### Post by default00 on 2008-07-01
i had some other problems with ubuntu so i just formatted and reinstalled and everything worked out. i just marked as solved cause i firefox 3 ended up working. ill change it to unsolved though, sorry, i didnt know anyone else was following along.

---

### Post by neogrammarian on 2008-07-02
np Default- just thought I'd chime in as it sounded like we had similar issues (though my 7.10's working fine, knock on wood, so I'd rather not follow your lead and scrub down the hd!)

---

### Post by Erky on 2008-07-06
Hello,
I am having the exact same problem. My outputs are also exactly the same as his, so if anyone could help, I would be very grateful!

---

