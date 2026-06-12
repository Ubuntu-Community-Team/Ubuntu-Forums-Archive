---
title: "about code blocks"
date: 2010-01-25
forum: Programming Talk
---

### Post by exchan on 2010-01-25
am not sure if this is the right board for this but this is whats happening... so I installed code blocks after clear installing ubuntu 64 everything went fine but when I try to compile/run my .cpp files code::blocks wont do anything  I dont get any messages on the build log so I dont understand whats happening I tried looking on the forums and checking other pages but no luck at all... any ideas?

---

### Post by mikejonesey on 2010-01-25
hmm any more info... not doing anything?

settings->comiler & debugger->other settings->compiler logging->full comnad line

then try and compile, any more info?

---

### Post by dwhitney67 on 2010-01-25
> **exchan said:**
> am not sure if this is the right board for this but this is whats happening... so I installed code blocks after clear installing ubuntu 64 everything went fine but when I try to compile/run my .cpp files code::blocks wont do anything  I dont get any messages on the build log so I dont understand whats happening I tried looking on the forums and checking other pages but no luck at all... any ideas?
Can you build from the command line?  Perhaps you have not yet installed the development tools?
```

sudo apt-get install build-essential

```

---

### Post by exchan on 2010-01-25
> **dwhitney67 said:**
> Can you build from the command line?  Perhaps you have not yet installed the development tools?
```

sudo apt-get install build-essential

```
thats one of the first things that I did when I dled code blocks

---

### Post by exchan on 2010-01-25
> **mikejonesey said:**
> hmm any more info... not doing anything?

settings->comiler & debugger->other settings->compiler logging->full comnad line

then try and compile, any more info?

I cant seem to find the "other settings" part there is a "other options tab but there is nothing displaying there D: is this what you meant?

[http://yfrog.com/7hscreenshotejp](http://yfrog.com/7hscreenshotejp)

---

### Post by mikejonesey on 2010-01-27
no...

[http://www.sakuiweb.com/otheroptionsdb.ogv](http://www.sakuiweb.com/otheroptionsdb.ogv)

---

### Post by cjminton on 2010-01-27
I had a problem with codeblocks too like where it just wouldn't do anything. It would say that there's nothing to build or something. All I had to do to fix it is make sure you save your source files ahead of time and make sure they end with the proper extension - i.e. *.cpp for C++ or *.c for C, *.h for header files. Then try building & running.

---

