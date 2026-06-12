---
title: "Java java.lang.Process"
date: 2008-07-07
forum: Programming Talk
---

### Post by rivera151 on 2008-07-07
Hi.  I'm kinda working on a program/API that can handle compiling from source automatically.  Since I'm using standard compiling tools, I need to run command line stuff.  While this is easily accomplished with the java.lang.Process, there is something that has given me trouble.  The javadoc says the following:

```
Because some native platforms only provide limited buffer size for standard input and output streams, failure to promptly write the input stream or read the output stream of the subprocess may cause the subprocess to block, and even deadlock.
```

I have run into this issue, where the buffer when it gets too big, the process hangs.  I have tried to find a way of finding out if the process is running to then grab the exit value, but the function that grabs the exit value throws an exception instead of returning some sentinel value.  And the API doesn't have an IsRunning() method or a Running or Exited field.

There are two questions here:
1.  How can I test if a process is still running so that I can keep checking if the buffer has been modified, and then read from it, to clear the text and avoid a buffer overrun leading to a crash?

2.  How can I avoid running into this buffer overflow?

That is all.  Thak you.

---

### Post by tinny on 2008-07-07
> **rivera151 said:**
> Hi.  I'm kinda working on a program/API that can handle compiling from source automatically.  Since I'm using standard compiling tools, I need to run command line stuff.  While this is easily accomplished with the java.lang.Process, there is something that has given me trouble.  The javadoc says the following:

```
Because some native platforms only provide limited buffer size for standard input and output streams, failure to promptly write the input stream or read the output stream of the subprocess may cause the subprocess to block, and even deadlock.
```

I have run into this issue, where the buffer when it gets too big, the process hangs.  I have tried to find a way of finding out if the process is running to then grab the exit value, but the function that grabs the exit value throws an exception instead of returning some sentinel value.  And the API doesn't have an IsRunning() method or a Running or Exited field.

There are two questions here:
1.  How can I test if a process is still running so that I can keep checking if the buffer has been modified, and then read from it, to clear the text and avoid a buffer overrun leading to a crash?

2.  How can I avoid running into this buffer overflow?

That is all.  Thak you.

Yeah I know exactly what you are talking about.

What you need to do is do the buffering yourself (basically).

Here is some very ugly code to get you started. (Just trying to get the OP started)

```

public class CLIProcess implements Runnable {

    private static final int WAIT = 500;
    public static final int IN_PROCESS = -1;
    private boolean running;
    private int result = IN_PROCESS;
    private String command;
    private String errorMessage;
    private String successMessage;

    public CLIProcess(String command) {
        this.command = command;
        running = false;
    }

    public void run() {
        running = true;

        try {
            Runtime runTime = Runtime.getRuntime();
            Process process = runTime.exec(command);

            try {
                Thread.sleep(WAIT);
            } catch (InterruptedException ex) {
                Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
            }

            //error stream
            BufferedReader br = new BufferedReader(new InputStreamReader(process.getErrorStream()));
            StringBuilder bs = new StringBuilder();

            while (br.ready()) {
                bs.append(br.readLine());
            }

            errorMessage = bs.toString();
            errorMessage = errorMessage.trim();

            br = new BufferedReader(new InputStreamReader(process.getInputStream()));
            bs = new StringBuilder();
            while (br.ready()) {
                bs.append(br.readLine());
            }
            successMessage = bs.toString();
            successMessage = successMessage.trim();

            result = process.waitFor();
        } catch (InterruptedException ex) {
            Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
        } catch (IOException ex) {
            Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
        } finally {
            running = false;
        }
    }

    public int getResult() {
        return result;
    }
    
    public boolean isRunning() {
        return running;
    }
    
    public String getErrorMessage() {
        return errorMessage;
    }
    
    public String getSuccessMessage() {
        return successMessage;
    }
}




public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        try {
            CLIProcess pro = new CLIProcess("java -version");
            Thread thread = new Thread(pro);
            thread.start();
            Thread.sleep(500);
            while (pro.isRunning()) {
                Thread.sleep(500);
            }

            System.out.println(pro.getSuccessMessage());
            System.out.println(pro.getErrorMessage());
        } catch (InterruptedException ex) {
               Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
        }

    }
}


```

In summary, you have to read the stream when bytes are available.

Hope this helps

---

### Post by jamesstansell on 2008-07-07
If you'd like to look at samples of actual working code, hudson and ant would be likely projects to start with.

---

### Post by tinny on 2008-07-07
(My code runs :) )

Yeah good idea, have a look at ANT.

If you find a generic solution please post your findings :)

---

### Post by rivera151 on 2008-07-07
> **jamesstansell said:**
> If you'd like to look at samples of actual working code, hudson and ant would be likely projects to start with.

Looks like ANT already does what I want, but still it is a good code example, thanks for posting.

Update: Actually, I'm not sure how it can help me, but I'll look at it.

As for the code example, I'm looking at it and I have some questions:

I see that you implement the Runnable interface so you can wrap the object within a thread.  You pass the argument to the thread, and call the Thread.start() function, which in turn calls the run() function overridden in your code.  This is as far as I get.

I really can't see how this gets data from the processes' standard output when it is available rather than starting the process, grabbing some output that is available shortly after starting the asynchronous process, and then waiting for the program to exit.  

The problem is that sometimes programs like "make" will suddenly stop standard output as they are in a lengthy compile, thus, I am anticipating that BufferedReader.ready() will return false (since there is no more new data to read) and the while loop will end prematurely.

I'll give it a try anyway and let you know.

Update 2: Yep, just as I expected.  I'm trying to download the source for my jdk but apparently I need credentials for the svn.  It's strange that this feature is not part of jdk, since I'm pretty sure C# has a much more useful process class.

(googling . . . )

Yep.  System.Diagnostics.Process has a HasExited Field/Property.  I might just port it to C# cause it just might be easier, given a decent IDE for mono.

---

