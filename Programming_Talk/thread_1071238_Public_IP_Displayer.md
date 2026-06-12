---
title: "Public IP Displayer"
date: 2009-02-15
forum: Programming Talk
---

### Post by MontananIce on 2009-02-15
I have writted a simple shell script to pull a public ip through lynx browser and display the public ip via console. My public ip changes often and I often need to know the current external ip for VOIP/Videoconferencing purposes. I would like to create an GNOME applet to display the text dump (the public ip numbers) from my shell script. I am sorta at odds on how to go about creating an applet since I'm an idiot in programming.

Can you guys suggest an simple applet maker? I looked at Glade-3 which has minimal documentation and also at this url [http://members.iinet.net.au/~adburton/articles/appletstutorial.html]("http://http://members.iinet.net.au/~adburton/articles/appletstutorial.html") Are there any applet creator program that does not require programming knowledge? All I need to create is a simple text displayer that runs the shell script every few minutes and shows the most recent text dump in the GNOME applet panel. Any ideas on where to get started?

I know theres already a public ip applet called GIPlet available but it seems to be a dead project and apparently also fails in displaying the external ip for many people including me.

---

### Post by unutbu on 2009-02-16
It might be easier to use Conky. 

Example screenshots: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

HOW TO: A Beginners Guide to Setting up Conky: [http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

Once you have conky installed and have a basic ~/.conkrc file, it would only take one extra line to tell conky to run your script periodically (however often you wish) and to display the results on your desktop (root) window.

For example, adding a line like this to ~/.conkrc
```

${execi 10 /path/to/script}
```
would run /path/to/script once every 10 seconds and display the result on the desktop.

---

### Post by MontananIce on 2009-02-18
Thank you for posting information about Conky. I will do research on Conky and see if this helps with what I want to do. Loving Ubuntu more every day I'm using it as I actually can even consider doing stuff like this.

Puts the fun back in computing! :)

---

