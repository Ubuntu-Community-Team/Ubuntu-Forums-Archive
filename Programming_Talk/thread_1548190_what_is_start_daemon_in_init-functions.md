---
title: "what is start_daemon in init-functions"
date: 2010-08-07
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-07
I am trying to understand this section from
/lib/lsb/init-functions
I have read the man page of start-stop-daemon

```
start_daemon () {
    local force nice pidfile exec i
    force=0
    nice=0
    pidfile=/dev/null

```I am not clear with the use of local force above are they here variables or nice etc is pointing to the nice command.
```

    OPTIND=1
    while getopts fn:p: opt ; do

```here getopts fn:p: opt;
use of while loop in such a way what is it doing.

```

        case "$opt" in
            f)  force=1;;
            n)  nice="$OPTARG";;
            p)  pidfile="$OPTARG";;
        esac
    done

```clear about above part

```

    shift $(($OPTIND - 1))
    if [ "$1" = '--' ]; then
        shift
    fi

```Not clear with this part.
```

    exec="$1"; shift

    if [ $force = 1 ]; then
        /sbin/start-stop-daemon --start --nicelevel $nice --quiet --startas $exec --pidfile /dev/null --oknodo -- "$@"
    elif [ $pidfile ]; then
        /sbin/start-stop-daemon --start --nicelevel $nice --quiet --exec $exec --oknodo --pidfile "$pidfile" -- "$@"
    else
        /sbin/start-stop-daemon --start --nicelevel $nice --quiet --exec $exec --oknodo -- "$@"
    fi
}
```how is start-stop-daemon used here and why so many arguments are passed on to it.
How are the nice values decided here in this script ?
For any process who decided what will be the nice value of process.

---

