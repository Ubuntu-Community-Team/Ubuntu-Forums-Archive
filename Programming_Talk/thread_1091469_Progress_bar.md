---
title: "Progress bar"
date: 2009-03-09
forum: Programming Talk
---

### Post by any.linux12 on 2009-03-09
Hi!

I'm doing some scripts for svn repositories and as the code is done I would like some more graphic just to look cooler.

I'm trying to programm a Progress bar and it kind of works but doesn't stop and as I think that some of you know this much better than me I want you help.

so the working code that I've is: 

> if [ $? -eq 0 ] ; then
    
    svn checkout svn+ssh://ruben@192.168.1.3/esp-server/svn/$URL &> $LOGFILE
  
    rm -f $LOGFILE
fi

then I copy some code from oder guy also in this forum and I tryid like this:

> if [ $? -eq 0 ] ; then
    
    while svn checkout svn+ssh://ruben@192.168.1.3/esp-server/svn/$URL &> $LOGFILE ; do
    
    sleep 0.25
    echo -n .
    done | zenity --progress --pulsate --auto-kill
    rm -f $LOGFILE
fi

It starts the code and the progress bar but after the code is finished never stops the bar!!!???!! Why?

thanks in advance

---

### Post by any.linux12 on 2009-03-10
bump

---

