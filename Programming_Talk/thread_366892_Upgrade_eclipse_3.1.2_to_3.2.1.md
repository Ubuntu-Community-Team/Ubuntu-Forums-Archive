---
title: "Upgrade eclipse 3.1.2 to 3.2.1"
date: 2007-02-21
forum: Programming Talk
---

### Post by tarek on 2007-02-21
Hi, I have ubuntu dapper and eclipse 3.1.2

how do I upgrade eclipse to 3.2.1?

I enabled all the repositories but still only get the old verion of eclipse.

Thanks,
tk

---

### Post by phossal on 2007-02-21
You could simply download it from eclipse.org. It downloads in a .tar.gz file, which you can simply extract.

---

### Post by tarek on 2007-02-21
I'm new to linux and want to install eclipse in the system rather than extracting it in my home directory. 

can you help with that?

---

### Post by phossal on 2007-02-21
You download eclipse from eclipse.org. You want this: [eclipse-SDK-3.2.2-linux-gtk.tar.gz ]("http://download.eclipse.org/eclipse/downloads/drops/R-3.2.2-200702121330/download.php?dropFile=eclipse-SDK-**3.2.2**-linux-gtk.tar.gz").

Then you extract it to your desktop. The extracted folder is called, appropriately, *eclipse.* Then you move it to /usr/lib (as an example) by issuing:
```
cd ~/Desktop
sudo mv ~/Desktop/eclipse /usr/lib
```
Then make a couple links:```

sudo ln -s /usr/lib/eclipse/eclipse /usr/bin/eclipse
sudo ln -s /usr/lib/eclipse/startup.jar /usr/bin/startup.jar
```
Then you'll have a fully working, system-wide ***eclipse 3.2.2.***

---

### Post by tarek on 2007-02-21
Thanks.

One more question, I program applets and gui's and found that there is a package called SWT which generate code - save time - do you know how to add it to eclipse?

thanks

---

### Post by phossal on 2007-02-21
[FINAL EDIT] No. I have no idea what that is.  :D

---

### Post by MadMan2k on 2007-02-21
> **tarek said:**
> 
can you help with that?
no he can't. 

you must not write random stuff in the system wide directories, since you get in conflict with the package manager. (if your its files overlap)
you also have no way to cleanly remove the files again.

if you want to use the eclipse tarball systemwide put it in /usr/local/ instead.

but the clean way would be getting deb-packages for it, which you will get if you upgrade to edgy.

edit:
this has also the advantage that you can simply install swt via synaptic(libswt) and it will automatically be available in eclipse.

---

### Post by phossal on 2007-02-21
MadMan2k has produced the package in the *backports* repositories called: sun-java6-jdk. While I recommend downloading the current version of Java directly from SUN in the form of their .bin file, MadMan2k insists that it isn't the *Ubuntu Way*. I respect his personal opinion, but I existed before him *and* the package manager. I still choose to do things *my* way, which is why I prefer linux over Windows. In his preparation of the package, he simply uses SUN's available .bin file anyway. The package, being third party, contains any security concerns in SUN's .bin file *plus* any that the self-named MadMan chooses to include. 

Why bother with packages when a direct install is typically so clean, so fast, and *current?* 

In addition, contrary to what he says, you *remove* eclipse using a similar sequence of steps that you used to install it:```

sudo rm -r /usr/lib/eclipse
sudo rm /usr/bin/eclipse
sudo rm /usr/bin/startup.jar
```

Doesn't seem complicated, does it? Once you *benefit* from a few non-package installs, you'll perceive the managers differently. The packages are commonly out of date (as you're realizing) and/or poorly packaged, it's a hassle to diagnose failed or partial installs, and many of the packages are *third* party. It's quite a useful *tool*, but not *always.*

---

### Post by phossal on 2007-02-21
~

---

### Post by lloyd mcclendon on 2007-02-21
before you do that you may want to go to file > export > preferences in eclipse so you won't lose your settings.  then when you get the new version of eclipse from [www.yoxos.com](www.yoxos.com) (highly recommended, check it out!), you can go to file >import and bring them back

ubuntu packages for java stuff makes no sense, just download and keep it in an isolated directory.  no need to go mucking up /etc and /usr/xyz when an extracted vanilla .tar.gz runs perfectly fine out of the box!!

---

### Post by tarek on 2007-02-21
Thanks for the feedback, here is what I did:

- upgraded to Edgy
- installed Java and eclipse using the package manager

I thought about downloading and installing the files myself but don't wanna get into this right now, still new to the system.

I also installed the SWT lib but cannot find it is in eclipse!

Do I have to import SWT to eclipse?

Thanks

---

### Post by phossal on 2007-02-21
> **lloyd mcclendon said:**
> ubuntu packages for java stuff makes no sense, just download and keep it in an isolated directory.  **no need to go mucking up /etc and /usr/xyz when an extracted vanilla .tar.gz runs perfectly fine out of the box!**!
I tend to agree. I download, use, and scrap Java programs continuously. However, I revised the "leave eclipse isolated" advice when I received a bunch of questions about how to get eclipse to function from the menu, in cooperation with package-installed Java's, for other users, etc. Where the folder is usually makes little difference, but adding the links to /usr/bin is a bonus in certain situations. For example, I've come to hate teaching people to add $JAVA_HOME variables to .bashrc.

As I've learned to state: I don't *care* how anyone maintains their system. However, I can help virtually anyone get up and running and solve typical problems if they'll follow my advice. To each his own.

---

### Post by MadMan2k on 2007-02-21
> **phossal said:**
> 
In addition, contrary to what he says, you *remove* eclipse using a similar sequence of steps that you used to install it:
I did not say that it would be complicated; I said you would run into conflicts with the package manager.

you wont be able to install anything eclipse related from synaptic while having it in /usr/lib/eclipse or you want be able to remove any previously installed version if you had  the synaptic version installed beforehand.

---

### Post by phossal on 2007-02-21
> **MadMan2k said:**
> I did not say that it would be complicated; I said you would run into conflicts with the package manager.

you wont be able to install anything eclipse related from synaptic while having it in /usr/lib/eclipse or you want be able to remove any previously installed version if you had  the synaptic version installed beforehand.

That's good advice. I don't *use* the package manager for eclipse, Java, java-related programs or *anything else.* I *hate* the package manager, because everything I find myself wanting to use is so poorly packaged, out-of-date, or difficult to configure (your package included), that I avoid it for everything other than build-essential.

Typically, once you've installed eclipse and java on your own, and avoided the headaches associated with packages like yours, you have no need to use the package manager anymore to maintain them. Your arguments are so tightly tied to your own experience that I find it useless to respond in most cases. Finally, with even a minimal understanding of Ubuntu, you can *still* use the package manager to do everything you're saying can't be done.

---

### Post by MadMan2k on 2007-02-21
> **tarek said:**
> 
I also installed the SWT lib but cannot find it is in eclipse!

Do I have to import SWT to eclipse?
in eclipse go to:
Help->Welcome->Tutorials->Create Hello World SWT Application

there you will find how to build a GUI using SWT. But you might consider keeping with SWING, since it got a real integration love with Java 1.6.

google for "native look and feel" to make your SWING apps look like GTK apps.

---

### Post by Hovang on 2007-05-17
> **MadMan2k said:**
> in eclipse go to:
Help->Welcome->Tutorials->Create Hello World SWT Application

there you will find how to build a GUI using SWT. But you might consider keeping with SWING, since it got a real integration love with Java 1.6.

google for "native look and feel" to make your SWING apps look like GTK apps.

A noob question on this. What does the package libswt3.2-gtk-java do then? The package does not contain the tar.gz SWT file refered in the Hello World tutorial and I can't find the user of the jar files included in the package. But I suppose they are related somehow.

Thanks!

---

