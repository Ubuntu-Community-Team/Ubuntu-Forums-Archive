---
title: "Weird thing going on with Java?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-16
Here's what happened:

I wanted to open a .jar file, so I double-clicked on its icon, then the splash screen appeared, then it hanged, then I had to Force Quit it, same thing happened at least ten times. Never managed to open it this way.

Tried Terminal. Typed directory of the .jar file. Same result as above.

Tried Terminal. Typed this ```
java -jar <file directory>
```. Same result as above.

Tried Terminal. Typed this ```
cd <directory of folder containing the .jar file>
java -jar <file name>.jar
```. Worked. Splash screen appeared for about 2 seconds and the program was launched. For the other attempts I waited for the splash screen for about 5 minutes. So I'm pretty sure it hanged for all the previous attempts.

Now, can someone tell me what's the difference between all 4 attempts? And how come only the last one worked? (I don't know about the first two, but I really don't see any difference in the third and fourth attempt, but how come it only worked on the fourth one?) Is there a simpler way to do it? Thanks.

---

### Post by txcrackers on 2008-08-16
The last one worked because (probably) there are some files the program needs in order to run and they're located with the .jar file. The developers of the program assumed that you'd be running the program from the directory the .jar file is in, so they use that as the basis for locating these files.

In cases like this, if you'd like to be able to "click and run," you'll need to write a small "wrapper" script around the program and then you can create a launcher/shortcut to the script.

---

