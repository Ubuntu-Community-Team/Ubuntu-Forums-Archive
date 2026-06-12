---
title: "[java] Stream output from wget"
date: 2008-06-24
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-24
Hello,

I was wondering how i would go about from streaming the output from wget. The example i would like to use would be this command:

*wget --progress=dot  [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso)*

Here is the code i had tried to use.
```

package main;

import java.io.*;

public class Java6 {
	public static void main(String[] args) throws IOException{
        
		Process p = Runtime.getRuntime().exec("wget");
        // read the standard output of the command

       BufferedReader stdInput = new BufferedReader(new InputStreamReader(p.getInputStream()));

       String s=null;
       String result=null;
       
       while (!procDone(p)) {
    	   while((s=stdInput.readLine()) !=null){
               result = result+s+"\n";
               System.out.println(result);
           }
      }

       stdInput.close();
	}
	
   public static boolean procDone(Process p) {
       try {
           @SuppressWarnings("unused")
	   final int v = p.exitValue();
           return true;
       }
       catch(IllegalThreadStateException e) {
           return false;
       }
   }
}

```

Thank you for any help
~Cody Woolaver

---

### Post by xlinuks on 2008-06-24
What are you trying to read?
The current state of the download or the bytes that "wget" is actually downloading?
In first case - it's gonna be a dirty work.
In second one - impossible.

---

### Post by dracayr on 2008-06-24
println already inserts a linebreak,so:

result = result + s; //without the + "\n"

however, now let's assume wget prints these lines: 
Line1
Line2
Line3

your program would output

Line1
Line1
Line2
Line1
Line2
Line3

because it always adds the last result (so all the previous lines) to the current line. So:

result = s; //wich makes result kind of unnecessary


dracayr

---

### Post by Pyro.699 on 2008-06-24
> **xlinuks said:**
> What are you trying to read?
The current state of the download or the bytes that "wget" is actually downloading?
In first case - it's gonna be a dirty work.
In second one - impossible.

I'm trying to get the current state of the download, and i don't mind the dirt ;)

[QUOTE=dracayr]
println already inserts a linebreak,so:

result = result + s; //without the + "\n"

however, now let's assume wget prints these lines:
Line1
Line2
Line3

your program would output

Line1
Line1
Line2
Line1
Line2
Line3

because it always adds the last result (so all the previous lines) to the current line. So:

result = s; //wich makes result kind of unnecessary


dracayr
[/QUOTE]

I have found a simpler way to achieve this:
```

package main;

import java.io.*;

public class Java6 {
	public static void main(String[] args) throws IOException{
        
		Process p = Runtime.getRuntime().exec("wget --progress=dot http://mirror.csclub.uwaterloo.ca/ubuntu-releases/hardy/ubuntu-8.04-alternate-i386.iso");

		OutputStream fout= p.getOutputStream();
		OutputStream bout= new BufferedOutputStream(fout);
		OutputStreamWriter out = new OutputStreamWriter(bout);
		out.write("locals");
		
		InputStreamReader reader = new InputStreamReader ( p.getInputStream () );
		BufferedReader buf_reader = new BufferedReader ( reader );
		String line;

		while ((line = buf_reader.readLine ()) != null)
		{
			System.out.println (line);
		}
	}
}

```

The problem i have encountered is that it is not a "live feed" it will print out all the data after the file has finished downloading. To make my goals simpler, i am making a download manager (with allot of custom modifications).

Thanks for all your help
~Cody Woolaver

---

### Post by geirha on 2008-06-24
wget prints the "progress dots" to stderr (that way the file can be downloaded to stdout with -O -), so try reading from p.getErrorStream()

---

