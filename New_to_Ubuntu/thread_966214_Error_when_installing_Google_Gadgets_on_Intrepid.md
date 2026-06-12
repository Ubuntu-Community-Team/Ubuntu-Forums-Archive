---
title: "Error when installing Google Gadgets on Intrepid"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by drazgo on 2008-11-01
Hi everyone, 

I'm having issues while installing google gadgets on the new ubuntu 8.10. This is the error I'm getting when configuring the installing: 

configure: WARNING: Library xml2 is not available, libxml2-xml-parser extension won't be built.


I checked in synaptic, and the package libxml2 is installed, so i really don't know how to solve this one. Can anyone help? 

thanks in advance!
Drazgo

---

### Post by falkTX on 2008-11-01
32 or 64 bit?

---

### Post by falkTX on 2008-11-01
I know there was some deb files for Hardy, not sure about Intrepid.
But I will check, I'm also interested on gadgets

---

### Post by drazgo on 2008-11-01
32 bit i'm using here :)

and i already did a search for the deb packages,and couldn't find any for intrepid. I tried and install the hardy packages, and all went find after installing some dependencies, but when i try to start ggl-gtk, i get another error message: 
> 
laurens@laurens-laptop:~/Bureaublad/gadgets/build/debug$ ggl-gtk
Not a regular file: /
org.freedesktop.DBus.Error.UnknownMethod: Method "getDevices" with signature "" on interface "org.freedesktop.NetworkManager" doesn't exist

No slot registered to handle this reply.
No slot registered to handle this reply.
No slot registered to handle this reply.
org.freedesktop.DBus.Error.UnknownMethod: Method "GetProperty" with signature "s" on interface "org.freedesktop.Hal.Manager" doesn't exist

Not a regular file: /
ggl-gtk: symbol lookup error: /usr/lib/google-gadgets/modules/smjs-script-runtime.so: undefined symbol: JS_SetOperationCallback

---

### Post by falkTX on 2008-11-01
I check it. There's no Intrepid edition on the GoogleGagets on Launchpad (for now).

You probably need the **libxml2-dev**. You seem to be compiling from source, so the *-devs are always required to do that

---

### Post by falkTX on 2008-11-01
I saw a tutorial in Softpedia:
[http://linux.softpedia.com/get/Desktop-Environment/Tools/Google-Gadgets-38486.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Google-Gadgets-38486.shtml)

I'll go try it right now

---

### Post by drazgo on 2008-11-01
nevermind mate! found the solution ;) 

this is how to install on intrepid: 

1. download and install libltdl3: 

[http://packages.ubuntu.com/nl/hardy/libltdl3](http://packages.ubuntu.com/nl/hardy/libltdl3)

it says hardy, but also works on intrepid ;)

2. now just download and install google gadgets 0.10.1-0:

[http://www.getdeb.net/release/3077](http://www.getdeb.net/release/3077)

3. run ggl-gtk
4. that's it! ;)

The problem with the other binaries i found was it was a version with bugs (0.10.1-1) so i just used a version lower and everything works fine ;)

---

### Post by falkTX on 2008-11-01
I don't like messing around with differents versions, but sometimes is necessary.

---

### Post by tgyorgyi on 2008-11-01
Most likely libltdl3 is an obsolete package in Intrepid, but since the installer is for Hardy, it is still looking for it. But this is a nice workaround until the Intrepid version comes out.

---

### Post by Chxta on 2008-11-02
Thanks for this. I was getting tired of the fact that Liquid Weather doesn't work well in Intrepid...

---

