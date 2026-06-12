---
title: "Java/ati driver related problem with minecraft please help"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by auroraa9420 on 2012-04-07
okay i made a post yesterday and i was sure someone will answer it somewhere in December 2013 so il make another post related with the same problem

and also iv done some reaserch and people say its probably related with ATI drivers not being compatible completely with minecraft linux and also i dont whant to play a game that has native linux support with wine

the error message is this:




pghg022@pghg:~$ java -jar MinecraftSP.jar
Hello!
URL: file:/home/pghg022/.minecraft/bin/lwjgl.jar
URL: file:/home/pghg022/.minecraft/bin/jinput.jar
URL: file:/home/pghg022/.minecraft/bin/lwjgl_util.jar
URL: file:/home/pghg022/.minecraft/bin/minecraft.jar
URL: file:/home/pghg022/.minecraft/bin/linux_natives.jar
27 achievements
182 recipes
Setting user: , 12345
LWJGL Version: 2.4.2
Loading: net.java.games.input.LinuxEnvironmentPlugin
Linux plugin claims to have found 5 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb77dc424, pid=4735, tid=1519385456
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/pghg022/hs_err_pid4735.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted

---

### Post by auroraa9420 on 2012-04-07
dump

---

### Post by auroraa9420 on 2012-04-07
does anybody have a solution

i have OpenJDK 6,7 and Suns Java platform and all of them seems to have the same error

---

### Post by Mark Phelps on 2012-04-07
Have a little patience!  Three posts in a few hours is unreasonable.

We are volunteers here, and we're not sitting around just waiting for you to post.

The forum standard is bumping only once every 24 hours.  Please observe that in the future.

---

### Post by maniaq on 2012-06-13
bump

---

### Post by afixane on 2012-06-13
Try to open ~/hs_err_pid4735.log and post the result here

---

