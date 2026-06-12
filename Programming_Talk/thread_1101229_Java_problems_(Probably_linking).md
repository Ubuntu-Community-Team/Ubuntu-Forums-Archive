---
title: "Java problems (Probably linking)"
date: 2009-03-20
forum: Programming Talk
---

### Post by Gediminas2 on 2009-03-20
Hello everyone, It's me again.

The thing is I now need to convert my c++ project into java and I hit too many roadblocks.

Before starting conversion from the real project, I decided to do testing first. (Yes, there was one month of java lectures in the university, but that was a year ago. Can't remember anything)

I downloaded jogl libraries, got examole code from wikipedia:
```


 import javax.media.opengl.GLCanvas;
 import java.awt.Frame;
 import java.awt.event.WindowAdapter;
 import java.awt.event.WindowEvent;
 
 public class JavaDia implements Runnable {
     static Thread displayT = new Thread(new JavaDia());
     static boolean bQuit = false;
 
     public static void main(String[] args) {
         displayT.start();
     }
 
     public void run() {
         Frame frame = new Frame("Jogl 3D Shape/Rotation");
         GLCanvas canvas = new GLCanvas();
         canvas.addGLEventListener(new JavaRenderer());
         frame.add(canvas);
         frame.setSize(640, 480);
         frame.setUndecorated(true);
         int size = frame.getExtendedState();
         size |= Frame.MAXIMIZED_BOTH;
         frame.setExtendedState(size);
 
         frame.addWindowListener(new WindowAdapter() {
             public void windowClosing(WindowEvent e) {
                 bQuit = true;
             }
         });
         frame.setVisible(true);
 //      frame.show();
         canvas.requestFocus();
         while( !bQuit ) {
             canvas.display();
         }
     }
}

```

```

import javax.media.opengl.GL;
 import javax.media.opengl.GLEventListener;
 import javax.media.opengl.GLAutoDrawable;
 import javax.media.opengl.glu.GLU;
 import java.awt.event.KeyEvent;
 import java.awt.event.KeyListener;
 
 public class JavaRenderer 
 implements GLEventListener, KeyListener {
    private float rotateT = 0.0f;
    private static final GLU glu = new GLU();
 
    public void display(GLAutoDrawable gLDrawable) {
        final GL gl = gLDrawable.getGL();
        gl.glClear(GL.GL_COLOR_BUFFER_BIT);
        gl.glClear(GL.GL_DEPTH_BUFFER_BIT);
        gl.glLoadIdentity();
        gl.glTranslatef(0.0f, 0.0f, -5.0f);
 
        gl.glRotatef(rotateT, 1.0f, 0.0f, 0.0f);
        gl.glRotatef(rotateT, 0.0f, 1.0f, 0.0f);
        gl.glRotatef(rotateT, 0.0f, 0.0f, 1.0f);
        gl.glRotatef(rotateT, 0.0f, 1.0f, 0.0f);
 
        gl.glBegin(GL.GL_TRIANGLES);
 
        // Front
        gl.glColor3f(0.0f, 1.0f, 1.0f); 
        gl.glVertex3f(0.0f, 1.0f, 0.0f);
        gl.glColor3f(0.0f, 0.0f, 1.0f); 
        gl.glVertex3f(-1.0f, -1.0f, 1.0f);
        gl.glColor3f(0.0f, 0.0f, 0.0f); 
        gl.glVertex3f(1.0f, -1.0f, 1.0f);
 
        // Right Side Facing Front
        gl.glColor3f(0.0f, 1.0f, 1.0f); 
        gl.glVertex3f(0.0f, 1.0f, 0.0f);
        gl.glColor3f(0.0f, 0.0f, 1.0f); 
        gl.glVertex3f(1.0f, -1.0f, 1.0f);
        gl.glColor3f(0.0f, 0.0f, 0.0f); 
        gl.glVertex3f(0.0f, -1.0f, -1.0f);
 
        // Left Side Facing Front
        gl.glColor3f(0.0f, 1.0f, 1.0f); 
        gl.glVertex3f(0.0f, 1.0f, 0.0f);
        gl.glColor3f(0.0f, 0.0f, 1.0f); 
        gl.glVertex3f(0.0f, -1.0f, -1.0f);
        gl.glColor3f(0.0f, 0.0f, 0.0f); 
        gl.glVertex3f(-1.0f, -1.0f, 1.0f);
 
        // Bottom
        gl.glColor3f(0.0f, 0.0f, 0.0f); 
        gl.glVertex3f(-1.0f, -1.0f, 1.0f);
        gl.glColor3f(0.1f, 0.1f, 0.1f); 
        gl.glVertex3f(1.0f, -1.0f, 1.0f);
        gl.glColor3f(0.2f, 0.2f, 0.2f); 
        gl.glVertex3f(0.0f, -1.0f, -1.0f);
 
        gl.glEnd();
 
        rotateT += 0.2f;
    }
 
    public void displayChanged(GLAutoDrawable gLDrawable, 
      boolean modeChanged, boolean deviceChanged) {
    }
 
    public void init(GLAutoDrawable gLDrawable) {
        final GL gl = gLDrawable.getGL();
        gl.glShadeModel(GL.GL_SMOOTH);
        gl.glClearColor(0.0f, 0.0f, 0.0f, 0.0f);
        gl.glClearDepth(1.0f);
        gl.glEnable(GL.GL_DEPTH_TEST);
        gl.glDepthFunc(GL.GL_LEQUAL);
        gl.glHint(GL.GL_PERSPECTIVE_CORRECTION_HINT, 
        GL.GL_NICEST);
        gLDrawable.addKeyListener(this);
    }
 
    public void reshape(GLAutoDrawable gLDrawable, int x, 
    int y, int width, int height) {
        final GL gl = gLDrawable.getGL();
        if(height <= 0) {
            height = 1;
        }
        final float h = (float)width / (float)height;
        gl.glMatrixMode(GL.GL_PROJECTION);
        gl.glLoadIdentity();
        glu.gluPerspective(50.0f, h, 1.0, 1000.0);
        gl.glMatrixMode(GL.GL_MODELVIEW);
        gl.glLoadIdentity();
    }
 
    public void keyPressed(KeyEvent e) {
        if(e.getKeyCode() == KeyEvent.VK_ESCAPE) {
            JavaDia.bQuit = true;
            JavaDia.displayT = null;
            System.exit(0);
        }
    }
 
    public void keyReleased(KeyEvent e) {
    }
 
    public void keyTyped(KeyEvent e) {
    }
 }

```

I compiled it using
```

javac -cp ./lib/jogl.jar   JavaRenderer.java JavaDia.java

```

Now how do I run the thing?

"java JavaDia" tells me that it cant find jogl libraries
if I try "java -cp ./lib/jogl.jar JavaDia"
it can't find the JavaDia class.

I'm no good at java. What should I do?

---

### Post by myrtle1908 on 2009-03-20
Are you running:-

```
java -cp ./lib/jogl.jar JavaDia
```

from the directory which contains the JavaRenderer.class and JavaDia.class files?

What is the exact error when you execute the above command?

---

### Post by Gediminas2 on 2009-03-20
> **myrtle1908 said:**
> Are you running:-

```
java -cp ./lib/jogl.jar JavaDia
```

from the directory which contains the JavaRenderer.class and JavaDia.class files?

What is the exact error when you execute the above command?

i run ```
java -cp ./:./lib/jogl.jar  JavaDia
```
from where i keep the class and java files 

i get this error now:
```

$ java -cp ./:./lib/jogl.jar  JavaDia
Exception in thread "Thread-0" java.lang.NoClassDefFoundError: com/sun/gluegen/runtime/DynamicLookupHelper
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
        at javax.media.opengl.GLCanvas.chooseGraphicsConfiguration(GLCanvas.java:520)
        at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:131)
        at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:90)
        at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:83)
        at JavaDia.run(JavaDia.java:18)
        at java.lang.Thread.run(Thread.java:619)
Caused by: java.lang.ClassNotFoundException: com.sun.gluegen.runtime.DynamicLookupHelper
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
        ... 33 more

```

It seems like java hates me. And I'm not a fan of it too.

---

### Post by jespdj on 2009-03-20
You need to put more than just the current directory and jogl.jar in your classpath - you also need to put gluegen-rt.jar (which is included with JOGL) into the classpath. JOGL has instructions on what you should do exactly; lookup the instructions. (Possibly there's more you have to include that I don't remember right now).

---

### Post by myrtle1908 on 2009-03-20
> **Gediminas2 said:**
> It seems like java hates me. And I'm not a fan of it too.

Java doesn't hate you.  Like all compiled languages you must tell the compiler where required libraries reside.  Compilers cannot read minds and "guess" where these things are.

You can either tell the Java compiler where your libraries are located via a command line switch (as you have done with '-cp') or set the CLASSPATH environment variable.

---

