---
title: "[Java] Monitor network traffic"
date: 2010-03-05
forum: Programming Talk
---

### Post by SpinningAround on 2010-03-05
I would like to create a program that monitor the traffic that pass throw a network interface, problem is that I don't know where to start or if it's even possible. The program should simply count the amount of byte that is sent and received by a certain interface.

---

### Post by Zugzwang on 2010-03-05
The application you are describing will be non-portable as there are, AFAIK, no Java built-in functions for doing so.

One possibility is to use the "Process" class for calling external utilities. With it, you can call GNU Linux' "ifconfig" utility every 5 seconds or so and parse the output.

---

### Post by kahumba on 2010-03-05
To get the amount of network data received or so you could read the file (say twice a second) /proc/net/dev and parse it accordingly. Might work, might not.

[http://linuxdevcenter.com/pub/a/linux/2000/11/16/LinuxAdmin.html](http://linuxdevcenter.com/pub/a/linux/2000/11/16/LinuxAdmin.html)

---

### Post by SpinningAround on 2010-03-06
Thanks for the answers, regarding using ifconfig is't possible not to use a script file and instead run the command from java. Problem with the last option that I can't get neither of this codes to work.

[PHP]
import java.util.*;
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.BufferedWriter;
public class A {

	public static void main (String args[]) throws InterruptedException,IOException{		
		Process process = new ProcessBuilder("echo $(ifconfig | grep RX|sed -n '2p'| sed 's/:/ /' | sed 's/:/ /' | awk '{print $8}' )").start();

		String s = null;
		BufferedReader input = new BufferedReader( new InputStreamReader(process.getInputStream()) );
		BufferedReader error = new BufferedReader( new InputStreamReader(process.getErrorStream()) );
		
		// read the output from the command
		System.out.println("Here is the standard output of the command:\n");
		while ((s = input.readLine()) != null) {
			System.out.println(s);
		}
            
		// read any errors from the attempted command
		System.out.println("Here is the standard error of the command (if any):\n");
		while ((s = error.readLine()) != null) {
			System.out.println(s);
		}
	}
}
[/PHP]

Give:
```

Exception in thread "main" java.io.IOException: Cannot run program "echo $(ifconfig | grep RX|sed -n '2p'| sed 's/:/ /' | sed 's/:/ /' | awk '{print $8}' )": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:459)
	at A.main(A.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
	at java.lang.ProcessImpl.start(ProcessImpl.java:65)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:452)
	... 1 more


```

This code:
[PHP]import java.util.*;
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.io.BufferedWriter;
public class A {

	public static void main (String args[]) throws InterruptedException,IOException{		
		Process process = new ProcessBuilder("echo","$(ifconfig | grep RX|sed -n '2p'| sed 's/:/ /' | sed 's/:/ /' | awk '{print $8}' )").start();

		String s = null;
		BufferedReader input = new BufferedReader( new InputStreamReader(process.getInputStream()) );
		BufferedReader error = new BufferedReader( new InputStreamReader(process.getErrorStream()) );
		
		// read the output from the command
		System.out.println("Here is the standard output of the command:\n");
		while ((s = input.readLine()) != null) {
			System.out.println(s);
		}
            
		// read any errors from the attempted command
		System.out.println("Here is the standard error of the command (if any):\n");
		while ((s = error.readLine()) != null) {
			System.out.println(s);
		}
	}
}
[/PHP]

give
```

Here is the standard output of the command:

$(ifconfig | grep RX|sed -n '2p'| sed 's/:/ /' | sed 's/:/ /' | awk '{print $8}' )
Here is the standard error of the command (if any):



```

---

### Post by kahumba on 2010-03-06
/proc/net/dev is a file.
Here's an example using it to display current network usage (of all available interfaces, 4 in my case) being renewed twice a second, screenshot attached:

Main.java (the JFrame)
[PHP]
import javax.swing.*;

public class Main extends JFrame{

    public static void main(String[] args) {
        new Main();
    }

    public Main() {
        setSize(550, 200);
        setTitle("Network Monitor");
        setContentPane(new NetworkMonitor());
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setVisible(true);
    }
}
[/PHP]
NetworkMonitor.java:
[PHP]
import java.awt.*;
import java.io.*;
import java.util.*;
import javax.swing.*;

public class NetworkMonitor extends JPanel implements Runnable {

    private ArrayList<String> lines;

    public NetworkMonitor() {
        lines = new ArrayList<String>();
        new Thread(this).start();
    }

    @Override
    public void run() {
        try {
            while (true) {
                String sContents = readFile();
                StringTokenizer tok = new StringTokenizer(sContents, "\n");
                lines = new ArrayList<String>();
                int x = 0;

                while (tok.hasMoreTokens()) {
                    String line = tok.nextToken();
                    if (x++ < 2) {//skip headers
                        continue;
                    }
                    lines.add(line);
                }
                repaint();
                Thread.sleep(500);//half a second
            }
        } catch (Exception exc) {
            exc.printStackTrace();
        }
    }

    @Override
    public void paint(Graphics gr) {
        super.paint(gr);
        Graphics2D g = (Graphics2D) gr;
        g.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g.setFont(new Font(Font.DIALOG_INPUT, Font.PLAIN, 14));
        g.drawString("Interface: receivedBytes/receivedPackets, sentBytes/sentPackets", 10, 20);
        for (int i = 0; i < lines.size(); i++) {
            drawLine(g, lines.get(i), i);
        }
    }

    private static final String readFile() {
        try {
            File file = new File("/proc/net/dev");
            StringBuilder sb = new StringBuilder();
            byte[] bytes = new byte[1024];
            int read = 0;
            InputStream in = new FileInputStream(file);
            while ((read = in.read(bytes)) != -1) {
                sb.append(new String(bytes, 0, read));
            }
            in.close();
            return sb.toString();
        } catch (Exception exc) {
            exc.printStackTrace();
        }
        return null;
    }

    private void drawLine(Graphics2D g, String line, int iLineIndex) {
        String[] words = line.split("\\s+");
        String sInterface = words[words[0].length() > 0 ? 0 : 1];
        int index = sInterface.indexOf(':');
        boolean jump = index != sInterface.length()-1;
        String receivedBytes = jump ? sInterface.substring(index+1) : words[2];
        String receivedPackets = jump ? words[2] : words[3];
        String sentBytes = jump ? words[9] : words[10];
        String sentPackets = jump ? words[10] : words[11];
        if(index > -1) {
            sInterface = sInterface.substring(0, index);
        }
        int x = 10, y = 50 + iLineIndex * 20;
        String sReceived = receivedBytes + "/" + receivedPackets;
        String sSent = sentBytes + "/" + sentPackets;
        g.drawString(sInterface + ":", x, y);
        g.drawString(sReceived, x+100, y);
        g.drawString(sSent, x+250, y);
    }
}
[/PHP]

---

### Post by SpinningAround on 2010-03-07
Thanks answers, I looking through your code to get some grip of it, something I don't understand is what the signs ':' and '?' do.
[PHP]
String sInterface = words[words[0].length() > 0 ? 0 : 1];
[/PHP]

---

### Post by kahumba on 2010-03-07
It's a shorthand for if-else and it's also available in other languages, thus:

[PHP]
String sInterface = words[words[0].length() > 0 ? 0 : 1];
[/PHP]equals
[PHP]
String sInterface;
if(words[0].length() > 0) {
    sInterface = words[0];
} else {
    sInterface = words[1];
}
[/PHP]A lot of info on the net about it, for example:
[http://devdaily.com/java/edu/pj/pj010018](http://devdaily.com/java/edu/pj/pj010018)

I'm rather interested whether the/my example does what you need or not.

---

### Post by SpinningAround on 2010-03-07
> **kahumba said:**
> It's a shorthand for if-else and it's also available in other languages, thus:

[PHP]
String sInterface = words[words[0].length() > 0 ? 0 : 1];
[/PHP]equals
[PHP]
String sInterface;
if(words[0].length() > 0) {
    sInterface = words[0];
} else {
    sInterface = words[1];
}
[/PHP]A lot of info on the net about it, for example:
[http://devdaily.com/java/edu/pj/pj010018](http://devdaily.com/java/edu/pj/pj010018)

I'm rather interested whether the/my example does what you need or not.

Thanks, yes I works perfectly. I needed someway to get info about the amount of traffic that pass through and interface and your code does it.

---

### Post by king vash on 2010-03-07
Awesome!

Your command line could be abbreviated a little.
```
sed 's/:/ /' | sed 's/:/ /'
```
could instead be written as
```
sed 's/:/ /g'
```

---

### Post by kahumba on 2010-03-07
@King vash The OP went with the other solution which doesn't make use of sed and ifconfig.

---

### Post by winterpig on 2010-11-07
where or how to locate /proc/net/dev in a window ??

---

### Post by muze4life on 2010-11-07
What d'you mean? Open up a terminal and say "cat /proc/net/dev" and see what happens, besides, "dev" in this case isn't a real file on the HDD but created on the fly by the kernel.

---

### Post by winterpig on 2010-11-07
Sorry, I mean where & how to locate proc/net/dev in **_windows 7_**?

I had taken the original code & run in windows 7 pc; the above path is not recognized. I understand /proc is a virtual file system and doesnt contain 'real' files but runtime system info. since this code is running under a regular pc windows (windows 7), I thought I should change the file path. Please tell me if my logic is wrong.

Can any one please also explain: 
boolean jump = index != sInterface.length()-1;
String receivedBytes = jump ? sInterface.substring(index+1) : words[2];

Thanks

---

### Post by muze4life on 2010-11-07
You are probably kidding...
In case you're not - don't try to run it on windows cause this solution is for Linux-based distros which windows is not a part of...

**1) boolean jump = index != sInterface.length()-1;**
**2) String receivedBytes = jump ? sInterface.substring(index+1) : words[2];**

1) "jump" will be true if "index" is not equal to "sInterface.length()-1".
2) second line is same as:
String receivedBytes = null;
if(jump) {
    receivedBytes = sInterface.substring(index+1);
} else {
    receivedBytes = words[2];
}

ps: thus, as you probably understand by now, if an app is written in Java it doesn't yet mean it's also cross-platform.

---

### Post by winterpig on 2010-11-07
thank you very much for the reply. I now fully understands the code. :KS

So, is there a similar path in windows 7 that I can substitute in & compile to monitor? I am trying to accomplish the same task (monitor network traffic) but monitor on windows 7. Any suggestions? 

Is it true that Java doesnt have a package to easily retrieve network traffic statistics in windows & has to use third party package called 'jpcap'??

---

### Post by muze4life on 2010-11-08
> **winterpig said:**
> 
So, is there a similar path in windows 7 that I can substitute in & compile to monitor?

I don't know, but since Windows doesn't follow the same philosophy as Linux "everything is a file" - it **probably** doesn't have such a path.

> **winterpig said:**
> 
Any suggestions? 

Yes, google.

> **winterpig said:**
> 
Is it true that Java doesnt have a package to easily retrieve network traffic statistics in windows & has to use third party package called 'jpcap'??

It's true.
Don't know about jpcap, you could google and implement the ideas (found through googling) yourself without using a third party (especially if that code is closed source, requires payment etc).

---

### Post by rskishorekumar on 2012-09-26
How we can monitor 2 system in network in java? possibly in ipaddress 
please some one give me solution in java program.

---

### Post by dwhitney67 on 2012-09-26
This is an old thread, for which you should not have resurrected.

Next time, open a new thread.

To answer your query, consider using SIGAR (System Information Gatherer and Reporting).  You can find it here: [http://support.hyperic.com/display/SIGAR/Home](http://support.hyperic.com/display/SIGAR/Home)

---

