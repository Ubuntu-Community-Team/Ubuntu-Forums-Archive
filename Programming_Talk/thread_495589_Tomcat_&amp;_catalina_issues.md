---
title: "Tomcat &amp; catalina issues"
date: 2007-07-08
forum: Programming Talk
---

### Post by aliov_85 on 2007-07-08
Hello every body.

When I try to start up the tomcat server by doing:

> /usr/local/tomcat/bin$ sh catalina.sh , I get this message:

> The BASEDIR environment variable is not defined correctly
This environment variable is needed to run this program

here is the "setclasspath.bat" content which may help you:

rem ---------------------------------------------------------------------------

rem Set CLASSPATH and Java options

rem

rem $Id: setclasspath.bat 355227 2005-12-08 21:44:16Z keith $

rem ---------------------------------------------------------------------------



rem Make sure prerequisite environment variables are set

if not "%JAVA_HOME%" == "" goto gotJdkHome

if not "%JRE_HOME%" == "" goto gotJreHome

echo Neither the JAVA_HOME nor the JRE_HOME environment variable is defined

echo At least one of these environment variable is needed to run this program

goto exit



:gotJreHome

if not exist "%JRE_HOME%\bin\java.exe" goto noJavaHome

if not exist "%JRE_HOME%\bin\javaw.exe" goto noJavaHome

if not ""%1"" == ""debug"" goto okJavaHome

echo JAVA_HOME should point to a JDK in order to run in debug mode.

goto exit



:gotJdkHome

if not exist "%JAVA_HOME%\bin\java.exe" goto noJavaHome

if not exist "%JAVA_HOME%\bin\javaw.exe" goto noJavaHome

if not exist "%JAVA_HOME%\bin\jdb.exe" goto noJavaHome

if not exist "%JAVA_HOME%\bin\javac.exe" goto noJavaHome

if not "%JRE_HOME%" == "" goto okJavaHome

set JRE_HOME=%JAVA_HOME%

goto okJavaHome



:noJavaHome

echo The JAVA_HOME environment variable is not defined correctly

echo This environment variable is needed to run this program

echo NB: JAVA_HOME should point to a JDK not a JRE

goto exit

:okJavaHome



if not "%BASEDIR%" == "" goto gotBasedir

echo The BASEDIR environment variable is not defined

echo This environment variable is needed to run this program

goto exit

:gotBasedir

if exist "%BASEDIR%\bin\setclasspath.bat" goto okBasedir

echo The BASEDIR environment variable is not defined correctly

echo This environment variable is needed to run this program

goto exit

:okBasedir



rem Set the default -Djava.endorsed.dirs argument

set JAVA_ENDORSED_DIRS=%BASEDIR%\common\endorsed



rem Set standard CLASSPATH

rem Note that there are no quotes as we do not want to introduce random

rem quotes into the CLASSPATH

set CLASSPATH=%JAVA_HOME%\lib\tools.jar



rem Set standard command for invoking Java.

rem Note that NT requires a window name argument when using start.

rem Also note the quoting as JAVA_HOME may contain spaces.

set _RUNJAVA="%JRE_HOME%\bin\java"

set _RUNJAVAW="%JRE_HOME%\bin\javaw"

set _RUNJDB="%JAVA_HOME%\bin\jdb"

set _RUNJAVAC="%JAVA_HOME%\bin\javac"



goto end



:exit

exit /b 1



:end




Can any body help me please?

---

### Post by jespdj on 2007-07-08
"setclasspath.bat" is a batch file for Windows. Why are you posting this, are you trying to start Tomcat on Linux with a Windows batch file? :confused:

The error message says you have to set the environment variable BASEDIR. Set it to the Tomcat installation directory, for example:

export BASEDIR=/usr/local/tomcat

---

### Post by AlexThomson_NZ on 2007-07-08
I'm not convinced you need to specify a BASEDIR variable- it is created in catalina.sh, and is not listed at the top in the variable pre-requisites (and I have never had to use it either).

I suspect there might be something else going on here

---

### Post by Ahbun on 2008-04-26
I encounter the same issue.
To solve it, make sure the $CATALINA_HOME and $JAVA_HOME are both set properly.

Then enable the following shell scripts as executable under $CATALINA_HOME\bin:

   chmod +x ./setclasspath.sh
   chmod +x ./startup.sh
   chmod +x ./shutdown.sh

It works in my case.

---

### Post by klimat on 2013-01-26
Thank you, Ahbun. It solves the same problem of mine.

---

