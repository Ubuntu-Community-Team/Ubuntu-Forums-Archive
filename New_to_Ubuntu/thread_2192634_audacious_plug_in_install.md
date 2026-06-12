---
title: "audacious plug in install?"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by soryu on 2013-12-08
I downloaded a plug in for audacious but have no idea how to install it.
it's a tar.gz file.(infinityplug in)
i've read a couple of how to install tar.gz files threads but still have no idea how to install.
:confused:

---

### Post by asus-user on 2013-12-09
> **soryu said:**
> I downloaded a plug in for audacious but have no idea how to install it.
it's a tar.gz file.(infinityplug in)
i've read a couple of how to install tar.gz files threads but still have no idea how to install.
:confused:


It would be much better if you give the complete **file name**,  or the files included in it, if there is a "readme.txt", that would explain everything to you. 
Some plugins need install and others need  only extraction and copy to the plugins directory of the application  (requires root privileges) and they work fine after restarting the  application.

The standard way to **install** tar packages is to open terminal in the directory of the tar archive and run the following command (replace <filename> with the actual file name, and use ***sudo*** infront the command if it asked for root privilege):
```

tar -zxvf <filename>.tar.gz
cd <filename>.tar.gz
make
make install
```

Try it and post any error messages you get here.

---

### Post by kulen19 on 2013-12-10
As far I remember you just have to move the plug-in to the correct location. Have you read this: [http://manual.audacityteam.org/o/man/faq_installation_and_plug_ins.html#linux_plugins](http://manual.audacityteam.org/o/man/faq_installation_and_plug_ins.html#linux_plugins) ? 

I can't remember if you have to unpack it first, but you can do that with installing unrar first(sudo apt-get install unrar) and then unpack it(either by the command-line, or rightclicking on the tar.gz file. I would recommend you put both the compressed file *and *the unpacked contents in the plug-in folder, so you can be sure that you've done it properly.

Best of luck.

EDIT: Sorry, I read Audacity instead of Audacious.

---

### Post by soryu on 2013-12-12
file name is infinity-plugin-4-audacious-0.7.1.
i tried to move the extracted folder to the audacious folder using gksu nautilus. nothing happend.

---

### Post by mc4man on 2013-12-12
It may be a source file that you'd need to compile & may only do so with older versions of audacious. (the plugin source is about 2 years old..
Look inside your extracted folder, should be fairly obvious if it is just the source & not a compiled plugin

---

### Post by sammiev on 2013-12-12
Why not use Synaptic package manager and select audacious?

---

### Post by asus-user on 2013-12-13
> **soryu said:**
> file name is infinity-plugin-4-audacious-0.7.1.
i tried to move the extracted folder to the audacious folder using gksu nautilus. nothing happend.

As I mentioned before, in the file list inside the package there might be a help text file to explain the steps of installing.
I found this link where I could download the mentioned package: 
[http://sourceforge.net/projects/infinity-plugin/files/infinity-plugin-4-audacious/0.7.1/](http://sourceforge.net/projects/infinity-plugin/files/infinity-plugin-4-audacious/0.7.1/) 
inside the package there is a file called "INSTALL" where everything about the installation of this plug-in is explained :)
in short, using Terminal: 
```
cd <the directory containing the package's source code=extracted files>
./configure
make
sudo make install
```

Refer to "INSTALL" file for more details and explanations.

---

### Post by asus-user on 2013-12-13
> **sammiev said:**
> Why not use Synaptic package manager and select audacious?
It is a plug-in which is wanted to be installed, not the main program :)

---

### Post by asus-user on 2013-12-13
> **mc4man said:**
> It may be a source file that you'd need to compile & may only do so with older versions of audacious. (the plugin source is about 2 years old.

yes, the plug-in might be not compatible with the current version of **audacious**, @soryu: I can't tell, and I am not using audacious, so consider that possibility.

---

### Post by soryu on 2013-12-16
> **asus-user said:**
> As I mentioned before, in the file list inside the package there might be a help text file to explain the steps of installing.
I found this link where I could download the mentioned package: 
[http://sourceforge.net/projects/infinity-plugin/files/infinity-plugin-4-audacious/0.7.1/](http://sourceforge.net/projects/infinity-plugin/files/infinity-plugin-4-audacious/0.7.1/) 
inside the package there is a file called "INSTALL" where everything about the installation of this plug-in is explained :)
in short, using Terminal: 
```
cd <the directory containing the package's source code=extracted files>
./configure
make
sudo make install
```

Refer to "INSTALL" file for more details and explanations.


the file is on my desktop how would i type that in?

CD<desktop>??
./configure
make
sudo make install[/???????]
i 've never really used the  terminal to install anything.

"README" says i need SDL1.0.6 or above to run  plugin.
how can i check if i have it?

---

### Post by asus-user on 2013-12-16
> **soryu said:**
> the file is on my desktop how would i type that in?

CD<desktop>??
./configure
make
sudo make install[/???????]
i 've never really used the  terminal to install anything.

"README" says i need SDL1.0.6 or above to run  plugin.
how can i check if i have it?

To navigate to your desktop folder in Terminal:
```
cd ~/Desktop/
```

If the extracted folder is on the desktop, also go in it before continuing by typing:
```
cd infinity-plugin-4-audacious-0.7.1/
```

In short, if the tar.gz file is on your dektop go to Terminal and type these commands one by one:
```
cd ~/Desktop/
sudo tar -zxvf infinity-plugin-4-audacious-0.7.1.tar.gz
cd infinity-plugin-4-audacious-0.7.1/
./configure
make
sudo make install

```

Press [Enter] key, don't write anything after:
```
sudo make install
```


This should install the plugin.

SDL:
To check your version of SDL, type in Terminal:
```
sdl-config --version
```
If the current version is old, you can install hte new one by typing:
```
sudo apt-get install libsdl1.2-dev
```

Hope everything works well for you now :)

---

