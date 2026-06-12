---
title: "Setting JAVA_HOME"
date: 2007-03-02
forum: Programming Talk
---

### Post by Turner.kj on 2007-03-02
I added the following to my ~/.bash_profile.  But, when I ask 'java -version' I get a different version.  How does one set JAVA_HOME?  And yes, '~/Dev/j2sdk1.4.2_13' does exist.

# set JAVA_HOME and PATH if it exists
if [ -d ~/Dev/j2sdk1.4.2_13 ] ; then
    export JAVA_HOME='~/Dev/j2sdk1.4.2_13'
    PATH=$JAVA_HOME:$JAVA_HOME/bin:"${PATH}"
fi

---

### Post by Turner.kj on 2007-03-02
got it

---

