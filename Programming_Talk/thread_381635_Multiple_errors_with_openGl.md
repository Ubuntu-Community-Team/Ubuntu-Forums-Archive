---
title: "Multiple errors with openGl"
date: 2007-03-11
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-11
Hi, I was looking into openGL program for a bit of fun, and found the following site [http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)
and proceeded to apt-get everything and then testing. 

I ran the test SDl test program, nothing came up (No errors or anything else, which is what's supposed to happen (I think)) and moved on to downloading the openGL Gears test. I downloaded it, ran ./configure, nothing came up. Then went make and these erros appeared
```
maver@maver-laptop:~/Desktop/game$ make
gcc -DPACKAGE=\"SDLgears\" -DVERSION=\"1.0.2\"  -I. -I.      -g -O2 -I/usr/include/SDL -D_REENTRANT -c gears.c
gears.c:39:21: error: GL/glut.h: No such file or directory
gears.c:45: error: syntax error before &#8216;T0&#8217;
gears.c:45: warning: data definition has no type or storage class
gears.c:46: error: syntax error before &#8216;Frames&#8217;
gears.c:46: warning: data definition has no type or storage class
gears.c:63: error: syntax error before &#8216;inner_radius&#8217;
gears.c: In function &#8216;gear&#8217;:
gears.c:66: error: &#8216;GLint&#8217; undeclared (first use in this function)
gears.c:66: error: (Each undeclared identifier is reported only once
gears.c:66: error: for each function it appears in.)
gears.c:66: error: syntax error before &#8216;i&#8217;
gears.c:67: error: &#8216;GLfloat&#8217; undeclared (first use in this function)
gears.c:71: error: &#8216;r0&#8217; undeclared (first use in this function)
gears.c:71: error: &#8216;inner_radius&#8217; undeclared (first use in this function)
gears.c:72: error: &#8216;r1&#8217; undeclared (first use in this function)
gears.c:72: error: &#8216;outer_radius&#8217; undeclared (first use in this function)
gears.c:72: error: &#8216;tooth_depth&#8217; undeclared (first use in this function)
gears.c:73: error: &#8216;r2&#8217; undeclared (first use in this function)
gears.c:75: error: &#8216;da&#8217; undeclared (first use in this function)
gears.c:75: error: &#8216;teeth&#8217; undeclared (first use in this function)
gears.c:77: error: &#8216;GL_FLAT&#8217; undeclared (first use in this function)
gears.c:82: error: &#8216;GL_QUAD_STRIP&#8217; undeclared (first use in this function)
gears.c:83: error: &#8216;i&#8217; undeclared (first use in this function)
gears.c:84: error: &#8216;angle&#8217; undeclared (first use in this function)
gears.c:85: error: &#8216;width&#8217; undeclared (first use in this function)
gears.c:95: error: &#8216;GL_QUADS&#8217; undeclared (first use in this function)
gears.c:142: error: &#8216;u&#8217; undeclared (first use in this function)
gears.c:143: error: &#8216;v&#8217; undeclared (first use in this function)
gears.c:144: error: &#8216;len&#8217; undeclared (first use in this function)
gears.c:166: error: &#8216;GL_SMOOTH&#8217; undeclared (first use in this function)
gears.c: At top level:
gears.c:180: error: syntax error before &#8216;view_rotx&#8217;
gears.c:180: warning: data definition has no type or storage class
gears.c:181: error: syntax error before &#8216;gear1&#8217;
gears.c:181: warning: data definition has no type or storage class
gears.c:182: error: syntax error before &#8216;angle&#8217;
gears.c:182: warning: data definition has no type or storage class
gears.c: In function &#8216;draw&#8217;:
gears.c:187: error: &#8216;GL_COLOR_BUFFER_BIT&#8217; undeclared (first use in this function)
gears.c:187: error: &#8216;GL_DEPTH_BUFFER_BIT&#8217; undeclared (first use in this function)
gears.c:218: error: &#8216;GLint&#8217; undeclared (first use in this function)
gears.c:218: error: syntax error before &#8216;t&#8217;
gears.c:219: error: &#8216;t&#8217; undeclared (first use in this function)
gears.c:220: error: &#8216;GLfloat&#8217; undeclared (first use in this function)
gears.c:220: error: syntax error before &#8216;seconds&#8217;
gears.c:222: error: &#8216;seconds&#8217; undeclared (first use in this function)
gears.c:222: error: &#8216;fps&#8217; undeclared (first use in this function)
gears.c: In function &#8216;special&#8217;:
gears.c:264: error: &#8216;GLUT_KEY_UP&#8217; undeclared (first use in this function)
gears.c:267: error: &#8216;GLUT_KEY_DOWN&#8217; undeclared (first use in this function)
gears.c:270: error: &#8216;GLUT_KEY_LEFT&#8217; undeclared (first use in this function)
gears.c:273: error: &#8216;GLUT_KEY_RIGHT&#8217; undeclared (first use in this function)
gears.c: In function &#8216;reshape&#8217;:
gears.c:286: error: &#8216;GLfloat&#8217; undeclared (first use in this function)
gears.c:286: error: syntax error before &#8216;h&#8217;
gears.c:288: error: &#8216;GLint&#8217; undeclared (first use in this function)
gears.c:288: error: syntax error before &#8216;width&#8217;
gears.c:289: error: &#8216;GL_PROJECTION&#8217; undeclared (first use in this function)
gears.c:291: error: &#8216;h&#8217; undeclared (first use in this function)
gears.c:292: error: &#8216;GL_MODELVIEW&#8217; undeclared (first use in this function)
gears.c: In function &#8216;init&#8217;:
gears.c:300: error: syntax error before &#8216;pos&#8217;
gears.c: At top level:
gears.c:302: error: syntax error before &#8216;red&#8217;
gears.c:303: warning: data definition has no type or storage class
gears.c:304: error: syntax error before &#8216;green&#8217;
gears.c:305: warning: data definition has no type or storage class
gears.c:306: error: syntax error before &#8216;blue&#8217;
gears.c:307: warning: data definition has no type or storage class
gears.c:309: warning: parameter names (without types) in function declaration
gears.c:309: warning: data definition has no type or storage class
gears.c:310: warning: parameter names (without types) in function declaration
gears.c:310: warning: data definition has no type or storage class
gears.c:311: warning: parameter names (without types) in function declaration
gears.c:311: warning: data definition has no type or storage class
gears.c:312: warning: parameter names (without types) in function declaration
gears.c:312: warning: data definition has no type or storage class
gears.c:313: warning: parameter names (without types) in function declaration
gears.c:313: warning: data definition has no type or storage class
gears.c:316: error: initializer element is not constant
gears.c:316: warning: data definition has no type or storage class
gears.c:317: warning: parameter names (without types) in function declaration
gears.c:317: warning: data definition has no type or storage class
gears.c:318: warning: parameter names (without types) in function declaration
gears.c:318: warning: data definition has no type or storage class
gears.c:319: error: syntax error before numeric constant
gears.c:319: error: conflicting types for &#8216;gear&#8217;
gears.c:65: error: previous definition of &#8216;gear&#8217; was here
gears.c:319: warning: data definition has no type or storage class
gears.c:320: warning: data definition has no type or storage class
gears.c:322: error: initializer element is not constant
gears.c:322: warning: data definition has no type or storage class
gears.c:323: warning: parameter names (without types) in function declaration
gears.c:323: warning: data definition has no type or storage class
gears.c:324: warning: parameter names (without types) in function declaration
gears.c:324: warning: data definition has no type or storage class
gears.c:325: error: syntax error before numeric constant
gears.c:325: warning: data definition has no type or storage class
gears.c:326: warning: data definition has no type or storage class
gears.c:328: error: initializer element is not constant
gears.c:328: warning: data definition has no type or storage class
gears.c:329: warning: parameter names (without types) in function declaration
gears.c:329: warning: data definition has no type or storage class
gears.c:330: warning: parameter names (without types) in function declaration
gears.c:330: warning: data definition has no type or storage class
gears.c:331: error: syntax error before numeric constant
gears.c:331: warning: data definition has no type or storage class
gears.c:332: warning: data definition has no type or storage class
gears.c:334: warning: parameter names (without types) in function declaration
gears.c:334: warning: data definition has no type or storage class
gears.c:336: error: syntax error before &#8216;if&#8217;
gears.c:336: error: syntax error before &#8216;[&#8217; token
gears.c:336: error: &#8216;argv&#8217; undeclared here (not in a function)
gears.c:336: error: &#8216;__s2&#8217; undeclared here (not in a function)
gears.c:336: error: syntax error before &#8216;if&#8217;
gears.c:336: error: non-static declaration of &#8216;__result&#8217; follows static declaration
gears.c:336: error: previous definition of &#8216;__result&#8217; was here
gears.c:336: warning: data definition has no type or storage class
gears.c:336: error: syntax error before &#8216;}&#8217; token
gears.c:336: error: static declaration of &#8216;__result&#8217; follows non-static declaration
gears.c:336: error: previous declaration of &#8216;__result&#8217; was here
gears.c:336: error: &#8216;__s1&#8217; undeclared here (not in a function)
gears.c:336: error: syntax error before &#8216;if&#8217;
gears.c:336: error: non-static declaration of &#8216;__result&#8217; follows static declaration
gears.c:336: error: previous definition of &#8216;__result&#8217; was here
gears.c:336: warning: data definition has no type or storage class
gears.c:336: error: syntax error before &#8216;}&#8217; token
gears.c:338: error: syntax error before string constant
gears.c:338: error: syntax error before &#8216;)&#8217; token
gears.c:339: error: syntax error before string constant
gears.c:339: error: syntax error before &#8216;)&#8217; token
gears.c:340: error: syntax error before string constant
gears.c:340: error: syntax error before &#8216;)&#8217; token
gears.c: In function &#8216;visible&#8217;:
gears.c:347: error: &#8216;GLUT_VISIBLE&#8217; undeclared (first use in this function)
gears.c: In function &#8216;main&#8217;:
gears.c:356: error: &#8216;GLUT_RGB&#8217; undeclared (first use in this function)
gears.c:356: error: &#8216;GLUT_DEPTH&#8217; undeclared (first use in this function)
gears.c:356: error: &#8216;GLUT_DOUBLE&#8217; undeclared (first use in this function)
make: *** [gears.o] Error 1

```

However, when I run the program ./SDLgears it works, a screen pops up and some gears spin around. Pretty cool looking. 

So, it works (kinda) but I get those errors when going 'make' so I was wondering what I was doing wrong. I probably forgot to download something, but I'm stumped as to what I forgot, so help would be very good.


P.S. Any links to good openGl and SDL tutorials would be much appreciated. I want to learn how to play around with graphicss (Not so much games *just* yet) kinda like the gears example... But not that advanced just yet.

---

### Post by hod139 on 2007-03-11
That's an annoying package.  The problem is that it builds both the SDL version and the GLUT version.  To fix that error you need to install GLUT
```

sudo aptitude install freeglut3-dev

```

---

### Post by grusifix on 2007-03-11
That sure is annoying. Why it has build them both? You should check [http://nehe.gamedev.net]("http://nehe.gamedev.net"). Quite many of tutorials there have Linux/SDL download option.

---

### Post by Darkness3477 on 2007-03-12
> **hod139 said:**
> That's an annoying package.  The problem is that it builds both the SDL version and the GLUT version.  To fix that error you need to install GLUT
```

sudo aptitude install freeglut3-dev

```

Thank you very much, that fixed it up nicely. I'm quite surprised that the tutorial didn't include that. Now, onto my goal: Making a ball hit the side 'wall' and bounce off at the correct angle.

---

