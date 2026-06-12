---
title: "Google Chrome not opening"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by ericstrom on 2012-06-30
Using Lucid Lynx and had Goggle Chrome working for quite a while. Recently it seemed to be opening slower than usual but then working fine after it opened. Now I can no longer open it at all. I click on the icon on the panel and nothing happens. Then I try opening it with Applications, Internet, Google Chrome and still no response at all.

Went to Synaptic and marked it for reinstall and that goes fine (no errors, successful re-installation message). But I still the same problem; nothing happens when I try to open it.

Next I tried the terminal. I tried: google-chrome. Absolutely no response in the terminal, just a flashing cursor. Then I tried: google-chrome --incognito. Again, no response, just a flashing cursor.

Suggestions ? I'd rather stick with Google Chrome then move to Chromium as it has worked well for me.

---

### Post by NikTh on 2012-06-30
Same thread here --> [http://ubuntuforums.org/showthread.php?t=1987940](http://ubuntuforums.org/showthread.php?t=1987940) 
Google Chrome must have problem with an update that recently received. Google Chrome is restricted so cannot do much.. 
i suggest you to try  Chromium (open source google chrome) instead 
or you can wait until Google release a fix.

---

### Post by vasa1 on 2012-06-30
What do you see when you type **google-chrome --version** in a terminal?
If you see **Google Chrome 20.0.1132.47**, you may trying launching the browser from a terminal with a switch:
```
google-chrome --disable-bundled-ppapi-flash
```

---

### Post by tristan8276 on 2012-06-30
So, I wake up this morning and see there's an update for my google chrome.. so, I install said update.  Now, I can load chrome if I use the --disable-bundled-ppapi-flash workaround, but flash is broken.  It's not only broken for my chrome now, though.. it's stopped working in my firefox as well.  I don't mind one of my browsers breaking... but, all of them??!!

I don't want to sound like a complainer, but isn't the point of calling it google-chrome-STABLE that it will be tested and stable before unleashing it on the unsuspecting public?

Anywho, I was wondering if there's any fix or workaround for this yet?  I tried uninstalling chrome, and firefox is still not loading flash.  I also reinstalled my adobe flash plugin through the installer, but to no avail.

---

### Post by vasa1 on 2012-06-30
> **tristan8276 said:**
> So, I wake up this morning and see there's an update for my google chrome.. so, I install said update.  Now, I can load chrome if I use the --disable-bundled-ppapi-flash workaround, but flash is broken.  It's not only broken for my chrome now, though.. it's stopped working in my firefox as well.  I don't mind one of my browsers breaking... but, all of them??!!

I don't want to sound like a complainer, but isn't the point of calling it google-chrome-STABLE that it will be tested and stable before unleashing it on the unsuspecting public?

Anywho, I was wondering if there's any fix or workaround for this yet?  I tried uninstalling chrome, and firefox is still not loading flash.  I also reinstalled my adobe flash plugin through the installer, but to no avail.
As people have pointed out before, this is a community effort where we help each other. Your negative comments are wasted here. If you need help, ask specifically without all the negativity.

---

### Post by tristan8276 on 2012-06-30
You're right... I shouldn't be negative and I will try to resolve this issue on my own.  I apologize to the community, as I truly didn't mean any negativity towards any of you.  I simply didn't understand why updating my software would cause these issues.  But, I know that these are sometimes unavoidable issues, and I should just figure it out.

I am truly sorry.

---

### Post by rippofunk on 2012-07-01
Same problems with flash. 12.04 64bit, I did an update yesterday, was a big one, kernel update, a bunch of other stuff. i check for updates maybe weekly. i run just stable generic everything, no dev, or the like. 
flash was broke in firefox (which was also updated), i uninstalled flash, then reinstalled and it fixed firefox. 
a lot of sites are broken in chrome. google plus, anything with flash content especially. but across the board, stuff is just not rendering properly. I am gonna give the disable flash flag a go.
I hope google jumps on this and squares it away.

---

### Post by ericstrom on 2012-07-08
> **vasa1 said:**
> What do you see when you type **google-chrome --version** in a terminal?
If you see **Google Chrome 20.0.1132.47**, you may trying launching the browser from a terminal with a switch:
```
google-chrome --disable-bundled-ppapi-flash
```

When I enter the code Vasa1 suggests into terminal Google Chrome opens. But if I go to Applications, Internet, Google Chrome, Chrome won't open. What does this tell me and how do I fix it so I can open Chrome from the Applications menu ?

---

### Post by gabmuks on 2012-07-09
**Re: Flash-player problems** 			
 			 			 		   		 		 		I just tried this out of desperation. Found it on Launchpad questions.
It restored the flash-player for Firefox on my machine, but not Chrome.

Hope it will help you.

[COLOR=Blue]
[actionparsnip (andrew-woodhead666)]("https://launchpad.net/%7Eandrew-woodhead666")[/COLOR] [COLOR=Blue]           said     on 2010-12-14:                  #1

 sudo  apt-get --purge remove flashplugin-nonfree flashplugin-installer; sudo  apt-get -clean; sudo apt-get update; sudo apt-get install  mozilla-plugin-gnash

 You will then be using Gnash.


[/COLOR]

---

### Post by ericstrom on 2012-07-11
I had already disabled flash and enabled Gnash. Chrome wouldn't open by clicking through ....Applications, Internet, Chrome. But if I put this statement into terminal,then Chrome opens up an fine

google-chrome --disable-bundled-ppapi-flash

So now I'm stuck having to open Chrome through the terminal using the above statement. It seems to run fie after that. But I notice that after it opens, I see the following in the terminal:


[4236:4236:10296935701:ERROR:gl_surface_glx.cc(65)] GLX 1.3 or later is required.
[4236:4236:10296935906:ERROR:gl_surface_linux.cc(55)] GLSurfaceGLX::InitializeOneOff failed.

So what does this all mean ? What do I do to fix it so I don't have to go into terminal ?

---

### Post by vasa1 on 2012-07-11
> **ericstrom said:**
> ... I see the following in the terminal:

[4236:4236:10296935701:ERROR:gl_surface_glx.cc(65)] GLX 1.3 or later is required.
[4236:4236:10296935906:ERROR:gl_surface_linux.cc(55)] GLSurfaceGLX::InitializeOneOff failed.

So what does this all mean ? What do I do to fix it so I don't have to go into terminal ?
I suspect you can ignore those errors. They seem to be technical stuff but stuff that doesn't need any fixing by us, the end-users.
If you want more detail, you can Google for "gl_surface_linux.cc(55)". I did. I couldn't understand most of the stuff though I got the hurried impression that these error messages may not be present in Chrome 21.

---

### Post by deadflowr on 2012-07-11
A new google-chrome-stable was released today.
 Version 20.0.1132.57-r145807. 

Hopefully it will fix the issues some people have been having.

[http://googlechromereleases.blogspot.com/]("http://googlechromereleases.blogspot.com/")

You should be able to upgrade through the update-manager.
Simply run the "check" feature or sudo apt-get update.

---

### Post by vasa1 on 2012-07-12
> **deadflowr said:**
> A new google-chrome-stable was released today.
 Version 20.0.1132.57-r145807. 

Hopefully it will fix the issues some people have been having. ...
I don't know. Looking at the [bug page]("https://code.google.com/p/chromium/issues/detail?id=134940"), it appears that Pepper Flash will _still_ be unavailable to those with the older CPUs mentioned. But Chrome 20 (or 21 ?) will now start without needing the "--disable-bundled-ppapi-flash" flag.

My *impression* is that Google have no intention of making Pepper Flash run with the older, affected CPUs.

---

