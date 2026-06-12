---
title: "Make error when trying to build program"
date: 2016-02-20
forum: Packaging and Compiling Programs
---

### Post by linuxguy11 on 2016-02-20
I am trying to build something off of github for my keyboard (logitech g-710+) and its called sidewinder. I have downloaded and setup the extracted files but when I did "make" after "cmake .." it fails and tells me: 

```

[ 14%] Building CXX object src/CMakeFiles/sidewinderd.dir/microsoft_sidewinder.cpp.o
/home//Downloads/sidewinderd-master/src/microsoft_sidewinder.cpp: In member function ‘void SideWinder::recordMacro(std::string)’:
/home//Downloads/sidewinderd-master/src/microsoft_sidewinder.cpp:167:17: error: ‘class tinyxml2::XMLElement’ has no member named ‘SetText’
     DelayEvent->SetText(delay);
                 ^
/home//Downloads/sidewinderd-master/src/microsoft_sidewinder.cpp:180:19: error: ‘class tinyxml2::XMLElement’ has no member named ‘SetText’
    KeyBoardEvent->SetText(inev.code);
                   ^
make[2]: *** [src/CMakeFiles/sidewinderd.dir/microsoft_sidewinder.cpp.o] Error 1
make[1]: *** [src/CMakeFiles/sidewinderd.dir/all] Error 2
make: *** [all] Error 2

```

Im at a loss here and have no clue how to fix this. Any ideas?

---

### Post by ajgreeny on 2016-02-20
Have you installed **build-essentials** package?

---

### Post by steeldriver on 2016-02-20
What version of Ubuntu / libtinyxml2-dev do you have? I suspect that SetText() is simply not implemented in the version you have

As the homepage says

> 
Note that the major version will (probably) change fairly rapidly. API changes are fairly common.


[http://grinninglizard.com/tinyxml2docs/index.html](http://grinninglizard.com/tinyxml2docs/index.html)

---

### Post by oldos2er on 2016-02-20
Moved to Packaging & Compiling Programs.

---

### Post by linuxguy11 on 2016-02-20
I have the latest Build-Essential installed (Ubuntu 14.04.4) and the version of tinyxml2 im running is 2.1 and I reread the github page for this program and it says I need tinyxml2 2.2 so I think I need to upgrade that and also libudev needs to be upgraded to 210 so how would I do that?

---

### Post by tolga9009 on 2016-03-10
Hi,

I'm the developer of sidewinderd. Yeah, the versioning of tinyxml can be a bit confusing (it will get replaced by jsoncpp in 0.4.0, but that's another story). There is tinyxml and tinyxml2. While tinyxml is currently available in version 2.6.2, tinyxml2 is on 2.2. They are 2 different, independently developed libraries. First, make 100% sure, that you really got the tinyxml2 library and not falsely installed tinyxml. According to [https://launchpad.net/ubuntu/+source/tinyxml2](https://launchpad.net/ubuntu/+source/tinyxml2), the current repos should be updated to tinyxml2 2.2. So, a simple update should be sufficient, either via GUI or via command-line apt-get ("sudo apt-get update" and "sudo apt-get upgrade").

About libudev: you don't need to upgrade it. Just try out your current version - most likely it will just work. libudev 210 is the minimal version I've successfully tested so far (and it's old enough to be supported by all major Linux distros) - it doesn't mean, that lower versions won't run at all.

If you have any further questions, problems or feedback, I'm all ears. Else, I wish you good luck and have fun with the software ;)! Btw.: the software works for both, the G710 and G710+. Logitech G105 support is coming next.

Cheers,
Tolga

---

