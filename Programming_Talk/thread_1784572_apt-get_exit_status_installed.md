---
title: "apt-get exit status installed"
date: 2011-06-17
forum: Programming Talk
---

### Post by GrantStoner on 2011-06-17
Say I wanted to put in a bash script a check to install a program that's not already installed, what would be the exit code of an installed program? With .rpms I could do
```
SVN="subversion"
rpm -q $SVN >/dev/null 2>&1
# 'rpm' exits with a 0 if the package is in the system
if [ "$?" -ne "0" ]; then
        yum -y install $SVN
fi
```I tried in Ubuntu with```

    if [ "subversion" != "0" ]; then
        echo "No suitable SVN package installed. Grabbing one now . . ."; sleep 1
        apt-get install -y subversion >/dev/null && echo "Got one."
    else
        echo -e "Dependencies met. Continuing on . . .\n"; sleep 1
    fi
```But it always does the 'then' action and never the 'else' action - regardless of if subversion is installed already. So this doesn't seem to be right? What's the exit status in apt-get if not 0?

---

