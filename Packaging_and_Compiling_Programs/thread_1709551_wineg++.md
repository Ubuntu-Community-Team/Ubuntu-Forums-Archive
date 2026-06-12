---
title: "wineg++"
date: 2011-03-18
forum: Packaging and Compiling Programs
---

### Post by acklavidian on 2011-03-18
I am trying to compile the D2dClock program from [http://archive.msdn.microsoft.com/ProgramForWindows/Release/ProjectReleases.aspx?ReleaseId=3983]("http://archive.msdn.microsoft.com/ProgramForWindows/Release/ProjectReleases.aspx?ReleaseId=3983") with wineg++. I have installed the windows 7 sdk with winetrick-alpha>>psdwin7 and everything seemed to go well accept it said:
"psdkwin7 install completed, but installed file C:/Program Files/Microsoft SDKs/Windows/v7.0/Bin/SetEnv.Cmd  not found
". I don't know what this means, but I have all of the headers in my wine install that I needed. However, when I try to compile I get include problems. First it said from my main file that it couldn't find "D2d1.h". I looked in the window 7 sdk folder and found it in the include folder with the name "d2d1.h". So I went to the main file, and changed my main file to "#include <d2d1.h>" instead of "#include <D2d1.h>". That got me past the first include error, but now in the windows 7 sdk it access d2d1.h to report another include error saying that "d2d1.h" includes another header called  "dcommon.h". Now I looked in the win 7 sdk, and found a file called "DCommon.h". So I changed that vanilla header to include "Dcommon.h". After that I got another error from d2d1.h asking for "D2DErr.h". I looked and sure enough there is a file called "d2derr.h". This confirmed a previously suspected pattern so I stopped. Now, I understand that windows commands are not case sensitive, so how am I supposed to deal with this in bash. My compile command is:

:~/Desktop/D2DClock$ wineg++ -mwindows main.cpp -I /home/eddie/.wine/drive_c/Program\ Files/Microsoft\ SDKs/Windows/v7.0/Include/

---

### Post by SevenMachines on 2011-03-18
Have you tried running winemaker? i think it 'lower cases' and other things so that your windows sources can be built with winelib

---

