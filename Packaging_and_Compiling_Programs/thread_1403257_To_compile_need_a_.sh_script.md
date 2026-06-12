---
title: "To compile need a .sh script"
date: 2010-02-10
forum: Packaging and Compiling Programs
---

### Post by fabis94 on 2010-02-10
So can anyone please convert a .bat file to a .sh file?

Here it is:

```
@ECHO OFF

SET cc=javac
SET cflags=
SET src=src
SET lib=lib
SET res=resources
SET out=bin

CALL Clean.bat 2>NUL
CALL "%res%\FindJDK.bat"

SET lstf=temp.txt
SET rsjar=%lib%\rs.jar
SET rs=%rsjar%!
SET imgdir=%res%\images
SET manifest=%res%\Manifest.txt
SET versionfile=%res%\version.txt
FOR /F %%G IN (%versionfile%) DO SET version=%%G
SET scripts=scripts
SET dist=RSBot-%version%.jar
SET full=1

IF "%1"=="/S" (
	SET full=0
	GOTO :scripts
)

ECHO Compiling bot
IF EXIST "%lstf%" DEL /F /Q "%lstf%"
FOR /F "usebackq tokens=*" %%G IN (`DIR /B /S "%src%\*.java"`) DO CALL :append "%%G"
IF EXIST "%out%" RMDIR /S /Q "%out%" > NUL
MKDIR "%out%"
"%cc%" %cflags% -d "%out%" "@%lstf%"
DEL /F /Q "%lstf%"

:scripts
ECHO Compiling scripts
ECHO. > "%scripts%\.class"
DEL /F /Q "%scripts%\*.class" > NUL
"%cc%" %cflags% -cp "%out%" %scripts%\*.java
IF "%full%"=="0" GOTO :end

ECHO Packing JAR

IF EXIST "%dist%" DEL /F /Q "%dist%"
IF EXIST "%lstf%" DEL /F /Q "%lstf%"
COPY "%manifest%" "%lstf%"
ECHO Specification-Version: "%version%" >> "%lstf%"
ECHO Implementation-Version: "%version%" >> "%lstf%"

IF EXIST "%rs%" RMDIR /S /Q "%rs%"
MKDIR "%rs%"
SET xcd=%CD%
CD "%rs%"
jar xf "%xcd%\%rsjar%"
CD "%xcd%"

jar cfm "%dist%" "%lstf%" -C "%out%" . %scripts%\*.class "%rs%" "%versionfile%" %imgdir%\*.png %res%\*.bat %res%\*.sh
RMDIR /S /Q "%rs%"
DEL /F /Q "%lstf%"

:end
ECHO Compilation successful.
GOTO :eof

:append
SET gx=%1
SET gx=%gx:\=\\%
ECHO %gx% >> %lstf%
GOTO :eof

```

---

### Post by gmargo on 2010-02-10
Here's a translation into a shell script.  Completely untested of course.  I wasn't sure what the ":append" function is doing, so you'll have to fix that.  See attached file.  In the future you'll probably want to move this into a makefile.

---

