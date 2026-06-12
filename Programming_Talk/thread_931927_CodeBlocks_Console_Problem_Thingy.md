---
title: "Code::Blocks Console Problem Thingy"
date: 2008-09-27
forum: Programming Talk
---

### Post by Alex J. on 2008-09-27
So, I decided that I want to start coding on my Ubuntu rather than Windows since I just lost my Visual Studio CD and I like Ubuntu better in general. I downloaded Code::Blocks and am somewhat satisfied with it to code in C++.

Unlike Visual Studio though, Code::Blocks doesn't pop up a little window for me that says "Hello World" when I build and run a hello world program or whatever. Am I missing something really simple? Can Code::Blocks do this?

I'd REALLY rather not code using pico or anything.....

---

### Post by SledgeHammer_999 on 2008-09-27
Yes it can! Are you sure you build the "DEBUG" target and not the "RELEASE"? If you manually created the project then go "Project->Properties" Choose the "Build targets" tab and choose the target you want(debug/release/custom) and change the "Type" to "console application" and check "pause when executing ends".

---

### Post by Alex J. on 2008-09-27
Oh awesome. Thanks...just had to play around with it a bit...too much time on VS I guess...
Now for my programming homework! YAY!

---

