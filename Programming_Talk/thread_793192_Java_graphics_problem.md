---
title: "Java graphics problem"
date: 2008-05-13
forum: Programming Talk
---

### Post by Sequences on 2008-05-13
Okay, this problem has plagued me for the past half a year-ever since I started using Ubuntu. Whenever I run a program that uses a GUI, nothing happens. 

Here is an example. I wrote a program that I can play minesweeper on. A window is supposed to pop up with the predetermined size and buttons on it that are blank, etc. When I run it on another computer - Windows or Mac - it works fine. But when I try to run it on my Ubuntu, it does not work properly. A window pops up but it remains blank; it is gray. I do not get any errors because there are none. The code is exactly the same as it is on the other computers. 

What could I do to get rid of this? I have friends who also use Linux - some other variant of Ubuntu- and it works fine. So I have no idea what is it that I am not doing that is giving me this problem.

Thanks in advance.

---

### Post by LaRoza on 2008-05-13
> **Sequences said:**
> Okay, this problem has plagued me for the past half a year-ever since I started using Ubuntu. Whenever I run a program that uses a GUI, nothing happens. 

Here is an example. I wrote a program that I can play minesweeper on. A window is supposed to pop up with the predetermined size and buttons on it that are blank, etc. When I run it on another computer - Windows or Mac - it works fine. But when I try to run it on my Ubuntu, it does not work properly. A window pops up but it remains blank; it is gray. I do not get any errors because there are none. The code is exactly the same as it is on the other computers. 

What could I do to get rid of this? I have friends who also use Linux - some other variant of Ubuntu- and it works fine. So I have no idea what is it that I am not doing that is giving me this problem.

Thanks in advance.

Could you show some code? And give the jre you are using as well.

If it is too long, just make a simple application that demonstrates this behavior.

---

### Post by Sequences on 2008-05-13
Alright, I took out basically everything and just left the basic things. I just want it to show a button. here goes.

```

import java.awt.*;
import javax.swing.*;

public class Test1 {

	
	public static void main(String[] args) {
		Test2 game = new Test2(1);
		
	}

}

```
```

import java.awt.*;
import java.awt.event.*;

import javax.swing.*;

public class Test2 extends JFrame implements ActionListener {
	
	private Container pane;		
	
	public Test2(int a){
		
		//super("Maxit");
		
		pane = getContentPane();
        pane.setLayout(new BorderLayout());
        
		pane.add(new JButton("234234"));        
        System.out.println(a);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(5*51, 5*50);
        setResizable(false);
        setVisible(true);
	}
	
	
	public void actionPerformed(ActionEvent ae) {
		
	}	
}

```

When I run this, a window pops up with nothing in it. The program runs without an error and on the console '1' appears as it should be. Hope this helps with what I mean.

---

### Post by LaRoza on 2008-05-13
It works fine on my end. What JRE are you using?

---

### Post by Sequences on 2008-05-13
See, that is the problem. It works for you, but it does not work for me. 

When I type java -version into the terminal i get:
```

Java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)

```
 I use Eclipse ( eclipse-SDK-3.3.2-linux-gtk.tar.gz )

---

### Post by LaRoza on 2008-05-13
> **Sequences said:**
> See, that is the problem. It works for you, but it does not work for me. 

When I type java -version into the terminal i get:
```

Java version "1.5.0_15"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_15-b04)

```
 I use Eclipse ( eclipse-SDK-3.3.2-linux-gtk.tar.gz )

Are you compiling on Ubuntu?

I don't know much about Java, so I don't know how much I can help.

Here is what I have: 

```

~$javac -version
javac 1.6.0_06

~$java -version
java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK Client VM (build 1.6.0-b09, mixed mode, sharing)

```

---

### Post by NormR2 on 2008-05-13
It works for me also.  I have Sun's java 1.6.0_06

What is the commandline you are using to execute it?

---

### Post by Sequences on 2008-05-13
I use Eclipse to run it. Maybe that is the problem, but I have seen these Eclipse run these programs on Ubuntu before. So I'm not sure what the problem is. This is not limited to the example I gave. Any program that I have written with any sort of pop up window displays nothing; all it does is pop up a window.

---

### Post by achelis on 2008-05-13
Eclipse shouldn't be a problem. I run swing-apps through Eclipse..

I don't know much about it, but heard there can be some problems with compiz and swing...

You might want to try the following, which supposedly can help.. 
```

export AWT_TOOLKIT=MToolkit

```

These url's might help as well

[http://ubuntuforums.org/archive/index.php/t-362821.html](http://ubuntuforums.org/archive/index.php/t-362821.html)
[http://thio4linux.wordpress.com/2007/10/11/compizjava-no-problem/](http://thio4linux.wordpress.com/2007/10/11/compizjava-no-problem/)

---

### Post by LaRoza on 2008-05-13
> **Sequences said:**
> I use Eclipse to run it. Maybe that is the problem, but I have seen these Eclipse run these programs on Ubuntu before. So I'm not sure what the problem is. This is not limited to the example I gave. Any program that I have written with any sort of pop up window displays nothing; all it does is pop up a window.

Here is how I made it:
```

~$javac Test1.java
~$java Test1
1
~$

```

---

### Post by Sequences on 2008-05-13
> **achelis said:**
> Eclipse shouldn't be a problem. I run swing-apps through Eclipse..

I don't know much about it, but heard there can be some problems with compiz and swing...

You might want to try the following, which supposedly can help.. 
```

export AWT_TOOLKIT=MToolkit

```

These url's might help as well

[http://ubuntuforums.org/archive/index.php/t-362821.html](http://ubuntuforums.org/archive/index.php/t-362821.html)
[http://thio4linux.wordpress.com/2007/10/11/compizjava-no-problem/](http://thio4linux.wordpress.com/2007/10/11/compizjava-no-problem/)

Thanks a lot. It works now. Though, every time I run something, I get this long list of errors. This is if I use the first link. The second link tells me to do something else and it did nothing when I tried it. 
```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1b7f767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb1b7f8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb1bc41bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1d3185e]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1ce6177]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1ce62f3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1ce6536]
#7 [0xb2668bfa]
#8 [0xb2662b3b]
#9 [0xb2662b3b]
#10 [0xb2660219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb781d2bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7931ed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb781d0ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb787ab9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb761430d]
#16 [0xb26684ab]
#17 [0xb2662a64]
#18 [0xb2660219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb781d2bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb1b7f767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb1b7f81e]
#2 /usr/lib/libX11.so.6 [0xb1bc3518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb1bba0a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1ce5479]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1ce56c3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so [0xb1ce63a1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb1ce6536]
#8 [0xb2668bfa]
#9 [0xb2662b3b]
#10 [0xb2662b3b]
#11 [0xb2660219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb781d2bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb7931ed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb781d0ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb787ab9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb761430d]
#17 [0xb26684ab]
#18 [0xb2662a64]
#19 [0xb2660219]
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-arphic-ar pl uming uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
Warning: Cannot convert string "-sazanami-gothic-medium-r-normal--*-140-*-*-c-*-jisx0208.1983-0" to type FontStruct
Warning: Cannot convert string "-baekmuk-gulim-medium-r-normal--*-140-*-*-c-*-ksc5601.1987-0" to type FontStruct
1

```

I tried:
```

 sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so

```
and it does not work, apparently.

---

### Post by achelis on 2008-05-14
Hmm.. I'm afraid that's beyond me :?

Hopefully someone else will be able to help you out.

---

