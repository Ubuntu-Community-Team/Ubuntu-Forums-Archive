---
title: "No such file or directory"
date: 2009-08-31
forum: Programming Talk
---

### Post by huangyingw on 2009-08-31
hello all,
   I am tring manually installation of Eclipse 3.5 on Ubuntu 9.4 32 bit, according to the guidance of [here]("http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/comment-page-1/#comment-41704").
   Following is my updated /usr/bin/eclipse file
  ```

#!/bin/bash

# Having any sort of classpath causes massive breakage, with Kaffe at least.
unset CLASSPATH; export CLASSPATH

# Allow the user to specify their own Java home, we check for it later.
#unset JAVA_HOME; export JAVA_HOME

CMDLINEARGS=""
VMARGS=""
INSTALL="/home/huangyingw/bin/packages/eclipse3.5/eclipse"
STARTUP="/usr/lib/eclipse/startup.jar"

if [ -x /usr/bin/zenity ]; then
    DIALOG=/usr/bin/zenity
    DIALOGW="$DIALOG --warning"
elif [ -x /usr/bin/kdialog ]; then
    DIALOG=/usr/bin/kdialog
    DIALOGW="$DIALOG --warningyesno"
elif [ -x /usr/bin/xdialog ]; then
    DIALOG=/usr/bin/xdialog
    DIALOGW="$DIALOG --warning"
else
    DIALOG=echo
    DIALOGW="$DIALOG"
fi


# Make sure this directory exists.
if [ ! -d ~/.eclipse ]; then
    mkdir ~/.eclipse > /dev/null 2>&1
    if [ $? -ne 0 ]; then
        $DIALOG \
            --error \
            --title="Could not launch Eclipse Platform" \
            --text="Could not create settings directory at ~/.eclipse."
    fi
fi

# Just in case Eclipse tries to put something in the home directory.
cd ~

# Load default settings from the user's configuration file.
if [ -f ~/.eclipse/eclipserc ]; then
    . ~/.eclipse/eclipserc
fi

# Process the command line options. These override the eclipserc file, so we do
# them after parsing that file.
while [ "$1" ]; do
    if [ "$1" = "-h" -o "$1" = "--help" ]; then
        echo "Eclipse Starter Script"
	echo "Usage:"
	echo "eclipse [options [value]]"
	echo "See eclipse(1) for more information."
	echo ""
	echo "Also see ~/.eclipse/eclipserc, which provides some default values"
        exit 0
    elif [ "$1" = "-vm" ]; then
        shift
        unset JAVA_HOME
        JAVACMD="$1"
        shift
    elif [ "$1" = "-install" ]; then
        shift
        INSTALL="$1"
        shift
    elif [ "$1" = "-startup" ]; then
        shift
        STARTUP="$1"
        shift
    elif [ "$1" = "-vmargs" ]; then
        shift
	while [ "$1" ]; do
		VMARGS="${VMARGS} $1"
	        shift
        done
    else
        CMDLINEARGS="${CMDLINEARGS} $1"
        shift
    fi
done

# If the user has specified a custom JAVA, we check it for validity.
# JAVA defines the virtual machine that Eclipse will use to launch itself.
if [ -n "${JAVA_HOME}" ]; then
    echo "using specified vm: ${JAVA_HOME}"
    if [ ! -x "${JAVA_HOME}/bin/java" ]; then
        $DIALOG \
            --error \
            --title="Could not launch Eclipse Platform" \
            --text="The custom VM you have chosen is not a valid executable."
        exit 1
    fi
fi

# If the user has not set JAVA_HOME, cycle through our list of compatible VM's
# and pick the first one that exists.
if [ -z "${JAVA_HOME}" -a ! -n "${JAVACMD}" ]; then
    echo "searching for compatible vm..."
    javahomelist=`cat /etc/eclipse/java_home  | grep -v '^#' | grep -v '^$' | while read line ; do echo -n $line ; echo -n ":" ; done`
    OFS="$IFS"
    IFS=":"
    for JAVA_HOME in $javahomelist ; do
        echo -n "  testing ${JAVA_HOME}..."
        if [ -x "${JAVA_HOME}/bin/java" ]; then
            export JAVA_HOME
            echo "found"
            break
        else
            echo "not found"
        fi
    done
    IFS="$OFS"
fi

# If we don't have a JAVA_HOME yet, we're doomed.
if [ -z "${JAVA_HOME}" -a ! -n "${JAVACMD}" ]; then
    $DIALOG \
        --error \
        --title="Could not launch Eclipse Platform" \
        --text="A suitable Java Virtual Machine for running the Eclipse Platform could not be located."
    exit 1
fi

# Set JAVACMD from JAVA_HOME
if [ -n "${JAVA_HOME}" -a -z "${JAVACMD}" ]; then
    JAVACMD="$JAVA_HOME/bin/java"
fi

# Set path for the Mozilla SWT binding
MOZILLA_FIVE_HOME=${MOZILLA_FIVE_HOME%*/}
if false && [ -n "$MOZILLA_FIVE_HOME" -a -e $MOZILLA_FIVE_HOME/libgtkembedmoz.so ]; then
    :
elif [ -e /usr/lib/mozilla/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/xulrunner/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
elif [ -e /usr/lib/mozilla-firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
elif [ -e /usr/lib/mozilla/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla
else
    $DIALOGW \
        --title="Integrated browser support not working" \
        --text="This Eclipse build doesn't have support for the integrated browser."
    [ $? -eq 0 ] || exit 1
fi

EXT=/usr/local/lib/eclipse/.eclipseextension
if [ ! -f $EXT ]; then
    if ! touch $EXT 2>/dev/null; then
	cat <<-EOF
	Could not create $EXT. Please run as root:
	    touch $EXT
	    chmod 2775 $EXT
	    chown root:staff $EXT
	EOF
    fi
    chmod 2775 $EXT 2> /dev/null || true
    chown root:staff $EXT 2> /dev/null || true
fi

# libraries from the mozilla choosen take precedence
LD_LIBRARY_PATH=$MOZILLA_FIVE_HOME${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}

# Do the actual launch of Eclipse with the selected VM.
exec /home/huangyingw/bin/packages/eclipse3.5/eclipse \
    -vm "${JAVACMD}" \
    -install "${INSTALL}" \
    -startup "${STARTUP}" \
    ${CMDLINEARGS} \
    -vmargs -Djava.library.path=/usr/lib/jni \
            -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db \
            -Dgnu.gcj.runtime.VMClassLoader.library_control=never \
            -Dosgi.locking=none ${VMARGS}
   
```
   However, no matter how hard I try, when I run eclipse in command line, I will alway got following error:
```

/usr/bin/eclipse: line 170: /home/huangyingw/bin/packages/eclipse3.5/eclipse: No such file or directory

```
While I am sure that this file exist, as following evidence:
```

root@eclipse:~# ls -al /home/huangyingw/bin/packages/eclipse3.5/eclipse
-rwxrwxrwx 1 huangyingw huangyingw 52932 2009-05-19 18:04 /home/huangyingw/bin/packages/eclipse3.5/eclipse

```
   What is the fault for this?

---

### Post by tyfius on 2009-08-31
Is there a reason you are doing all this?

I downloaded the PDT Eclipse ZIP from the website, but you can do the same with the regular Linux Eclipse package, extracted the ZIP file to a folder in my home directory and simple ran the eclipse executable that's in the folder. As far as I can tell everything works out of the box.

---

### Post by huangyingw on 2009-09-07
> **tyfius said:**
> Is there a reason you are doing all this?

I downloaded the PDT Eclipse ZIP from the website, but you can do the same with the regular Linux Eclipse package, extracted the ZIP file to a folder in my home directory and simple ran the eclipse executable that's in the folder. As far as I can tell everything works out of the box.
     My only reason is just want to use a latest version of eclipse.
     While, I have tried what you have describe. After unziping the eclipse file, run chmod -R 777 to grant all right. And, when I just clicking on the executable eclipse file, no response. When I execute it from terminal, only got "no such file or directory".
    I think I must have missed dependancy.
    I used to install 3.2 version of eclipse through "apt-get install eclipse", thus, the defautl java and jdk would also be installed and configured. Anything else should I do.
    Waitting for your more detailed instructions.

---

### Post by MindSz on 2009-09-07
Someone posted a similar thread a couple of weeks ago in this same forum. Try searching old threads to see if you can find it.

---

### Post by zoniq on 2009-09-29
I've the same problem. It says no such file. Are there any updates on this?

I wasn't able to locate the older thread with the similar problem.

---

