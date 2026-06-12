---
title: "Could not reserve enough space for object heap etc"
date: 2012-01-29
forum: Programming Talk
---

### Post by Daveth on 2012-01-29
Hi.
In desperation and despite trawling the web for ages, I have been unable to fix this issue. I have a programme called LightZone which runs in /opt and which has its own bundled JRE. It is launched by a shell script and used to run just fine. I have 5.9gb of physical memory and the system purs along only using about 14% of that most of the time. The shell script has within it, this:

#!/bin/bash
#
# Find the amount of physical memory, divide that number by two, and use the
# result to append a Java heap limit option to the install4j environment
# variable that determines VM options.
#
# If the physical memory exceeds 4GB, then cap the Java heap limit at its
# intrinsic limit of 2GB.  (GB figures are rounded down, to accomodate slop
# in how linux counts memory and how Java fails near its limit.)

totalmem=`cat /proc/meminfo | grep MemTotal | sed -r 's/.* ([0-9]+) .*/\1/'`
fourGB=4000000
twoGB=2000000
if [ $totalmem -ge $fourGB ]; then
  maxmem=$twoGB
else
  maxmem=$(( $totalmem / 2 ))
fi
option=-Xmx${maxmem}k


I did install a virtual machine a way back just to play with, so do not know if that somehow reset some parameters, but I no longer have it. I have deleted and re-installed LightZone several times now, deleted various config files in /home, and poked about in just about anywhere where a solution might hide.
Can anyone walk me through how you reset java heaps, in simple terms? Or, given that I will move from Lucid to Pangolin in a few months, tell me if that will sort it? Sorry if this is wrong forum, just seemed a bit heavy for "beginner"!

---

### Post by Tony Flury on 2012-01-31
Is it just me or does your script just do a calculation, and not actually change any options.

```

option=-Xmx${maxmem}k

```
Just sets a bash script variable (it appears to be an command line options string for another program), but the actual variable is never used anywhere (or even echo'd).

Is part of your script missing ?

---

### Post by Bodsda on 2012-01-31
Someone should really tell those LightZone developers that they can grep the contents of a file without cat'ing it.

---

### Post by ofnuts on 2012-01-31
> **Daveth said:**
> Hi.
In desperation and despite trawling the web for ages, I have been unable to fix this issue. I have a programme called LightZone which runs in /opt and which has its own bundled JRE. It is launched by a shell script and used to run just fine. I have 5.9gb of physical memory and the system purs along only using about 14% of that most of the time. The shell script has within it, this:

#!/bin/bash
#
# Find the amount of physical memory, divide that number by two, and use the
# result to append a Java heap limit option to the install4j environment
# variable that determines VM options.
#
# If the physical memory exceeds 4GB, then cap the Java heap limit at its
# intrinsic limit of 2GB.  (GB figures are rounded down, to accomodate slop
# in how linux counts memory and how Java fails near its limit.)

totalmem=`cat /proc/meminfo | grep MemTotal | sed -r 's/.* ([0-9]+) .*/\1/'`
fourGB=4000000
twoGB=2000000
if [ $totalmem -ge $fourGB ]; then
  maxmem=$twoGB
else
  maxmem=$(( $totalmem / 2 ))
fi
option=-Xmx${maxmem}k


I did install a virtual machine a way back just to play with, so do not know if that somehow reset some parameters, but I no longer have it. I have deleted and re-installed LightZone several times now, deleted various config files in /home, and poked about in just about anywhere where a solution might hide.
Can anyone walk me through how you reset java heaps, in simple terms? Or, given that I will move from Lucid to Pangolin in a few months, tell me if that will sort it? Sorry if this is wrong forum, just seemed a bit heavy for "beginner"!

Seems to work for me. Issue
```

ps -eaf | grep java

```
to get the command line arguments and see if the JVM is indeed started with "-Xmx2000000k". But "-Xmx" sets a maximum, nothing says tat the code will require all that memory...

---

### Post by Daveth on 2012-01-31
Ok, so when i run that code I get

davy     11899 11877  0 22:42 pts/0    00:00:00 grep java

which means absolutely nothing to me. I did not include all of the shell script that came with LightZone, only the bit that i thought referred to memory. So, in case I have got that wrong, the full thing is here appended (sorry for the length!). Hope this means more to you than it does to me, and thanks in advance for your insights.
David

#! /bin/sh

# Uncomment the following line to override the JVM search sequence
# INSTALL4J_JAVA_HOME_OVERRIDE=
# Uncomment the following line to add additional VM parameters
# INSTALL4J_ADD_VM_PARAMS=

read_db_entry() {
  if [ -n "$INSTALL4J_NO_DB" ]; then
    return 1
  fi
  db_file=$HOME/.install4j
  if [ ! -f "$db_file" ]; then
    return 1
  fi
  if [ ! -x "$java_exc" ]; then
    return 1
  fi
  found=1
  exec 7< $db_file
  while read r_type r_dir r_ver_major r_ver_minor r_ver_micro r_ver_patch<&7; do
    if [ "$r_type" = "JRE_VERSION" ]; then
      if [ "$r_dir" = "$test_dir" ]; then
        ver_major=$r_ver_major
        ver_minor=$r_ver_minor
        ver_micro=$r_ver_micro
        ver_patch=$r_ver_patch
        found=0
        break
      fi
    fi
  done
  exec 7<&-

  return $found
}

create_db_entry() {
  tested_jvm=true
  echo testing JVM in $test_dir ...
  version_output=`"$bin_dir/java" -version 2>&1`
  is_gcj=`expr "$version_output" : '.*libgcj'`
  if [ "$is_gcj" = "0" ]; then
    java_version=`expr "$version_output" : '.*"\(.*\)".*'`
    ver_major=`expr "$java_version" : '\([0-9][0-9]*\)\..*'`
    ver_minor=`expr "$java_version" : '[0-9][0-9]*\.\([0-9][0-9]*\)\..*'`
    ver_micro=`expr "$java_version" : '[0-9][0-9]*\.[0-9][0-9]*\.\([0-9][0-9]*\).*'`
    ver_patch=`expr "$java_version" : '.*_\(.*\)'`
  fi
  if [ "$ver_patch" = "" ]; then
    ver_patch=0
  fi
  if [ -n "$INSTALL4J_NO_DB" ]; then
    return
  fi
  db_new_file=${db_file}_new
  if [ -f "$db_file" ]; then
    awk '$1 != "'"$test_dir"'" {print $0}' $db_file > $db_new_file
    rm $db_file
    mv $db_new_file $db_file
  fi
  dir_escaped=`echo "$test_dir" | sed -e 's/ /\\\\ /g'`
  echo "JRE_VERSION	$dir_escaped	$ver_major	$ver_minor	$ver_micro	$ver_patch" >> $db_file
}

test_jvm() {
  tested_jvm=na
  test_dir=$1
  bin_dir=$test_dir/bin
  java_exc=$bin_dir/java
  if [ -z "$test_dir" ] || [ ! -d "$bin_dir" ] || [ ! -f "$java_exc" ] || [ ! -x "$java_exc" ]; then
    return
  fi

  tested_jvm=false
  read_db_entry || create_db_entry

  if [ "$ver_major" = "" ]; then
    return;
  fi
  if [ "$ver_major" -lt "1" ]; then
    return;
  elif [ "$ver_major" -eq "1" ]; then
    if [ "$ver_minor" -lt "6" ]; then
      return;
    fi
  fi

  if [ "$ver_major" = "" ]; then
    return;
  fi
  app_java_home=$test_dir
}

add_class_path() {
  if [ -n "$1" ] && [ `expr "$1" : '.*\*'` -eq "0" ]; then
    local_classpath="$local_classpath${local_classpath:+:}$1"
  fi
}

old_pwd=`pwd`

progname=`basename "$0"`
linkdir=`dirname "$0"`

cd "$linkdir"
prg="$progname"

while [ -h "$prg" ] ; do
  ls=`ls -ld "$prg"`
  link=`expr "$ls" : '.*-> \(.*\)$'`
  if expr "$link" : '.*/.*' > /dev/null; then
    prg="$link"
  else
    prg="`dirname $prg`/$link"
  fi
done

prg_dir=`dirname "$prg"`
cd "$prg_dir"
prg_dir=`pwd`
app_home=.
cd "$app_home"
app_home=`pwd`
bundled_jre_home="$app_home/jre"

cd "$old_pwd"


if [ -f "$bundled_jre_home/lib/rt.jar.pack" ]; then
  old_pwd200=`pwd`
  cd "$bundled_jre_home"
  echo "Preparing JRE ..."
  jar_files="lib/rt.jar lib/charsets.jar lib/plugin.jar lib/deploy.jar lib/ext/localedata.jar lib/jsse.jar"
  for jar_file in $jar_files
  do
    if [ -f "${jar_file}.pack" ]; then
      bin/unpack200 -r ${jar_file}.pack $jar_file

      if [ $? -ne 0 ]; then
        echo "Error unpacking jar files. Aborting."
        echo "You might need administrative priviledges for this operation."
exit 1
      fi
    fi
  done
  cd "$old_pwd200"
fi
if [ -z "$app_java_home" ]; then
  test_jvm $INSTALL4J_JAVA_HOME_OVERRIDE
fi

if [ -z "$app_java_home" ]; then
if [ -f "$app_home/.install4j/pref_jre.cfg" ]; then
    read file_jvm_home < "$app_home/.install4j/pref_jre.cfg"
    test_jvm "$file_jvm_home"
    if [ -z "$app_java_home" ] && [ $tested_jvm = "false" ]; then
        rm $HOME/.install4j
        test_jvm "$file_jvm_home"
    fi
fi
fi

if [ -z "$app_java_home" ]; then
  test_jvm "$app_home/jre"
  if [ -z "$app_java_home" ] && [ $tested_jvm = "false" ]; then
    rm $HOME/.install4j
    test_jvm "$app_home/jre"
  fi
fi

if [ -z "$app_java_home" ]; then
  path_java=`which java 2> /dev/null`
  path_java_home=`expr "$path_java" : '\(.*\)/bin/java$'`
  test_jvm $path_java_home
fi


if [ -z "$app_java_home" ]; then
  common_jvm_locations="/opt/i4j_jres/* /usr/local/i4j_jres/* /usr/bin/java* /usr/bin/jdk* /usr/bin/jre* /usr/bin/j2*re* /usr/bin/j2sdk* /usr/java* /usr/jdk* /usr/jre* /usr/j2*re* /usr/j2sdk* /usr/java/j2*re* /usr/java/j2sdk* /usr/java/jdk* /usr/java/jre* /usr/lib/java/jre /usr/local/java* /usr/local/jdk* /usr/local/jre* /usr/local/j2*re* /usr/local/j2sdk* /usr/lib/java* /usr/lib/jdk* /usr/lib/jre* /usr/lib/j2*re* /usr/lib/j2sdk*"
  for current_location in $common_jvm_locations
  do
if [ -z "$app_java_home" ]; then
  test_jvm $current_location
fi

  done
fi

if [ -z "$app_java_home" ]; then
  test_jvm $JAVA_HOME
fi

if [ -z "$app_java_home" ]; then
  test_jvm $JDK_HOME
fi

if [ -z "$app_java_home" ]; then
  test_jvm $INSTALL4J_JAVA_HOME
fi

if [ -z "$app_java_home" ]; then
if [ -f "$app_home/.install4j/inst_jre.cfg" ]; then
    read file_jvm_home < "$app_home/.install4j/inst_jre.cfg"
    test_jvm "$file_jvm_home"
    if [ -z "$app_java_home" ] && [ $tested_jvm = "false" ]; then
        rm $HOME/.install4j
        test_jvm "$file_jvm_home"
    fi
fi
fi

if [ -z "$app_java_home" ]; then
  echo No suitable Java Virtual Machine could be found on your system.
  echo The version of the JVM must be at least 1.6.
  echo Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
  echo You can also try to delete the JVM cache file $HOME/.install4j
exit 83
fi



vmoptions_val=""
vmoptions_file="$prg_dir/$progname.vmoptions"
if [ -r "$vmoptions_file" ]; then
  exec 8< "$vmoptions_file"
  while read cur_option<&8; do
    is_comment=`expr "$cur_option" : ' *#.*'`
    if [ "$is_comment" = "0" ]; then 
      vmoptions_val="$vmoptions_val $cur_option"
    fi
  done
  exec 8<&-
fi
INSTALL4J_ADD_VM_PARAMS="$INSTALL4J_ADD_VM_PARAMS $vmoptions_val"

local_classpath=""
add_class_path "$app_home/.install4j/i4jruntime.jar"
for i in `ls "$app_home/." | egrep "\.(jar$|zip$)"`
do
  add_class_path "$app_home/./$i"
done

LD_LIBRARY_PATH="$app_home/.:$LD_LIBRARY_PATH"
DYLD_LIBRARY_PATH="$app_home/.:$DYLD_LIBRARY_PATH"
SHLIB_PATH="$app_home/.:$SHLIB_PATH"
LIBPATH="$app_home/.:$LIBPATH"
LD_LIBRARYN32_PATH="$app_home/.:$LD_LIBRARYN32_PATH"
LD_LIBRARYN64_PATH="$app_home/.:$LD_LIBRARYN64_PATH"
export LD_LIBRARY_PATH
export DYLD_LIBRARY_PATH
export SHLIB_PATH
export LIBPATH
export LD_LIBRARYN32_PATH
export LD_LIBRARYN64_PATH

#!/bin/bash
#
# Find the amount of physical memory, divide that number by two, and use the
# result to append a Java heap limit option to the install4j environment
# variable that determines VM options.
#
# If the physical memory exceeds 4GB, then cap the Java heap limit at its
# intrinsic limit of 2GB.  (GB figures are rounded down, to accomodate slop
# in how linux counts memory and how Java fails near its limit.)

totalmem=`cat /proc/meminfo | grep MemTotal | sed -r 's/.* ([0-9]+) .*/\1/'`
fourGB=4000000
twoGB=2000000
if [ $totalmem -ge $fourGB ]; then
  maxmem=$twoGB
else
  maxmem=$(( $totalmem / 2 ))
fi
option=-Xmx${maxmem}k

INSTALL4J_ADD_VM_PARAMS="$INSTALL4J_ADD_VM_PARAMS $option"

"$app_java_home/bin/java" -client -Dinstall4j.jvmDir="$app_java_home" -Dinstall4j.appDir="$app_home"  -Dexe4j.moduleName="$prg_dir/$prg" -Dcom.lightcrafts.licensetype=ESD $INSTALL4J_ADD_VM_PARAMS -classpath "$local_classpath" com.install4j.runtime.Launcher launch com.lightcrafts.platform.linux.LinuxLauncher true false "$prg_dir/LightZone.log" "$prg_dir/LightZone.log" false  true false "" true true -1 -1 "" 20 20 "Arial" "0,0,0" 8 500 "" 20 40 "Arial" "0,0,0" 8 500 -1  "$@"


exit $?$test_dir

---

### Post by ofnuts on 2012-02-01
> **Daveth said:**
> Ok, so when i run that code I get

davy     11899 11877  0 22:42 pts/0    00:00:00 grep java

which means absolutely nothing to me.

Do this when lightzone is running and this should show you the whole java command that started lightzone.

---

### Post by Daveth on 2012-02-02
thanks for the come back, but I can no longer run LightZone as it runs entirely in java and it cannot form the heap to run it. Everytime I try it either stalls at the "cannot form heap" statement in the terminal, or the terminal flashes by so quickly and crashes out I have never known what it says.
Can anyone tell me, instead, if wiping Lucid out and installing Pangolin over the top will sort this?

---

### Post by ofnuts on 2012-02-02
> **Daveth said:**
> thanks for the come back, but I can no longer run LightZone as it runs entirely in java and it cannot form the heap to run it. Everytime I try it either stalls at the "cannot form heap" statement in the terminal, or the terminal flashes by so quickly and crashes out I have never known what it says.
Can anyone tell me, instead, if wiping Lucid out and installing Pangolin over the top will sort this?
Hardly... have you asked the LightZone people?

You can also edit the script to execute
```

**echo** "$app_java_home/bin/java" ...

```
instead of 
```

"$app_java_home/bin/java" ...

```
and then invoke it in a terminal and see the command it would execute.

---

### Post by Daveth on 2012-02-02
thanks. added that but it flashed by so fast in the terminal I could not see what it said. Did not launch LightZone whatever though.
Sadly, the company stopped trading (without telling their customers either!), and though there is a bit of a community forming around it, I thought I would try here first. There is a bit of a move to see if it could be open-sourced, though the Linux-side developer now works for Apple.

---

### Post by pbrane on 2012-02-02
This is the command line to run the app (from the end of the script)
```

"$app_java_home/bin/java" -client -Dinstall4j.jvmDir="$app_java_home" -Dinstall4j.appDir="$app_home" -Dexe4j.moduleName="$prg_dir/$prg" -Dcom.lightcrafts.licensetype=ESD $INSTALL4J_ADD_VM_PARAMS -classpath "$local_classpath" com.install4j.runtime.Launcher launch com.lightcrafts.platform.linux.LinuxLauncher true false "$prg_dir/LightZone.log" "$prg_dir/LightZone.log" false true false "" true true -1 -1 "" 20 20 "Arial" "0,0,0" 8 500 "" 20 40 "Arial" "0,0,0" 8 500 -1 "$@"

```

You'd think if it was a java app you could just run it with a normal java command like
```

java -Xms1G -Xmx2G -cp com.install4j.runtime.Launcher launch com.lightcrafts.platform.linux.LinuxLauncher

```
but what they are doing looks way too complicated.

EDIT: after looking at this script is looks like you should be able to use Oracle java, the script searches for java using an array of search paths.

---

### Post by ofnuts on 2012-02-02
> **Daveth said:**
> thanks. added that but it flashed by so fast in the terminal I could not see what it said. Did not launch LightZone whatever though.
It was not meant to launch it, but to list the command. Did you start the script from a terminal session? The output should have remained on the terminal.

---

### Post by Daveth on 2012-02-03
sorry, my error- it gives this after launching the shell script in terminal
/opt/LightZone/jre/bin/java -client -Dinstall4j.jvmDir=/opt/LightZone/jre -Dinstall4j.appDir=/opt/LightZone -Dexe4j.moduleName=/opt/LightZone/LightZone -Dcom.lightcrafts.licensetype=ESD -Xmx2000000k -classpath /opt/LightZone/.install4j/i4jruntime.jar:/opt/LightZone/./jh.jar:/opt/LightZone/./lcjai.jar:/opt/LightZone/./lightcrafts.jar:/opt/LightZone/./lightcrafts-linux.jar:/opt/LightZone/./lightzonehelp.jar:/opt/LightZone/./mlibwrapper_jai.jar:/opt/LightZone/./script-api.jar:/opt/LightZone/./substance-lite.jar com.install4j.runtime.Launcher launch com.lightcrafts.platform.linux.LinuxLauncher true false /opt/LightZone/LightZone.log /opt/LightZone/LightZone.log false true false  true true -1 -1  20 20 Arial 0,0,0 8 500  20 40 Arial 0,0,0 8 500 -1 ps -eaf

I see the -Xmx2000000k section is present!! 
Where next then?

---

### Post by ofnuts on 2012-02-04
If I start a java process with -Xmx2000000k, my process monitor shows it with a virtual memory size slighly over  2G but with a real memory of 31M.  Maybe your problem isn't memory related, and it's something else that prevent LZ to reach a stage where it would use memory.

You can also edit the script to hardcode some intermediate values (1G, 512M) to see if that improves things.

---

### Post by phillips321 on 2012-05-31
I'm have the same issues as well.

Kubuntu 12.04 64bit

[http://lightzombie.org/node/113#comment-306]("http://lightzombie.org/node/113#comment-306")

---

