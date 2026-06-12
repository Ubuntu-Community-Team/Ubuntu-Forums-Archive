---
title: "[java]Checking for terminal and getting its window id"
date: 2008-09-23
forum: Programming Talk
---

### Post by Pyro.699 on 2008-09-23
Hello,

I was wondering how I would go about checking for the existence of a gnome-terminal process. If it exists I would retrieve the **WINDOWID** from it and return that value. If it didn't exist, it would make a window, and then retrieve the **WINDOWID** normally. I would have started already and posted for assistance but my knowledge on this topic is quite limited. Here are the steps that need to be taken:

A) Check if a terminal window is already open
B) If the window is not open, create a new one
C) After there is a positive existence of a terminal window, retrieve the **WINDOWID** of that window.

Thanks for all your help,
~Cody Woolaver

---

### Post by Pyro.699 on 2008-09-24
Alright, i have gotten the code to check for the windows existence. If its not detected it will make a new one.

```

package java;

import java.io.*;

public class TerminalExists {

    public static void main(String[] args) throws IOException, InterruptedException{
        int pid;
        
        if((pid = exists()) == 0){
            Process make = Runtime.getRuntime().exec("gnome-terminal");
            make.hashCode();
            pid = exists();
        }
        
        System.out.println(pid);
    }
    
    public static int exists() throws IOException, InterruptedException{    
        Process p = Runtime.getRuntime().exec("ps -u cody");
        InputStreamReader reader = new InputStreamReader ( p.getInputStream () );
        BufferedReader buf_reader = new BufferedReader ( reader );
        String line;

        int pid=0;
        while ((line = buf_reader.readLine ()) != null)
        {
            if (line.indexOf("gnome-terminal") > 0) {
                pid = getPid(line);
            }
        }
        
        return pid;
    }
    
    public static int getWindowId(){return 1;}
    
    public static int getPid(String line){
        String rep = line.replace(" ", "");
        String[] spl = rep.split("\\?");
        int ret = Integer.parseInt(spl[0]);
        return ret;
    }
}

```Right now i need to figure out how to get a windows id from just its process id. I have made a simple script to get the pid that only requires the output from **ps -u cody** so that part is simple. Just getting the window id is now the tricky part.

What if were able to send a stream to that pid, and get the output back?

Just an idea...

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2008-09-25
Sorry for the bump but i need a hand with this baddly, still no progress after 2 days

---

### Post by kavon89 on 2008-09-25
Try asking the [Java forums]("http://forums.sun.com/index.jspa"), I go there for most of my specific Java related questions.

There are only a handful of people I see that frequent this forum and know Java well enough to answer your question, tinny comes to mind.

---

### Post by Pyro.699 on 2008-09-27
Thanks for the tip, but i posted and i still havn't gotten a reply from anyone on the [Java Forums](http://forums.sun.com/thread.jspa?threadID=5334723&tstart=0). Although you said there wern't many people on these forums who knew java to that level, but i do have faith of the people on these forums :D

---

### Post by stroyan on 2008-09-27
The gnome-terminal application sets an environment variable WINDOWID
with the X11 window ID of its terminal window.  That is the window for
the terminal emulator.  It is not the top-level window.  To find the
top-level window you would need to use XQueryTree and XGetWindowProperty
to get parent window IDs until you find a window with a WM_STATE property.

```

import java.io.*;
import java.util.*;

public class WindowID {

  public static void main( String [] args ) {
    Integer window;
    System.out.println( "WINDOWID is " + System.getenv("WINDOWID") );
    try {
	window = new Integer(System.getenv("WINDOWID"));
	System.out.println( "WINDOWID is " + window.toString() );
    } catch (NumberFormatException e) {
	System.out.println("WINDOWID is not valid");
    }
  }
}

```

---

### Post by Pyro.699 on 2008-09-27
How would this work if the only piece of information i am given is the process id, and also the window title.

Basically im going to be using **xterm --into {WINDOWID}** and i need to find the simpleist way to get that window id

---

### Post by drubin on 2008-09-27
> **Pyro.699 said:**
> Thanks for the tip, but i posted and i still havn't gotten a reply from anyone on the [Java Forums](http://forums.sun.com/thread.jspa?threadID=5334723&tstart=0). Although you said there wern't many people on these forums who knew java to that level, but i do have faith of the people on these forums :D

Does this have to be written in java? Java really isn't suited  to this type system level applications.

---

### Post by Pyro.699 on 2008-09-27
no, not really...but im not familiar with any other system languages (other than python, but i dont know if that counts). If you wanted to write me a program that could retrieve a WindowID from a terminal with just the process ID, i would absloutely love you, but other than that, the only language im confortable with is JAVA.

[EDIT]
I do know some c++ but nothing to the level where id be doing that. If someone were to write something in c++ i could compile it

---

### Post by Pyro.699 on 2008-10-03
Does anyone know another language i could use to get this? or point me in a relative direction?

Thanks

---

