---
title: "How to grab pid of a specific process that was started inside a bash script?"
date: 2009-02-07
forum: Programming Talk
---

### Post by tr333 on 2009-02-07
I have the following bash script to play music to an Apple Airtunes device:
```
#!/bin/bash

IP='192.168.0.250'
VOLUME='-30'  # range is -144 to 0
JUSTEPORT='/usr/local/bin/JustePort'
MIME=`file -b -i "$*"`

if [[ "$MIME" = 'audio/mpeg' ]] ; then
    mpg123 -s "$*" | $JUSTEPORT - $IP $VOLUME
elif [[ "$MIME" = 'audio/ogg' || "$MIME" = 'application/ogg' ]] ; then
    oggdec -Q -R -o - "$*" | $JUSTPORTE - $IP $VOLUME
elif [[ "$MIME" = 'audio/aac' || "$MIME" = 'audio/mp4' ]] ; then
    faad -q -w -f 2 "$*" | $JUSTEPORT - $IP $VOLUME
else
    echo "Don't know how to handle this filetype, giving up."
    exit 1
fi

exit 0
```

If I run this script from another program, how can I kill the JustePort (mono/cli) process at a later time from the program that ran the bash script?  Running 'pidof' could potentially return multiple PIDs if there is multiple mono programs running as all mono programs run under the 'cli' process name.  Killing the bash script won't stop the mono/cli process.

---

### Post by jpkotta on 2009-02-07
```

foo & pid=$!
sleep 10
kill $pid # kills foo

```

---

### Post by geirha on 2009-02-07
```

script.sh & 
pid=$!                    # $pid should now have the pid of script.sh, 
                          # which in turn will the parent of JustePort
pgrep -P $pid JustePort   # This should list the pids of all processes that
                          # matches the name "JustePort" AND has $pid as 
                          # parent process id.
pkill -P $pid JustePort   # This will do the same, but instead of printing
                          # the pid, it will kill it.

```

---

### Post by tr333 on 2009-02-07
Thanks for the replies.  I will be executing the bash script from a perl script, but perl doesn't seem to have an equivalent of the bash $! operator :(.  What would be the best way for the perl script to grab that PID value?
I thought about writing the $$ value in the top of the bash script to a file somewhere but then either the perl script or the bash script would have to clean up the file later, which the bash script would be incapable of doing if cancelled with CTRL+C (bash doesn't have an atexit() equivalent?).

---

### Post by geirha on 2009-02-07
Can't help you with perl, but with bash I can. You can use a trap in bash to have something run on exit. ```
trap "rm somefile; some other command" EXIT
```

---

### Post by unutbu on 2009-02-07
This is how you can launch (fork) a bash script from perl and have the parent know the PID:

[PHP]#!/usr/bin/perl
use strict;
use warnings;

my $pid = fork();
if (not defined $pid) {
    warn "resources not avilable.\n";
} elsif ($pid == 0) {
    warn "I'M THE CHILD\n";
    exec("bash_script.sh");
    exit(0);
} else {
    warn "I'M THE PARENT, PID=$pid\n";
    waitpid($pid,0);
}[/PHP]

---

### Post by tr333 on 2009-02-15
Thanks for the info.  This is what I ended up with in my bash script:
```
trap cleanup EXIT
cleanup() {
    /bin/rm /tmp/airtunes.pid
}
echo -n "$$" > /tmp/airtunes.pid

```
and in my perl script:
```
...
use sigtrap qw(die normal-signals);

...
END {
    # grab the pid of the running airtunes script
    my $pid = `cat /tmp/airtunes.pid` || undef;
    if (defined $pid) {
        # kill any remaining JustePort processes
        # this should kill the audio-decoding processes with SIGPIPE
        system("pkill -P $pid cli");
        # kill the airtunes script process
        for my $signal (qw{TERM INT HUP KILL}) {
            last if kill $signal, $pid;
            #warn "warning: kill failed: pid=$pid, signal=$signal\n";
            sleep 1;
        }
    }
}

```

---

