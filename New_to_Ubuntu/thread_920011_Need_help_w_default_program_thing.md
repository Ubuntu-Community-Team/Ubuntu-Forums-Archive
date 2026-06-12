---
title: "Need help w/ default program thing"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-09-14
well for some reason I was an idiot and I removed crossover for the default executable program to run. So now I need to know what program I need to get..... or use to be able to run the installation file for like poweriso...... that kinda thing.......

---

### Post by pytheas22 on 2008-09-14
I'm not positive I understand what you're asking, but if you're looking for a way to run Windows software on Linux, you want to install wine.  You can do that by typing at a terminal:
```

sudo apt-get install wine
```

If you have Crossover, that would work too (Crossover is basically a commercial version of wine that's designed to be as user-friendly as possible), but I've never installed Crossover.

---

### Post by 133794m3r on 2008-09-14
i'm talking about like if I go to let's say this site.... i had the trial version and I have wine installed now....[http://www.regnumonline.com.ar/index.php?l=1&sec=6](http://www.regnumonline.com.ar/index.php?l=1&sec=6) 
I go there and let's say I dl the 32 bit installer...... ok now when I go to properties and say allow file to run like an executable then when i double click i get nothing.... nothing at all.....

---

### Post by pytheas22 on 2008-09-14
Are you downloading the 32-bit Linux or Windows installer?  Did you try running the file from the command-line?

---

### Post by 133794m3r on 2008-09-14
i was talking about something like the Poweriso thing...... I double click and it does nothing....... that site was just an example..... if i dl a different installer will it work?

---

### Post by pytheas22 on 2008-09-14
It depends on what you're downloading.  If you download an installation package meant for Ubuntu (it would have the extension .deb), then yes, you should be able to double-click on it and it would install.  If you download some other kind of file meant for Linux, like source code (extension .tar.gz) or an RPM (packages for Red Hat-based distributions), then an installer wouldn't open.  So you need to know what kind of file you're downloading, as the behavior is different for each type of file.

If you download a .exe installer meant for Windows, I believe that you can't run it by double-clicking--this is disabled as a security feature.  You have to right-click and select "Open with Wine Windows Emulator" (or something close to that) to run the program.  Also keep in mind that there might be a bug that prevents wine from opening the .exe file, but you wouldn't get any feedback unless you run it from the command-line.

If you tell me the specific location of the file you're trying to run, I'll see what you need to do to get it to work.

---

### Post by 133794m3r on 2008-09-14
well the 32 bit version of the one program is just a binary file.... i was just seeing if I dled a binary file..... then allowed to execute it'd still work...... b/c I understand how to install from a .deb and a .tar.gz and other installation archives....

---

### Post by pytheas22 on 2008-09-14
Again, it depends on what kind of file it's supposed to be--most files are binary files but they all do different things.  For example, you could have an executable for a program that only runs on the command-line, and it would execute when you double-click on its icon, but you wouldn't see anything because it would only output to a command-line.  Another example: you could have a binary executable built for the wrong kind of architecture (i.e., you could be trying to run a Mac OS X program in Linux, or a 64-bit executable on a 32-bit processor), in which case it wouldn't run, but you wouldn't get any feedback either.

If there's a particular file that you need to run and nothing happens when you double-click even though you think it should, then you should try running it form the command-line, which will provide useful feedback in the event of an error.

---

### Post by 133794m3r on 2008-09-15
ah ok thanks for the info...

---

