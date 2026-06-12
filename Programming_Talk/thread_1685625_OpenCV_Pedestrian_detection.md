---
title: "OpenCV Pedestrian detection"
date: 2011-02-11
forum: Programming Talk
---

### Post by bhaskarb04 on 2011-02-11
Hi,
I am running VC++ 2010 express edition along with OpenCV2.2 . I am trying to use the pedestrian detection present there. The pedestrian detection binary works well but the source code build but while running is giving me issues. On line 58 or near there is the following line:
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] 
hog.setSVMDetector(HOGDescriptor::getDefaultPeopleDetector());
 
It seems to be a relatively harmless piece of code but it inexplicably crashes there. I believe it seems to be some sort of segementation fault. I have tried to find the definition of "getDefaultPeopleDetector()" but I can't find it. 
 
If anybody can help me that would be great!! Or consequently if you can tell me where the defnition of the function is and I will try to figure it out from there.
 
Thanks in advance[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000] 
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Some Penguin on 2011-02-11
You're using an IDE.  It should have the ability for you to at least get a stack trace, and to step through code and set breakpoints.

---

### Post by lovabill on 2012-10-02
Maybe you can search in the source code.
opencv/modules/objectdetection/hog etc

or try search in opencv for *hog*.cpp

or try search inside the documents for the function.

---

### Post by itmanhieu on 2012-10-24
Hi, I am making pedestrian detection by using OpenCV 2.4.
I read frames from video. The HJ_detectAndDraw() that is the function to detect pedestrian for each frame. When I debug for the program. My program just run for well for the first frame. After that when when my program call the function HJ_detectAndDraw() for the second frame, one error happens as following:" First-chance exception at 0x759b96c3 (KernelBase.dll) in beta.exe: Microsoft C++ exception: cv::Exception at memory location 0x001de3e4".
And output window is: Assertion failed...". I think this error relates to the allocate and release memory for Mat, IplImage or Vector. Bus I dont know how to find exactly the place my error happens. Anyone has give me some advice. How can I solve this problems. Thanks in advance.

---

