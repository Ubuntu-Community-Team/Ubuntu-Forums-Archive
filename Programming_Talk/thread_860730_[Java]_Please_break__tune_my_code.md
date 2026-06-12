---
title: "[Java] Please break / tune my code"
date: 2008-07-15
forum: Programming Talk
---

### Post by tinny on 2008-07-15
Hi all

(I have coders block :( )

I am looking to write a robust generic command line interface class for Java. I have hacked together something that is working quite well. I am hoping that I can get a few people to try different commands and see how well it works on machines other than my own. Also suggestions on how the code could be tuned are appreciated. 

Im not 100% happy with the “processErrorMessage” and “processResultMessage” methods.

Who knows, maybe it works well and people will actually like it...?

```

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;

public class CLIProcess implements Runnable {

    private static final int INIT_WAIT = 1000;
    private static final int STREAM_WAIT = 1000;
    public static final int IN_PROGRESS = -1;
    private boolean running;
    private int result = IN_PROGRESS;
    private String command;
    private String errorMessage;
    private String successMessage;
    private Process process;

    public CLIProcess(String command) {
        this.command = command;
        running = false;
    }

    public void run() {
        running = true;

        try {
            Runtime runTime = Runtime.getRuntime();
            process = runTime.exec(command);

            try {
                Thread.sleep(INIT_WAIT);
            } catch (InterruptedException ex) {
                ex.printStackTrace();
            }

            errorMessage = processStream(process.getErrorStream());
            successMessage = processStream(process.getInputStream());

            result = process.waitFor();
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        } catch (IOException ex) {
            ex.printStackTrace();
        } finally {
            running = false;
        }
    }
    
    private String processStream(InputStream is) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(is));
        StringBuilder bs = new StringBuilder();
        
        while (br.ready()) {
            bs.append(br.readLine());
            try {
                Thread.sleep(STREAM_WAIT);
            } catch (InterruptedException ex) {
                ex.printStackTrace();
            }
        }
        return bs.toString().trim();
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

```

```

public class Main {

    public static void main(String[] args) {
        try {
            CLIProcess pro = new CLIProcess("gksu apt-get update");
            Thread thread = new Thread(pro);
            thread.start();
            Thread.sleep(500);
            while (pro.isRunning()) {
                Thread.sleep(500);
            }

            System.out.println("Result Code: " + pro.getResult());
            System.out.println("Result: " + pro.getSuccessMessage());
            System.out.println("Error: " + pro.getErrorMessage());
        } catch (InterruptedException ex) {
               ex.printStackTrace();
        }
    }
}

```

Cheers :)

---

### Post by txcrackers on 2008-07-16
I have one very simple question: what the heck are you sleeping for?

I'd go back and re-look at ProcessBuilder and think more about multi-threading instead of a single thread (possibly even nio).

---

### Post by Quikee on 2008-07-16
processErrorMessage() and processResultMessage() do exactly the SAME thing!

---

### Post by tinny on 2008-07-16
> **txcrackers said:**
> I have one very simple question: what the heck are you sleeping for?

I'd go back and re-look at ProcessBuilder and think more about multi-threading instead of a single thread (possibly even nio).

Have you run the code? Did it work? Try setting the sleeps to 0 and see what happens.

Also it is a multi-threaded application have a look at the main method. You have your main method of execution and a "CLIProcess" thread.

Ill have a look at ProcessBuilder.

---

### Post by ceclauson on 2008-07-16
Hmmm...interesting problem :-)

I went ahead and took a crack at it.  Here's my solution (I tried it and it seems to work):

```


public class CLIProcess implements Runnable {

	//the command associated with this CLIProcess
	private final String command;
	//whether or not the process is running
	private boolean processIsRunning = false;
	//the result of the last process that ran;
	private int result;

	public CLIProcess(String command) {
		this.command = command;
	}

	//synchronized so than only one thread can be
	//in this method at a time
	public synchronized void run() {
		//start the process executing the command
		final Process process = Runtime.getRuntime().exec(command);
		//and record that this is being done
		processIsRunning = true;

		//references to the error and output streams of the process
		//stream representing standard error
		final InputStream errorStream = process.getErrorStream();
		//confusingly, stream representing standard out
		final InputStream outputStream = process.getInputStream();
		//create a new thread whose sole purpose in life is to
		//flush the output stream and error stream to standard
		//out and standard error
		new Thread(new Runnable() {
			void run() {
				//thread simply keeps flushing while
				//the process is running
				while(processIsRunning) {
					flushStreamToError(errorStream);
					flushStreamToOutput(outputStream);
				}
				//when process ends, do one more flush
				flushStreamToError(errorStream);
				flushStreamToOutput(outputStream);
				//and then die
			}
		}).start();
		
	private static void flushStreamToError(InputStream is) {
		while((int i = is.read) != -1)
			System.err.write((byte) i);

	}

	private static void flushStreamToOutput(InputStream is
		while((int i = is.read) != -1)
			System.out.write((byte) i);
	}
}

```

This class is similar to yours in that it runs the command.  But it's different in that instead of saving the command output, it prints it to standard out and standard error in real time.  The thread that enters the run method "splits" -- one thread monitors the output of the process and prints it as it comes, and the other monitors the process to see if it's finished.  Once the process is finished, the second thread notifies the first thread of this, which dies, and then the second thread (i.e., the original thread) exits.

However, if you're not interested in getting the output in real time, but caching it for later retrieval, which it seems you're interested in doing, you could easily do this with just one thread.  Just have the thread wait on the process, and then when the process is over, do all of the flushing of the output and error at the end.

Again, it's an interesting problem.  Hopefully you find this post helpful.

Cooper

---

### Post by tinny on 2008-07-16
> **Quikee said:**
> processErrorMessage() and processResultMessage() do exactly the SAME thing!

Yeah, they are pretty much the same.

They do read different streams and build different Strings.

Ive created a generic "processStream" method.

See my edited original post.

Of course none of this makes my code more robust or helps me know what other commands run / dont run with this code.

---

### Post by tinny on 2008-07-16
Thanks for giving it a crack ceclauson.

I think you may have a cut and paste error in your code?

---

### Post by drubin on 2008-07-16
May I ask why you would want to do this in java?

---

### Post by Diabolis on 2008-07-16
> **rubinboy said:**
> May I ask why you would want to do this in java?

Might be handy for Java applications that use other programs written in different languages. Probably I use some of this code, of course I'll post back If something does not work.

---

### Post by drubin on 2008-07-16
I have an idea :) That I have from some old code that I wrote a while back... 

Will post some of it when i get home.

---

### Post by Diabolis on 2008-07-16
I tried to run ceclauson code, but It didn't work as I expected. Apparently the commands were executed, the gksudo popped up, but I didn't see any output being printed. So I modified it. I don't fully understand threads yet, so I couldn't figure out how to stop the "FlusherThread" before it fires the IOException, If its possible.

[PHP]package util;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;

public class CLIProcess implements Runnable {

    //the command associated with this CLIProcess
    private final String command;
    //whether or not the process is running
    private boolean processIsRunning = false;

    private enum StreamType {
        OUTPUT, ERROR
    };

    public static void main(String[] args) {
        String command = "gksu apt-get update";
        CLIProcess cliProcess = new CLIProcess(command);
        cliProcess.run();
    }

    public CLIProcess(String command) {
        this.command = command;
    }

    //synchronized so than only one thread can be
    //in this method at a time
    public synchronized void run() {
        try {
            //start the process executing the command
            final Process process = Runtime.getRuntime().exec(command);
            //and record that this is being done
            processIsRunning = true;

            //references to the error and output streams of the process
            //stream representing standard error
            final InputStream errorStream = process.getInputStream();
            //confusingly, stream representing standard out
            final InputStream outputStream = process.getInputStream();
            //create a new thread whose sole purpose in life is to
            //flush the output stream and error stream to standard
            //out and standard error
            FlusherThread flusherThread = new FlusherThread(errorStream, outputStream);
            flusherThread.start();
            
            //Wait until the process ends
            process.waitFor();
            
            //Stop FlusherThread
            flusherThread.stop();
            
        } catch (IOException ex) {
            System.out.println("CLIProcess IOException: " + ex.getMessage());
        } catch (InterruptedException ex) {
            System.out.println("CLIProcess InterruptedException: " + ex.getMessage());
        }
    }

    private class FlusherThread extends Thread {

        private InputStream errorStream;
        private InputStream outputStream;

        public FlusherThread(InputStream errorStream, InputStream outputStream) {
            this.errorStream = errorStream;
            this.outputStream = outputStream;
        }

        @Override
        public void run() {
            //thread simply keeps flushing while
            //the process is running
            while (processIsRunning) {
                this.flushStream(this.errorStream, StreamType.ERROR);
                this.flushStream(this.outputStream, StreamType.OUTPUT);
            }
            //when process ends, do one more flush
            this.flushStream(this.errorStream, StreamType.ERROR);
            this.flushStream(this.outputStream, StreamType.OUTPUT);
        //and then die
        }

        private void flushStream(InputStream inputStream, StreamType type) {
            try {
                BufferedReader br = new BufferedReader(new InputStreamReader(inputStream));
                String line;
                while ((line = br.readLine()) != null) {
                    if (type == StreamType.ERROR) {
                        System.err.println(line);
                    }
                    if (type == StreamType.OUTPUT) {
                        System.out.println(line);
                    }
                }
                br.close();
            } catch (IOException ex) {
                System.out.println("FlusherThread IOException: " + ex.getMessage());
                this.stop();
            }
        }
    }
}[/PHP]

---

### Post by ceclauson on 2008-07-16
Ah, yes.  I called "getInputStream" for both the output stream and the error stream.  I fixed it.

Thank you.

---

### Post by tinny on 2008-07-16
Im hoping someone can provide some magic within the "processStream" method.


This is what I am concerned will happen:

If you are running the "apt-get update" command and one of the update site "gets" takes longer than STREAM_WAIT to return then you will exit the read loop and miss the rest of the input stream.

Does "br.ready()" just return true if there are no bytes in the stream (I think it does this), or is it smart enough to know that the stream has not been close and we may receive more bytes in the future.

```

    private String processStream(InputStream is) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(is));
        StringBuilder bs = new StringBuilder();
        
        while (br.ready()) {
            bs.append(br.readLine());
            try {
                Thread.sleep(STREAM_WAIT);
            } catch (InterruptedException ex) {
                ex.printStackTrace();
            }
        }
        return bs.toString().trim();
    }


```

Also ive noticed that "process.waitFor()" will block until the input streams have been fully read and the process has finished. Maybe I need an additional thread that will call "waitFor" and then when it returns set a "finishedStreaming" variable. Then I will only exit the "processStream" method once "finishedStreaming" is set to true, while "finishedStreaming" is false I will continue to check for bytes from the stream.

Having said all this I now need to create a thread for each stream (error and input stream). They will run until "finishedStreaming" is true.

This probably sounds quite confusing, ill try and put all this into code later tonight.

---

### Post by ceclauson on 2008-07-17
I tried this code and it worked on my system.  It runs apt-get update.

```

import java.io.*;

public class CLIProcess implements Runnable {

	//the command associated with this CLIProcess
	private final String command;
	//whether or not the process is running
	private boolean processIsRunning = false;
	//the result of the last process that terminated
	private int result;

	public CLIProcess(String command) {
		this.command = command;
	}

	//for multithreaded error handling
	private Exception cachedException;
	
	//synchronized so than only one thread can be
	//in this method at a time
	public synchronized void run() {
		try {
			//start the process executing the command
			final Process process = Runtime.getRuntime().exec(command);
			//and record that this is being done
			processIsRunning = true;

			//references to the error and output streams of the process
			//stream representing standard error
			final InputStream errorStream = process.getErrorStream();
			//confusingly, stream representing standard out
			final InputStream outputStream = process.getInputStream();
			
			
			//this part is just for error handling.
			//cache a reference to this thread
			final Thread blockingThread = Thread.currentThread();
			
			//create a new thread whose sole purpose in life is to
			//flush the output stream and error stream to standard
			//out and standard error
			new Thread(new Runnable() {
				public void run() {
					try {
						//thread simply keeps flushing while
						//the process is running
						while(processIsRunning) {
							flushStreamToError(errorStream);
							flushStreamToOutput(outputStream);
						}
						//when process ends, do one more flush
						flushStreamToError(errorStream);
						flushStreamToOutput(outputStream);
						//and then die
					} catch(IOException e) {
						//this shouldn't really happen, and could be handled a few ways.
						//We'll just cause execution of this method to end with a runtime
						//exception.
						
						//cache a reference to the exception so that the looping thread
						//can throw it
						cachedException = e;
						//causes the run() method to return, at which point it will throw
						//the exception we cached
						blockingThread.interrupt();
						//this thread dies here.
					}
				}
			}).start();

			//now have this thread block until the process is over
			try{
				result = process.waitFor();
			} catch(InterruptedException e) {
				//this will happen if the looping thread excounters an exception
				throw new RuntimeException("Trouble processing command " + command + ": " + cachedException);
			}
		} catch(IOException e) {
			throw new RuntimeException("Trouble processing command " + command + ": " +e);
		} finally {
			//this should kill the thread that is handling the output
			//and error
			processIsRunning = false;

			//exit
		}
	}

	private static void flushStreamToError(InputStream is) throws IOException {
		int i;
		while((i = is.read()) != -1)
			System.err.write((byte) i);

	}

	private static void flushStreamToOutput(InputStream is) throws IOException {
		int i;
		while((i = is.read()) != -1)
			System.out.write((byte) i);
	}
	
	public static void main(String[] args) {
		new CLIProcess("gksu apt-get update").run();
	}
}

```

I got the same output as I got in the terminal, so I think it works.

By the way, Diabolis, you probably shouldn't put your name on code that was mostly written by someone else...

---

### Post by tinny on 2008-07-17
Thanks for posting that code.

I am looking for a solution that will store any returned process results in a String. Then this returned String can later be parsed by some other external code.

Further to my previous post, I have put together some code that I am quite happy with.

Some of the changes / additions I have made are as follows:

The CLIProcess thread now relies on the “process.waitFor()” method call for confirmation that the runtime process has finished executing (this method blocks until the runtime process has finished). 

“StreamWorker” threads are now used to process the two input streams so that they can be continually scanned in parallel until the “process.waitFor()” method has returned with an exit value from the runtime process.

The rest of the changes are just basic refactoring mods.

I've tried to test this code to deal with pauses etc.. in the runtime process. If I wait several minutes before inputing a password for “gksu” it is now robust enough to execute as expected.

New CLIProcess code...
[PHP]
/**
 * @author Chuck Norris
 */

package org.lang;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;

/**
 * A robust command line interface process for executing commands with the 
 * current platforms runtime.
 */
public class CLIProcess implements Runnable {
    
    /**
     * Default thread wait time for start-up and shut-down of the CLI process.
     */
    private static final int INIT_WAIT_DEFAULT = 1000;
    
    /**
     * Default input stream scan wait time.
     */
    private static final int STREAM_WAIT_DEFAULT = 1000;
    
    /**
     * Default result value.
     */
    public static final int IN_PROGRESS = -1;
    
    /**
     * CLI process running status.
     */
    private boolean running;
    
    /**
     * CLI process result;
     */
    private int result = IN_PROGRESS;
    
    /**
     * Wait time for start-up and shut-down of the CLI process.
     */
    private int initWait;
    
    /**
     * Input stream scan wait time.
     */
    private int streamWait;
    
    /**
     * The command to execute.
     */
    private String command;
    
    /**
     * The returned error message.
     */
    private String errorMessage;
    
    /**
     * The success error message.
     */
    private String successMessage;
    
    /**
     * The runtime process executing the command.
     */
    private Process process;
    
    /**
     * Init the CLI process.
     * @param command the command to execute.
     * @param initWait wait time for start-up and shut-down of the CLI process.
     * @param streamWait Input stream scan wait time.
     */
    public CLIProcess(String command, int initWait, int streamWait) {
        this.command = command;
        this.initWait = initWait;
        this.streamWait = streamWait;
        running = false;
    }
    
    /**
     * Init the CLI process.
     * @param command the command to execute.
     */
    public CLIProcess(String command) {
        this(command, INIT_WAIT_DEFAULT, STREAM_WAIT_DEFAULT);
    }

    /**
     * DO NOT call this method directly.
     */
    public void run() {
        running = true;

        try {
            //Init the runtime process.
            Runtime runTime = Runtime.getRuntime();
            process = runTime.exec(command);
            try {
                Thread.sleep(initWait);
            } catch (InterruptedException ex) {
                ex.printStackTrace();
            }

            //Start the stream workers and wait till the process has finished
            //executing.
            StreamWorker successWorker = new StreamWorker(process.getInputStream(), streamWait);
            StreamWorker errorWorker = new StreamWorker(process.getErrorStream(), streamWait);
            new Thread(successWorker).start();
            new Thread(errorWorker).start();
            result = process.waitFor();
            
            //Retrieve the stream results once the stream worker threads have finished.
            while (successWorker.isWorkerRunning() || errorWorker.isWorkerRunning()) {
                try {
                    Thread.sleep(initWait);
                } catch (InterruptedException ex) {
                    ex.printStackTrace();
                }
            }
            successMessage = successWorker.getMessageResult();
            errorMessage = errorWorker.getMessageResult();
          
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        } catch (IOException ex) {
            ex.printStackTrace();
        } finally {
            running = false;
        }
    }
    
    /**
     * Get the processes returned result code.
     * @return result code. -1 if still processing.
     */
    public int getResult() {
        return result;
    }
    
    /**
     * Check if the CLI process is still running.
     * @return true if running.
     */
    public boolean isRunning() {
        return running;
    }
    
    /**
     * Get the error message if any.
     * @return error message.
     */
    public String getErrorMessage() {
        return errorMessage;
    }
    
    /**
     * Get the success message if any.
     * @return success message.
     */
    public String getSuccessMessage() {
        return successMessage;
    }
    
    /**
     * This is a small worker class that is used to process a "processes" input
     * streams.
     */
    private class StreamWorker implements Runnable {
        
        /**
         * Input stream scan wait time.
         */
        private int streamWait;
        
        /**
         * Worker thread running status.
         */
        private boolean workerRunning;
        
        /**
         * Input stream being processed.
         */
        private InputStream is;
        
        /**
         * The result message if any that was obtained from the input stream.
         */
        private String messageResult;

        /**
         * Init a stream worker.
         * @param is input stream to process.
         * @param streamWait input stream wait period.
         */
        public StreamWorker(InputStream is, int streamWait) {
            this.is = is;
            this.streamWait = streamWait;
            workerRunning = false;
            messageResult = null;
        }
        
        /**
         * Init a stream worker.
         * @param is input stream to process.
         */
        public StreamWorker(InputStream is) {
            this(is, STREAM_WAIT_DEFAULT);
        }

        /**
         * DO NOT call this method directly.
         */
        public void run() {
            workerRunning = true;
            messageResult = processStream();
            workerRunning = false;
        }

        /**
         * Scan the supplied input stream.
         * @return message obtained from input stream.
         */
        private String processStream() {
            BufferedReader br = new BufferedReader(new InputStreamReader(is));
            StringBuilder bs = new StringBuilder();
            try {
                //Continue to scan if the CLI process is still processing.
                while (result == IN_PROGRESS) {
                    if (br.ready()) {
                        bs.append(br.readLine());
                        try {
                            Thread.sleep(streamWait);
                        } catch (InterruptedException ex) {
                            ex.printStackTrace();
                        }
                    }
                }
            } catch (IOException ex) {
                ex.printStackTrace();
            } finally {
                return bs.toString().trim();
            }
        }

        /**
         * Check if this stream worker thread is still running.
         * @return true if still running.
         */
        public boolean isWorkerRunning() {
            return workerRunning;
        }

        /**
         * The message obtained from the input stream.
         * @return message.
         */
        public String getMessageResult() {
            return messageResult;
        }
    }
}
[/PHP]

Same main method...
[PHP]
    public static void main(String[] args) {
        try {
            CLIProcess pro = new CLIProcess("gksu apt-get update");
            Thread thread = new Thread(pro);
            thread.start();
            Thread.sleep(500);
            while (pro.isRunning()) {
                Thread.sleep(500);
            }
            
            System.out.println("Result Code: " + pro.getResult());
            System.out.println("Result: " + pro.getSuccessMessage());
            System.out.println("Error: " + pro.getErrorMessage());
        } catch (InterruptedException ex) {
               ex.printStackTrace();
        }
    }
[/PHP]

I have also attached the source code in a zip file.

What do you think?

---

### Post by Diabolis on 2008-07-17
Yeah, I forgot. I tweaked the code in Netbeans and it adds my name to every class I make. Anyway, nobody can really claim that code, if you google a bit the core part of it is in examples in a few other sites.

If you want to parse the output of the command, store it in a global variable, probably a String. Since you are using SwingWorker, the thread will run in a background so the event dispatch thread is still responsive. This means you can display the output in a TextComponent while the user works on something else.

Maybe something like this:
[PHP]
package util;

import java.awt.Dimension;
import java.awt.Toolkit;
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;
import javax.swing.JFrame;
import javax.swing.JScrollPane;
import javax.swing.JTextArea;
import javax.swing.SwingWorker;

/**
 *
 * @author Gastón I. Silva
 */
public class CommandExecuter {

    public static void main(String[] args) {
        CommandExecuter ce = new CommandExecuter();
        ce.run();
    }
    
    public void run() {
        String[] command = {"gksudo","apt-get update"};
        ExecuteCommand ec = new ExecuteCommand(command);
        ec.execute();
    }

    /*
     * 
     * Worker Thread
     * 
     */
    private class ExecuteCommand extends SwingWorker<String, String> {

        private String[] command;
        private JFrame frame;
        private JTextArea textArea;

        public ExecuteCommand(String[] command) {
            this.command = command;
                this.frame = new JFrame("Command Running");
                Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
                this.textArea = new JTextArea(20, 70);
                this.textArea.setEnabled(false);
                this.frame.add(new JScrollPane(this.textArea));
                this.frame.pack();
                int x = (int) ((screenSize.getWidth() / 2) - (this.textArea.getWidth() / 2));
                int y = (int) ((screenSize.getHeight() / 2) - (this.textArea.getHeight() / 2));
                this.frame.setLocation(x, y);
                this.frame.setVisible(true);
        }

        @Override
        protected String doInBackground() {
            try {
                Process process = Runtime.getRuntime().exec(this.command);
                    //Print command
                    String output = "";
                    for (int i = 0; i < this.command.length; i++) {
                        output += this.command[i] + " ";
                    }
                    output += "\n";
                    this.textArea.setText(output);

                    //Read InputStream
                    this.ProcessCommandOutput(process.getInputStream());

                    //Read ErrorStream
                    this.ProcessCommandOutput(process.getErrorStream());
                    
            } catch (Exception ex) {
                ErrorPane.showErrorMessage("CommandExecuter: \ncommand: " + this.command, ex);
            }
            return this.textArea.getText();
        }

        private void ProcessCommandOutput(InputStream inputStream) throws IOException {
            BufferedReader br = new BufferedReader(new InputStreamReader(inputStream));
            String text = this.textArea.getText();
            String line;
            while ((line = br.readLine()) != null) {
                text += (line + '\n');
                this.textArea.setText(text);
            }
            br.close();
        }

    }
}
[/PHP]

---

### Post by tinny on 2008-07-17
Why are we talking about Swing now???

I just want a process that will reliably obtain a runtime process result as a String so that some external Java code can interpret the result and perform some logic that is dependant on the result.   

Has anyone run my code? :(

The last code I posted seems to be running well for me. Can anyone test it with some other interesting commands?

---

### Post by nanolithium on 2008-07-17
You don't need to sleep at all, since readLine() blocks by itself. This seems to work for me:

```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStream;
import java.io.InputStreamReader;

import java.io.InputStreamReader;

public class CLIProcess extends Thread {
    private int result = -1;
    private String command;
    private String errorMessage;
    private String successMessage;
    private Process process;

    public CLIProcess(String command) {
        this.command = command;
    }

    public void run() {
        try {
            process = Runtime.getRuntime().exec(command);
            errorMessage = processStream(process.getErrorStream());
            successMessage = processStream(process.getInputStream());
            result = process.waitFor();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    
    private String processStream(InputStream is) throws IOException {
	BufferedReader br = new BufferedReader(new InputStreamReader(is));
        StringBuilder bs = new StringBuilder();
		while (true) {
			String c = br.readLine();
			if (c == null)
				break;
			bs.append(c);
			bs.append("\n");
		}
        return bs.toString().trim();
    }
    
    public int getResult() {
        return result;
    }
    
    public String getErrorMessage() {
        return errorMessage;
    }
    
    public String getSuccessMessage() {
        return successMessage;
    }
}

```

```
public class Main {
	public static void main(String[] args) {
		try {
			CLIProcess pro = new CLIProcess("gksu apt-get update");
			pro.start();
			pro.join();
			System.out.println("Result Code: " + pro.getResult());
			System.out.println("Result: " + pro.getSuccessMessage());
			System.out.println("Error: " + pro.getErrorMessage());
		} catch (InterruptedException ex) {
			 ex.printStackTrace();
		}
	}
}

```

---

### Post by tinny on 2008-07-18
I have made 3 more small changes to my code.

I have changed the "processStream" method from this...

[PHP]
        private String processStream() {
            BufferedReader br = new BufferedReader(new InputStreamReader(is));
            StringBuilder bs = new StringBuilder();
            try {
                //Continue to scan if the CLI process is still processing.
                while (result == IN_PROGRESS) {
                    if (br.ready()) {
                        bs.append(br.readLine());
                        try {
                            Thread.sleep(streamWait);
                        } catch (InterruptedException ex) {
                            ex.printStackTrace();
                        }
                    }
                }
            } catch (IOException ex) {
                ex.printStackTrace();
            } finally {
                return bs.toString().trim();
            }
        } 
[/PHP]

To this...

[PHP]
        private String processStream() {
            BufferedReader br = new BufferedReader(new InputStreamReader(is));
            StringBuilder bs = new StringBuilder();
            try {
                //Continue to scan if the CLI process is still processing.
                while (result == IN_PROGRESS) {
                    if (br.ready()) {
                        bs.append(br.readLine() + "\n");
                    } else {
                        try {
                            Thread.sleep(streamWait);
                        } catch (InterruptedException ex) {
                            ex.printStackTrace();
                        }
                    }
                }
            } catch (IOException ex) {
                ex.printStackTrace();
            } finally {
                return bs.toString().trim();
            }
        }
[/PHP]

1. The thread will now wait (sleep) if the stream is not ready (br.ready() == false) allowing the stream to build the next line.

2. If the stream is ready (br.ready() == true) we will keep reading lines until it is no longer ready (with out waiting).

3. Each read line now has a line feed appended (\n). The last line feed is trimmed before the result is returned.

I have attached the code.

---

