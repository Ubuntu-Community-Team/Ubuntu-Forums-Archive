---
title: "[SOLVED] Running a command in java"
date: 2007-05-06
forum: Programming Talk
---

### Post by stinkinrich88 on 2007-05-06
Hello!

can anyone explain to me why this:

try{Process p = Runtime.getRuntime().exec("halt -p");}
catch(Exception nFE){}

use to shut my computer down in fedora, but now I've changed to ubuntu, it doesnt!

thanks!

---

### Post by Ramses de Norre on 2007-05-06
Is it ran with root privileges?

---

### Post by stinkinrich88 on 2007-05-06
> **Ramses de Norre said:**
> Is it ran with root privileges?

Don't think so... But then again it wasn't in Fedora either...

Would running the application as root be enough or would i need extra coding?

---

### Post by stinkinrich88 on 2007-05-06
actually, I'm pretty sure this isn't the problem as when I replace the command with this:

try{Process p = Runtime.getRuntime().exec(/*"halt -p"*/"echo hello");}
catch(Exception nFE){}

'hello' does not get printed to standard output

---

### Post by phossal on 2007-05-06
What do you use such a program for? Why use Java to shut down your pc?

---

### Post by stinkinrich88 on 2007-05-06
> **phossal said:**
> What do you use such a program for? Why use Java to shut down your pc?

Well, basically, I made a shutdown timer so I can watch a DVD in bed and have the computer shutdown itself when the specified time runs out! Lazy, yes, but so handy

---

### Post by phossal on 2007-05-06
Here:

```
package com;

import java.io.*;

public class ShutDown {
	
	
	public ShutDown() {
		 try {
		        // Execute command
		        String command = "sudo poweroff";
		        Process child = Runtime.getRuntime().exec(command);
		    
		        // Get output stream to write from it
		        OutputStream out = child.getOutputStream();
		    
		        out.write("PASSWORD".getBytes()); //ADD YOUR PASSWORD
		        out.close();
		    } catch (IOException e) {
		    }
	}
	
	public static void main(String args[]) {
		ShutDown s = new ShutDown();
	}
}

```

------------------------------------------
If you *man halt*, which is a funny audible command, you'll realize that its invocations are spicier than they once were. Instead of the simple halt, you have *reboot, poweroff*, etc. Also, the average dope who uses the getRuntime.exec() method hardly ever writes bytes back to it. How many *good* command line arguments can you send that don't require some additional input? (In Windows, I often call batch (.bat) files to do my bitch work rather than using the exec() for all of it.) Anyway, that's ^ power. Use it wisely.

---

### Post by phossal on 2007-05-06
The fun part is, I know you'll be gone awhile before you get to post back. Because it *works*, you'll spend at least half the time between posts restarting your machine. :)

---

### Post by Ayman on 2007-05-06
While unrelated, this may also solve your problem: use the "at" command. For example:
```
$ at now + 2 hours
at> shutdown -h now
at> <EOT>
```

man at for more info.

Another option is command chaining, which I use in situations similar to yours:
```
$ command1 && command2
```
In the above snippet, command2 will be executed only after command1 successfully finishes. If command1 fails, command2 will not be run.

---

### Post by stinkinrich88 on 2007-05-06
> **phossal said:**
> Here:

------------------------------------------
If you *man halt*, which is a funny audible command, you'll realize that its invocations are spicier than they once were. Instead of the simple halt, you have *reboot, poweroff*, etc. Also, the average dope who uses the getRuntime.exec() method hardly ever writes bytes back to it. How many *good* command line arguments can you send that don't require some additional input? (In Windows, I often call batch (.bat) files to do my bitch work rather than using the exec() for all of it.) Anyway, that's ^ power. Use it wisely.

Ahh!! Worked a treat! Thanks! 

So I did need root privileges after all! (my echo example was bad because it didn't work anyway!)

Shame it needs my password... but I suppose at least it doesnt have to be hard-coded (I could ask for it on load... but that would involve typing (even that's annoying just before bed!))

I don't mind restarting ubuntu! It's way quicker than fedora! Plus firefox remembered my page, and MPD carried on where it left off! Excellent!

Thanks!!!!

And thanks Ayman! I'll check it out!

---

### Post by phossal on 2007-05-06
Stellar. :) Happy to help, of course. Thanks for posting back.

---

### Post by Ramses de Norre on 2007-05-06
```
sudo shutdown -h <time in minutes>
```

---

