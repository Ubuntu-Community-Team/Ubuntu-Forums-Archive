---
title: "Running java applet in terminal"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by mbyrd11 on 2011-11-29
I can run applets just fine in an IDE but I can't from the terminal 

the java command requires a main method and when I do applets I don't have a main method.

Is there anyway that I can run my applets from the terminal?

Thanks in advance!

---

### Post by bluexrider on 2011-11-29
I don't believe terminal was designed to do that.

---

### Post by dave0109 on 2011-11-30
Sure, take a look at 'appletviewer' which can be invoked from the command line, though I recall that you need to create some HTML to wrap the applet in.

```

$ appletviewer -?
Usage: appletviewer <options> url(s)

where <options> include:
  -debug                  Start the applet viewer in the Java debugger
  -encoding <encoding>    Specify character encoding used by HTML files
  -J<runtime flag>        Pass argument to the java interpreter

The -J option is non-standard and subject to change without notice.

```

This will bring up another window - the viewer of the applet.  It just depends on how much of it you wanted to run in the terminal.

---

### Post by mbyrd11 on 2011-11-30
Alright thanks I will give that a shot!

---

### Post by mbyrd11 on 2011-11-30
appletviewer worked thanks a ton!
and you do need a .html file.

Thanks!

---

