---
title: "Bash options within a function"
date: 2010-10-15
forum: Programming Talk
---

### Post by paulsp on 2010-10-15
I just started looking around in bash and options to tweak it. Absolutely interesting! But I am stuck at the following. The idea is that you type "apache" and get the option list. This works fine. But I also want - alternatively - to be able to type "apache Start" and right away run the command listed under the Start option. Is this possible?

```
function apache
{
 OPTIONS="Start Stop Restart Status"
           select opt in $OPTIONS; do
               if [ "$opt" = "Start" ]; then
                sudo /etc/init.d/apache2 start
                return
               elif [ "$opt" = "Stop" ]; then
                sudo /etc/init.d/apache2 stop
        return
        elif [ "$opt" = "Restart" ]; then
                sudo /etc/init.d/apache2 restart
        return
        elif [ "$opt" = "Status" ]; then
                sudo /etc/init.d/apache2 status
        return
        else
                echo "Sorry, not valid"
               fi
           done
}
```

---

### Post by gmargo on 2010-10-16
Typically one would use a **case** statement for this.  Here's an example (uses standard shell syntax and only echoes for demonstration purposes):

```

#!/bin/sh

apache()
{
    case $1 in
        Start)
            echo "Start"
            ;;
        Stop)
            echo "Stop"
            ;;
        Restart)
            echo "Restart"
            ;;
        Status)
            echo "Status"
            ;;
        *)
            echo "Invalid: specify Start, Stop, Restart, or Status"
            ;;
    esac
}

apache
apache "Start"
apache Status

```Output:
```

$ sh ap.sh
Invalid: specify Start, Stop, Restart, or Status
Start
Status

```

---

### Post by paulsp on 2010-10-16
Thanks, I will try this out! The idea is that if there is no action specified, that the options come into place. So something like:

```
apache()
{
    case $1 in
        Start)
                sudo /etc/init.d/apache2 start
            ;;
        Stop)
                sudo /etc/init.d/apache2 stop
            ;;
        Restart)
                sudo /etc/init.d/apache2 restart
            ;;
        Status)
                sudo /etc/init.d/apache2 status
            ;;
        *)
             OPTIONS="Start Stop Restart Status"
           select opt in $OPTIONS; do
               if [ "$opt" = "Start" ]; then
                sudo /etc/init.d/apache2 start
                return
               elif [ "$opt" = "Stop" ]; then
                sudo /etc/init.d/apache2 stop
        return
        elif [ "$opt" = "Restart" ]; then
                sudo /etc/init.d/apache2 restart
        return
        elif [ "$opt" = "Status" ]; then
                sudo /etc/init.d/apache2 status
        return
        else
                echo "Sorry, not valid"
               fi
           done

            ;;
    esac
}


```

I am not using an Ubuntu machine so I will try this later.

---

