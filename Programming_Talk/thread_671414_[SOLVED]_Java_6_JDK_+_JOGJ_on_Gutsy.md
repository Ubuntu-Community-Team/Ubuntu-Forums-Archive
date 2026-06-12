---
title: "[SOLVED] Java 6 JDK + JOGJ on Gutsy"
date: 2008-01-18
forum: Programming Talk
---

### Post by tbranham on 2008-01-18
Howdy folks,

Perhaps I could get some help with this: I'm trying to get Java and JOGL up and running on my box. I've only ever dabbled in Java programming (I come from a C/C++ background generally) so it's no surprise that I'm a bit lost. Anyway, I'm having a devil of a time getting JOGL up and running on my system.

There seems to be 2 distinct camps about how to do this:
1) Unpack the files from the jogl-1.1.0-linux-i586.zip file and place the .jar's in [jre_location]/lib/ext/ and the .so's in [jre_location]/lib/i386/
(see [http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/](http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/) )
or...
2) Update the LD_LIBRARY_PATH and CLASSPATH environment variables to reflect the user-defined install path.
(see [http://cgi.cse.unsw.edu.au/~cs3421/wordpress/using-jogl/](http://cgi.cse.unsw.edu.au/~cs3421/wordpress/using-jogl/) and [http://www.cs.gmu.edu/~jchen/graphics/jogl/notes/joglSetup.html](http://www.cs.gmu.edu/~jchen/graphics/jogl/notes/joglSetup.html) )

Now, the documentation that came from [https://jogl.dev.java.net/](https://jogl.dev.java.net/) says explicitly not to place the files in the jre instillation directory. Obviously, I'm not sure what to believe. Anyway, I ended up installing the files in the JRE directories. Here's what I have now:

```
tbranham@gemini:~$ ls -l /usr/lib/jvm/java-6-sun/jre/lib/i386/
total 7200
drwxr-xr-x 2 root root    4096 2008-01-18 13:06 client
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 headless
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 jli
lrwxrwxrwx 1 root root      23 2008-01-18 12:57 jvm.cfg -> /etc/java-6-sun/jvm.cfg
-rw-r--r-- 1 root root   12462 2007-09-25 02:08 libattach.so
-rw-r--r-- 1 root root  584864 2007-09-25 02:08 libawt.so
-rw-r--r-- 1 root root  403679 2007-09-25 02:08 libcmm.so
-rw-r--r-- 1 root root  180433 2007-09-25 02:08 libdcpr.so
-rw-r--r-- 1 root root   50538 2007-09-25 02:10 libdeploy.so
-rw-r--r-- 1 root root   18694 2007-09-25 02:08 libdt_socket.so
-rw-r--r-- 1 root root  647643 2007-09-25 02:08 libfontmanager.so
-rw-r--r-- 1 root root    7319 2008-01-18 13:10 libgluegen-rt.so
-rw-r--r-- 1 root root  222057 2007-09-25 02:08 libhprof.so
-rw-r--r-- 1 root root   46135 2007-09-25 02:08 libinstrument.so
-rw-r--r-- 1 root root   19910 2007-09-25 02:08 libioser12.so
-rw-r--r-- 1 root root   39833 2007-09-25 02:08 libj2gss.so
-rw-r--r-- 1 root root   11760 2007-09-25 02:08 libj2pcsc.so
-rw-r--r-- 1 root root   66464 2007-09-25 02:08 libj2pkcs11.so
-rw-r--r-- 1 root root    6434 2007-09-25 02:08 libjaas_unix.so
-rw-r--r-- 1 root root   25431 2007-09-25 02:08 libjava_crw_demo.so
-rw-r--r-- 1 root root   80875 2007-09-25 02:10 libjavaplugin_jni.so
-rw-r--r-- 1 root root  358202 2007-09-25 02:10 libjavaplugin_nscp_gcc29.so
-rw-r--r-- 1 root root  268961 2007-09-25 02:10 libjavaplugin_nscp.so
-rw-r--r-- 1 root root  188962 2007-09-25 02:08 libjava.so
-rw-r--r-- 1 root root    5405 2007-09-25 02:08 libjawt.so
-rw-r--r-- 1 root root   71163 2007-09-25 02:08 libJdbcOdbc.so
-rw-r--r-- 1 root root  278377 2007-09-25 02:08 libjdwp.so
-rw-r--r-- 1 root root   10279 2008-01-18 13:10 libjogl_awt.so
-rw-r--r-- 1 root root  191161 2008-01-18 13:10 libjogl_cg.so
-rw-r--r-- 1 root root 1212850 2008-01-18 13:10 libjogl.so
-rw-r--r-- 1 root root  211066 2007-09-25 02:08 libjpeg.so
-rw-r--r-- 1 root root    8190 2007-09-25 02:08 libjsig.so
-rw-r--r-- 1 root root   80797 2007-09-25 02:08 libjsoundalsa.so
-rw-r--r-- 1 root root  235601 2007-09-25 02:08 libjsound.so
-rw-r--r-- 1 root root   33900 2007-09-25 02:08 libmanagement.so
-rw-r--r-- 1 root root  831403 2007-09-25 02:08 libmlib_image.so
-rw-r--r-- 1 root root    5315 2007-09-25 02:08 libnative_chmod_g.so
-rw-r--r-- 1 root root    5331 2007-09-25 02:08 libnative_chmod.so
-rw-r--r-- 1 root root   95830 2007-09-25 02:08 libnet.so
-rw-r--r-- 1 root root   37081 2007-09-25 02:08 libnio.so
-rw-r--r-- 1 root root   12931 2007-09-25 02:08 libnpt.so
lrwxrwxrwx 1 root root      31 2008-01-18 12:57 libodbcinst.so -> ../../../../../libodbcinst.so.1
lrwxrwxrwx 1 root root      27 2008-01-18 12:57 libodbc.so -> ../../../../../libodbc.so.1
-rw-r--r-- 1 root root    4902 2007-09-25 02:08 librmi.so
-rw-r--r-- 1 root root   37570 2007-09-25 02:08 libsaproc.so
-rw-r--r-- 1 root root  266365 2007-09-25 02:08 libsplashscreen.so
-rw-r--r-- 1 root root  141709 2007-09-25 02:08 libunpack.so
-rw-r--r-- 1 root root   56701 2007-09-25 02:08 libverify.so
-rw-r--r-- 1 root root   76152 2007-09-25 02:08 libzip.so
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 motif21
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 native_threads
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 server
drwxr-xr-x 2 root root    4096 2008-01-18 12:57 xawt
tbranham@gemini:~$ ls -l /usr/lib/jvm/java-6-sun/jre/lib/ext/
total 3708
-rw-r--r-- 1 root root    8241 2007-09-25 01:54 dnsns.jar
-rw-r--r-- 1 root root   17829 2008-01-18 10:19 gluegen-rt.jar
-rw-r--r-- 1 root root 1065888 2008-01-18 10:19 jogl.jar
-rw-r--r-- 1 root root    7319 2008-01-18 10:19 libgluegen-rt.so
-rw-r--r-- 1 root root   10279 2008-01-18 10:19 libjogl_awt.so
-rw-r--r-- 1 root root  191161 2008-01-18 10:19 libjogl_cg.so
-rw-r--r-- 1 root root 1212850 2008-01-18 10:19 libjogl.so
-rw-r--r-- 1 root root  837852 2007-10-03 08:56 localedata.jar
-rw-r--r-- 1 root root     429 2007-09-25 02:05 meta-index
-rw-r--r-- 1 root root  170257 2007-09-25 01:47 sunjce_provider.jar
-rw-r--r-- 1 root root  224493 2007-09-25 01:53 sunpkcs11.jar

```

OK, so here's the problem: I'm trying to compile/run the demos found here: [http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/#sourceCode](http://www.cs.umd.edu/~meesh/kmconroy/JOGLTutorial/#sourceCode)

```
tbranham@gemini:~/Desktop/code$ make go
rm -f *.class *~
javac *.java
----------
1. ERROR in CommandMediator.java (at line 23)
        import net.java.games.jogl.GL;
               ^^^
The import net cannot be resolved
----------
2. ERROR in CommandMediator.java (at line 24)
        import net.java.games.jogl.GLDrawable;
               ^^^
The import net cannot be resolved
----------
3. ERROR in CommandMediator.java (at line 25)
        import net.java.games.jogl.GLU;
               ^^^
The import net cannot be resolved
----------
4. ERROR in CommandMediator.java (at line 69)
        public void draw(GLDrawable glDrawable) {
                         ^^^^^^^^^^
GLDrawable cannot be resolved to a type
----------
5. ERROR in CommandMediator.java (at line 89)
        public void clearScreen(GLDrawable glDrawable) {
                                ^^^^^^^^^^
GLDrawable cannot be resolved to a type
----------
6. ERROR in CommandMediator.java (at line 90)
        final GL gl = glDrawable.getGL();
              ^^
GL cannot be resolved to a type
----------
7. ERROR in CommandMediator.java (at line 94)
        gl.glClear(GL.GL_COLOR_BUFFER_BIT); // clear the window
                   ^^
GL cannot be resolved
----------
8. ERROR in CommandMediator.java (at line 273)
        public void initalize(GLDrawable glDrawable) {
                              ^^^^^^^^^^
GLDrawable cannot be resolved to a type
----------
9. ERROR in CommandMediator.java (at line 274)
        final GL gl = glDrawable.getGL();
              ^^
GL cannot be resolved to a type
----------
10. ERROR in CommandMediator.java (at line 275)
        final GLU glu = glDrawable.getGLU();
              ^^^
GLU cannot be resolved to a type
----------
11. ERROR in CommandMediator.java (at line 277)
        gl.glMatrixMode(GL.GL_PROJECTION);
                        ^^
GL cannot be resolved
----------
12. ERROR in CommandMediator.java (at line 280)
        gl.glMatrixMode(GL.GL_MODELVIEW);
                        ^^
GL cannot be resolved
----------
13. ERROR in CommandMediator.java (at line 298)
        public void reshape(GLDrawable gLDrawable, int x, int y, int width,
                            ^^^^^^^^^^
GLDrawable cannot be resolved to a type
----------
14. ERROR in CommandMediator.java (at line 306)
        final GL gl = gLDrawable.getGL();
              ^^
GL cannot be resolved to a type
----------
15. ERROR in CommandMediator.java (at line 307)
        final GLU glu = gLDrawable.getGLU();
              ^^^
GLU cannot be resolved to a type
----------
----------
16. ERROR in IGLObject.java (at line 32)
        public abstract void draw(GLDrawable glDrawable);
                                  ^^^^^^^^^^
GLDrawable cannot be resolved to a type
----------
----------
17. ERROR in JoglEventMediator.java (at line 39)
        implements GLEventListener, KeyListener, MouseListener, MouseMotionListener {
                   ^^^^^^^^^^^^^^^
GLEventListener cannot be resolved to a type
----------
17 problems (17 errors)make: *** [compile] Error 255

```

Obviously, the compiler is not happy with the net.java.games.jogl path from the start. I decided to give the environment variable route a try. I placed the JOGL files in a common location and added this to my .bashrc:
```
JOGL=/usr/local/lib/jogl-1.1.0-linux-i586/lib
export CLASSPATH=${CLASSPATH}:.:$JOGL/jogl.jar:$JOGL/gluegen-rt.jar 
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$JOGL/

```

No dice.

The interesting part, however is that the demos found here: [https://jogl-demos.dev.java.net/](https://jogl-demos.dev.java.net/) all seem to work! Now I'm really confused.

Any guidance would be greatly appreciated.
-T-

---

### Post by tbranham on 2008-01-18
Hmmm, interesting. I realized that I was using the correct Java, but 'javac' was not set properly. I did a 'sudo update-alternatives --configure javac' and set it to /usr/lib/jvm/java-6-sun/bin/javac.

When I try to compile/run the demo I still get errors related to the JOGL library. Here's the output...

```
tbranham@gemini:~/Desktop/code$ make go
rm -f *.class *~
javac *.java
JoglEventMediator.java:28: package net.java.games.jogl does not exist
import net.java.games.jogl.GLCanvas;
                          ^
JoglEventMediator.java:29: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
JoglEventMediator.java:30: package net.java.games.jogl does not exist
import net.java.games.jogl.GLEventListener;
                          ^
JoglEventMediator.java:39: cannot find symbol
symbol: class GLEventListener
        implements GLEventListener, KeyListener, MouseListener, MouseMotionListener {
                   ^
JoglEventMediator.java:44: cannot find symbol
symbol  : class GLCanvas
location: class JoglEventMediator
        private GLCanvas _canvas = null;
                ^
CommandMediator.java:23: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
CommandMediator.java:24: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
CommandMediator.java:25: package net.java.games.jogl does not exist
import net.java.games.jogl.GLU;
                          ^
JoglEventMediator.java:60: cannot find symbol
symbol  : class GLCanvas
location: class JoglEventMediator
        public JoglEventMediator(GLCanvas canvas) {
                                 ^
JoglEventMediator.java:82: cannot find symbol
symbol  : class GLDrawable
location: class JoglEventMediator
        public void display(GLDrawable gLDrawable) {
                            ^
JoglEventMediator.java:120: cannot find symbol
symbol  : class GLDrawable
location: class JoglEventMediator
        public void displayChanged(GLDrawable gLDrawable, boolean modeChanged, boolean deviceChanged) {
                                   ^
JoglEventMediator.java:132: cannot find symbol
symbol  : class GLDrawable
location: class JoglEventMediator
        public void init(GLDrawable gLDrawable) {
                         ^
JoglEventMediator.java:154: cannot find symbol
symbol  : class GLDrawable
location: class JoglEventMediator
        public void reshape(GLDrawable gLDrawable, int x, int y, int width, int height) {
                            ^
CommandMediator.java:69: cannot find symbol
symbol  : class GLDrawable
location: class CommandMediator
    public void draw(GLDrawable glDrawable) {
                     ^
CommandMediator.java:89: cannot find symbol
symbol  : class GLDrawable
location: class CommandMediator
    public void clearScreen(GLDrawable glDrawable) {
                            ^
CommandMediator.java:273: cannot find symbol
symbol  : class GLDrawable
location: class CommandMediator
    public void initalize(GLDrawable glDrawable) {
                          ^
CommandMediator.java:298: cannot find symbol
symbol  : class GLDrawable
location: class CommandMediator
    public void reshape(GLDrawable gLDrawable, int x, int y, int width,
                        ^
IGLObject.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
IGLObject.java:32: cannot find symbol
symbol  : class GLDrawable
location: interface IGLObject
        public abstract void draw(GLDrawable glDrawable);
                                  ^
EmptyGLObject.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
EmptyGLObject.java:40: cannot find symbol
symbol  : class GLDrawable
location: class EmptyGLObject
    public void draw(GLDrawable glDrawable) {
                     ^
GLMatrixLoader.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
GLMatrixLoader.java:21: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
GLMatrixLoader.java:49: cannot find symbol
symbol  : class GLDrawable
location: class GLMatrixLoader
    public void draw(GLDrawable glDrawable) {
                     ^
GLRectangle2D.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
GLRectangle2D.java:21: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
GLRectangle2D.java:48: cannot find symbol
symbol  : class GLDrawable
location: class GLRectangle2D
    public void draw(GLDrawable glDrawable) {
                     ^
GLRotate2D.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
GLRotate2D.java:21: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
GLRotate2D.java:65: cannot find symbol
symbol  : class GLDrawable
location: class GLRotate2D
    public void draw(GLDrawable glDrawable) {
                     ^
GLTranslate2D.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
GLTranslate2D.java:21: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
GLTranslate2D.java:73: cannot find symbol
symbol  : class GLDrawable
location: class GLTranslate2D
    public void draw(GLDrawable glDrawable) {
                     ^
GLTriangleEqil2D.java:20: package net.java.games.jogl does not exist
import net.java.games.jogl.GL;
                          ^
GLTriangleEqil2D.java:21: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawable;
                          ^
GLTriangleEqil2D.java:47: cannot find symbol
symbol  : class GLDrawable
location: class GLTriangleEqil2D
    public void draw(GLDrawable glDrawable) {
                     ^
HelloWorldWindow.java:25: package net.java.games.jogl does not exist
import net.java.games.jogl.GLCanvas;
                          ^
HelloWorldWindow.java:26: package net.java.games.jogl does not exist
import net.java.games.jogl.GLCapabilities;
                          ^
HelloWorldWindow.java:27: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawableFactory;
                          ^
MainWindow.java:27: package net.java.games.jogl does not exist
import net.java.games.jogl.GLCanvas;
                          ^
MainWindow.java:28: package net.java.games.jogl does not exist
import net.java.games.jogl.GLCapabilities;
                          ^
MainWindow.java:29: package net.java.games.jogl does not exist
import net.java.games.jogl.GLDrawableFactory;
                          ^
CommandMediator.java:90: cannot find symbol
symbol  : class GL
location: class CommandMediator
        final GL gl = glDrawable.getGL();
              ^
CommandMediator.java:94: cannot find symbol
symbol  : variable GL
location: class CommandMediator
        gl.glClear(GL.GL_COLOR_BUFFER_BIT); // clear the window
                   ^
CommandMediator.java:274: cannot find symbol
symbol  : class GL
location: class CommandMediator
        final GL gl = glDrawable.getGL();
              ^
CommandMediator.java:275: cannot find symbol
symbol  : class GLU
location: class CommandMediator
        final GLU glu = glDrawable.getGLU();
              ^
CommandMediator.java:277: cannot find symbol
symbol  : variable GL
location: class CommandMediator
        gl.glMatrixMode(GL.GL_PROJECTION);
                        ^
CommandMediator.java:280: cannot find symbol
symbol  : variable GL
location: class CommandMediator
        gl.glMatrixMode(GL.GL_MODELVIEW);
                        ^
CommandMediator.java:306: cannot find symbol
symbol  : class GL
location: class CommandMediator
        final GL gl = gLDrawable.getGL();
              ^
CommandMediator.java:307: cannot find symbol
symbol  : class GLU
location: class CommandMediator
        final GLU glu = gLDrawable.getGLU();
              ^
GLMatrixLoader.java:50: cannot find symbol
symbol  : class GL
location: class GLMatrixLoader
        final GL gl = glDrawable.getGL();
              ^
GLRectangle2D.java:49: cannot find symbol
symbol  : class GL
location: class GLRectangle2D
        final GL gl = glDrawable.getGL();
              ^
GLRotate2D.java:66: cannot find symbol
symbol  : class GL
location: class GLRotate2D
        final GL gl = glDrawable.getGL();
              ^
GLTranslate2D.java:74: cannot find symbol
symbol  : class GL
location: class GLTranslate2D
        final GL gl = glDrawable.getGL();
              ^
GLTriangleEqil2D.java:48: cannot find symbol
symbol  : class GL
location: class GLTriangleEqil2D
        final GL gl = glDrawable.getGL();
              ^
GLTriangleEqil2D.java:69: cannot find symbol
symbol  : variable GL
location: class GLTriangleEqil2D
        gl.glBegin(GL.GL_POLYGON); // draw it
                   ^
HelloWorldWindow.java:45: cannot find symbol
symbol  : class GLCanvas
location: class HelloWorldWindow
        GLCanvas canvas = GLDrawableFactory.getFactory()
        ^
HelloWorldWindow.java:46: cannot find symbol
symbol  : class GLCapabilities
location: class HelloWorldWindow
                        .createGLCanvas(new GLCapabilities());
                                            ^
HelloWorldWindow.java:45: cannot find symbol
symbol  : variable GLDrawableFactory
location: class HelloWorldWindow
        GLCanvas canvas = GLDrawableFactory.getFactory()
                          ^
MainWindow.java:48: cannot find symbol
symbol  : class GLCanvas
location: class MainWindow
                GLCanvas canvas = GLDrawableFactory.getFactory().createGLCanvas(new GLCapabilities());
                ^
MainWindow.java:48: cannot find symbol
symbol  : class GLCapabilities
location: class MainWindow
                GLCanvas canvas = GLDrawableFactory.getFactory().createGLCanvas(new GLCapabilities());
                                                                                    ^
MainWindow.java:48: cannot find symbol
symbol  : variable GLDrawableFactory
location: class MainWindow
                GLCanvas canvas = GLDrawableFactory.getFactory().createGLCanvas(new GLCapabilities());
                                  ^
Note: Some input files use or override a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
62 errors
make: *** [compile] Error 1

```

So, I'm still stuck...

---

### Post by tbranham on 2008-01-18
OK, I found this: [http://pepijn.fab4.be/software/nehe-java-ports/](http://pepijn.fab4.be/software/nehe-java-ports/)

Specifically... 
> net.java.games.jogl is the package name that was used by jogl. Jogl was used as the basis for the reference implementation of jsr-231. This api uses the javax.media.opengl package name. As far as I know the old jogl is not being developed anymore and has been replaced by jsr-231. Unfortunately the new api has retained the jogl name, which might be a bit confusing. You can find more details at [https://jogl.games.dev.java.net](https://jogl.games.dev.java.net).

For questions related to the correct usage of these apis I recommend you check out the Java Gaming forums at [http://www.javagaming.org](http://www.javagaming.org). There is a forum dedicated to jogl there.


That took care of it. Apparently, the demo I was using before was old. I was able to successfully compile and run another demo.

I guess we really do learn something new every day :)

Thanks,
T

---

