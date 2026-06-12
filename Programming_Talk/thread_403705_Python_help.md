---
title: "Python help"
date: 2007-04-07
forum: Programming Talk
---

### Post by JackTheRipper on 2007-04-07
Well, i installed IDLE as i can save my programs with that. Once i have a programmed saved i go under properties and make the file an executable one but when i try to run it nothing happens. Am i doing something wrong? Thanks in advanced.

---

### Post by MadeR on 2007-04-07
> **JackTheRipper said:**
> Well, i installed IDLE as i can save my programs with that. Once i have a programmed saved i go under properties and make the file an executable one but when i try to run it nothing happens. Am i doing something wrong? Thanks in advanced.

I did not understand your problem.

may be you wanted to add #!/usr/bin/python
or
you desire a development environment: in this case install Eric

sorry :(

---

### Post by JackTheRipper on 2007-04-07
Basically, i have my program all layed out. I save it as a .py and make it an executable file. When i open it a dialog box comes up and gives me the options to "run in terminal", "Display", "Cancel", or "Run". I've tried both Run in Terminal and Run and neither seem to work. Am i doing something wrong here?

---

### Post by MadeR on 2007-04-07
> **JackTheRipper said:**
> Basically, i have my program all layed out. I save it as a .py and make it an executable file. When i open it a dialog box comes up and gives me the options to "run in terminal", "Display", "Cancel", or "Run". I've tried both Run in Terminal and Run and neither seem to work. Am i doing something wrong here?
```
cat prog.py
#!/usr/bin/python

print "ciao"
```
```
chmod +x prog.py
```

---

### Post by pmasiar on 2007-04-07
> **JackTheRipper said:**
> Basically, i have my program all layed out. I save it as a .py and make it an executable file. When i open it a dialog box comes up and gives me the options to "run in terminal", "Display", "Cancel", or "Run". I've tried both Run in Terminal and Run and neither seem to work. Am i doing something wrong here?

You open it in file manager?

To run it like that, you need the shebang line as first line of your script: "#!/usr/python" or wherever your python lives, to tell bash which program should interpret that script.

But you can open your file in IDLE and run it from there too (Run, or F5), even without making it executable. Check "Instant Hacking" and "IDLE toying" links here: [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

---

### Post by jerryrw on 2007-04-07
After you set the permissions run the app in the same term

./prog.py

The dot slash are important to tell the shell where the script is located.

---

### Post by JackTheRipper on 2007-04-07
Alright, thanks guys. I'm pretty new to the world of linux and ubuntu so i'm still learning.

---

### Post by MadeR on 2007-04-08
You are welcome :)

---

