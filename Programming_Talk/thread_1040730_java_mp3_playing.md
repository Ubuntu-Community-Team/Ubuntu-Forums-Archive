---
title: "java mp3 playing?"
date: 2009-01-15
forum: Programming Talk
---

### Post by sandyd on 2009-01-15
I have a java computer summative assignment going on and i would like to know how to play mp3s 
1. during the background of the game 
2. when a ship is hit. 

Ive tried Jlayer, but after reading all the tutorials and stuff, i still don't know how to put it into my program :(
Included is the netbeans project. 

P.S. the file was originally too large so i cut out the classes and the jar. Theyll have to be rebuilt to run the applet. 

Thanks!

---

### Post by cl333r on 2009-01-15
Here's an example in one class that works fine for me, but notice that on Linux if there's a music player playing in the background that could block java from playing the mp3 file, so, if the example isn't working - make sure nothing else is playing in the background.

The example expects the mp3 file to be called "file.mp3" and be located in your home directory.

```

package mp3test;

import java.io.*;
import javazoom.jl.player.Player;

public class Main implements Runnable {
	private Thread th;

	public static void main( String[] args ) {
		new Main();
	}

	public Main() {
		play();
	}

	private void play() {
		if( th == null ) {
			th = new Thread( this );
			th.start();//calls the run() method
		}
	}

	public void run() {
		String sFilePath = System.getProperty("user.home") + File.separator + "file.mp3";
		File mp3File = new File( sFilePath );

		if( !mp3File.exists() ) {
			System.err.println( "Couldn't find mp3 file at: " + mp3File.getPath() );
			th = null;
			return;
		}


		try {
			FileInputStream fis = new FileInputStream(mp3File);
			BufferedInputStream bis = new BufferedInputStream(fis);
			Player player = new Player(bis);
			
			System.out.println( "Going to play file.." );
			player.play();
			System.out.println( "Done playing the file." );
		} catch (Exception e) {
			System.out.println("Problem playing file " + mp3File.getPath());
			System.out.println(e);
		}
	}
}

```
Since this example doesn't provide a way to stop the player you'll either have to wait for the whole mp3 file to be played or terminate the execution from NetBeans: see the attached image.

---

### Post by sandyd on 2009-01-16
...
double post

---

### Post by sandyd on 2009-01-16
Thanks!

---

