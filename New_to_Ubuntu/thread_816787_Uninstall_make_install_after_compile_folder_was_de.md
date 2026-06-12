---
title: "Uninstall make install after compile folder was deleted"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by dmitrijledkov on 2008-06-03
I did ./configure, make, make install on WebKit and epiphany. Now I have deleted those folders, where I was compiling. How do I know uninstall it know? BTW I didn't use any prefix, I think it's installed in /usr/local now.

Could you please help me. Or is my only chance downloading, configuring, compiling again and then fingers cross I'll be able to make uninstall?

Was so silly of me to do this :lolflag:

---

### Post by Yuki_Nagato on 2008-06-03
Lets get things straight: did you delete the files in /usr that control the applications, and now you want to uninstall the application?

Or did you delete the libraries for compiling and making?

---

### Post by dmitrijledkov on 2008-06-03
```

svn checkout http://url.com/trunk Webkit
cd Webkit
./autogen.sh
make
sudo make install
cd ..
sudo rm -r Webkit
```

That's what I did by memory. Everything is still in place (and I can still run epiphany on that WebKit), but I don't know how to uninstall it to build different version. And it is still in /usr/local I think.

:popcorn:

I've heard that I should have used prefix /opt/local or something like that to make uninstalling easier but I don't know how.

---

### Post by Yuki_Nagato on 2008-06-03
Try resetting you computer.  Linux will continue to run things until the computer is reset.  Perhaps you accidentally did a crude uninstall from what I see.

---

