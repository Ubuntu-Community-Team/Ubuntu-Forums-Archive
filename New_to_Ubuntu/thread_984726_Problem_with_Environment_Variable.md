---
title: "Problem with Environment Variable"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by eweibust on 2008-11-16
I am trying to create a couple env vars and am confused at my problem.  This is the last 4 lines in my .bashrc

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin:.

export GRAILS_HOME=~/dev/apps/grails-1.0.4
export PATH=$PATH:$GRAILS_HOME/bin

My problem is I can't cd to $GRAILS_HOME after sourcing my .bashrc. I will start to type "cd $GRA" and then I hit tab for completion but it expands incorrectly to "cd \$GRAILS_HOME".  I hit enter trying to execute the cmd and get the following "bash: cd: $GRAILS_HOME: No such file or directory"

So my question is why don't my env vars work?

---

### Post by eweibust on 2008-11-21
Has anybody read this?  Any ideas?

---

