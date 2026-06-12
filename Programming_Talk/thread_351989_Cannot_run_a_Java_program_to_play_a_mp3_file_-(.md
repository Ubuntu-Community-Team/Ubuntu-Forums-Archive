---
title: "Cannot run a Java program to play a mp3 file :-("
date: 2007-02-02
forum: Programming Talk
---

### Post by André on 2007-02-02
Hi everybody,

i am a bit afraid that the following problem might be just another CLASSPATH setting problem.

But i could not get i going and i think i tried much :-(

So here we go:

I want to play a MP3 file in a Java program. I googled a bit and found the following tutorial: [http://www.javalobby.org/java/forums/t18465.html](http://www.javalobby.org/java/forums/t18465.html).

In this tut the author uses code from ww.Javazoom.net and i thought that's the way to go. So i downloaded the code from the tutorial and got three jar-files. First i tried to set my CLASSPATH to include the jars... I added every jar to it with:

```
export CLASSPATH=$CLASSPATH:~/Uni/REX_Software/MP3lib/jl1.0.jar:~/Uni/REX_Software/MP3lib/mp3spi1.9.4.jar:~/Uni/REX_Software/MP3lib/tritonus_share.jar

```

which gives me

```
andre@watson:~$ echo $CLASSPATH
:/home/andre/Uni/REX_Software/MP3lib/jl1.0.jar:/home/andre/Uni/REX_Software/MP3lib/mp3spi1.9.4.jar:/home/andre/Uni/REX_Software/MP3lib/tritonus_share.jar

```

I copied over the code from the tutorial. After building and running i get:
```

andre@watson:~/Uni/REX_Software/MP3lib$ java JLayerPlayer test.mp3
Exception in thread "main" java.lang.NoClassDefFoundError: JLayerPlayer (wrong name: com/javalobby/tnt/jlayer/JLayerPlayer)
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

I tinkered around with the CLASSPATH but no go. I decided to use the dirty way: I copied over the jar files to the lib/ext diretcory in the Java - directory (found out the directory with sudo update-alternatives...).

I always get the same error :-(

So i thought about trying something new ;-) Surfing over to Sun i found a MP3 Plugin: [http://java.sun.com/products/java-media/jmf/mp3/download.html](http://java.sun.com/products/java-media/jmf/mp3/download.html)

```

Copying the jar over, trying the code gives: Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/media/codec/audio/AudioCodec
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:299)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

As you can see here the files are in place:

```

andre@watson:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext$ ls -al
insgesamt 1468
drwxr-xr-x  2 root root   4096 2007-02-02 23:58 .
drwxr-xr-x 16 root root   4096 2007-02-02 17:37 ..
-rw-r--r--  1 root root   8176 2006-07-11 19:46 dnsns.jar
-rw-r--r--  1 root root 105446 2007-02-02 23:58 jl1.0.jar
-rw-r--r--  1 root root 802388 2006-08-18 01:48 localedata.jar
-rw-r--r--  1 root root  82415 2007-02-02 18:37 mp3plugin.jar
-rw-r--r--  1 root root  24538 2007-02-02 23:58 mp3spi1.9.4.jar
-rw-r--r--  1 root root 158417 2006-07-11 19:28 sunjce_provider.jar
-rw-r--r--  1 root root 175811 2006-07-11 19:28 sunpkcs11.jar
-rw-r--r--  1 root root 102723 2007-02-02 23:58 tritonus_share.jar

```

Hey guys, any idea what i going wrong here? Any help is soo appreciated as i really need this :-(

Greetings
André

---

### Post by phossal on 2007-02-02
I recommend downloading Java 6 directly from Sun. You can do that, and integrate it fully, using the directions in my signature.

I pulled the Jar files from the site you used myself. I put the three of them in my /JDK/jre/lib/ext path, and then compiled the example source code (listed in the web page) using eclipse.

I didn't have any problems.

---

### Post by André on 2007-02-02
Hi phossal,

first thanks for your quick answer.

Before i try the new Java stuff i would like to analyze something else - i am pretty new to Eclipse but i also added the project to it.

I called the sample file JLayerPlayer.java - that is right, isn't it? Now when i rightclick on the file i cannot choose "Run as -> Java application". So i choos Run and edit the settings: Now it does not find JLayerPlayer as main class (I hope i use the right words - i am using the german version).

Any ideas why this is happening? How did you compile it? Am i doing something wrong here?

Greetings and thanks again
André

---

### Post by phossal on 2007-02-02
Andre, I won't be home for a couple hours. I'm *sure* we can get you up and running, if you're not already. I just need time to leave my office and get home.

---

### Post by phossal on 2007-02-02
Any success?

---

### Post by André on 2007-02-03
Hi phossal,

i live in Germany and there it was 2.00 in the night. So i had to go to bed ;-)

I will start trying again now using your tutorial and setting up Java 6.

Btw, did you notice that you do not have the tutorial in your signature as you told? But it was no problem to find it in the forum.

Thanks for your help up til now, man!
André

---

### Post by phossal on 2007-02-03
> **André said:**
> I will start trying again now using your tutorial and setting up Java 6.
Good. I'll be here to help.
> **André said:**
> Btw, did you notice that you do not have the tutorial in your signature as you told? But it was no problem to find it in the forum.
You could not find my Java Tutorial in my signature? Perhaps you have signatures turned off? I can see them.[/QUOTE]

---

### Post by André on 2007-02-03
Okay,

i never turned that stuff off but it you are right. Turned it on again and cen see your signature now... and your avatar - nice picture ;-)

Greetings
André

---

### Post by André on 2007-02-03
Hey phossal,

just saw Java6 packages in backports. Is there anything why i should not install these?

Would give me updates and stuff :-)

Greetings
André

---

### Post by André on 2007-02-03
Okay,

used the backports stuff -> no go!

Really trying your tutorial now *including eclipse*... it was just because i normally prefer to have stuff in Synaptic ;-)

Tell you how it goes when i am finished.

Greetings
André

---

### Post by phossal on 2007-02-03
Wait! The backports would work *fine* for Java 6. The issue isn't about the version or where you get it, really. You just need to make sure you have a clean install of the JDK. I realize I suggested downloading JDK 6 from SUN and eclipse from eclipse.org, but that's just because I feel they're the best packages - and they're *easiest* for me to support. I can move stuff around and help users configure based on what they need. It's the most *adaptable*.

Your problem is much simpler though. You just need to get a clean JDK, and then pop those three .jar files [(Jar Files)]("http://www.javazoom.net/mp3spi/sources/mp3spi1.9.4.tar.gz") in /path_to_jdk/jre/lib/ext/

Then launch eclipse, create a new project, create a class (in the "default" package) named: JLayerPlayer   and then copy and paste this:
```
[COLOR="DimGray"][SIZE="1"]
//Package statement not necessary in "Default" package.

import java.io.File;
import java.io.IOException;
 
import javax.sound.sampled.*;
 
public class JLayerPlayer {
	
	public static void main(String[] args) {
		AudioInputStream din = null;
		try {
			File file = new File(args[0]);
			AudioInputStream in = AudioSystem.getAudioInputStream(file);
			AudioFormat baseFormat = in.getFormat();
			AudioFormat decodedFormat = new AudioFormat(
					AudioFormat.Encoding.PCM_SIGNED,
					baseFormat.getSampleRate(), 16, baseFormat.getChannels(),
					baseFormat.getChannels() * 2, baseFormat.getSampleRate(),
					false);
			din = AudioSystem.getAudioInputStream(decodedFormat, in);
			DataLine.Info info = new DataLine.Info(SourceDataLine.class, decodedFormat);
			SourceDataLine line = (SourceDataLine) AudioSystem.getLine(info);
			if(line != null) {
				line.open(decodedFormat);
				byte[] data = new byte[4096];
				// Start
				line.start();
				
				int nBytesRead;
				while ((nBytesRead = din.read(data, 0, data.length)) != -1) {	
					line.write(data, 0, nBytesRead);
				}
				// Stop
				line.drain();
				line.stop();
				line.close();
				din.close();
			}
			
		}
		catch(Exception e) {
			e.printStackTrace();
		}
		finally {
			if(din != null) {
				try { din.close(); } catch(IOException e) { }
			}
		}
	}
 
}[/SIZE][/COLOR]
```

---

### Post by phossal on 2007-02-03
Yeah, to confirm, once the .jar files are in the proper folder, and you've compiled the class JLayerPlayer.class, you can execute it like normal:
```
java JLayerPlayer music.mp3
```

Works great, although I'm not sure why you would choose this over the native support for mp3.

---

### Post by André on 2007-02-03
Downloading stuff right now.

For your question: I just wanted a method to playback a mp3 file. Actually i did not prefer any of them but just wanted one that works :-)

But right now it looks like it is my own setup that makes problems. Do you have some sample code for the native version for me?

With native you mean the mp3 plugin, right?

I would like to try this one also :-)

Greetings
André

---

### Post by phossal on 2007-02-03
Yeah, the native api: [Java Media Framework]("http://java.sun.com/products/java-media/jmf/")

To quote the SUN site:
> [COLOR="DimGray"]The Java Media Framework API (JMF) [/COLOR][COLOR="Black"]enables audio, video and other time-based media[/COLOR] to be added to applications and applets built on Java technology. [COLOR="Black"]This optional package, which can capture, playback, stream, and transcode multiple media formats, extends the Java 2 Platform, Standard Edition (J2SE) [/COLOR][COLOR="DimGray"]for multimedia developers by providing a powerful toolkit to develop scalable, cross-platform technology.[/COLOR]

---

### Post by André on 2007-02-03
Tried that one with the MP3 Plguin which you can download here: [http://java.sun.com/products/java-media/jmf/mp3/download.html](http://java.sun.com/products/java-media/jmf/mp3/download.html)

As i described in my first post i could not get this to work either :-(

---

### Post by phossal on 2007-02-03
Where are you in the process now?

---

### Post by André on 2007-02-03
What should i say: Listening to the nicest MP3 file for days right now ;-)

It works and i am pretty happy right now!

So, after doing all these posts - are you willing to help me to get some code together to play it natively? I would like this much more.

Greetings and a BIG thanks!
André

---

### Post by André on 2007-02-03
Hi phossal,

on my search for some example code for jmf i found no good code and this article: [http://www.sitepoint.com/blogs/2005/06/05/playing-mp3s-with-java/](http://www.sitepoint.com/blogs/2005/06/05/playing-mp3s-with-java/)

I think i will stick with the javazoom packages right now since i have to get work done and they work for me right now ;-)

Greetings
André

P.S.: If you have sample Java code i am really willing to try JMF

---

### Post by phossal on 2007-02-03
Congrats on getting up and running. I don't really know much about JMF - except for the last hour I spent trying to get a single sample to work. I couldn't. lol I agree that, for simple projects, I'd stick with the other option. It appears JMF requires a lot of the same classes to encode/decode mp3 anyway. 

Again, congrats. Good luck!

---

### Post by phossal on 2007-02-03
Just to follow up, I spent a few more minutes messing around with the JMF api, which is *okay*. It does some things very well, as this example from O'Reilly (modified slightly by me) shows:

```
package Core;

import java.awt.*;
import java.net.URL;
import javax.media.*;
import javax.swing.*;

//SOURCE CODE COURTESY OF "Learning Java" published by O'Reilly
public class SimplePlayer  {
    
	public static void main(String[] args) throws Exception {
		final JFrame frame = new JFrame("MediaPlayer");
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		//Downloaded babylow.avi from: http://www.fink.com/chachababy/babylow.avi
		
		URL url = new URL( "file://home/phossal/Desktop/babylow.avi" );
		final Player player = Manager.createPlayer(url);
		
		player.addControllerListener( new ControllerListener() {
			public void controllerUpdate( ControllerEvent ce ) {
				if ( ce instanceof RealizeCompleteEvent ) {
					Component visual = player.getVisualComponent();
					Component control = player.getControlPanelComponent();
					if ( visual != null ) {
						frame.getContentPane().add( visual, "Center" );
					}
					frame.getContentPane().add( control, "South");
					frame.pack();
					frame.setVisible(true);
					player.start();
				}
			}
		});
		
		player.realize();
		
	}

}

```

For mp3 support though? Not a winner. I chased down all kinds of .jar files, and ended up right where you started - back at the JLayer option. This whole .mp3 fiasco is a zit on the face of computing. I've always found the O'Reilly books to be awesome on the whole, but I've read the occasional review that says the author(s) of "Learning Java" brushed over important topics without giving any usable detail. Mp3 support appears to be one of them. He keeps saying that .mp3 support will be covered in a later section, and then the chapter ends. Disappointing.

---

