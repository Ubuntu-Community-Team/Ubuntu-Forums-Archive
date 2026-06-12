---
title: "Java Compiler issue"
date: 2007-01-02
forum: Programming Talk
---

### Post by welshboy on 2007-01-02
Hey folks, you probably all ready know this, but still I'll post it here just in case.  

I installed Java some time ago now, (the Sun Version) , I installed it from Repos, and did the whole 
sudo update-alternatives --config java, and everything worked nicely.  At least until today.

I use eclipse for my java developement, but I use a terminal window to run the code, so that I can log error messages.  So there I was compiling an example out of a book when I got told that the source code had to be version 5.0 for it to work.

I typed in javac -v only to find it wasn't using the proper compiler, and it turned out that somehow or other, it was using Eclipse's version of Javac, hence the error messages.

So I ran this command instead sudo update-alternatives --config javac

And now I am using the proper Sun compiler.  

Once again, I'm pretty sure someone will have noticed this before, but I've only been using Ubuntu for four months, and I'm pretty chuffed that I found this all on my own :D

If it has helped anyone out there, then please let me know, it'll make my day :D

welshboy

---

### Post by hod139 on 2007-01-02
You shouldn't be using update-alternatives, you should be using 
```

sudo update-java-alternatives -s java-1.5.0-sun
```

which will set all the java related settings (java, javac, javaw, jar, etc).  This will ensure everything java related is set to sun's version.

---

### Post by welshboy on 2007-01-02
Then I gladly stand corrected :D

Many thanks for that, it's now in my notepad of linux commands :)

---

