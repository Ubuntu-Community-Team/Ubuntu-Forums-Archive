---
title: "OpenGL java libs under Eclipse?"
date: 2009-09-25
forum: Programming Talk
---

### Post by Ferrat on 2009-09-25
Well been trying to install OpenGL java libs and using them in Eclipse but can't seem to find one workable guide on how to do this? 

I got lastest Eclipse and it's working fine, got the android SDK installed under it without any problems but now that I want to do a normal java app I need it to use OpenGL. 

I downloaded the jogl natives and gluegen and I can see them in the java build paths, I can import some of the libs under them but not opengl for some reason? :S 

Could someone point me to a guide or maybe tell me what I'm missing?? really annoying, feels like I'm missing a lib or two or something but can't find any documentation that seems fairly uptodate about how to do this?

---

### Post by geirha on 2009-09-26
Have you tried this one? [http://timelessname.com/jogl/lesson01/](http://timelessname.com/jogl/lesson01/)

---

### Post by Ferrat on 2009-09-26
Thanks that worked, is there any way to make jogl part of the standard libs? So I don't have to do it everytime?

---

### Post by Ferrat on 2009-09-27
Ok trying to compile it and I get this error 

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: 
no gluegen-rt in java.library.path
```

tried a few fixes I've found but still get the same error :(

---

### Post by Ferrat on 2009-09-27
ok, gotten past the first error now at least, had to use a newer "unstable" build, but now I get another error ```
Exception in thread "main" java.lang.NoClassDefFoundError:
 javax/media/nativewindow/Capabilities
```

anyone?

---

### Post by myrtle1908 on 2009-09-27
In Java, whenever you receive "java.lang.NoClassDefFoundError" in a stack trace it is because the java runtime/compiler cannot find a particular class.  In your case it cannot find the "javax/media/nativewindow/Capabilities" class.  You need to ensure you have this class in your build/run path.  This class is most likely part of a JAR file you are missing ... perhaps try [www.findjar.com](www.findjar.com)

---

### Post by Ferrat on 2009-09-27
thanks a lot, relativly new to Java but should be relativly straight forward to locate and link it :)

---

### Post by Ferrat on 2009-09-27
Ok, got passed that and a few similar once, how ever now I get stuck with this? 

```
Exception in thread "main" java.lang.ExceptionInInitializerError

Caused by: javax.media.opengl.GLException: No profile available: [GL2, GL2ES2, GL2ES1, GLES2, GLES1, GL2GL3, GL3]
```

```
		Color bgColor = new Color(220,220,220);
		
		GLProfile profile = GLProfile.get(GLProfile.GL2);

		GLCapabilities capabilities = new GLCapabilities(profile);		

		[COLOR="Red"]GLCanvas canvas = new GLCanvas(capabilities); [/COLOR]
		canvas.setBackground(bgColor);
```
That's the code part that is giving me the finger ^^ 
I've had a look around and can't really find the the class in any of the jogl, gluegen-rt, nativewindow or newt jars and they seem to be the only jars provided from the jogl homepage :( 

How ever it imports ok and so on and the breakpoint (in Eclipse) is the line in red, also the debugger can't locate the source for GLProfile.class.

Ideas? 
Will keep trying but setting this up seems harder than actually doing something in opengl ^^
GLProfile
EDIT:
It seems to indicate that the problem is in line 750 of GLProfile but since I don't seem to have the source I can't really say what that line does

EDIT2:
Found that GLProfile was missing from their build, the nightly had it

---

