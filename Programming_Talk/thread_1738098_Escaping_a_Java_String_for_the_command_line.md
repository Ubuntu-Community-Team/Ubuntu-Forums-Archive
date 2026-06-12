---
title: "Escaping a Java String for the command line"
date: 2011-04-24
forum: Programming Talk
---

### Post by tornadof3 on 2011-04-24
I'm having trouble running a command line program from Java, mainly due to escape characters being sent literally. Any ideas?

```
import  java.io.*;

public class notify {
	public static void main(String[] args) {
	try {
		String $s = null;
                String $cmdErr = null;
                String $notifyTitle="\"Java Output\"";
                String $notifyMsg="\"Notify Message\"";
		String $command="notify-send -i face-cool " + $notifyTitle + " " + $notifyMsg;
                System.out.println("Command is: " + $command);
                //String $command="ls -l";
		Process $p=Runtime.getRuntime().exec($command);

		BufferedReader stdInput = new BufferedReader(new InputStreamReader($p.getInputStream()));

		BufferedReader stdError = new BufferedReader(new InputStreamReader($p.getErrorStream()));

                while(($s = stdInput.readLine()) != null) {
		System.out.println("Command output: " + $s);
	}

        	while(($cmdErr = stdError.readLine()) != null) {
		System.out.println("Command errors: " + $cmdErr);
	}
	} catch(Exception $execErr) {
		System.out.println($execErr.toString());
	}
	}
}

```

The Java executes fine but the notify-send command in ubuntu does not execute properly, generating an error of invalid number of arguments. But if you copy/paste the content of $command and run that with Alt-F2, the desired effect is fine!

---

### Post by r-senior on 2011-04-24
Doesn't the command and arguments need to be assembled into a String array as individual items?

So you'd have an array with "notify-send", "-i", "face-cool", etc.

[http://download.oracle.com/javase/6/docs/api/java/lang/Runtime.html](http://download.oracle.com/javase/6/docs/api/java/lang/Runtime.html)

---

### Post by tornadof3 on 2011-04-24
Great, that worked, thanks!

---

