---
title: "Java Shutdown Hook and SIGTERM"
date: 2008-10-11
forum: Programming Talk
---

### Post by HuseUrDaddy on 2008-10-11
Hi,

I created a Java Gui Program (using SWT) and Java's Shutdown Hook doesn't work in Ubuntu.

I am using Sun Jre 1.6 installed via the Synaptic Package Manager.

When my application starts, I am creating a lock file and when my application successfully shutsdown, I am deleting the lock file. The delete lock file code is in the shutdown hook thread.

If I leave my application running while I log off or restart Ubuntu, I still see the lock file, meaning, the shutdown hook never got fired.

If I END PROCESS the java process while my application is running (via System Monitor's Processes tab) then the shutdown hook works.

However, if I KILL PROCESS the java process, then the shutdown hook doesn't work.

So, that makes me believe that when Ubuntu shutsdown, restarts or when the user logs off, Ubuntu sends Kill Process (SIGKILL) to the Java process and may be to all processes instead of sending SIGTERM?

One solution I thought was to create a script which will run during Ubuntu's Shutdown and will simply send SIGTERM to my app's Java process.

But its an over-kill. LoL. No puns intended. Any other suggestions will be greatly appreciated.

Thanks.

---

### Post by jespdj on 2008-10-11
This is not a problem that's specific to Ubuntu, the Ubuntu version of Java or Java in general.

The shutdown hook can't be guaranteed to run. When you kill a process (with SIGKILL), the process doesn't get a chance to clean up; the operating system just deletes the process from memory immediately. SIGKILL is meant to stop processes that are in a state where they can't be stopped gracefully.

Read the Java API documentation of the method Runtime.addShutdownHook() carefully. It says:
> In rare circumstances the virtual machine may abort, that is, stop running without shutting down cleanly. This occurs when the virtual machine is terminated externally, for example with the SIGKILL signal on Unix or the TerminateProcess call on Microsoft Windows. The virtual machine may also abort if a native method goes awry by, for example, corrupting internal data structures or attempting to access nonexistent memory. If the virtual machine aborts then no guarantee can be made about whether or not any shutdown hooks will be run. 
So, you should not design your program in such a way that it depends on the shutdown hook to always execute.

---

### Post by Reiger on 2008-10-11
In this case you can compensate for having the clean-up code extracted to a (public static) method of its own.

Now, when you *start* your program you can check for existance of the file indicating a bad shutdown, and clean up the mess before actually starting the program. A bit like a recovery of 'lost' data.

---

### Post by HuseUrDaddy on 2008-10-13
> **Reiger said:**
> In this case you can compensate for having the clean-up code extracted to a (public static) method of its own.

Now, when you *start* your program you can check for existance of the file indicating a bad shutdown, and clean up the mess before actually starting the program. A bit like a recovery of 'lost' data.

Thanks. My program is already doing that.

Also, I am using HSQLDB for embedded database and it already has a mechanism to detect and recover from abnormal db shutdown.

The Java Shutdown hook works as expected in Windows, Mac and Solaris. Looks like I am out of luck when it comes to Linux. I guess I have to prevent my application from minimizing itself into the system tray otherwise the user might forget to close it when restarting or logging off from Linux.

---

### Post by cl333r on 2008-10-14
There's a powerful and crossplatform solution
```

javax.swing.JOptionPane.showMessageDialog( null, "Attention", "Please press your computer's shutdown button", 1 ); 

```

---

### Post by Reiger on 2008-10-14
I'm sorry, but I don't think people are going to enjoy that one -- especially not as there is no guarantee that it will work on Linux (again) :

requiring people to shutdown next time they start up after a shutdown... ?

At any rate your code would improve if you didn't use a predefined int, but rather one of the JOptionPane constants as it (should) be compatible with any future version of Javax Swing that doesn't deprecate JOptionPanes altogether. :)

What the OP can do, however is looking into ways of sending a signal to his app -- likely through executing scripts on shutdown...

---

### Post by cl333r on 2008-10-14
That was sarcasm

---

### Post by Reiger on 2008-10-14
I'm sorry, my post informs me I should've gone to bed (and sleep) by 3:26. Or at least certainly not engaging in something remotely intelligent. ;)

---

### Post by i30817 on 2012-07-12
Bump. This is terrible. How the hell is a program supposed to save state if a kill is sent without a first sending a sigterm? (*Which is what i think is happening on restart*)

---

