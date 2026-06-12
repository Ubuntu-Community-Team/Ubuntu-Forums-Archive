---
title: "About cross compiling libgtk2.0-dev library"
date: 2012-03-10
forum: Packaging and Compiling Programs
---

### Post by djaniel on 2012-03-10
Hi,

       I'm using Parrot's SDK to compile one demo app for Android and ARDrone. This drone is controlled through wifi and is capable of video streaming from two cameras on board. I've been trying to get the Android Demo working on my tablet, it's included in Parrot's SDK. So  far, I've successfully cross compiled both, android application and its native libraries. 



The app runs and I'm able to make the ARDrone take off, but then my  application crashes and no video  is displayed on the screen.


For building native libraries, the make file first runs 'check_dependencies.sh' and install them if they aren't present in the system. One of the dependencies is library libgtk2.0-dev (freely available on Ubuntu repositories). I discovered that this library makes the cross compiler display one weird message:
```

 arm-eabi-gcc: unrecognized option '-pthread'. 


```

My best bet is I'm incorrectly linking library libgtk2.0-dev to create the native libraries, which in term, will be linked to main app for android. 



According to some documents I  found elsewhere in the web, that library supports armel, but I'm not  sure if all flags settings or versions are set correctly for the arm  architecture.
       

Is there a way to make sure all dependencies are set correctly for the arm architecture?

       Any help on this would be greatly appreciated,
@djaniel


ps. I'm also linking these libs:
```


#To use FFMPEG recording
            verify "libavformat-dev";
            verify "libavcodec-dev";
            verify "libavutil-dev";
            verify "libswscale-dev";
            verify "libavfilter-dev";

            #To use the Wiimote in Navigation
            verify "libcwiid-dev";
            verify "libbluetooth-dev";
        
            #To compile Navigation
            verify "libsdl1.2-dev";
            verify "libgtk2.0-dev";
              verify "libxml2-dev";
              verify "libudev-dev";
              verify "libiw-dev";

 

```

---

