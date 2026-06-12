---
title: "tomboy latex plugin help"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by JollyLlama on 2008-10-27
Hi, im pretty new to linux and ubuntu and im having troubles trying to install a latex plugin for tomboy notes. the file i downloaded is the latest version at [http://www.reitwiessner.de/programs/tomboy-latex.html](http://www.reitwiessner.de/programs/tomboy-latex.html) i can manage to extract the files but from there the previous attempts to install it have all failed. ive searched the forums for a couple hours and cant find anything that works, any help at all with this would be greatly appreciated. if you need any more information just let me know. thank you again for any help.

---

### Post by Swermed on 2008-10-27
This is a problem ... ... you are not missing any components?	
Or do not have sufficient authority

---

### Post by JollyLlama on 2008-10-27
> **Swermed said:**
> This is a problem ... ... you are not missing any components?	
Or do not have sufficient authority

honestly, im not sure if i have all the components, but i do know i have the sufficient authority. im really very new to linux and am not sure of a lot. thanks for any more help you can provide.

---

### Post by ad_267 on 2008-10-27
Wow I had no idea this existed. Ok I'm going to install it and work through the steps. So first I've downloaded and extracted the file. I opened a terminal (applications - accessories - terminal) and used the cd command to change into the new directory. Eg if it's on your desktop:

```
cd ~/Desktop/tomboy-latex-0.5/
```

I ran the configure script and I had to install a mono compiler ("configure: error: Can't find "mcs", the mono compiler in your PATH"), you should also make sure you have build-essential installed too:
```
sudo apt-get install build-essential mono-mcs mono-gmcs
```

Now to compile and install:
```
make
sudo make install
```

The sudo in front of make install is required to obtain root priveleges to install the plugin.

Then right click on the tomboy icon and go preferences - Add-ins - Tools and enable LaTeX Math Addin.

---

### Post by JollyLlama on 2008-10-27
ad_267, i followed your instructions as best i could but something still doesn't seem to be working, there was no option for latex in the tomboy addins. i know its long but this is what came up in terminal: ```
christopher@christopher-laptop:~/Desktop/tomboy-latex-0.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/christopher/Desktop/tomboy-latex-0.5/missing: Unknown `--run' option
Try `/home/christopher/Desktop/tomboy-latex-0.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for mcs... /usr/bin/mcs
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for TOMBOY_ADDINS... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
christopher@christopher-laptop:~/Desktop/tomboy-latex-0.5$ make
Making all in src
make[1]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
gmcs -debug -out:Latex.dll -target:library -resource:Latex.addin.xml -pkg:tomboy-addins -r:Mono.Posix Latex.cs
make[1]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
make[1]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5'
christopher@christopher-laptop:~/Desktop/tomboy-latex-0.5$ sudo make install
Making install in src
make[1]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
make[2]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/christopher/Desktop/tomboy-latex-0.5/install-sh -d /usr/lib/tomboy/addins
/usr/bin/install -c -m 644 Latex.dll /usr/lib/tomboy/addins
make[2]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
make[1]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5/src'
make[1]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5'
make[2]: Entering directory `/home/christopher/Desktop/tomboy-latex-0.5'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5'
make[1]: Leaving directory `/home/christopher/Desktop/tomboy-latex-0.5'
christopher@christopher-laptop:~/Desktop/tomboy-latex-0.5$ 
```

im still learning what exactly all the commands do so this is mostly greek to me. any suggestions? thank you very much for the help by the way.

---

### Post by JollyLlama on 2008-10-27
scratch that! i just had to fully close down tomboy and reopen for the addin to appear. im still confused as to what that warning message about the missing file in the code was. thank you again so much for your help.

---

### Post by ad_267 on 2008-10-27
Oops sorry I forgot the step about restarting Tomboy.

I get that error about the missing script being too old too, so I don't think it's anything to worry about. That script is part of the download so it's probably the authors error.

It's not very often you have to compile something in Ubuntu, most things are available from the repositories. But if you want to learn a few of the details there are guides at [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Thanks for introducing me to that plugin! I use LaTeX a lot, hopefully this will be useful.

---

### Post by JollyLlama on 2008-10-27
There seems to be something else wrong now. whenever i put the latex code into tomboy it crashes the program. i have the proper latex packages installed and imagemagick to display the images so im not sure whats going wrong here. in the add in's readme file it says the requirments are:
* tomboy-0.7 or higher
* LaTeX including the ams package on the PATH
* convert (ImageMagick) on the PATH
i have all this installed but on not sure what "on the PATH" means.
thank you for any advice.

---

### Post by ad_267 on 2008-10-27
The PATH is just a list of locations where executable files can be placed so that they can be run just using their name, so this should be satisfied.

It's working fine for me. What version of Ubuntu do you have? The LaTeX packages I have are texlive, texlive-base, texlive-base-bin, texlive-common, texlive-bibtex-extra, texlive-fonts-recommended, texlive-latex-base, texlive-latex-extra, texlive-latex-recommended and texlive-pictures.

One possible way of working out what the problem is is to close Tomboy and then run "tomboy" in a terminal. Then when it crashes it should output an error to the terminal. You can post the output here inside a code block.

Also try running "convert" in a terminal and make sure you get some output giving the ImageMagick version and usage options.

---

### Post by JollyLlama on 2008-10-27
I have ubuntu 8.04 hadry heron. i have the appropriate latex packages and imagemagick seems to be working correctly. here are the unusual things i got for an oput while running tomboy in a terminal:
```
christopher@christopher-laptop:~$ tomboy &
[1] 9473
christopher@christopher-laptop:~$ [DEBUG]: NoteManager created with note path "/home/christopher/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
WARNING: The add-in 'Tomboy.LatexAddin,0.4' is trying to extend '/Tomboy/NoteAddins', but there isn't any compatible add-in defining this extension point
...
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True


```

and it only crashes when i have the addin enabled and i attempt to open a note with latex code already inputed. this is the output when i try to open one of those notes

```

[DEBUG]: Creating Buffer for 'New Note 9'...
[DEBUG]: New Note 9 tags:
[DEBUG]: Latex: Creating image for \[5=i\]...
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.GException: Couldn't recognize the image file format for file '/tmp/tbltx_45535836.png'
  at Gdk.Pixbuf..ctor (System.String filename) [0x00000] 
  at Tomboy.Latex.LatexManager.CreatePixbufAndNotify (Tomboy.Latex.LatexImageRequest request, System.String imageFile) [0x00000] 
  at Tomboy.Latex.LatexManager+<>c__CompilerGenerated4.<WorkOnQueue>c__5 (System.Object +7, System.EventArgs +8) [0x00000] 
  at Gtk.Application+InvokeCB.Invoke () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)
[2]+  Exit 127                tombtomboy

```

---

### Post by ad_267 on 2008-10-27
I get that first error so I don't think that's a problem. I have Ubuntu 8.10 so that could be why it's working for me. I've got no idea what to do to fix this sorry, maybe it would be a good idea to file a bug report at [http://launchpad.net](http://launchpad.net) or contact the plugin author.

Other than that you could try upgrading to 8.10 and see if it helps. The final version is due out in a few days I think.

---

### Post by ad_267 on 2008-10-27
Maybe try installing libpng12-0 if it isn't already installed, although I don't know if that will help.

---

### Post by JohnGalt131 on 2008-10-29
> **JollyLlama said:**
> I have ubuntu 8.04 hadry heron. i have the appropriate latex packages and imagemagick seems to be working correctly. here are the unusual things i got for an oput while running tomboy in a terminal:
```
christopher@christopher-laptop:~$ tomboy &
[1] 9473
christopher@christopher-laptop:~$ [DEBUG]: NoteManager created with note path "/home/christopher/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
WARNING: The add-in 'Tomboy.LatexAddin,0.4' is trying to extend '/Tomboy/NoteAddins', but there isn't any compatible add-in defining this extension point
...
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True


```

and it only crashes when i have the addin enabled and i attempt to open a note with latex code already inputed. this is the output when i try to open one of those notes

```

[DEBUG]: Creating Buffer for 'New Note 9'...
[DEBUG]: New Note 9 tags:
[DEBUG]: Latex: Creating image for \[5=i\]...
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.GException: Couldn't recognize the image file format for file '/tmp/tbltx_45535836.png'
  at Gdk.Pixbuf..ctor (System.String filename) [0x00000] 
  at Tomboy.Latex.LatexManager.CreatePixbufAndNotify (Tomboy.Latex.LatexImageRequest request, System.String imageFile) [0x00000] 
  at Tomboy.Latex.LatexManager+<>c__CompilerGenerated4.<WorkOnQueue>c__5 (System.Object +7, System.EventArgs +8) [0x00000] 
  at Gtk.Application+InvokeCB.Invoke () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at Tomboy.Application.StartMainLoop()
   at Tomboy.Tomboy.StartTrayIcon()
   at Tomboy.Tomboy.Main(System.String[] args)
[2]+  Exit 127                tombtomboy

```

I'm using 8.10 and I get the top error message as well. The terminal output is ```
[DEBUG]: Latex: Creating image for \[ \int{f(x)} \]...
[DEBUG]: Latex: Creating image for \[ f(x) \]...
[DEBUG]: Latex: Creating image for \[ \int{f(x)} \]...
[DEBUG]: Latex: Creating image for \[ f(x) \]...
[DEBUG]: Saving 'New Note 12'...
[DEBUG]: Populating context menu..
```
When I type latex but the images never show up

---

### Post by ad_267 on 2008-10-29
I've got no idea what the problem is there. I think the program developer is the only person who can really help. I'm just lucky it seems to work fine for me I guess.

---

### Post by Alendit on 2008-11-19
Hi,

got same problem here, got pretty much all texlive packages installed and imagemagick is also on board.

EDIT: Nevermind, it works now. No idea why.

Alendit

---

