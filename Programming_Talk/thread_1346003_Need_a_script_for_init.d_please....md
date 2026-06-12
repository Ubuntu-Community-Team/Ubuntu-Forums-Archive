---
title: "Need a script for init.d please..."
date: 2009-12-04
forum: Programming Talk
---

### Post by Krupski on 2009-12-04
Hi all,

I am running the "Folding at Home" distributed computing client on my Linux based file server. 

Currently I start it "by hand" after booting up the box, I SSH into it and start the client.

I would like to make a nice, robust script for it that gets autostarted at boot time, but I'm not sure how to go about it. The script should also follow the new "rules" concerning script structure.

If someone would like to donate a few minutes of their time to help me out here, I would really appreciate it!

OK, here's what I would like the script to do:

* start
* stop
* status

"Start" would of course, start the client and be the default bootup action. "Start" needs to check if there's already an instance running and NOT try to run a second instance.

"Stop" would stop the client. By killing "fah6", everything else (child processes) also quit.

"Status" would just report if the client is running by checking if there's an "fah6" in memory (i.e. using ps -A).

Now, here's (I think) the information needed:

```

Location of executables: **/home/folding-at-home**

Executable to run: **/home/folding-at-home/fah6**

Command line parameters for fah6: **-smp -verbosity 9 -advmethods**

All stdout and stderr to /dev/null (since it writes a separate log file anyway).

Processes when it's running (from ps -A): 

    fah6
    mpiexec
    FahCore_a2.exe
    FahCore_a2.exe
    FahCore_a2.exe
    FahCore_a2.exe


```

Note: there is one instance of "FahCore_a2.exe" for each CPU core... mine's a quad core - hence 4 instances.

The presence of "fah6" is what "status" should use to determine if the client is running and there should be only ONE instance of "fah6".

Thank you!

-- Roger

---

### Post by falconindy on 2009-12-04
The F@H page has instructions on how to do this:

[http://folding.stanford.edu/Spanish/LinSMPGuide](http://folding.stanford.edu/Spanish/LinSMPGuide)

Also, you **do** know there's a release that uses SMP, yes?

---

### Post by Krupski on 2009-12-04
> **falconindy said:**
> The F@H page has instructions on how to do this:

[http://folding.stanford.edu/Spanish/LinSMPGuide](http://folding.stanford.edu/Spanish/LinSMPGuide)

Also, you **do** know there's a release that uses SMP, yes?

Um... yes... that's what the '-smp' command line parameter is for.

Are you saying that I should be using a different *VERSION*?

---

### Post by Krupski on 2009-12-04
> **falconindy said:**
> The F@H page has instructions on how to do this:


The instructions on the FAH site do not create a "proper" init.d script... don't know exactly how to explain it...

Scripts need a proper header and proper format... like this:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          description
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Long description
### END INIT INFO

case "$1" in
    start)
           do(stuff)
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
esac

```


Kinda like above... if that makes sense?

-- Roger

---

