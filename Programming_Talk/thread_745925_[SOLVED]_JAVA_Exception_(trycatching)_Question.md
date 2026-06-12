---
title: "[SOLVED] JAVA Exception (try/catching) Question"
date: 2008-04-05
forum: Programming Talk
---

### Post by Griff on 2008-04-05
I'm having a problem with the BufferedReader and BufferedWriter classes.  I created a class specifically for the handling of file input and output.  It will not have a main method.

Normally the following would work:
```

	try {
	BufferedReader in = new BufferedReader(new FileReader("Accounts"));
	}
	catch (IOException ex) {
		System.err.println(ex);
	}

```
But now it won't.  I tested this exact code in my main method of the public class file that resides within the same file and it worked.  What is wrong with this now?  My class at the bottom of the page is simply:
```

class WhatEv {
	try {
	BufferedReader in = new BufferedReader(new FileReader("Accounts"));
	}
	catch (IOException ex) {
		System.err.println(ex);
	}
}

```

---

### Post by Balazs_noob on 2008-04-05
well you can  not just put code in a class that way,
you need to put code in methods....

like this way 
[PHP]
import java.io.*;

public class WhatEv {

    public void read() {
        try {
            BufferedReader in = new BufferedReader(new FileReader("Accounts"));
        } catch (IOException ex) {
            System.err.println(ex);
        }
    }
}
[/PHP]

---

### Post by drubin on 2008-04-05
> **Balazs_noob said:**
> well you can  not just put code in a class that way
you need to put code in methods....


That is not 100% true.
You could have something like this 
[PHP]
import java.io.*;
class WhatEv {
        static BufferedReader in;
         static{
	       try {
	           in = new BufferedReader(new FileReader("Accounts"));
	      }
	      catch (IOException ex) {
		System.err.println(ex);
	     }
       }
}
[/PHP]

---

### Post by heikaman on 2008-04-05
> **rubinboy said:**
> That is not 100% true.
You could have something like this 
[PHP]
import java.io.*;
class WhatEv {
        static BufferedReader in;
         static{
	       try {
	           in = new BufferedReader(new FileReader("Accounts"));
	      }
	      catch (IOException ex) {
		System.err.println(ex);
	     }
       }
}
[/PHP]

The static block will execute when the JVM loads the class, I don't think this is what he wants.

---

### Post by themusicwave on 2008-04-05
The problem with your code is that you need a proper class.  You need a constructor, arguments(variables) and a method.

I would not recommend using the static block, static has it's place and is very useful, but is not meant for this kind of thing.

Also, you have to declare the class as public to be able to use it.  If it isn't public then nothing else can reference/use it.

Also, if you declare you a variable inside a try block it only exists inside that try block.  Variables have a scope, which is where they are defined.  Basically whatever innermost set of {} they are contained in.

I think this would work best:

[PHP]
import java.io.*;

public class WhatEv {

	private BufferedReader inReader = null;
	
	public WhatEv(String file){
		
		try{
		inReader = new BufferedReader(new FileReader(file));
		}
		catch(FileNotFoundException fnfex){
			fnfex.printStackTrace();
		}
	}
	
	public String readLine() throws IOException{
		String line = "";
		
		try{
		 line = inReader.readLine();
		}
		catch(IOException ioex){
			throw ioex;
		}
		
		return line;
	}
}
[/PHP]

Then to use it you would say:

[PHP]
WhatEv whatEv = new WhatEv("Accounts");

try{
   //Loop of some sort
        whatEv.readLine();
}
catch(IOException ioex){
    ioex.printStackTrace();
}
[/PHP]

Then you could use this to read the file.  Not sure exactly what you are going for, but it sounds like you just want to wrap the BufferedReader Class.  Static is not what you want need here.

---

### Post by Griff on 2008-04-05
Thanks for the quick responses! It's been a while since I did any real programming and am a little rusty.  I'll try your suggestions after I get me some dinner.

Thanks,
Griff

---

