---
title: "Why doesn't my function go through all of it's steps?"
date: 2013-03-25
forum: Programming Talk
---

### Post by Enkouyami on 2013-03-25
Why doesn't the CheckJavas function go through all of it's steps? ```
#-------------------#
#   Java Checking   #
#-------------------#
CheckJavas() { # Here, this script will attempt to check for Java by checking to see if installation folders are present.
echo -n "Checking for Java"
echo ""
echo "Looking for Sun Java 6"
if [ -e /usr/lib/jvm/java-6-sun ] && [ -e /usr/lib/jvm/java-6-sun/bin ] && [ -e /usr/lib/jvm/java-6-sun/bin/java ]; then
    echo "Sun Java 6 is installed!"
    echo ""
else
    echo "Sun Java 6 is NOT installed"
    echo ""
fi
echo -n "Looking for Oracle Java 7"
if [ -e /usr/lib/jvm/java-7-oracle ] && [ -e /usr/lib/jvm/java-7-oracle/bin ] && [ -e /usr/lib/jvm/java-7-oracle/bin/java ]; then
    echo "${txtcyn}Oracle Java 7 is installed"
    echo ""
else
    echo "Oracle Java 7 is NOT installed"
    echo ""
fi
echo -n "Looking for OpenJDK 6"
if [ -e /usr/lib/jvm/java-6-openjdk-common ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre/lib ]; then
    echo "OpenJDK 6 is installed"
    echo ""
else
    echo "OpenJDK 7 is NOT installed"
    echo ""
fi
echo -n "Looking for OpenJDK 7"
if [ -e /usr/lib/jvm/java-7-openjdk-common ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre/lib ]; then
    echo "OpenJDK 7 is installed"
    echo ""
else
    echo "OpenJDK 7 is NOT installed"
    echo ""
fi
echo "${txtylw}Detected java folders:"
ls /usr/lib/jvm/
echo "Default java client detected:"
java -version
echo ""
ls /usr/lib/jvm/
} ## END CheckJavas
CheckJavas

```

In in full script, those problems existed. When I cut the script into  just the faulty function and ran it, the Detected java folders output  came after the Default java client detected. I fixed that then pasted in  back into my script and everything works. Here is what I should have done:
```
#-------------------#
#   Java Checking   #
#-------------------#
CheckJavas() { # Here, this script will attempt to check for Java by checking to see if installation folders are present.
echo "Checking for Java"
echo ""
echo "Looking for Sun Java 6"
if [ -e /usr/lib/jvm/java-6-sun ] && [ -e /usr/lib/jvm/java-6-sun/bin ] && [ -e /usr/lib/jvm/java-6-sun/bin/java ]
then
    echo "Sun Java 6 is installed!"
    echo ""
else
    echo "Sun Java 6 is NOT installed"
    echo ""
fi
echo -n "Looking for Oracle Java 7"
if [ -e /usr/lib/jvm/java-7-oracle ] && [ -e /usr/lib/jvm/java-7-oracle/bin ] && [ -e /usr/lib/jvm/java-7-oracle/bin/java ]
then
    echo "Oracle Java 7 is installed"
    echo ""
else
    echo "Oracle Java 7 is NOT installed"
    echo ""
fi
echo -n "Looking for OpenJDK 6"
if [ -e /usr/lib/jvm/java-6-openjdk-common ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre/lib ]
then
    echo "OpenJDK 6 is installed"
    echo ""
else
    echo "OpenJDK 7 is NOT installed"
    echo ""
fi
echo -n "Looking for OpenJDK 7"
if [ -e /usr/lib/jvm/java-7-openjdk-common ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre/lib ]
then
    echo "OpenJDK 7 is installed"
    echo ""
else
    echo "OpenJDK 7 is NOT installed"
    echo ""
fi
echo "Detected java folders:"
ls /usr/lib/jvm/
echo ""
echo "Default java client detected:"
java -version
} ## END CheckJavas
CheckJavas
```

---

### Post by schragge on 2013-03-26
> **Enkouyami said:**
> ```

if [ -e /usr/lib/jvm/java-6-sun ] && [ -e /usr/lib/jvm/java-6-sun/bin ] && [ -e /usr/lib/jvm/java-6-sun/bin/java ]; then

```Wouldn't the last check be enough? It can succeed only if all directories on the path leading to java binary exist.

---

