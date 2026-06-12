---
title: "Getting QT-Designer to work with ERIC - the Python IDE"
date: 2007-03-11
forum: Programming Talk
---

### Post by Ted_Smith on 2007-03-11
Hi

My apologies for being such a dummy....I have searched for the answer but Ubuntu forums are so large now I could not find it (though I am sure it will exist). 

I have installed ERIC, the Python IDE. I also want to use it's GUI developer, QT-Designer for which I note there is a button within ERIC to launch it. When I first pressed it it reported "Could not start QT-Designer. Ensure that it is available at /usr/bin/designer". I looked there, and there was no sub-folder called /designer within ../bin. 

So I went to Trolltech.com and downloaded the opensource X11 version from here : [http://www.trolltech.com/developer/downloads/qt/x11](http://www.trolltech.com/developer/downloads/qt/x11), unzipped the tar file to ~/Downloads where all my downloads go by default. I then followed the 'INSTALL' file instructions which were as follows : 

```


"To configure the Qt library for your machine type, run the
    ./configure script in the package directory."

To create the library and compile all the demos, examples, tools,
    and tutorials, type:

        make


```

followed by 

```


sudo make install


```

All this took a while, about half an hour. 

However, there is still no '/designer' sub folder in /usr/bin, and when I restart ERIC and click the QT-Designer button it comes up with the same error. 

Can anyone help explain what I have done wrong? The INSTALL file did make reference to "If you did not configure Qt using the -prefix-install option, you need to install the library, demos, examples, tools, and tutorials in the appropriate place. To do this, type:

        su -c "make install"   and enter the root password."

which I did not notice until afterwards. Could this be the problem? 

In addition, it mentions about setting environment variables for PATH in the .profile folder. However, I cannot find that. There is a .profile folder for the root user, but not in my user folder? 

I realise my problem is due to a lack of undertsnaidng about compliling from source. If anyoen could tell me what I need to do next, I'd be very much obliged. 

Thanks

Ted

---

### Post by AnRa on 2007-03-17
Type this in Konsole:
```
sudo apt-get install qt3-designer
```
That should do the trick! ;)

---

### Post by Ted_Smith on 2007-03-20
Would you believe it...I had actually tried that but just not with the 3 in the package name! I tried qt, qt-designer, qtdesigner etc, but not qt3-designer!

Thanks a lot

---

