---
title: "[ask] Using ffmpeg in java"
date: 2012-07-21
forum: Programming Talk
---

### Post by ancruk on 2012-07-21
can anyone helpl me how to use ffmpeg in java??:confused:

---

### Post by lykeion on 2012-07-22
Do you mean a) executing ffmpeg commandline conversions in Java code or b) using a Java wrapper library for ffmpeg?

a) Simple example using Java Runtime to exec a ffmpeg command (avconv -version).
Note: I'm using 'avconv' instead of 'ffmpeg' since Ubuntu/Debian has shifted to use the libav fork of ffmpeg.

[PHP]import java.util.*;
import java.io.*;

class StreamGobbler extends Thread {
	InputStream is;
	String type;

	StreamGobbler(InputStream is, String type) {
		this.is = is;
		this.type = type;
	}

	public void run() {
		try {
			InputStreamReader isr = new InputStreamReader(is);
			BufferedReader br = new BufferedReader(isr);
			String line=null;
			while ( (line = br.readLine()) != null)
				System.out.println(type + ">" + line);    
			} catch (IOException ioe)
			  {
				ioe.printStackTrace();  
			  }
	}
}

public class ExecExample {

	public static void main(String[] args) {
		try {
			Runtime rt = Runtime.getRuntime();
			Process proc = rt.exec("avconv -version");

			StreamGobbler errorGobbler = new StreamGobbler(proc.getErrorStream(), "ERROR");            
			
			StreamGobbler outputGobbler = new StreamGobbler(proc.getInputStream(), "OUTPUT");
				
			errorGobbler.start();
			outputGobbler.start();
			
			int exitVal = proc.waitFor();
			System.out.println("ExitValue: " + exitVal);
			
		} catch(Throwable t) {
			t.printStackTrace();
		}
	}
}[/PHP]

b) I'd suggest [Xuggler]("http://www.xuggle.com/xuggler/documentation"), or you can google for another with 'ffmpeg java wrapper' or similar.

---

