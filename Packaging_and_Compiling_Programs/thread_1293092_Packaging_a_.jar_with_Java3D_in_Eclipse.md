---
title: "Packaging a .jar with Java3D in Eclipse"
date: 2009-10-16
forum: Packaging and Compiling Programs
---

### Post by JCoster on 2009-10-16
Right, i'm stumped.
Attempting to package a jar in Eclipse with a program which uses the Java3D file, and I can't seem to export the J3D libraries with it successfully.
Whenever I attempt to run it on a machine where J3D is not natively installed it throws errors saying that it's not installed. However, am I right in thinking that if I package the libraries with it then there should be no problem?
When exporting, I choose to 'Package required libraries into generated JAR' and as such the libraries end up in the root of the exported .jar file.
I don't really understand build-paths and as such I think this may be where I'm going wrong?
I imported the libraries to the Java Build Path and my 'JARs and class folders on the build path:' read as follows:
- j3dcore.jar
- j3dutils.jar
- vecmath.jar
- JRE System Library
..and the jars are imported externally from '/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/amd64'.
The jar runs perfectly on this machine (which obviously has j3d libs installed) but attempting to run it on Windows without it just throws errors.
Any help is greatly appreciated,
JC

---

### Post by JCoster on 2009-10-18
Sorry, but bump!

---

### Post by nullmind on 2009-10-18
1.) How are you running the JAR on Windows? If you're not using a .bat file or something to set the native directory it probably won't work.

2.) Do you have your native libs outside of your JAR? Without a special loader they can't be in the JAR IIRC.

3.) Are you using System.loadLibrary or System.load ? The former lets you specify the exact shared library file (.so or .dll), whereas the loadLibrary picks one IIRC.

---

### Post by JCoster on 2009-10-19
I'm attempting to launch it from command line with:
```
java.exe -jar ProjectName
```

This works fine with a "HelloWorld" example, so it's just a case of getting the libraries to load as I've programmed it to throw an error when the libraries can't be found and print a message in the console.

I've told Eclipse to package the Java3D libs in with the jar file.

As for the System.loadLibrary part, I'm not using either...  I've just configured the project build-path to contain the libraries?

Thanks for your help in advance.

---

