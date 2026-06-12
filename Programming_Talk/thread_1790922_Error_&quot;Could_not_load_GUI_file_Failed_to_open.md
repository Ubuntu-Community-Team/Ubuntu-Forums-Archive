---
title: "Error &quot;Could not load GUI file: Failed to open file 'gui/gui.glade': No such file or&quot;"
date: 2011-06-25
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-06-25
Hello friends,
              I am running a chat application that is based on a framework called as spovnet. I have downloaded a simple chat application which i can use to chat,but when i run the actual output file,i get the error as:

akshay@akshay-desktop ~/Downloads/ariba-0.7.0/sample/hello-spovnet-0.1.0/source $ sudo ./hellospovnet Could not load GUI file: Failed to open file 'gui/gui.glade': No such file or directory
akshay@akshay-desktop ~/Downloads/ariba-0.7.0/sample/hello-spovnet-0.1.0/source $ 

And the glade file is present there,in the GUI folder,jst above the source directory. I also copied it at several locations.
If u need to find spovnet u can go on [http://www.spovnet.de](http://www.spovnet.de)  and for this chat application program :- [https://svn.tm.kit.edu/trac/SpoVNet-Software](https://svn.tm.kit.edu/trac/SpoVNet-Software)

Kindly let me know guys.Thanks a lot... :-)

---

### Post by megabytemonster on 2011-06-30
Did you just run make within the source directory? Because there's also a make file in ~/Downloads/ariba-0.7.0/sample/hello-spovnet-0.1.0/

The gui.glade path isn't relative to where you're trying to run it from, so it can't find it. I don't think you've installed the software completely.

---

### Post by akshay.sulakhe on 2011-06-30
@megabytemonster :- can u temme how to install glade then,so it will find it?which package has it???and how do i add it,so i can run make anywhere.kindly let me know.thanks.

---

