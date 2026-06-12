---
title: "About Cmake problems when portin from windows to ubuntu"
date: 2011-12-27
forum: Programming Talk
---

### Post by y10linux on 2011-12-27
Hi, 

I have had a couple of bad programming days when porting some old libraries from windows to ubuntu 10.10. I have already managed to solve my problems, so I am only posting this in case someone else gets stuck in a similar problem.

I was trying to compile some libraries a workmate had programmed a few years ago. The code was written in C++ and used qt3 (I finally could make do with the installation provided by the synaptic package manager) and used Cmake to compile.

[B]1) Capitalization problems in file names.
[/B]
I had previous experience in this, so I located this quite fast, this time I detected a few more of these than in previous occasions. Most .h files where actually named .H, my workmate assures this was unintentional and due to using visual C++ in windows.

There is really not much to do once you find yourself having this problem, gather some patience and manually change file names and #includes . The long term solution is obviously to get everybody in the same programming environment to use a better programming style.

[B]2) Order problems in included libraries
[/B]
A typical cmakeLists.txt sequence to add an executable might look something like this:

#ADD_EXECUTABLE(exec1 main.cpp) 
# Link the executable to the libraries. 
#TARGET_LINK_LIBRARIES(exec1  lib2 lib3 lib1)

In my case the problem was that some of the code in "lib2" used classes in "lib1", when I tried to link the whole thing to create exec1 I got a lot of "undefined reference" linking error messages.

Just changing the order did the trick, but it took me quite a while to realise what was going on.

#ADD_EXECUTABLE(exec1 main.cpp) 
# Link the executable to the libraries. 
#TARGET_LINK_LIBRARIES(exec1  lib1 lib2 lib3)

Finally, bear in mind that the same command worked in windows, I am not exactly sure if the difference is in Cmake or in the compiler (most probably).

Hope this saves some time to someone and please feel free to improve/correct my explanation wherever necessary.

---

