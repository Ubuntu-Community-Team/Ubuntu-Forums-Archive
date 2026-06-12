---
title: "Using git and mercurial in Ubuntu"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by JohanDuPlessis on 2013-02-17
***Git and Mercurial (hg***) are dependancies for a script that I need to run.  How do you install them in Ubuntu so that they will be available for your script

---

### Post by The Cog on 2013-02-17
I think this command will do the trick:
```
sudo apt-get install git mercurial
```

---

### Post by JohanDuPlessis on 2013-02-17
Thank You I have done that - but when I run the script I have an error about git repositories

---

### Post by TheFu on 2013-02-17
> **JohanDuPlessis said:**
> Thank You I have done that - but when I run the script I have an error about git repositories

Did you initialize the git repository where you wanted it?

There is a free PDF book that explains git. ProGIT - google will find it. There are also lots of git tutors that google will find and youtube videos.  I could give you commands, but without understanding what those commands do, I will not be doing you any favor.  An understanding of DVCS is needed to use both git and hg.

---

### Post by hlysig on 2013-02-17
Could you please paste the error/link to the script.

The script might be referencing invalid location to the git application on your system.

---

### Post by schragge on 2013-02-17
Judging from his previous inputs, I guess the OP means [this script]("https://github.com/lxdvs/apk2gold"). Rather not the script itself, but the file [.gitmodules]("https://github.com/lxdvs/apk2gold/blob/master/.gitmodules") that comes with it.

---

### Post by JohanDuPlessis on 2013-02-17
Thank You - got the PDF Progit. Read the contents. Made the required repositories and executed the make.sh script that comes with the apk2gold download.  Keeps on failing at two lines and I have come to the conclusion that the routine only works with 64bit version which I do not have.

---

### Post by schragge on 2013-02-17
The APK decompiler is written in Java, you're building it from source. I don't see why it shouldn't work on a 32-bit system. What error messages do you get?

Anyway, this is how I initialize the repository for apk2gold, and build the program.

```

git clone https://github.com/lxdvs/apk2gold.git
cd apk2gold
git submodule init
git submodule update
./make.sh

```

---

### Post by TheFu on 2013-02-17
> **JohanDuPlessis said:**
> Thank You - got the PDF Progit. Read the contents. Made the required repositories and executed the make.sh script that comes with the apk2gold download.  Keeps on failing at two lines and I have come to the conclusion that the routine only works with 64bit version which I do not have.

Do you have the other tools installed as spelled out on the github page?
Do you have a full java SDK environment installed?
Based on what others are saying here, those are needed before any building will be successful.

---

### Post by JohanDuPlessis on 2013-02-19
I finally got it all together with all the help from above...then found I also had to install the full **JDK** and then I got an error message about **mvn not found**.  Figured I had to install **maven.**.which I did and now everything runs as it should but I am now stuck at the following error:

***Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/johand/apk2gold/jd-cli/libjd-intellij.so: /home/johand/apk2gold/jd-cli/libjd-intellij.so: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)***

Googled this and found it to mean that the routine I am trying to run has been compiled as 64bit and my system is 32bit.  So near and yet so far.  I suppose this little excercise will have to wait until I upgrade to 64bit.  
 
I must say this is my first exposure to **Linux and what a great system**.  I am going to use it as my operating system of choice...so I guess there is a lot of reading to do. ** How do I mark this as SOLVED?**

---

### Post by alexdavis on 2013-02-19
Hey guys!
Just wanted to let you know that I logged this issue in the github project [https://github.com/lxdvs/apk2gold/issues/4](https://github.com/lxdvs/apk2gold/issues/4)

I have no doubt you are right. Its probable that the included binary ripped out of JD-GUI doesnt work on 32-bit, ill look for a workaround.

Alex

---

### Post by JohanDuPlessis on 2013-02-19
A workaround will be much apreciated and get me going again Thanx

---

### Post by TheFu on 2013-02-20
> **JohanDuPlessis said:**
> A workaround will be much apreciated and get me going again Thanx

The tool you are trying to install says is it a Java Decompiler.  This is extremely advanced stuff for Java gurus. I would not tackle it with my limited java skills.

I'm just sayin'.

git and mercurial are easy tools to use, which is the subject of this thread. After the entire DVCS idea is understood - there are youtube videos which explain and introduce it - then just a few commands are needed:
```

git config
git init
git add
git commit
git remote add origin
git branch
git status
git push
git pull
```

That's all that most people need to know.  To get the specifics for each, check the git man page. **man git**

I'm slightly perplexed that a 32-bit or 64-bit issue is stopping anyone with access to source code (regardless of language). I must be missing something.

---

