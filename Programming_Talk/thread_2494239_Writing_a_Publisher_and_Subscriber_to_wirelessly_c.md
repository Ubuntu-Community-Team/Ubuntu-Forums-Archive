---
title: "Writing a Publisher and Subscriber to wirelessly communicate over 2 Linux PCs in C"
date: 2024-01-09
forum: Programming Talk
---

### Post by emwilliams19 on 2024-01-09
Hello, I have also published this question to Stack Overflow and AskUbuntu here: [https://stackoverflow.com/questions/77788683/writing-a-publisher-and-subscriber-to-wirelessly-communicate-over-2-linux-pcs-in](https://stackoverflow.com/questions/77788683/writing-a-publisher-and-subscriber-to-wirelessly-communicate-over-2-linux-pcs-in) and [20.04 - Writing a Publisher and Subscriber to wirelessly communicate over 2 Linux PCs in C - Ask Ubuntu]("https://askubuntu.com/questions/1499530/writing-a-publisher-and-subscriber-to-wirelessly-communicate-over-2-linux-pcs-in").
I wanted to also post here to increase my chance of getting responses but please let me know if I should not repost here. I read that it is okay as long as I link the post but I am new to these platforms so sorry if I am mistaken. I am especially new to Ubuntu Forums so I'm hoping this is an appropriate question for the forum.
 
I have code that is written in C that has a corresponding executable file and both work the same. Both run in a terminal and everything outputs into the same terminal. I am trying to make that code a publisher so that the output values can be sent to my other computer wirelessly which would need a subscriber program on that computer. I have successfully tested the basic ROS tutorials for using simple publishers and subscribers, but ROS only provides examples in Python and C++. I am not familiar enough with C to know how to translate those examples into C and I can't seem to find examples anywhere.


These examples are using strings, but I will be using integers and floats. I'm not asking anyone to translate the entire thing unless you really want to or already have. Any help or advice is appreciated. If there are any other websites, articles, or forums that I just haven't found please link them for me.


I am working with 2 Ubuntu 20.04 computers, one is ROSCube and the other is a Dell PC that has Linux running on it and both use ROS noetic. Thank you!!!


Here are the 3 links for the examples I followed. (I tried to link them but the website wont let me post unless I format it like code). <http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29> <http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29> 
<http://wiki.ros.org/ROS/Tutorials/MultipleMachines>


I have tried all of these successfully I just don't know how to make them compatible to be integrated into my C file.

---

### Post by TheFu on 2024-01-10
This wheel has been re-re-re-invented 50 times.  Why do it again when existing tools already handle it?  Between systems can be as low-level as using sockets. or as high level as using the built-in bash method or anywhere in between, say using ssh or nc.  In the 1990s, we did it using CORBA, but I wouldn't wish that on my worst enemy.  

Today, the modern method is using a REST interface. That lets the sender provide whatever data type they have from json/xml/yaml/csv and the receiver handle each as needed. Use what works best.

Unix sorta has remote stuff built-in by using a pipe too.  One of the first things I learned was how to make a backup using a tape system on a different computer and the tar program on my local system over an rsh/ssh connection between the two systems.  I'd never do that with tar today, but I do push VM storage (binary) between systems really fast using nc about once a year for each VM.

Advanced Unix Programming has multiple chapters on IPC which can be either local or remote.

Or did I completely miss the point of this homework exercise?

---

### Post by emwilliams19 on 2024-01-17
This isn't a homework assignment this is just on my own that I'm trying to figure it out. I'm just trying to run my C code on one computer and have the outputs go to another computer (wirelessly) instead of the host computer's terminal. I'm not sure what you mean in your response ROS tutorials give example in C++ but I need help incorperating it into my C file. You mentioned there are already existing tools to help accomplish this do you have any links that I can look at?

---

### Post by TheFu on 2024-01-17
> **TheFu said:**
> _Advanced Unix Programming_ has multiple chapters on IPC which can be either local or remote.

That's a book.  With paper pages.  Crazy, right?

I listed a number of commands too.  Did you look at those commands, perhaps look at their code?

If you want to run code on a different computer, but have the output shown at the workstation you sit at, use ssh.  Seriously, this has been solved since the days of rlogin and rsh in the 1970s.  rsh/rlogin have been replaced by ssh, which is THE standard for remote stuff like this.  Heck, I have about 15 terminals open right now and all but 2 are actually running on other systems around the world.

If you want to know the details, get that book.

---

