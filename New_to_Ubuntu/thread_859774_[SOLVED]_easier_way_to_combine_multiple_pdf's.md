---
title: "[SOLVED] easier way to combine multiple pdf's?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by iansane on 2008-07-14
Hi, I've found several howto's on using gs pdftk. It is really simple but is there a gui for when I have 30 or 40 single pdf's that need to be combined into one? That's an awful lot of typing.

I was thinking of trying to make a small c++ program that will let me select them all and then put the file names into a script and run it for me but I only have some experience in windows with visual studios for making gui's so I want to see if there is already an alternative.

Thanks

---

### Post by tramir on 2008-07-14
You can try [PDF Split And Merge]("http://www.pdfsam.org/"). It's a Java GUI which allows you to select (many) PDFs that you want to merge. No need for a script or anything.

---

### Post by iansane on 2008-07-14
can split and merge be installed in ubuntu from source and how would one go about doing that?

I'm installing the win version in my virtual machine since that's actually where the pdf's are but this would be a good app for linux if I can install it from source

---

### Post by weirdfox on 2008-07-14
You don't need to compile/install it from source, java use a virtual machine to run it's code, so binary, or bytecode for java, (.jar) should work on all java-enabled OS.

I hope this helps !

---

### Post by iansane on 2008-07-14
Yeah thanks guys. I installed it in windows virtual machine and it's a great program.

Also thanks for the info about java. I'll have to run it on ubuntu too, if it doesn't have problems with open-java which is installed by default. I never did fix the problems I had with frostwire not liking it, but that's another issue I don't put high priority on right now

Thanks a lot :-)

---

### Post by ChameleonDave on 2008-07-14
> **iansane said:**
> Hi, I've found several howto's on using gs pdftk. It is really simple but is there a gui for when I have 30 or 40 single pdf's that need to be combined into one? That's an awful lot of typing.

I was thinking of trying to make a small c++ program that will let me select them all and then put the file names into a script and run it for me but I only have some experience in windows with visual studios for making gui's so I want to see if there is already an alternative.

Thanks
Hi.

What you need to do with the PDF thingy is download not the Windows installer but the zip archive with just the java stuff inside.  Unzip it on your desktop.

Then, if you run "java -jar pdfsam-1.0.0.jar" on your desktop, it will run and work!

To install it like a normal program, you just have to move it all to a directory in /usr/local, and then set up a tiny script in /usr/local/bin to run that java command on it.

---

### Post by iansane on 2008-07-15
Thanks a lot guys, I've had to be away from my computer but your replies helped a lot.

Through my confusion I wound up with both the 0.7 and 1.0.0 and they both work fine just like you said.

Now if I could get adobe digital editions in Ubuntu I wouldn't need my windows machine at all. See I have legally purchaced class ebooks that will only open on a machine with digital editions installed and then only so many machines I can authorise to open them, so I installed a virtual printer driver in windows but it prints every page to it's own pdf so I wind up printing 20 30 or even 100 pdfs and then need to put them back together into one again so I can open them anywhere. There might be a simpler solution but as far as I'm concerned, problem solved. 

Thanks

---

