---
title: "Java: Process output in System.out"
date: 2005-10-20
forum: Programming Talk
---

### Post by Cyrus on 2005-10-20
Hi,

I start processes in a Java application. How can I get the output of those to the Java System console?

```
Process p = Runtime.getRuntime().exec("program");
```

p.getErrorStream()
p.getOutputStream() 

I guess they are the responsible methods - how to get them on System.out or System.err

---

### Post by ape on 2005-10-20
How about something like this:

 try {

           // start up the command in child process
           String cmd = "/bin/ls -lrt";
           Process child = Runtime.getRuntime().exec(cmd);

           // hook up child process output to parent
           InputStream lsOut = child.getInputStream();
           InputStreamReader r = new InputStreamReader(lsOut);
           BufferedReader in = new BufferedReader(r);

           // read the child process' output
           String line;
           while ((line = in.readLine()) != null)
               System.out.println(line);

       } catch (Exception e) {  // exception thrown

           System.out.println("Command failed!");

       }

---

### Post by Cyrus on 2005-10-20
This works really fine - thanks.

I just have 3 problems now:
1. The output is shown when the process is finished - as it is a long process (maybe  20 minutes) it would be good to see what the child process is doing.
2. If this is not possible it would be good to show (maybe in console) that this process is working.
3. child process is only returning error streams, also when they are actually no error messages

---

### Post by Cyrus on 2005-10-20
I have just another problem:

when I write:

mkdir "Folder name with blanks" - the folder with blanks is created

when I do the same with a java process:

Process mkdir = Runtime.getRuntime().exec("mkdir \"Folder name with blanks\"");

it creates following folders:

"Folder
name
with
blanks"

any ideas?

---

### Post by carbon-12 on 2005-10-20
[UNTESTED!]

Well I'm new to Java but can't you just do:

import java.io.File;
...

new File("Folder name with blanks").mkdirs();

---

