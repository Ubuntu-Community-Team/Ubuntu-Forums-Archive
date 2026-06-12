---
title: "Java Swing Multithread never exits"
date: 2008-06-10
forum: Programming Talk
---

### Post by smmalis on 2008-06-10
I have a program (SuDoKu solver) that a swing program with two threads.  The main thread does everything except that the second thread handles the solve method.  This avoids GUI freeze while solve is running.  However, for some reason, since I added the thread code the program never exits properly.  By that I mean that if you close the window the java process is still running.  If you run it from the terminal, it never allows you to enter another command, it just keeps running doing nothing.  Any ideas?

---

### Post by NormR2 on 2008-06-10
Does the program call System.exit(0) when the window is closed? That should end the Java VM and stop all threads. Without the exit() call, the program will continue to run even without a window.

What **happens/is supposed to happen**   when the window is closed?

---

### Post by Woei on 2008-06-10
> **smmalis said:**
> I have a program (SuDoKu solver) that a swing program with two threads.  The main thread does everything except that the second thread handles the solve method.  This avoids GUI freeze while solve is running.  However, for some reason, since I added the thread code the program never exits properly.  By that I mean that if you close the window the java process is still running.  If you run it from the terminal, it never allows you to enter another command, it just keeps running doing nothing.  Any ideas?

You want to create a so called "daemon" thread, which is just an ordinary thread except that it doesn't prohibit the JVM from stopping if it or a number of other daemon threads are still running. See [Thread's JavaDoc](http://java.sun.com/javase/6/docs/api/java/lang/Thread.html#setDaemon(boolean)) for more information.

---

### Post by Npl on 2008-06-10
first you shouldnt intitalise a GUI from the main thread, [read this]("http://java.sun.com/docs/books/tutorial/uiswing/concurrency/initial.html"). It likely doesnt matters if you have only 1 Windows, but if you open multiple you are running into coherency-issues - Swing aint threadsafe!

As for the App not exiting, thats normal. You need to explicitely call System.exit(0) as NormR2 already said. Swing can handle more than 1 Window and if its started (creating first window) the GUI-Thread(s) will continue to live if you just close Windows.
Theres a shortcut somewhere to change the window-closing behaviour to also exiting app, but I cant remember now.

Edit: its the method .setDefaultCloseOperation(int), call it with WindowConstants.EXIT_ON_CLOSE

---

