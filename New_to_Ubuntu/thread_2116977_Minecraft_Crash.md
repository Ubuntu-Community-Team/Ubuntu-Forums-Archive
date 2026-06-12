---
title: "Minecraft Crash"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Sennah on 2013-02-17
This is my first Lunix OS; one of the first things I tried to do was install minecraft.  
When I try to launch minecraft, I get the attached error.

If there's more info that I didn't provide, let me know.

---

### Post by ubudog on 2013-02-17
Welcome to the forums!

What's your graphics card?

Have you installed any drivers for it?

---

### Post by Sennah on 2013-02-17
Aha.

I didn't think about that.

I'll give it a shot and see if it works.

---

### Post by Sennah on 2013-02-25
updated drivers, re-installed java, did a rain dance, still doesn't work.

this is the error I'm getting in the terminal, when I run this command:

-Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame



Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/ryan/.minecraft/bin/natives/liblwjgl.so: /home/ryan/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at net.minecraft.client.Minecraft.F(SourceFile:1976)
	at asz.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:75)
	at asq.<init>(SourceFile:38)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:38)
	at net.minecraft.Launcher.replace(Launcher.java:136)
	at net.minecraft.Launcher$1.run(Launcher.java:79)

---

### Post by ubudog on 2013-02-26
Ok, looks like the graphics issues have been solved.  Now it appears you're missing lwjgl.  You can download lwjgl from their site [here]("http://www.lwjgl.org/download.php").

I'd recommend getting the stable version.  Unzip it in your .minecraft/bin/ directory.

Regards,
ubudog

---

