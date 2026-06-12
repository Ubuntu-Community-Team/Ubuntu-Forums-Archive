---
title: "windows command line problem"
date: 2009-04-22
forum: Programming Talk
---

### Post by christoforever on 2009-04-22
I'm writing an IDE in java for ruby programming. The problem comes when it's time to execute the ruby program... Doing this on ubuntu( and/or any other linux variant) is a piece of cake... Windows seems to be the problem here. I'm trying to specify the absolute path name for ruby and the file name to pass it... however it's not working that easily. This is what I'm trying to do on windows...

C:\ruby\bin\ruby.exe C:\Documents And Settings\cdancy\Desktop\test.rb

then it gives the error that C:\ruby\bin\ruby.exe is not recognized as an internal or external command. I have no idea what to do and their are no windows forums that i know of, So i've come here for answers if anyone knows?

Sincerely,
Chris Dancy

---

### Post by MadCow108 on 2009-04-22
the quotes for the path containing spaces are missing in what you wrote.
C:\ruby\bin\ruby.exe "C:\Documents And Settings\cdancy\Desktop\test.rb"

---

### Post by Darryl Moore on 2009-04-22
Missing quotes would not explain why he is getting the message "C:\ruby\bin\ruby.exe is not recognized as an internal or external command"

I'd say the the OS cannot find ruby.exe. It's a dumb question, but are you sure that the directory "C:\ruby\bin\" exists?

---

### Post by christoforever on 2009-04-22
To darryl and Madcow... putting the file argument in quotes actually worked... which is odd. By any chance you guys would not happen to know how to keep the windows command prompt open after the program exits? Im looking for something similar to how xterm does...

xterm -hold -e <some program> <some file>

---

### Post by doas777 on 2009-04-22
> **christoforever said:**
> To darryl and Madcow... putting the file argument in quotes actually worked... which is odd. By any chance you guys would not happen to know how to keep the windows command prompt open after the program exits? Im looking for something similar to how xterm does...

xterm -hold -e <some program> <some file>

in dos, you would use "Pause". the user will see "Press any key to continue". if it is the last line in your bat, then the prompt will close.

I would execute from a batch, and put the pause command at the bottom.

---

### Post by christoforever on 2009-04-22
I'm not going to lie to you, I have heard of batch files( which i assume is like a shell script ), but I've not used windows as an operating system on a day to day basis in over 6 years. The only reason I'm writing this program to include windows is for not alienating the potential amount of users who may be using the program and for the sake of completeness as a java application. So.... DAMN WINDOWS!!!!

---

