---
title: "how do i execute files marked for executable?"
date: 2015-06-29
forum: New to Ubuntu
---

### Post by sirethsargas77 on 2015-06-29
i am a long time windows user, but finally took the plunge and did a hard drive format and fresh installed ubuntu 14.04 LTS. and so far i love it. i really dont want to go back to windows. i know in windows the .exe extension generally means a double click away form opening the desired program. but in ubuntu i am having a hard time finding out exactly how executable files work. i know the software center is the gui way to do it, which i enjoy. but it seems like if i download a program designed for linux, say from a website not the software cetner i have a hard time figuring out how to run it. when i research it i always come up with a series of terminal commands i have to enter, which assumes that i am familiar with the terminal. i guess what im asking is, do i need to do terminal work everytime i need to run a program that didnt come with the install package of in the software center? is there a way to make a launcher for programs?

i know its not windows i need to kind of reset the way i think of how files work in this os compared to windows. but i am finding it very aggrevating and am almost ready to go back to windows with how complicated it seems to be to do something like run a program designed for linux. can someone please explain in a simple way how executables work in linux? is there any good tutorials for this kind of thing someone can provide some links for?

i recently also started to learn how to use C++ using code blocks. i made a basic program similar to the "hello world" program that compiles and runs fine inside of code blocks. it builds a release version that makes a executable file to run the program. it is a console application. but when i double click it nothing happens. no errors, no messages, just nothing. the whole idea of executable files and programs is aggrevating me to where i almost want to go back to windows for the easier interface and no terminal work whenever i want to do something system related. so if anyone can steer this noob in the right direction on how ubuntu works as a whole with this sort of thing i would greatly appreciate it. i apalogize if this is posted in the wrong category.

---

### Post by TheFu on 2015-06-29
Start here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  Read the reading list starting from the top down.

Linux doesn't use extensions to determine what type of file it is. It uses the 1st line of a file which normally contains a "magic number" that can be recognized by the system.  As far a whether a program can be run or not, that is controlled through the POSIX permissions module used by all Unix and Linux operating systems.  These are multi-user OSes, so if you want to learn Linux, you **must** learn about file permissions and consider the OS multi-user - even if you are the only person on the machine.

Don't know anything about IDEs - don't use them. They had too many details IMHO and lead to people who know the IDE, not how to program.  I've interviewed hundreds of java programmers who knew Eclipse, but didn't know anything about the OS, for example. It was just sad and they didn't get the job.

If you want to be a Unix programmer, you will need to use the shell. That link above has a free PDF book you can work through to gain that mandatory knowledge.  End-users shouldn't need to know this stuff, but programmers should/must.

Any Unix has a steep learning curve for the first 6 months. We've all been there. It is like learning a new language - similarly - like learning a new language, the best way to get there is total immersion. Only use Linux all day, every day. There are a few things that still must be done on Windows (even for me), but limit that to 1 hr per day at most. The struggle is part of the learning technique.

As to running programs downloaded ... best not to load any programs from non-repos for the first 6-12 months.  Then you can add in PPAs ... as a systems admin, I never want to load a program from source or even a .deb package. Doing so removes 90% of why I prefer Linux over all other OSes - the package management and maintenance.  As a programmer, you'll have trouble doing this ... many libraries are only available as source. Not much we can do about it.  That just means you'll need to understand the OS even more to ensure these rogue libraries do not impact anything else running in the system.  That isn't hard, but an understanding of LD_LIBRARY_PATH is necessary.

In 6 months, assuming you do stick with this, your entire life will be changed.

Oh - and to see file/directory permissions the cmd is **ls -al**.  Learn what everything displayed from that command means - everything.  Run it in your HOME and in /tmp. See the differences? Why is that?

---

### Post by dellboy56 on 2015-06-30
Hi there right click on the file you want to execute depending on what distro u have u should see a thing saying execute click that and It will tell you what do you want to use on what file

---

### Post by Bucky Ball on 2015-06-30
Welcome. Windows .exe files are not for Ubuntu. They are for Windows. Unless they are designed to, they won't run natively in Linux and are not applicable. Ubuntu/Linux is not free Windows and not the same in lots of ways and does not work the same way under (or above) the hood. You may need to find alternative applications for your Windows ones, and there are plenty about. Read [this]("http://linux.oneandoneis2.org/LNW.htm"). 

As far as .exe files go, go back, wrong way. Different mindset and thinking. :)

---

### Post by grahammechanical on 2015-06-30
What Microsoft calls executable (exe) Linux calls binary (bin). Each of these bin files needs permission to allow executing the file as a program. The same applies to scripts that we want to run. This is part of the security practice of Linux.

In Ubuntu even though we are administrator we usually work as a standard user. Some Linux distributions allow the user the run a session as administrator or root as it is called in Linux. Ubuntu does not allow us to do that. So, I would not be surprised if a bin file downloaded from some web site did not have permission to allow executing the file as a program. That would happen because at the time of the action we were working as a standard user who does not have authority to give permission to a file to execute as a program. That is part of the security practice of Ubuntu.

And then there is the matter of packaging. The purpose of package management is to tell the application installer  utility about all the libraries that the application depends upon  (called dependencies) so that these can be downloaded and installed at  the same time. They do not necessarily come with the application. Then the application will not crash when we try to run  it.

Ubuntu is built on the Debian distribution of Linux. So we need applications and libraries that are packaged according to the Debian package management method (deb). There is another package format called Redhat Package Management (RPM). Those type of files will need to be converted to deb files if they are to run in Ubuntu.

It is standard practice for Linux programmers to provide icons that will run the application when clicked. This is fine for most of us. Especially when we are a new user to Ubuntu. It is still the method I use after using Ubuntu since 2007.

It is our choice. If we want to run a Linux OS as root and then access the internet and then download who knows what, that is up to us. But we should not be surprised if we find ourselves in the same security mess that Windows uses are in.

On this forum we do not recommend running a Ubuntu session as root. We do not discuss how to do that. Nor, do we feel obligated to help sort out the mess once it happens.

Regards

---

### Post by coldraven on 2015-06-30
I don't know about C++ but say you wrote a program in Python (which is already installed) and called it my-prog.py
You can create a shell script to run it by opening a text editor like Gedit and copying the code below. 
```
#!/bin/sh 
python my-prog.py
```
Save the text file as Myprog (or whatever) and make it executable by right click Properties>permissions> Allow executing file as a program.
Then you can double click Myprog to run it. It does not need a file extention

I did a quick search and found this for compiling C++ on Ubuntu
[http://www.cyberciti.biz/faq/howto-compile-and-run-c-cplusplus-code-in-linux/](http://www.cyberciti.biz/faq/howto-compile-and-run-c-cplusplus-code-in-linux/)

---

### Post by Bucky Ball on 2015-06-30
Please post a new thread in Programming Talk for support with C++ and programming as it has nothing to do with the title or original topic of this thread. Asking two support questions in one thread causes confusion and dilutes community effort. One support request per thread, thanks. Good luck. ;)

---

