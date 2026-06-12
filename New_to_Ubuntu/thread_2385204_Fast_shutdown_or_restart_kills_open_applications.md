---
title: "Fast shutdown or restart kills open applications"
date: 2018-02-17
forum: New to Ubuntu
---

### Post by jwo2 on 2018-02-17
Hi all! First time linux user, just loaded Lubuntu 17.10.1 on my aging Acer Aspire One and it's running quite smoothly on this 9 year old netbook. I noticed that shutdowns are restarts are extremely fast, so much so that any browser (e.g. Firefox and Chromium) does not close properly.  By that I mean when launch the browser again, it detects that my previous session was killed and asks if I want to restore the session.  Any idea if this can be "fixed" in Lubuntu?  Thanks!

---

### Post by ajgreeny on 2018-02-17
I'm not sure it can be fixed.

You should always close all running applications properly before shutting down the OS on which they're running.
That is also true in Windows, I believe, if it is shutdown fully rather than to the hibernation state that is now the standard in Windows 10, and was also in Windows 8, I think.

Perhaps I'm just very old-fashioned about such things but I have always closed all apps before shutting down, as I used to in Windows XP, the last version I used.

---

### Post by jwo2 on 2018-02-17
I guess that's my point, on Windows 7 or 10 if you issue a Shutdown or Restart command, it will try to close all your running applications first.  You then get a prompt to immediately Restart/Shutdown without waiting for running applications to close.  So was hoping Lubuntu would have a similar feature?

---

### Post by DuckHook on 2018-02-17
It is not a good idea to shut down without closing all of your apps first. While modern versions of 'buntu are sophisticated enough to try shutting down open apps elegantly, this really isn't the operating system's job and insisting on doing so *will* lead to data loss and corrupted files sooner or later. If you insist on doing so, then you should suspend rather than shut down. However, that practice brings the risk of breakage and lost data with power loss. In the same vein, hibernation is turned off in Ubuntu by default because it leads to all sorts of problems, especially in multi-boot environments. Therefore, the best answer (safest) is to shut down all apps completely before shutting down the computer.

EDIT: Ninja-ed by ajgreeny.

---

### Post by jwo2 on 2018-02-17
How about a script that will close open apps for me before the Shutdown/Restart command?  I found something about this on StackExchange, but I'm fairly new to all this so I'm not exactly sure what to do with this information:
[https://unix.stackexchange.com/questions/48973/execute-a-command-before-shutdown/294539#294539](https://unix.stackexchange.com/questions/48973/execute-a-command-before-shutdown/294539#294539)

---

### Post by DuckHook on 2018-02-18
The link you refer to does not provide generalized instructions on how to close all apps that happen to be open. It instructs only on how to close *specific* apps and services that you define within your script. The example given is of a ramdisk that is presumably always created at login. The script calls the *systemd* shutdown process to always shut down this ramdisk.

If I understand you properly, this is not what you are asking for. You want to change the system so that it shuts down whatever apps happen to be running. I know of no procedure that does this except doing it manually.

For what it's worth, I don't find the process of shutting down apps to be troublesome at all. The shortcut key <Ctrl>+<Q> shuts down the app that currently has the focus. Once the focused app shuts down, focus automatically shifts to the next app, and so on. By holding down <Ctrl> and just hitting a succession of <Q>s, the entire desktop can be cleared in seconds. This process also has the benefit of reminding you to save any unsaved work. It is far safer than any nuclear option that just wipes off your desktop irrespective of damage caused. I shudder at the thought of a process that force-closes a running virtual machine. That would just be asking for file corruption and OS breakage—even host kernel panics—since the VM still has hooks into your bare metal and is not given the chance to shut down gracefully.

If you are still intent on automating a dirty shutdown, I'm afraid I don't know how to do that.

---

### Post by vasa1 on 2018-02-18
What about [https://forums.bunsenlabs.org/viewtopic.php?id=508](https://forums.bunsenlabs.org/viewtopic.php?id=508) as a starting point?

---

### Post by Impavidus on 2018-02-18
To automatically close applications you can use the terminate signal (SIGTERM) to kindly request applications to terminate or the kill signal (SIGKILL) if the application doesn't listen. It's what the system does when you shutdown without first closing applications. That doesn't necessarily lead to a clean shutdown. SIGKILL immediately kills the application, without giving it a chance to clean up or save anything. Applications not designed to handle SIGTERM respond to that signal in the same way, but applications that have been designed to handle SIGTERM may exit cleanly, usually within seconds and without asking any further user interaction. They may save some files, but don't ask the user where to save them and without overwriting any version previously saved by the user. If you like an analogy with stopping a train, manually closing the application is like gently stopping for a red signal, SIGTERM is like running through a red signal and relying on the safety system to apply the emergency brake and SIGKILL is like running over a derailer.

Not all applications use ctrl+q to close. My xfce terminal uses ctrl+shift+q, evince uses ctrl+w, there's q, :wq to first close the text editor running in a terminal (followed by ctrl+d to close the terminal), maybe Esc etc. And there are people like me who spread their open applications over 15 workspaces so you have to check each of them. But I agree that closing them one by one is better than simply clicking shutdown.

---

### Post by him610 on 2018-02-20
Hello jwo2,

> ...asks if I want to restore the session
I thought this was a feature. I too have An Acer AOA ZG5 loaded with Xubuntu x86 16.04

---

### Post by kerry_s on 2018-02-20
+1 just close all you apps before restart/shutdown. common sense if you want to avoid data loss or corruption . you can use the quit feature in the bowser(ctrl+q) or the close button on the window, as long as you close it after use it should not be an issue.

---

