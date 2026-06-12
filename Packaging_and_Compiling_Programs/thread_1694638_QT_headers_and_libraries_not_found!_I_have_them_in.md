---
title: "QT headers and libraries not found! I have them installed!"
date: 2011-02-24
forum: Packaging and Compiling Programs
---

### Post by xdunlapx on 2011-02-24
I'm running 10.10 and I'm trying to install kpumpe (a diabetes management application). I am getting this error:

checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!

I have libqt4 installed as well as the dev. I have no idea what to do to get this to configure. Any help will be greatly appreciated. Thank you.

Brittany

---

### Post by SevenMachines on 2011-02-26
it might be a struggle, kpumpe looks quite old. anyways, qt4 and qt3 are different things, you'll need qt3.
```
 $ sudo apt-get install libqt3-mt-dev
```
should do it. if configure still can't find the headers try passing the directories 
```
 $ ./configure --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/qt3
```

---

### Post by xdunlapx on 2011-02-26
Thanks. It said that I already had qt3 installed. Then it told me I need KDE installed. Oh well I don't feel like installing it. Not if kpumpe is not well maintained. I really need a diabetes management app that can download my meter readings. I was using healthengage.net in Windows but java crashes with it in ubuntu. Oh well. Thank you for your help though. I appreciate it.

Brittany

---

### Post by SevenMachines on 2011-02-26
you can probably get past that with kdelibs4-dev but it looks like the last work done on it was 2002 which is obviously quite a long time ago now so it's likely there would still be issues. You might be able to sort the java problems, but the tired developers pun on their slogan "write once, debug everywhere" is unfortunately still fairly true at least in my experience

---

### Post by xdunlapx on 2011-02-26
Ouch, then kpumpe probably won't work with my Onetouch meter as I assume they were made well after 2002. Darn. I'm surprised I haven't been able to find any current projects for diabetes management in linux. I could try to run it one in wine but I'm not sure it would work. Plus I much prefer healthengage.net as I can just do a list of the glucose readings for my doctor instead of having them bunched into sections of time like midnight-6am, 6am-noon, etc. Most of the applications I've seen for windows do that, which I find frustrating and pretty much useless. I do have a windows machine (my parents laptops) so I'll just use their machines to upload to healthengage.net when I need to in 3 months (when I see my doctor next). Thank you for your help. :)

---

### Post by SevenMachines on 2011-02-26
You should probably look into trying out a couple of different java virtual machines with the website and see how that works out. By default ubuntu uses the certified openjdk, but i've heard that sun/oracles java jre tends to work a little better with some websites

---

### Post by xdunlapx on 2011-02-26
Oh, I hadn't thought of that. I'll see which I have installed and try another one. Thanks!

---

