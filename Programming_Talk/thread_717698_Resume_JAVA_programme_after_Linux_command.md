---
title: "Resume JAVA programme after Linux command"
date: 2008-03-07
forum: Programming Talk
---

### Post by Bungler on 2008-03-07
First of all:
I'm quite new in using Ubuntu and JAVA, so plz make your replies not too complicated ;).

I'm trying to fiddle a timer to shutdown the computer after a given amount of minutes. At this point is is going surprisingly well: I can specify an amount of minutes and using:

"Process p = Runtime.getRuntime().exec("sudo shutdown -h +"+min);"

(in which "min" is the amount of minutes) I can make the system shutdown.

The problem is:  I want to fit in a cancel option, but I don't know how to do this. After the shutdown command, the terminal just idles and does not continue the JAVA program.

How can I continue the program after the shutdown command? Preferably in the same terminal window?

---

### Post by Zugzwang on 2008-03-07
> **Bungler said:**
> 
The problem is:  I want to fit in a cancel option, but I don't know how to do this. After the shutdown command, the terminal just idles and does not continue the JAVA program.


You mainly have two options:[LIST]
[*]Use the "&" modifier in the command (which might require you to run a shell, I'm not sure if Java does this automatically). So you would have something like: [PHP]Process p = Runtime.getRuntime().exec("bash sudo shutdown -h +"+min+" &");[/PHP]
[*]Using threads in Java is easy, so you could start a thread executing the program while doing some other stuff. Your code would look like: [PHP]
(new Thread() {
  public void run() {
    Process p = Runtime.getRuntime().exec("sudo shutdown -h +"+min);
  }
}).start();
// Do whatever you want to do in parallel. [/PHP]
[/LIST]
Note that in the latter case the "min" variable has be non-local. Both versions are untested!

---

### Post by Bungler on 2008-03-07
Tnx for your reply, but unfortunately I can't get neither one of the options to work.

First I searched for the defenition of "&". I found it and it seems to make sense what you do:
"If a command is terminated by the control operator &, the shell executes the command in the background in a subshell. The shell does not wait for the command to finish, and the return status is 0."

However, the command is just not executed. If I remove "bash", the command is executed, but then the "&" operator doesn't work:
Putting for example "& sudo shutdown -c" should cancel the shutdown immediately, but it is just printed as text.

The second option is interesting. I played around with it, to get familiar  with it. Again it makes sense for me, but somehow, the shutdown command does not run in a separate thread. It does not seem to make any different if I put it in a separate thread.

---

### Post by Zugzwang on 2008-03-07
For the bash method, you have to put it a little bit differently (as already stated, I haven't tested it). You need to specify the "-c" option:

Try for example:

[PHP]
Runtime.getRuntime().exec("bash -c \"sudo shutdown -h +"+min+" &\"");  
[/PHP]

The threaded version however should work. No idea why it doesn't. :(

---

### Post by xlinuks on 2008-03-07
> **Bungler said:**
> First of all:
The problem is:  I want to fit in a cancel option, but I don't know how to do this. After the shutdown command, the terminal just idles and does not continue the JAVA program.

How can I continue the program after the shutdown command? Preferably in the same terminal window?

The biggest problem here is that you let the bash application do the countdown, thus it gets hard to figure out how to cancel that countdown from Java.
IMO a better implementation would be for your Java app to do the countdown and when the time is up you just call the bash command to shutdown the computer. This way you have full control over the countdown process and can cancel it anytime.
The implementation (the code) itself depends on whether you're willing to create a GUI or a command line Java application.

---

