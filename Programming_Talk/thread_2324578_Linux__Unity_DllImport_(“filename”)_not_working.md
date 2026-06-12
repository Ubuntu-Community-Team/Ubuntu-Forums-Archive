---
title: "Linux : Unity DllImport (“filename”) not working"
date: 2016-05-14
forum: Programming Talk
---

### Post by ashokbugude on 2016-05-14
I have imported "Kinect with OpenNI2"( [https://www.assetstore.unity3d.com/en/#!/content/10693]("https://www.assetstore.unity3d.com/en/#%21/content/10693")) from Unity Asset store. When I run the code , I get below error message
...................................................................
System.DllNotFoundException: UnityInterface2
at (wrapper managed-to-native) KinectWrapper:Init (bool,bool,bool) at  KinectManager.Start () [0x00000] in /home/ashok/New Unity  Project/Assets/KinectScripts/KinectManager.cs:657
UnityEngine.Debug:LogError(Object) KinectManager:Start() (at Assets/KinectScripts/KinectManager.cs:808)
..................................................................
The error message is generated when below code is executed

[DllImport("UnityInterface2", SetLastError=true)]
public static extern int Init(bool isInitDepthStream, bool isInitColorStream, bool isInitInfraredStream);

.......................................................................

I have found below things

[DllImport("UnityInterface2", SetLastError=true)] ------- not working
[DllImport("UnityInterface2.dll", SetLastError=true)] ------- not working
[DllImport("UnityInterface2.dylib", SetLastError=true)] ------- not working
[DllImport("UnityInterface2.so", SetLastError=true)] ------- working but  do not want to use it ( unreferenced symbols as I am unable to compile  the .cpp and .h files properly from [https://github.com/rfilkov/OpenNi2UnityInterface](https://github.com/rfilkov/OpenNi2UnityInterface) to generate .so file)


**Aim :** To do gesture recognition (hand tracking) on Linux 

**Hardware :** Kinect xbox360

**Softwares :** Linux,OpenNI2, NiTE2

**Unity Package used :** Kinect with OpenNI2 ([https://www.assetstore.unity3d.com/en/#!/content/10693]("https://www.assetstore.unity3d.com/en/#%21/content/10693"))
                    

**Existing things about the package (code ):**Its meant for windows OS and Osx (Apple)
                                          (Package contains UnityInterface2.dll (Windows) and libUnityInterface2.dylib(OsX))
                                          (Package does not contain UnityInterface2.so (Linux))

**Existing Platform dependency code  :**
   .....Platform Independent C# code (specifying location of OpenNI2/NiTE2 installation directories(OsX/Linux)..............

                                       If(OS == WIndows OS ) 
                                          use UnityInterface2.dll library [DllImport("UnityInterface2.dll")] ;

                                       else if (OS == OsX ) 
                                          use libUnityInterface2.dylib library; [DllImport("libUnityInterface2.dylib")] ;
  

                             ......... Platform Independent C# code (calling functions in library ) ..............

**Requirement :**  To modify the code to make it work with Linux in following ways
               
               **1.** Use the existing library files (.dll and .dylib ) and call its functions, ie

                   If( OS == Linux ) use UnityInterface2.dll library; [DllImport("UnityInterface2.dll")]---- **(NOT WORKING))**
                               
                                         **OR** 

                   If( OS == Linux ) use libUnityInterface2.dylib Library [DllImport("libUnityInterface2.dylib")]**(NOT WORKING))**


               **2.** Create a .so file (UnityInterface2.so) by compiling the .h and .cpp files in  [https://github.com/rfilkov/OpenNi2UnityInterface](https://github.com/rfilkov/OpenNi2UnityInterface) location and use the following code

                   If( OS == Linux ) use libUnityInterface2.so Library [DllImport("libUnityInterface2.so")]
                 

                   Result : unreferenced symbols as I am unable to compile the .cpp and .h files properly


**Basically Trying to use 1st option, ie to make Linux identify .dll or .dylib files)**

---

