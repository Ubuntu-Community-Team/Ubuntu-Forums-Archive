---
title: "Java Applets Super Slow"
date: 2008-04-17
forum: Programming Talk
---

### Post by valyok on 2008-04-17
Hi everybody!

I am fairly new to Ubuntu but I was a bit surprised when I ran into the problem that I will describe now.

I use Eclipse to create an applet but when I run it, it first slows down the system significantly and itself runs very very slow.

I got Ubuntu 7.10; Eclipse SDK Version: 3.2.2; java version is 1.5.0_13.

I also tried to embed the applet into html and run it with Firefox - same thing - slows down the system and is extremely slow.

But when I run the same applet on the Windows machine in Eclipse - it work fine!

Any ideas? I didn't seem to find anything about that anywhere on the forum.

Thnx

---

### Post by themusicwave on 2008-04-17
This is just a crazy idea, but could it be your code?

What does you applet do?  Does it have an infinite loop in it or something like that?

Source code helps.

---

### Post by CptPicard on 2008-04-17
If your applet does something heavy, you really need to put that into a thread that can be scheduled outside of the applet's UI thread...

---

### Post by coolkid5 on 2008-04-17
I have experienced this problem a few times as well and have not found a solution.

My old applet ran perfectly on Windows and OS X but on Ubuntu my CPU usage went up to like 100% on both cores and the applet slowed down a lot.

Perhaps it was my code, but I don't believe my drawing thread was doing any calculations...

Post your code,  I'm not sure I still have my code, but the problem seems very similar.

---

### Post by themusicwave on 2008-04-17
Another question is which version of Java are you running?

Are you running Sun Java or the GNU version of Java or Iced Tea?

In my experience the GNU version of Java is much slower than the Sun version.  

That could definitely be the issue.

---

### Post by coolkid5 on 2008-04-17
The OP says he is running sun java 5.

I have also experienced this problem, but I have sun java 6.

---

### Post by themusicwave on 2008-04-17
The only reason I ask if you are using Sun Java is that merely installing it isn't enough.  Even if you have it installed Ubuntu may still default to the GNU version which is slower.

This is a pretty common mistake people make on Ubuntu.

run:
sudo update-alternatives --config java

Make sure Sun Java is selected.

---

### Post by coolkid5 on 2008-04-17
Ok, I checked and sun java is the one that I have.

---

### Post by coolkid5 on 2008-04-17
Here is a very basic applet that I basically copied and pasted together that makes my CPU usage go to 99-100%.

```
import java.applet.*;
import java.awt.*;

public class Test extends Applet implements Runnable{
	
	public void init(){
		Thread thread = new Thread(this);
		thread.start();
	}
	
	public void paint(Graphics g){
		g.drawString("Hello", 100, 120);
	}
	
	public void run(){
		long time = System.currentTimeMillis();
		while(true){
			repaint();
			
			try{
				long tmpTime = System.currentTimeMillis()-time;
				if(tmpTime<=20){
					Thread.sleep(20-tmpTime);
				}
			} catch(InterruptedException ex){
				ex.printStackTrace();
			}
		}
	}
}
```

Any ideas?

---

### Post by CptPicard on 2008-04-17
No wonder, it's an infinite loop that never sleeps after the first 20ms but calls repaint constantly.. :)

---

### Post by themusicwave on 2008-04-17
Don't use the while(True)  then it won't hog all of your CPU.

Or if you really want an infinite loop add some sleep time to it like this:

this.sleep(500)

Add that to the end of the loop and it won't totally starve your CPU.

---

### Post by CptPicard on 2008-04-17
while (true) would be ok if the idea that the thing tries to implement was implemented correctly.. :) but the time variable is never updated, so currenttime - time is of course always > 20 after the first 20ms :)

---

### Post by themusicwave on 2008-04-17
> **CptPicard said:**
> while (true) would be ok if the idea that the thing tries to implement was implemented correctly.. :) but the time variable is never updated, so currenttime - time is of course always > 20 after the first 20ms :)


Very good point Captain.  And after missing that I realize it is bed time...

---

### Post by coolkid5 on 2008-04-18
Lol, oops, that example was bad. 

 I don't know what happened to my original slow applet so I'm not really sure what was wrong with that one.

Its strange that the applet did not run slowly on windows even though the code was messed up...

---

