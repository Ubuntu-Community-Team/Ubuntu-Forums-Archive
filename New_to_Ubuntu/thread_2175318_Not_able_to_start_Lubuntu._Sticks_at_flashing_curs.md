---
title: "Not able to start Lubuntu. Sticks at flashing cursor"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by Lesley_Beech on 2013-09-18
I have an old laptop which I have reformatted the disk on and loaded Lubuntu Alternate 13.04. I received the successful install message but after rebooting to launch the system I get the Lubuntu logo then a black screen except for the flashing cursor. After researching the Lubuntu web pages I used Ctrl+Alt+F1 to bring up the ubuntu login: message. I entered my user login name and pressed return and got the password: message. I typed my password and received the following script
[I]Last login: "date" "time" BST 2013 on tty1
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic i686)
*Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
0 packages can be updated
0 updates are security updates
"name"@ubuntu:~$"flashing cursor"
[/I]
The date and time in the message are from my previous attempt to load the application and name is my login name. The flashing cursor at the end of the message is waiting for me to enter something but I don't know what?
My laptop spec is Pentium 3, 600MHz, 512MB RAM, Video memory 8MB, Laptop Hard Drive is 6GB.

Can someone tell me what I should be typing at the flashing cursor and also whether my laptop spec is sufficient toi run Lubuntu Alternate.
Thank you.

---

### Post by Jonathan Precise on 2013-09-18
This means you are in a command-line session (it means you type commands).
Press ALT+F7. That should give you a graphical system.

PS. Why did you install via the Alternate CD? You can use the regular desktop CD to test before using. Edit: mörgæs makes a good point about your spec. The desktop cd might not run too well.

> ... and also whether my laptop spec is sufficient to run Lubuntu Alternate?

Lubuntu Alternate means that it is a text-based installer. The desktop CD gives a preview of what the installed system will look like (you can "test drive it").

However, I think 6GB HDD is too little. Try [Puppy-Linux]("http://puppylinux.org/main/Long-Term-Supported%20Puppy.htm") instead (install to a usb stick, not to HDD). Edit 2: You might not be able to boot a USB. mörgæs makes a good point that anything with a GUI can be heavy for that computer.

---

### Post by mörgæs on 2013-09-18
> **Jonathan Precise said:**
> 
Why did you install via the Alternate CD? You can use the regular desktop CD to test before using.


The alternate ISO was probably a good choice. It's not likely that this old fella runs a full ISO.

> **Jonathan Precise said:**
> 

Try [Puppy-Linux]("http://puppylinux.org/main/Long-Term-Supported%20Puppy.htm") instead (install to a usb stick, not to HDD)

- and it's not likely either that it boots from USB.

---

### Post by Jonathan Precise on 2013-09-18
> **mörgæs said:**
> - and it's not likely either that it boots from USB.

Then a CD for Puppy linux is possible, though everything will have to be saved to a USB flash drive.

Edit: you can also try [Bodhi Linux]("http://www.bodhilinux.com") (no PAE)

---

### Post by mörgæs on 2013-09-18
Running from a USB stick is slower than from the hard disk. No need for that.

If you install Bodhi you can also use the PAE version, as this is a Pentium 3. Not that PAE matters much in this case.

But... whichever distro you choose be prepared that it will work in slow motion. Personally I wouldn't run anything with a GUI on hardware like this. Sorry...

---

