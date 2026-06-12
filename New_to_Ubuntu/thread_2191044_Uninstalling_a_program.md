---
title: "Uninstalling a program"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by zeneslev on 2013-11-30
I have installed Qt Creator from an installer that was independent from apt-get. I don't know where it is on my machine, but I see the icon for it in the task bar (or whatever it's called) on the left of the screen. Is there a way I can see what executable is ran when I click on the Qt Creator icon so I can go about removing it from my system? And in general, can I view which file a process was executed from if I have the PID?

Thanks

---

### Post by papibe on 2013-11-30
Hi zeneslev.

A few ideas:

I would start by reviewing the content of what you downloaded. It should be include documentation like txt files, or README files. It is usually included how to uninstall the program.

Even if you found the executable, if you delete it, you may be ignoring libraries and config files, so I would avoid doing that.

In some cases, the installation adds a repository where you can get updates. If that's the case, it may be possible to uninstall it using apt-get itself. If this is the case, this situation may be described on the documentation you downloaded, the website where you get it from, or the support forums of the package itself.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by grahammechanical on 2013-11-30
Another couple of ideas is to see if the application is recorded as installed in the Ubuntu Software Centre. Its icon should have a green tick mark against it. There should then be an option to remove. A second idea is to install Synaptic Package Manager and find the application in Synaptic. If you select one part of the applications files and right click you should see an option to mark for complete removal. That usually removes all Libraries that are part of the dependencies of that program unless they are required by other programs.

Regards.

---

### Post by BenjaminCHILOE IS. on 2013-12-01
Hi,
yes I would firstly checked what apps I had installed lately: Then I would go to the Software Center  click on installed and uninstall those last apps and see if that QTcreator app is gone. Hope this could help.

---

### Post by deadflowr on 2013-12-01
How was qt creator installed?

What installer did you use?

---

### Post by heir4c on 2013-12-01
You can look in the UbuntuSoftwareCenter if it's installed. Type qtcreator (the real name of the package) and see if it's marked with a green icon.

---

### Post by jimmyh1972 on 2013-12-03
try apt-get purge [COLOR=#000000]Qt Creator  (or whatever its name is...)

if not - type in the terminal:

locate [/COLOR][COLOR=#000000]Qt Creator  (or whatever its name is...)

a list will pop up - remove all the components manually:-([/COLOR]

---

### Post by childsey01 on 2013-12-05
please don't try a manual remove. There are always some files you'll miss.
'which' will get you the location of the binary (executable). If you only know a bit of the filename hit tab a few times to get a list of them
You could try dpkg --get-selections and then pipe it to grep to search for anything installed as a debian package.
If you installed it by compiling it and using "sudo make install" then you'll want to go back to where you compiled it from and use "sudo make uninstall" to clean everything up.
If you installed it via a .rpm package then good luck..

---

