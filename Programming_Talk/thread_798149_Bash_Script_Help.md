---
title: "Bash Script Help"
date: 2008-05-17
forum: Programming Talk
---

### Post by mike.grabowski on 2008-05-17
I am working on writing my first Bash script. I have a Logitech Quickcam Pro 9000 which in order to use with Gyachi, needs the Flashcamwrap workaround. I wanted to write a script for loading the driver and starting the flashcam server and load Gyachi. So far, this is what I have:

```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
gksudo flashcam -L

# Start Flashcam Loopback service
flashcam -qD

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi
```

This seems to work just fine for getting Flashcam running and launching Gyachi with the flashcamwrap. What I was wondering is if there is a way to monitor the gyachi process and upon quiting the application to issue one last command - killall flashcam - to terminate the flashcam server and release the webcam? I've looked around a little bit in the Bash command lists but haven't seen anything very straightforward for performing this function. My guess is that something might be able to be done with PS. But I'm not sure yet unless I do some testing. Any info on known ways of doing this would be greatly appreciated.

Thanks!
Mike

---

### Post by empthollow on 2008-05-17
I'm not sure what you mean when you say monitor the process, to see the process you can do a:
```
ps aux | grep flashcam
```
but that will output one line and quit.

If you want to test to see if the process is running and if it is then kill it, you can use an if then statement.

```
if [ $(pidof gyachi) != 0 ] ; then
killall flashcam
```

that may be a little excessive because you the script that executed the  gyachi command is still running until you quit the program so you could just put a 
```
killall flashcam
```
at the end of the script.

Hope that helps

---

### Post by slavik on 2008-05-17
```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
gksudo flashcam -L

# Start Flashcam Loopback service
flashcam -qD

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi

killall flashcam
```

---

### Post by mike.grabowski on 2008-05-18
Hi! Thanks for the replys.

I don't want to just kill the flashcam process at the end of the script, it needs to continue running until I exit the Gyachi program. Basically, after I exit the Gyachi program, I want to exit the flashcam program as well.

Maybe I'm looking at this the wrong way, maybe I need a different script to 'killall flashcam' that would run when I exit the Gyachi program. Is there a way to have a script run automatically when I exit a particular program?

---

### Post by stroyan on 2008-05-18
> **mike.grabowski said:**
> Hi! Thanks for the replys.

I don't want to just kill the flashcam process at the end of the script, it needs to continue running until I exit the Gyachi program. Basically, after I exit the Gyachi program, I want to exit the flashcam program as well.


You misunderstand how your script works.  You script will not end when
it starts the flashwrap command.  It will block waiting for flashwrap
to exit.  The flashwrap command will block waiting for gyachi to exit.
You can put the 'killall flashcam' at the end of your script because
that won't happen until gyachi is done.

There can be exceptions to that pattern when a program intentionally
places itself into the background.  Such a 'daemonized' program actually
starts a separate process and lets the original process die so its
parent go on.  But there is no sign that gyachi ever does that.

---

### Post by mike.grabowski on 2008-05-20
Ah... right you are. Thanks so much! Throwing that at the end of the script does exactly as you stated. 

Thanks for helping me out with my first Bash script!

---

### Post by loell on 2008-05-20
by far you are the third person, that confirmed flashcam works with gyachi:)

thanx

---

### Post by mike.grabowski on 2008-05-21
> **loell said:**
> by far you are the third person, that confirmed flashcam works with gyachi:)

thanx

Yes, it appears to work pretty well once you get it going. I think the instructions could be dumbed down a little more yet for newer folks. I struggled a little figuring it out before I finally got it. But the cam works pretty well. The size of the image is a little small though, especially compared to Skype. Skype has a much larger and higher quality image with its webcam support. But, its nice to be able to use it with Yahoo on Linux now too!

---

### Post by mike.grabowski on 2008-05-23
> **mike.grabowski said:**
> 

```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
gksudo flashcam -L

# Start Flashcam Loopback service
flashcam -qD

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi
```


Ok, one last question on this script involving the use of sudo in a bash script like this. The script runs perfectly if I have recently run the sudo command at the command line and typed in my password. If i haven't though, the flashcam driver never gets loaded because the gksudo command never gets the password. Is there an easy way to have the script prompt for the password through a dialog box or something if its needed? Most of the stuff I've been able to find for using sudo in a script is a little different and seems a bit complicated for what I'm trying to achieve. I would just like to be able to double click on the script, tell it to run and type the password in if I need to.

Any thoughts?

Thanks,
Mike

---

### Post by unutbu on 2008-05-23
What happens if you take the gksudo out of the script and instead run the script command with

```
gksudo script
```
?

```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
flashcam -L

# Start Flashcam Loopback service
flashcam -qD

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi
```

---

### Post by mike.grabowski on 2008-05-23
> **unutbu said:**
> What happens if you take the gksudo out of the script and instead run the script command with

```
gksudo script
```
?

```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
flashcam -L

# Start Flashcam Loopback service
flashcam -qD

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi
```


That seems to work ok like that. Can I launch 'gksudo script' from a shortcut?

---

### Post by mike.grabowski on 2008-05-24
> **mike.grabowski said:**
> That seems to work ok like that. Can I launch 'gksudo script' from a shortcut?

Well... I figured out how to launch it from a Launcher now. The only weird thing is, I just rebooted and tried launching it. It asks for my password and Gyachi comes up. But the Flashcam doesn't fire up right. If I close it down and do it again it comes up fine. Not sure why it wouldn't do it on the first try properly. I suppose I can live with that for now though.

Thanks to everyone for your help. The Ubuntu community is the best!

Mike

---

### Post by unutbu on 2008-05-24
This is just a guess, but perhaps it's worth a shot:

```
#!/bin/bash
# Launch Gyachi with Flashcamwrap

# Load Flashcam Driver
flashcam -L
sleep 10

# Start Flashcam Loopback service
flashcam -qD
sleep 10

# Launch Gyachi with Flashcamwrap
flashcamwrap gyachi
```

If it works, then you can play with the sleep numbers. They may need to be increased, hopefully they can be reduced, maybe only one is needed.

---

