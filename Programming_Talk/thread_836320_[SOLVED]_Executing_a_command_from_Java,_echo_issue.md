---
title: "[SOLVED] Executing a command from Java, echo issue"
date: 2008-06-21
forum: Programming Talk
---

### Post by Diabolis on 2008-06-21
I am writing an application in Java and it needs to execute some commands. This is the code that I am using:

[PHP]private static String executeCommand(String[] cmdLine) {
                String output = "";
                try {
                    Process p = Runtime.getRuntime().exec(cmdLine);
                    BufferedReader input = new BufferedReader(new InputStreamReader(p.getInputStream()));
                    String line;
                    while ((line = input.readLine()) != null) {
                        output += (line + '\n');
                    }
                    input.close();
                } catch(IOException ex) {
                    System.out.println(ex.getStackTrace());
                }
                return output;
        }[/PHP]

The code seems to work fine. I've been running other programs with it from my Java application.

Now my program needs to identify the home folder of the user that is running the application, so I tried the following:

[PHP]String[] command = {"echo","$HOME"};
CMDExecuter.executeCommand(command);[/PHP]

The problem is that the output always is **$HOME** instead of something like this **/home/userX**. Anyone knows another way to get the path of the home folder or why the "echo" command is not working?

---

### Post by xlinuks on 2008-06-21
```

System.getProperty( "user.home" );

```
should do the trick.

---

### Post by xlinuks on 2008-06-21
If you're interested, here's the full list of the system properties for Java 1.5, I created this list a long ago as a reference for the sys props for Java 5 (the values are for my particular computer, the point is to give you a hint what the values might look like), to the left of "=" are the keys, to the right - the values:
#Wed Dec 05 20:58:19 EET 2007
```

java.runtime.name=Java(TM) 2 Runtime Environment, Standard Edition
sun.boot.library.path=/home/fox/apps/jdk1.5.0_14/jre/lib/i386
java.vm.version=1.5.0_14-b03
java.vm.vendor=Sun Microsystems Inc.
java.vendor.url=http\://java.sun.com/
path.separator=\:
java.vm.name=Java HotSpot(TM) Client VM
file.encoding.pkg=sun.io
sun.java.launcher=SUN_STANDARD
user.country=US
sun.os.patch.level=unknown
java.vm.specification.name=Java Virtual Machine Specification
user.dir=/home/fox/dev/java/bin
java.runtime.version=1.5.0_14-b03
java.awt.graphicsenv=sun.awt.X11GraphicsEnvironment
java.endorsed.dirs=/home/fox/apps/jdk1.5.0_14/jre/lib/endorsed
os.arch=i386
java.io.tmpdir=/tmp
line.separator=\n
java.vm.specification.vendor=Sun Microsystems Inc.
os.name=Linux
sun.jnu.encoding=UTF-8
java.library.path=/home/fox/apps/jdk1.5.0_14/jre/lib/i386/client\:/home/fox/apps/jdk1.5.0_14/jre/lib/i386\:/home/fox/apps/jdk1.5.0_14/jre/../lib/i386
java.specification.name=Java Platform API Specification
java.class.version=49.0
sun.management.compiler=HotSpot Client Compiler
os.version=2.6.22-14-generic
user.home=/home/fox
user.timezone=Europe/Bucharest
java.awt.printerjob=sun.print.PSPrinterJob
file.encoding=UTF-8
java.specification.version=1.5
java.class.path=.
user.name=fox
java.vm.specification.version=1.0
java.home=/home/fox/apps/jdk1.5.0_14/jre
sun.arch.data.model=32
user.language=en
java.specification.vendor=Sun Microsystems Inc.
java.vm.info=mixed mode, sharing
java.version=1.5.0_14
java.ext.dirs=/home/fox/apps/jdk1.5.0_14/jre/lib/ext
sun.boot.class.path=/home/fox/apps/jdk1.5.0_14/jre/lib/rt.jar\:/home/fox/apps/jdk1.5.0_14/jre/lib/i18n.jar\:/home/fox/apps/jdk1.5.0_14/jre/lib/sunrsasign.jar\:/home/fox/apps/jdk1.5.0_14/jre/lib/jsse.jar\:/home/fox/apps/jdk1.5.0_14/jre/lib/jce.jar\:/home/fox/apps/jdk1.5.0_14/jre/lib/charsets.jar\:/home/fox/apps/jdk1.5.0_14/jre/classes
java.vendor=Sun Microsystems Inc.
file.separator=/
java.vendor.url.bug=http\://java.sun.com/cgi-bin/bugreport.cgi
sun.io.unicode.encoding=UnicodeLittle
sun.cpu.endian=little
sun.desktop=gnome
sun.cpu.isalist=

```

---

### Post by NormR2 on 2008-06-21
What command could you call from java (as above) to list what environment variables are set in the context that the command is being executed in?

Something like:
String[] command = {"env"};

Seeing what is set from the above, might help a user to set any environment variables by putting his env vars in the same place as those that he sees displayed by the above.

---

### Post by Diabolis on 2008-06-21
> **xlinuks said:**
> ```

System.getProperty( "user.home" );

```
should do the trick.

Yeah this works, thank you. However, I still wonder why echo does not work. As far as I know that would be the only way to get the values from other environment variables (values that you couldn't get with the keys that you posted).

---

### Post by lloyd_b on 2008-06-21
> **Diabolis said:**
> Yeah this works, thank you. However, I still wonder why echo does not work. As far as I know that would be the only way to get the values from other environment variables (values that you couldn't get with the keys that you posted).
Just a guess, but I'd say it's because it's executing the "echo" command directly, instead of using a shell.  It's the shell that translates the $HOME into /home/userX.

As a test, try with the arguments "sh" "-c echo $HOME" and see if it gives you the desired results.

---

### Post by Diabolis on 2008-06-21
> **lloyd_b said:**
> 
As a test, try with the arguments "sh" "-c echo $HOME" and see if it gives you the desired results.

Yep, you are right. It worked with this:
[PHP]String[] command = {"sh","-c","echo $HOME"};
CMDExecuter.executeCommand(command);[/PHP]

Note: I had to separate the "-c".

---

