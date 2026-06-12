---
title: "HOWTO: Console and Hardware based CPU monitor and new email/RSS alert"
date: 2006-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Randomskk on 2006-08-03
This How-To will lead you through making and using a small hardware device, which can indicate CPU usage and whether you've got new email/RSS.
Alternatively, you can skip over the hardware part and just use the program itself, which can be run in a console and will output "virtual LEDs" to the console.

To get started, here's a picture of the final project, with all LEDs lit up:
[IMG]http://randomskk.net/lptmon/images/allon.jpg[/IMG]

There are two main sections for this, hardware and software. If you're not going to make the hardware, just skip the hardware section.

[SIZE="4"]HARDWARE[/SIZE]
First, you'll need to gather components. The things you absolutely must have are 8 LEDs (ideally four of one colour and four of another), 8 resistors (ideally 330ohm, but 200 to 500 will work) and a parallel cable.
Nice extras are a switch, and an DB-25 connector which lets you solder to a parallel cable easily. You could also make a cheap cardboard case, as shown in the picture ;P

Anyway, you then connect resistors to pins 2,3,4,5,6,7,8 and 9, connect these to the long lead on an LED (positive), and then connect all the short LED leads together and connect them to any pin between 18-25. 
If you've got a switch, this goes between pins 10 and also 18 to 25 (ideally a different pin from the one you're using for LEDs).
This quick and dirty circuit diagram should give you the general idea:
[IMG]http://randomskk.net/lptmon/images/circuit.jpg[/IMG]

That's it! The hardware involved is fairly simplistic.


[SIZE="4"]SOFTWARE[/SIZE]
The first thing to do here is acquire the software itself.
It's written in C++, and you can either get the source and compile it yourself, or download a pre-compiled binary.
In either case, downloads are [here](http://randomskk.net/lptmon/#download).

Once it's downloaded, there are a couple of options for running it.
First, the program neeeds to run in the background all the time to process new RSS and new emails. When running in the background it also needs to be run as root, so that it can access the parallel port.
The simple way to do this is (from the directory with the program):
```
sudo ./lptmon
```
This works well if you are manually starting the program.
However, this isn't such a good choice if you want to be able to start the program at startup.
One option to setUID the program to root - this means that when the program is run, it gets run as root.
To set this, do:
```
sudo chmod a+s lptmon
sudo chown root lptmon
```
Then you can just run ./lptmon and it will have all the permissions it needs.

Running in the background also has two options - -nolpt and -nographics.
Using -nolpt means the program will not access the parallel port, and thus you do not need root. Instead, the program will only output to the console.
Using -nographics means that the program will not output to the console, and will only write to the parallel port (this still needs root).

Once the program is running in the background, you can all it again with arguments that will trigger the "new RSS" and "new email" alerts.
To say there's a new email, configure your mail reader to run the program with the argument newemail, for instance:
~/lptmon newemail
The same for RSS, only with newrss instead of newemail.
If your client supports running commands when there's no new email/rss, you can run the program with the argument "noemail" and "norss".
Finally if you haven't got a button and your programs won't run the noemail and norss commands, you can manually run it with the argument "nonew", which does the same as pressing the button.
You could also bind a keyboard shortcut to running this, so you can press a keyboard shortcut to clear both statuses.

That's pretty much it for setting it up and using it!
If you've got any questions, you can reply to this thread or email me directly (my email's in my profile on the forums).
There's some more information available both at the top of the source code, on the project site ([http://randomskk.net/lptmon](http://randomskk.net/lptmon)) and if you run the program with the -h argument.

Thanks!

---

### Post by Randomskk on 2006-08-04
Some more pictures:

1) showing new email and new RSS:
[IMG]http://randomskk.net/lptmon/images/new.jpg[/IMG]

2) after pressing the button..:
[IMG]http://randomskk.net/lptmon/images/button.jpg[/IMG]

3) plain CPU monitor:
[IMG]http://randomskk.net/lptmon/images/cpu.jpg[/IMG]

---

### Post by DC@DR on 2006-08-04
This is really nice HOWTO, I would love to try it in the school laboratory. Let's see what my lab teacher would say about this. Thanks Randomskk :)

---

### Post by Randomskk on 2006-08-19
Whoops! I fixed the download links on the main randomskk.net/lptmon page.
Sorry about that, didn't realise they were broken until just now ><

---

### Post by jason.b.c on 2006-09-21
Your [download links]("http://randomskk.net/lptmon/32/lptmon") still don't work right...:(   Uh-OH

---

### Post by Randomskk on 2006-09-21
Really? The link you just posted works fine here. Just right click, save as, lptmon, save.
Then run it with sudo ./lptmon

If that still doesn't work, I'd try downloading the source for it and compiling it yourself:
```
sudo apt-get install build-essential
wget http://randomskk.net/lptmon/lptmon.cpp
g++ -o lptmon lptmon.cpp
sudo ./lptmon
```

---

### Post by jason.b.c on 2006-09-22
```
ELFELF
```

This is what is on the page when i click the link to it...   Is that not what you see when you click it...??

---

### Post by Randomskk on 2006-09-22
Yes, that's the program. That's what a compiled binary looks like when you open it with notepad etc.
Try right clicking the link and going save as, instead of left clicking, which should allow you to save the plain binary. I imagine my server is giving it out as a plain text file for some reason.

---

### Post by jason.b.c on 2006-09-22
> **Randomskk said:**
> Yes, that's the program. That's what a compiled binary looks like when you open it with notepad etc.
Try right clicking the link and going save as, instead of left clicking, which should allow you to save the plain binary. I imagine my server is giving it out as a plain text file for some reason.

Oh ok , See i was all confused about it before , I thought that when i clicked on the link for that page it was then supposed to pull up a download prompt...:oops: 

I get it now i think..\\:D/

---

