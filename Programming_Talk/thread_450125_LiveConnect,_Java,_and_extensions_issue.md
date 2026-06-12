---
title: "LiveConnect, Java, and extensions issue"
date: 2007-05-21
forum: Programming Talk
---

### Post by metalnemesis on 2007-05-21
Hello,

I am having a problem getting extensions to work with the Sun JVM  installed from the repositories. Currently, whenever I try to load a class using the javascript Packages object, I get an error like the following:

Packages.org.xmldb.api.DatabaseManager is not a constructor

The extensions I'm trying to use are JAR files distributed with the Exist XML database product that were copied into the jre/lib/ext directory. The JVM extension mechanism simply doesn't seem to work and can't load any classes from any JAR files (including Sun's own extensions) in the extensions directory. This same application works fine with 2000/XP (where I originally wrote it).

According to Sun's documentation, the extensions mechanism is a standard facility within the JVM. There are no documented ways to "turn it off" other than to set the java.ext.dirs system variable to an empty string.

This is what I've tried so far:

1. Launching Firefox from root on the off-chance that it's a permissions issue. Didn't work. Same error.
2. Checked the permissions of the ext directory and each jar file and they are all as expected: root: all access, everyone else: read.
3. From the java console I've verified that the java.ext.dirs system variable points to the jre/lib/ext directory. It does.
4. Tried adding the jars to the classpath. No change.
5. Tried loading a Sun class, sun.net.spi.nameservice.dns.DNSNameService, contained in the dnsns.jar supplied by Sun. Same error,
7. Tried loading a standard java class from rt.jar, java.lang.string("Hello World") and display the java string with alert(). That worked. Hello World pops up in a dialog box. From this I know that LIveConnect is working, that it is able to communicate with the JVM, and that the JVM is responding correctly and returning the correct object.

At this point I'm stumped. This all works smooth as silk on Win2000 and XP. I am using the same extension JAR files as I do on Windows, the same version of the JVM and plugin, 1.5.0.11-b03, the same version of Firefox, 2.0.0.3 (I use Firefox as my default browser on XP as well), and the same javascript code (I'm actually running it directly from a FAT32 partition so I;m literally using the same file that I use on Windows, not a copy). In short, my Windows and Ubuntu setups are identical, yet none of the installed extensions can be loaded when running Ubuntu and everything works fine on Windows.

One other note. In order for this to work properly I have to modify the java.policy file to allow global unrestricted access, so my java.policy file looks like this:

// default permissions granted to all domains

grant { 
        permission java.security.AllPermission;
};

So the normal restrictions imposed by the standard policy file for javascript do not apply. I obviously do not use this policy file when doing general surfing and use a script to switch the unrestricted and standard policy files back and forth depending on what I'm doing.

I realize that Exist, my custom web app, and the Sun JVM are not official Ubuntu software and therefore, not officially supported. But if anyone else has had problems with extensions that work on Windows but not on Ubuntu and have a fix or workaround, I'd really appreciate your help!

If I can get this app to work, I can FINALLY start using Ubuntu as my everyday desktop and relegate Windows to the "once in a while when I need to" desktop. Thanks in advance for your help!

---

### Post by brettz9 on 2007-08-09
This may be totally unrelated, and I'm new to Java, not to mention LiveConnect, so please forgive me if I'm off base but...

I've been working to get Berkeley DB XML into Firefox, and have basically succeeded (with the exception of try-catch blocks not seeming to work on Java exceptions--any help on this would be appreciated).

You can see the latest at:
[http://forums.oracle.com/forums/thread.jspa?messageID=1995559](http://forums.oracle.com/forums/thread.jspa?messageID=1995559)

Anyhow, what got things working for me was using the following in a global context (otherwise one can only call the extension once without it failing):

var fURL = new Array();
fURL[0] = new java.net.URL("file:///C:/Berkeley DB XML/jar/dbxml.jar");
fURL[1] = new java.net.URL("file:///C:/Berkeley DB XML/jar/db.jar");
loader = new java.net.URLClassLoader(fURL);

and putting the DLL files into the C:\Program Files\Mozilla Firefox directory. (I'd incidentally like to know how to get these DLL files instead bundled with the extensions directory (or somehow referenced in the script though java.lang.System.load() did not seem to work) as well as bundle the .java.policy file somehow so that Firefox will recognize it and so that the user of the extension won't need to copy it...

Hope this helps, and I'd appreciate any help on the above if anybody knows, too...

thanks,
Brett

---

### Post by brettz9 on 2007-08-09
And in case it wasn't clear, I'm using Windows currently, so I don't know about how it may be different for Linux unfortunately... :(

---

### Post by brettz9 on 2007-08-10
Ok, by putting the DLL's into the components folder and deleting compreg.dat and xpti.dat, I was able to get Firefox to recognize the files (even though I'm not using the files for my own XPCOM component).

---

