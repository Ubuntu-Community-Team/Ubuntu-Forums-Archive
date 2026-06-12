---
title: "Vaio (noob questions)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mtonsbeek on 2008-04-27
Hi,
Go gentle on me! This is my first post on this forum and I have a few questions.

I have installed 8.04 as a dual boot on my Vaio SZ1XP T2400 1.83GHz and have been impressed that almost everything worked. Thank you developers! I have attempted a switch to linux a few times before but have abandoned it on all occasions. So far I am really happy with hardy.

The only things that don't work are the built in microphone and webcam. Not really essential but if anyone knows a fix I would love to hear from you.

The other thing that is slighly annoying is the fact that after having logged in with name and password, I get a message "application 'nm-applet' (/usr/bin/nmapplet) wants access to the default keyring, but is is locked". Can I enter this password somewhere so that it memorises it.

NB: ultra noob so please explain as if my IQ is below zero!!!

Thanks

---

### Post by Martin Witte on 2008-04-27
the keyring issue is covered in this thread [Stop having to enter keyring over and over again]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1")

---

### Post by grazed on 2008-04-27
double click on the volume control next the clock, typically you will see the microphone control on the very right most side.

someone else is going to have to help you with your webcam. =P

on another note... you said everything worked out of the box. did your video drivers auto install? you can check by right clicking the desktop and going into "change wallpaper" then, desktop effects and seeing if they are / can be enabled.

---

### Post by southernman on 2008-04-27
Ok, going easy on you.

The keyring issue may get resolved if you look at the thread below:
[http://ubuntuforums.org/showthread.php?t=130192](http://ubuntuforums.org/showthread.php?t=130192)

The other issues someone else will have to help, but give as much info about what specific hardware you have... deal? Like what webcam and mic it is. Find out by doing these two commands:
```
lspci
```
and
```
lsmod
```
paste the output of those two commands (applications, accessories, terminal) in this thread.

For what it's worth, when you're given an error (such as the keyring error), if you'll copy and paste the entire error into Google... you'll be surprised how quickly and easily you could resolve the issues yourself. Just saying as it's obviously been covered by the google results below:
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=BdO&q=application+%27nm-applet%27+wants+access+to+the+default+keyring%2C+but+is+is+locked&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=BdO&q=application+%27nm-applet%27+wants+access+to+the+default+keyring%2C+but+is+is+locked&btnG=Search)

Some may call that last bit snide, but I mean it to be empowering.

Good luck...

---

### Post by mtonsbeek on 2008-04-27
> **Martin Witte said:**
> the keyring issue is covered in this thread [Stop having to enter keyring over and over again]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1")

Oh blast! I think I have mucked this up!
I followed the instructions as per the link and now have a message: "authentication failed". I can start the system with Live CD but not from the hard drive. 

There is nothing on the Ubuntu partition that I need so I can start again without too much trouble but I would propably have to delete the partition that is there now?

---

### Post by mtonsbeek on 2008-04-29
> **southernman said:**
> Ok, going easy on you.

The keyring issue may get resolved if you look at the thread below:
[http://ubuntuforums.org/showthread.php?t=130192](http://ubuntuforums.org/showthread.php?t=130192)

The other issues someone else will have to help, but give as much info about what specific hardware you have... deal? Like what webcam and mic it is. Find out by doing these two commands:
```
lspci
```
and
```
lsmod
```
paste the output of those two commands (applications, accessories, terminal) in this thread.

For what it's worth, when you're given an error (such as the keyring error), if you'll copy and paste the entire error into Google... you'll be surprised how quickly and easily you could resolve the issues yourself. Just saying as it's obviously been covered by the google results below:
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=BdO&q=application+%27nm-applet%27+wants+access+to+the+default+keyring%2C+but+is+is+locked&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=BdO&q=application+%27nm-applet%27+wants+access+to+the+default+keyring%2C+but+is+is+locked&btnG=Search)

Some may call that last bit snide, but I mean it to be empowering.

Good luck...
Sorry for taking some time to respond. I have actually reinstalled Hardy and in doing so have now got a rid of the keyring issue.
The mike and webcam still are not working. Below I have pasted the info the above commands gave. I have to say that I cannot deduct much fromthem but would be interested to know who can:

---

