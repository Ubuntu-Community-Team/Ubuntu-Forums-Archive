---
title: "Apparently I have a invisible typo"
date: 2013-04-29
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-04-29
I have been over the code a dozen or so times and i don't see why i am getting a error
```
 cat -n script 
     1    #!/bin/sh
     2    # This script is for installing from a recovery console where you can't copy/paste
     3    if [ "$USER" = "root" ];then
     4        echo "Do not run me as root\nYou can run me using this:\n\tsudo -u userNameOtherThanRoot $(basename $0)"
     5        exit
     6    fi
     7    cd /tmp
     8    zip="Ubuntu-Mainline-Kernel-Updater.zip"
     9    url="//github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater"
    10    if [ -f "/usr/bin/git" ];then
    11        git clone "git:$url"
    12    elif [ -f "/usr/bin/wget" ];then
    13        wget "https://$url/archive/master.zip" -O "$zip"
    14    elif [ -f "/usr/bin/curl" ];then
    15        curl "https://$url/archive/master.zip" > "$zip"
    16    else
    17        echo "You need to install git, curl, or wget to run this script"
    18        exit
    19    fi
    20    if [ -f "/tmp/$zip" ];then
    21        unzip "$zip"
    22        bash Ubuntu-Mainline-Kernel-Updater-master/install
    23    else
    24        bash Ubuntu-Mainline-Kernel-Updater/install
    25    fi
    26    KernelUpdateChecker -no-rc
chad@A54C-NB91:/tmp$ sh script 
script: 12: script: Syntax error: "elif" unexpected (expecting "then")

```

---

### Post by Vaphell on 2013-04-29
are you sure you don't have some \r there attached to **then** which makes shell not recognize that **then** as a keyword?

```
$ eval $'*if [ 1 ];then echo a; elif true; then echo b; else echo c; fi*'
a
$ eval $'*if [ 1 ];then[COLOR="#0000CD"]\r[/COLOR] echo a; elif true; then echo b; else echo c; fi*'
bash: syntax error near unexpected token `elif'
```

---

### Post by schragge on 2013-04-29
+1
*cat -v* will display non-printing characters as ^C. Also, try to execute the script with *bash script* as bash' error messages usually better comprehensible.

---

### Post by pqwoerituytrueiwoq on 2013-04-29
see anything now? i don't
```
$ cat script -nv
     1    #!/bin/sh^M
     2    # This script is for installing from a recovery console where you can't copy/paste^M
     3    if [ "$USER" = "root" ];then^M
     4        echo "Do not run me as root\nYou can run me using this:\n\tsudo -u userNameOtherThanRoot $(basename $0)"^M
     5        exit^M
     6    fi^M
     7    cd /tmp^M
     8    zip="Ubuntu-Mainline-Kernel-Updater.zip"^M
     9    url="//github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater"^M
    10    if [ -f "/usr/bin/git" ];then^M
    11        git clone "git:$url"^M
    12    elif [ -f "/usr/bin/wget" ];then^M
    13        wget "https://$url/archive/master.zip" -O "$zip"^M
    14    elif [ -f "/usr/bin/curl" ];then^M
    15        curl "https://$url/archive/master.zip" > "$zip"^M
    16    else^M
    17        echo "You need to install git, curl, or wget to run this script"^M
    18        exit^M
    19    fi^M
    20    if [ -f "/tmp/$zip" ];then^M
    21        unzip "$zip"^M
    22        bash Ubuntu-Mainline-Kernel-Updater-master/install^M
    23    else^M
    24        bash Ubuntu-Mainline-Kernel-Updater/install^M
    25    fi^M
    26    KernelUpdateChecker -no-rc^M
```

---

### Post by steeldriver on 2013-04-29
yeah all those ^M characters are Windows-style carriage returns - you need to strip them all off e.g.

```
tr -d $'\r' < script > newscript
```

---

### Post by Vaphell on 2013-04-29
proof:
```
$ cat -v <( echo $'abc\r' )
abc^M
```

---

### Post by pqwoerituytrueiwoq on 2013-04-29
Guess I cant host a script on pastebin.com and download the raw script and it work... guess they use a windows server...

---

### Post by cortman on 2013-04-29
You probably already have tried this, but it can be useful to run the script with the debugging flag:

```
bash -x myscript.sh
```

---

### Post by linuxonbute on 2013-04-30
What if you zipped it up before uploading and get the user to unzip it after they download it?

---

### Post by pqwoerituytrueiwoq on 2013-04-30
i just used the tr command to patch the download in the [readme file](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

### Post by Vaphell on 2013-04-30
you can shorten wget approach like this
```
wget http://pastebin.com/raw.php?i=5UBBzzky -O- | tr -d '\r' > script
```

---

