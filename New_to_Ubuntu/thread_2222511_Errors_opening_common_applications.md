---
title: "Errors opening common applications"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by exekiel2 on 2014-05-06
Errors opening common applications
 

 My level of experience with ubuntu is minimal (approx. 1 week) but can grasp pretty advance concepts because of my experience in technical support.
 

 I am currently running ubuntu 14.04 which I installed to dual boot on my hp pavilion laptop.  
 

 My goal with ubuntu is to gain a better understanding of linux and eventually switch to backtrack or kali (would like to get into the network security field).  I was told the best way to learn the “deep” functionality of linux was to use the command prompt as often as possible which lead me to find a lot of error messages when opening applications such as firefox, thunderbird, and pithos.
 

 The firefox and thunderbird error message:
 	(process:24156): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed 
 

 I found that this is a known issue (I am still able to run both programs without problem but I am unable to close the terminal without closing the program because it never finishes the process and has to kill it).  The question I have about this comes from the “patch” I found on this website [https://bugzilla.mozilla.org/show_bug.cgi?id=672671](https://bugzilla.mozilla.org/show_bug.cgi?id=672671) . I click on the patch but have no idea how to apply it.  Is there a guide I am missing or could someone give me some tips on how to apply this?
 

 The error message I am getting from pithos:
 	/usr/bin/pithos:805: GtkWarning: Ignoring the separator setting 
   builder.add_from_file(ui_filename) 
 

 I looked around the internet and found this line before error messages. But never something addressing just the warning.  I feel like I am missing something about how the command line works.  Once I open an application with the terminal I should be able to enter another line after the application starts correct?

---

### Post by vasa1 on 2014-05-06
> **exekiel2 said:**
> ...  The question I have about this comes from the &#8220;patch&#8221; I found on this website [https://bugzilla.mozilla.org/show_bug.cgi?id=672671](https://bugzilla.mozilla.org/show_bug.cgi?id=672671) . I click on the patch but have no idea how to apply it. ...
Please provide the exact url. That bug has over 40 comments. To pinpoint the comment you're referring to, please provide the url of the particular comment, like this: 
[https://bugzilla.mozilla.org/show_bug.cgi?id=672671#c11](https://bugzilla.mozilla.org/show_bug.cgi?id=672671#c11)
Note the **#c11**. So right click on "Comment 11", for example, to get a context menu providing you with an option to copy the link. Then paste it here.

I have been following this error from a distance and am unaware of any "patch" that you or I can apply unless we're building Fx/Tb from source. And because, other than that error, the standard Fx works for me, I see no need to compile to incorporate a patch, even if one exists.

If you have time, please look at [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400) and the links there. That may provide you some perspective on some errors encountered when you launch errors in the terminal. 
> **exekiel2 said:**
> ... Once I open an application with the terminal I should be able to enter another line after the application starts correct?
I don't think that's the case.
If you want to see the errors generated when a program launches (in the terminal), runs, and closes, you need to keep that particular terminal window/tab open, AFAIK.

If you just want to launch a program from the terminal and get back the prompt, I'm sure there are tricks for that. I don't know them because I have no use for such a mode of operation. Anyone else?

---

### Post by Impavidus on 2014-05-07
Applications started from the terminal can run in the foreground or in the background, using a trailing & on the command line:```
#Start one in the background
application1 &
#Start another in the foreground
application2
```If you run a program in the foreground its standard input remains attached to the terminal, so if the program wishes it can accept input from the terminal. GUI programs rarely do so, but for interactive programs running in the terminal it is required. You won't get a new prompt before the program has terminated. If you run a program in the background you'll get your prompt back for a new command whilst the program is still running. Some GUI programs produce a lot of error or warning messages in the terminal (mostly gtk warnings in my experience), others can be used without the disrupting messages breaking into the other things you do in the terminal. I often use it to start a bunch of GUI programs with (nearly) identical command line arguments, like document viewers each showing a different page of the same document simultaneously.

I don't know the specifics of the following, but I think it's more or less like this.
When you run a program from the terminal and close the terminal by clicking on the close button, the shell running in the terminal is sent the SIGHUP signal. The shell reacts by sending this signal to the programs that had been started from the shell, by default resulting in termination of the program, and then terminating itself. If you close the terminal by typing exit in the shell (or by sending the shell for example the SIGTERM signal, or even the SIGKILL signal), the shell does not signal the program to terminate. The shell is terminated, the program that had been started from the shell is inherited by init and after termination of the shell the terminal terminates too – or at least the tab in which that shell was running.

---

### Post by buzzingrobot on 2014-05-07
> **exekiel2 said:**
>   Once I open an application with the terminal I should be able to enter another line after the application starts correct?

You can append a line with the '&' character, which will place that process into the background and display a new prompt. Obviously, this is almost always pointless for GUI applications.

In my experience, GUI programs launched from the command line often display error messages related, in one way or another, to their inability to locate needed graphic resources.  GUI applications are typically intended to be launched from an icon.

The program you are using when you use the command line in a terminal is, generically, called the "shell".  Ubuntu's specific implementation is the Bash shell, as it is almost everywhere in Linux. If you boot Linux in so-called text mode, without launching the X graphics engine, Bash is the program that displays the prompts, accepts the commands you enter, parses them and dispatches them to the appropriate programs, and displays the results. A terminal window is program that provides an emulation of that in a graphics environment.

Bash is a very capable and flexible tool and can be used as a programming tool to construct complex scripts.

So... Bash is the thing you specifically need to target.

---

### Post by exekiel2 on 2014-05-07
Thank you for the help guys.  This makes a lot more sense and i tested opening apps with the other commands you gave and they worked the way I wanted my initial commands to work so that helps a lot!  In regaurds to the "patch" I was talking about it was attatched to that page.  I will put it here too: [https://bug672671.bugzilla.mozilla.org/attachment.cgi?id=546933](https://bug672671.bugzilla.mozilla.org/attachment.cgi?id=546933)

---

