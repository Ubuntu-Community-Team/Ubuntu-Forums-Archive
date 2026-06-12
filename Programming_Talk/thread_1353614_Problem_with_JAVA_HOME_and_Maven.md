---
title: "Problem with JAVA_HOME and Maven"
date: 2009-12-13
forum: Programming Talk
---

### Post by partyk1d24 on 2009-12-13
Ok this one is killing me how do I change the JAVA_HOME in Maven

@BigBoy:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.16/
@BigBoy:~$ mvn --version
Apache Maven 2.2.1 (rdebian-1)
Java version: 1.6.0_16
Java home: /usr/lib/jvm/java-6-sun-1.6.0.16/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux" version: "2.6.31-16-generic" arch: "i386" Family: "unix"
@BigBoy:~$ 


This doesn't make sense why isn't it showing up correctly?

---

### Post by partyk1d24 on 2009-12-13
In case anyone comes across the same issue here is how I solved it..

first: sudo gedit /usr/bin/mvn (may be good to backup)
second: add turn this...
exec "$JAVACMD" \
  $MAVEN_OPTS \
  -classpath "${M2_HOME}"/boot/classworlds.jar \
  "-Dclassworlds.conf=${M2_HOME}/bin/m2.conf" \
  "-Dmaven.home=${M2_HOME}"  \
  ${CLASSWORLDS_LAUNCHER} $QUOTED_ARGS

into 

exec "$JAVACMD" \
  $MAVEN_OPTS \
  -classpath "${M2_HOME}"/boot/classworlds.jar \
  "-Dclassworlds.conf=${M2_HOME}/bin/m2.conf" \
  "-Dmaven.home=${M2_HOME}"  \
  **"-Djava.home=${JAVA_HOME}"** \
  ${CLASSWORLDS_LAUNCHER} $QUOTED_ARGS

---

### Post by jtuchscherer on 2009-12-13
I am not sure if I will be able to answer you. I installed maven manually because apt pulls in all these nasty dependencies (like gcj and ant).

But I think in the Ubuntu installed version the JAVA_HOME gets overwritten in the mvn shell file.
Try this:

$whereis mvn

This should tell you where the mvn file is located (like /usr/bin/mvn)

Then do:

$cat /usr/bin/mvn (or where ever you found the mvn file from step one)

Check if there is a line where JAVA_HOME gets exported. If yes, then either change it or remove it (comment it out for testing first).

I hope that helps.

---

### Post by jtuchscherer on 2009-12-13
I guess you beat me to it.

Just one note about your solution: You will still use the java executable from the jdk installation that you don't want, but all other java libs will be called from your desired jdk. That could have some weird implications.

If you want to be sure that it works, change the mvn file and export JAVA_HOME with your desired jdk.

---

### Post by partyk1d24 on 2009-12-13
Yeah it lead to a lot of complications, I have tried to remove the apptitude JDK package and am going to try and reinstall it myself. This is because the JDK has symlinks to the JRE and this throws off maven.

Jackie

---

