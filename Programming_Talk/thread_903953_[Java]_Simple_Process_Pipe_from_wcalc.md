---
title: "[Java] Simple Process Pipe from wcalc"
date: 2008-08-28
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-28
Hello,

I just created a post that was inquiring about phasing a string sentence like **(6+3)** into a math expression but i decided to see if there were any command line calculators already available to use and there is, wcalc. I downloaded and installed and its exactly what i need to use; one problem is that i forgot how to stream a single process. Wcalc will continue to run until the user types in quit so there is no need to start and stop the process. All i need to be able to do is send a line (such as **(6+3)** ) and then have the value from wcalc returned to me. Im asuming the best way to do this would be to create a method which i could call simply by going "calc("(6 + 3)");" which could return the value (which is 9 xP).

Thanks again
~Cody Woolaver

---

### Post by Zugzwang on 2008-08-29
After you created your external process with Runtime.Exec() you can call getInputStream() and getOutputStream() of the resulting Process object. You then simply write "quit\n" to its output stream any you're done. The result can be stream from the input stream.

---

### Post by tinny on 2008-08-29
You should find this thread useful. The thread discusses how to write Java code that can be used to run external processes.

[http://ubuntuforums.org/showthread.php?t=860730](http://ubuntuforums.org/showthread.php?t=860730)

Post #19 has some code attached that I know works well. (You will need to modify it a little for your application)

---

