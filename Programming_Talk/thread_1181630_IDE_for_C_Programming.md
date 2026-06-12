---
title: "IDE for C Programming"
date: 2009-06-08
forum: Programming Talk
---

### Post by rahul_shilps on 2009-06-08
Hi,

Which one is the good IDE for C Programming. 

I don't want to follow that boring traditional process for executing C program and see the o/p through ./a.out.

I want a nice IDE which can compile my 'C' programs and display output very neatly and good.

Is there any IDE you know and should be compatible to Ubuntu 8.04. On HP Pavillion dv9601AU Laptop OR My Dell OPTIPLEX 330 Desktop.
):P

---

### Post by pmlxuser on 2009-06-08
you can check

Code::Blocks IDE

found in Add/remove  under programming in ubuntu

---

### Post by ad_267 on 2009-06-08
This has been done a hundred times before. Do a search. MonoDevelop is good if you're used to Visual Studio.

---

### Post by froggyswamp on 2009-06-08
How about googling first?
[http://www.google.com/search?hl=en&q=linux+c+ide&aq=1&oq=Linux+C+&aqi=g10](http://www.google.com/search?hl=en&q=linux+c+ide&aq=1&oq=Linux+C+&aqi=g10)

---

### Post by dileepm on 2009-06-09
You may go for **Netbeans**. Eats RAM a bit but thats ok for 1GB+

---

### Post by dwhitney67 on 2009-06-09
> **rahul_shilps said:**
> ...

Is there any IDE you know and should be compatible to Ubuntu 8.04. On HP Pavillion dv9601AU Laptop OR My Dell OPTIPLEX 330 Desktop.
):P

AFAIK, there are no IDEs for your system.  Sorry to say, but you are going to have to rely on vi or emacs, and then use the command line for building your applications.  Sort of like what K&R did.

---

### Post by dileepm on 2009-06-09
No Netbeans has a really fine support for C/C++ programs also, compatible with GCC too

---

### Post by mdurham on 2009-06-09
Try QtCreator, it's in the repos. I've found it to be the best IDE for me so far.
Cheers, Mike

---

### Post by Mirge on 2009-06-09
Geany - [http://www.geany.org/](http://www.geany.org/)

---

### Post by Jimleko211 on 2009-06-09
Geany is amazing for C/C++.  Try KDevelop as well, if you're in KDE.

---

### Post by Mirge on 2009-06-09
> **mdurham said:**
> Try QtCreator, it's in the repos. I've found it to be the best IDE for me so far.
Cheers, Mike

Hm, I haven't been able to find QtCreator in synaptic. Any thoughts? I have universe/multiverse enabled..

---

### Post by Mirge on 2009-06-09
Nevermind, I just downloaded the .bin from the QTCreator website. I'm gonna take a look at it... watched the Intro video and it looks pretty dang nice.

---

### Post by z0mbie on 2009-06-09
I'd recommend [Geany]("apt:geany") also.

---

### Post by Mirge on 2009-06-09
Wow heh, running the installer (.bin) caused a complete freeze... had to reboot & re-download. Lets see if it freezes again...

EDIT:
[http://blog.dixo.net/2009/03/14/using-qt-creator-with-ubuntu-810/](http://blog.dixo.net/2009/03/14/using-qt-creator-with-ubuntu-810/)

Had to follow instructions at top of page:
```

sudo apt-get install libfreetype6-dev  libfontconfig-dev  libxrender-dev libsm-dev libglib2.0-dev
sudo apt-get install libxext-dev libxext6-dbg x11proto-xext-dev 

```

---

### Post by Mirge on 2009-06-09
Well I've been playing with Qt Creator, and I really like the interface.

```

 p, li { white-space: pre-wrap; }  #include <iostream>
 #include <string>
 #include <fstream>

using namespace std;
 
 int main() {
     ofstream writer("/home/mike/cpp/testing.txt", ios::app);
 
     if(!writer) {
         cout << "Unable to open file for writing!" << endl;
     }
 
     writer << "This should be appended to the end of the file!" << endl;
     writer.close();
 }
 

```This is called write2.cpp in /home/mike/cpp.

The "Build" menu is grayed out though, so I can't compile/link in the IDE. Any ideas?

---

### Post by OutOfReach on 2009-06-09
> **Mirge said:**
> Well I've been playing with Qt Creator, and I really like the interface.

```

 p, li { white-space: pre-wrap; }  #include <iostream>
 #include <string>
 #include <fstream>

using namespace std;
 
 int main() {
     ofstream writer("/home/mike/cpp/testing.txt", ios::app);
 
     if(!writer) {
         cout << "Unable to open file for writing!" << endl;
     }
 
     writer << "This should be appended to the end of the file!" << endl;
     writer.close();
 }
 

```This is called write2.cpp in /home/mike/cpp.

The "Build" menu is grayed out though, so I can't compile/link in the IDE. Any ideas?

Hm..I'm not familiar with QtCreator, but if it's like KDevelop then you'll need to create a project and then you might be able to build.

---

### Post by Mirge on 2009-06-09
Yeah, had to create a project then it let me. Was just coming back to post lol.

Really like this IDE, shame it only supports C++ right now.

---

### Post by TheBuzzSaw on 2009-06-09
I would adore Netbeans if it were not such a memory hog. It runs slower than mud, but the interface is amazing. It has intelligent autocomplete and code assistance. I'm downloading the 6.7 RC right now for testing.

CodeBlocks is my weapon of choice right now. It's not as smart as Netbeans, but it runs lightning fast. I'm certainly a fan.

I'm gonna try Geany thanks to all the recommendations here.

---

### Post by Mirge on 2009-06-09
You'll like geany a lot I think. I use it daily and can't live without it now.

Qt Creator seems great, but I can't seem to figure out how to configure/customize it. Edited main.cpp template file, but it's not being used by Qt Creator apparently.

---

### Post by Mirge on 2009-06-10
Tried NetBeans, after 5 mins of tinkering, uninstalled it.

Geany it remains for now... though Qt Creator really does look promising.. just a couple things I wish I could change.

---

### Post by ActiveFrost on 2009-06-10
Geany works enoguh good/fast for me - haven't found anything similar yet :)

---

