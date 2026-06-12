---
title: "Java Dual Screen Application"
date: 2009-03-24
forum: Programming Talk
---

### Post by _gokce_ on 2009-03-24
Hello all,

I'm not anywhere around the computer I'm normally working at so I can't post here the specific settings I'm using on it but I will nevertheless try to explain the problem I'm having:

I'm writing a Java application that has two frames (dimension of each: 1280X1024) to be displayed on two different monitors. The application reads the pixel coordinates of the locations these frames will be open from an xml file and calls "setLocation" on those two frames. And I know this simple line used to work as I'd been using it for a long time.

With the new computer, however, which is again running Ubuntu, I've not been able to make the application open the two frames on two monitors. I changed the nvidia-settings configurations but was unable to open two frames on the locations I set them to open and started to suspect that it might be something else... It seems to me that no matter what changes I make to that xml file, my application always opens the two frames on 0x0 on top of eachother.

Has anyone had a similar problem? Or any ideas as to why I may be having this problem?

---

