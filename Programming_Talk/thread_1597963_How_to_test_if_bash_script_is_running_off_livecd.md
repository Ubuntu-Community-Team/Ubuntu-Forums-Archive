---
title: "How to test if bash script is running off livecd?"
date: 2010-10-15
forum: Programming Talk
---

### Post by shaggy999 on 2010-10-15
I have a script I'm working on that may run on installations but may also run off of liveCD environments. The script acts differently depending on if it's running off a liveCD or local install and I am trying to figure out how to test if the environment is running off a liveCD environment or usb stick. At the moment I just have a parameter I pass to my script, but it would be nice if I had some sort of "magical check" so I didn't have to do that.

Any ideas?

---

### Post by shaggy999 on 2010-10-15
Figured it out myself. Live environment always runs with 'ubuntu' as the username. So I grab the uid of the parent process (this is required because the command runs sudo and is the only method I've found to grab the real username of a script run as superuser). Then I grep the /etc/passwd file, which I know is world readable to grab the username associated with the uid.

If the username is 'ubuntu' then I know I'm in a liveCD environment. Technically I guess I don't even need to do the second statement because the ubuntu user is always 999 and the first user in an installed environment is 1000. But anyways, it works. Unless there's some really stupid simple way better than what I'm doing.

```

USER_ID=`ps -o uid $PPID | grep -o [0-9]*`
USER_NAME=`cat /etc/passwd | grep ${USER_ID} | cut -d: -f1`

```

---

### Post by worksofcraft on 2010-10-16
Hey that's really neat solution... I think there should be some kind of data base where all these answers are stored... I know Google is pretty good, but 9 times out of 10 the links it gives don't have a decent answer I find... anyway I'm making a copy of your solution incase I need it one day :)

---

### Post by shaggy999 on 2010-10-17
Thanks. The full solution looks like this:

```

# User executing the script (if 999, running on livecd)
USER_ID=`ps -o uid ${PPID} | grep -o [0-9]*`

if [ `dpkg --get-selections | grep -c ubuntu-netbook` -gt 0 ]; then
    if [ "${USER_ID}" -eq 999 ]; then
      DIST="net_live"
    else
      DIST="net_inst"
    fi
else
  if  [ `uname -m` == "i686" ]; then
    if [ "${USER_ID}" -eq 999 ]; then
      DIST="x86_live"
    else
      DIST="x86_inst"
    fi
  elif [ `uname -m` == "x86_64" ]; then
    if [ "${USER_ID}" -eq 999 ]; then
      DIST="x64_live"
    else
      DIST="x64_inst"
    fi
  fi
fi

```

Then later on I can do something like:

```

if [ ${DIST} == "x86_live" ] ||
   [ ${DIST} == "x64_live" ] ||
   [ ${DIST} == "net_live" ] 
then
  echo "This environment is running off a LiveCD or USB Stick."
fi

```

---

### Post by shaggy999 on 2010-10-17
I should mention this method isn't foolproof. If the script is run from crontab or something then the parent process will also be root. A better way may be to just go straight to /etc/passwd and see if there's a user with id 999 named ubuntu instead of grabbing the uid of the parent process.

But as long as the script is executed manually, with or without sudo, it will work correctly.

---

