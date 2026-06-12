---
title: "How to launch an app from a folder"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by Cyber72 on 2012-12-20
When I install an app I would like to make a shortcut in a folder. Then when I have time I can run it and learn how the app works. As the moment I find I forget the app's name.

I have tried dragging the icon from the dash and dropping it in the "New Apps" folder which I created. There are two problems with this
1) The icon changes
2) When I try to launch the application from the New Apps folder I get the message
* The application launcher "whatever.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.*
(where* whatever *is the name of the app)

The folder New Apps is in my home folder.

---

### Post by Mengsk91 on 2012-12-20
I don't know how to create the shourtcut you say, but you can also try creating a document in the folder (or desktop, as you wish); name it "New Apps" or something of the sort, and take note of your installed apps you wish to try later on. 
Just another idea for the same porpouse;)

---

### Post by twipley on 2012-12-20
Create a text document that will work as a shortcut. Set the executable flag to 1 through file properties (for that file).

Then on the first line type the name of the program, for example:
```
rdesktop & exit
```

(Which would fire up the program internally known as "rdesktop," then exit the terminal at once.) Sometimes I think two &s are needed, but then the terminal windows stays there until the launched process is exited.

Good luck. ;)

---

### Post by cortman on 2012-12-20
Or you can simply find the location of the binary by running

```
which program_name
```

in a terminal, then create a symlink to the binary using the path returned.

---

