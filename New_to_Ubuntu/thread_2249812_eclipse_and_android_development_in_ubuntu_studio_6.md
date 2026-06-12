---
title: "eclipse and android development in ubuntu studio 64 bit."
date: 2014-10-24
forum: New to Ubuntu
---

### Post by logannewbanks on 2014-10-24
Hi everyone. this is my first post on here so ill do my best.  my background is smartphone and gadget repair. i have used ubuntu for years but am just now getting into more than just casual use. 
  I am wanting to set up eclipse on here for android app development. running into some issues ill go into detail about
   I am currently running ubuntu studio 14.04 64 bit on a lenovo ultrabook s405
following a tutorial on youtube to set up the software bundle.   the issue started when i was unable to install the 32 bit libs using "sudo apt-get install ia32-lib."  terminal told me it wasnt available and gave me 3 alternatives to install. i installed them and continued with the process. 
where im at a standstill at this point is when i went to install android packages setting up the sdk tools were showing up to install after i put in the google address but ndk tools were nowhere to be found. i feel like this may be linked to the ia32-lib issue. im gonna link the tutorial im using so you all can see where im at. 
[https://www.youtube.com/watch?v=-qk9c-Ug2UI](https://www.youtube.com/watch?v=-qk9c-Ug2UI)

if anyone can help me with this it will be immensely appreciated. :p

---

### Post by grahammechanical on 2014-10-24
I am not suggesting this as the solution to your problem but  the Ubuntu Developer Tools Center might be another way of doing what you want to do.

[http://blog.didrocks.fr/post/Ubuntu-loves-Developers](http://blog.didrocks.fr/post/Ubuntu-loves-Developers)

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

[https://wiki.ubuntu.com/ubuntu-developer-tools-center](https://wiki.ubuntu.com/ubuntu-developer-tools-center)
> 
[COLOR=#333333][FONT=Ubuntu Beta]The Ubuntu Developer Tools Center is a command line tool which allows you to download the latest version of Android Studio (beta), alongside the latest Android SDK, and all the required dependencies (which will only ask for sudo access if you don't have all the required dependencies installed already), enable multi-arch on your system if you are on a 64 bit machine, integrate it with the Unity launcher&#8230;[/FONT][/COLOR]

In time the Ubuntu Developer Tools Center will support Android Development Tools (ADT) using eclipse.

Regards.

---

