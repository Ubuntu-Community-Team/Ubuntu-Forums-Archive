---
title: "bash script convert /dev/tcp to use netcat or other"
date: 2008-04-02
forum: Programming Talk
---

### Post by wcoolnet on 2008-04-02
I found a script on this forum that checks http response times and orders the list fastest to slowest. The problem is the script uses the bash /dev/tcp function which has been disabled in ubuntu and also debian. 
Can anyone help me rewrite it to use something like netcat, curl or other? I am willing to pay for it if I have to. :(
Or maybe someone can point me to a different script? 
```
#!/bin/bash
# ffmirror.sh - http://grulos.blogspot.com
# find fastest mirror (?!?)
# give it a list of hosts and it will sort them
# according to their response time
# no switches (ATM) just ./ffmirror<mirrors.txt
# www.foo.org or http://www.foo.org or
# http://foo.org/page or ...

trap 'printf "\ncaught signal\nGot only ${#slist[@]}\n" &&
  printf "%s\n" "${slist[@]}" && exit 1' 2

while read line; do
  # get host & page
  line=${line/[hH][tT][tT][pP]:\/\//}
  [ "${line#*\/}" == "$line" ] && page="/" || page="/${line#*\/}"
  host="${line%%\/*}"

  # connect to host
  exec 3<>/dev/tcp/$host/80

  # b-a to get time difference.
  # could have used date +%s%N
  # I guess this won't work on a BSD
  a=$(</proc/uptime)
  a=${a%%\ *}
  a=${a/./}

 # send a GET request and read 1st line of response
 printf "GET $page HTTP/1.1\nHost: $host\n\n">&3 &&
   read -u 3 -t 2 -a response &&  exec 3>&- &&
     b=$(</proc/uptime) &&
       b=${b%%\ *} &&
         b=${b/./}

  # printf "%06s%04s%s\n" "$((b-a))0ms ${response[1]} $host"

  # try next if not connected within 2s
  [ $((b-a)) -lt 0 ] && continue

  # this is my lazy sort algorithm (c)
  c=$(((b-a)*100))
  until [ "${slist[$c]}" == "" ]; do
    ((c++))
  done
  slist[$c]="$((b-a))0ms http://$host$page"

  exec 3>&-

done

printf "%s\n" "${slist[@]}"

```
or check original thread : [http://ubuntuforums.org/showthread.php?t=331126](http://ubuntuforums.org/showthread.php?t=331126)

---

### Post by wcoolnet on 2008-04-03
can anyone recommend a good freelance broker website where I could find someone to do this for me?

---

### Post by nanotube on 2008-04-03
why not just use wget... here's a version of the script with all the /dev/tcp stuff ripped out and replaced with a wget:

```

#!/bin/bash
# ffmirror.sh - http://grulos.blogspot.com
# find fastest mirror (?!?)
# give it a list of hosts and it will sort them
# according to their response time
# no switches (ATM) just ./ffmirror<mirrors.txt
# www.foo.org or http://www.foo.org or
# http://foo.org/page or ...

trap 'printf "\ncaught signal\nGot only ${#slist[@]}\n" &&
  printf "%s\n" "${slist[@]}" && exit 1' 2

while read line; do

  # b-a to get time difference.
  # could have used date +%s%N
  # I guess this won't work on a BSD
  a=$(</proc/uptime)
  a=${a%%\ *}
  a=${a/./}

  # wget stuff
  wget --spider -q -O /dev/null $line &&
     b=$(</proc/uptime) &&
       b=${b%%\ *} &&
         b=${b/./}

  # printf "%06s%04s%s\n" "$((b-a))0ms ${response[1]} $host"

  # try next if not connected within 2s
  [ $((b-a)) -lt 0 ] && continue

  # this is my lazy sort algorithm (c)
  c=$(((b-a)*100))
  until [ "${slist[$c]}" == "" ]; do
    ((c++))
  done
  slist[$c]="$((b-a))0ms $line"

done

printf "%s\n" "${slist[@]}"

```

tested to work fine, behold:
```
$ echo -e "http://google.com\nhttp://www.mozilla.org" | bash ./ffmirror.sh
310ms http://google.com
590ms http://www.mozilla.org
```

enjoy! :)

edit: added the --spider option to wget, to avoid actually downloading any files.

edit2: and if you really feel the need to give someone money for this... just donate something to ubuntu. :)

---

