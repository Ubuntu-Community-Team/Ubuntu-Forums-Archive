---
title: "Installing a game, not sure what to do here."
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Jrdrag on 2012-08-22
Just got ubuntu today, and I'm loving it. The only thing I'm a little concerned about are the different file extensions that come with linux. But anyway, I am downloading Urban Terror, and it comes in a .tar package, and when I extract it, the installer is in a .x86 file. I'm not sure what to do with this, and ubuntu doesn't either. Any insight on what to do?

---

### Post by alexftw. on 2012-08-22
As far as I know, UrbanTerror doesn't need to be installed. You have to launch the executable file (I think it's "ioUrbanTerror.x86_64"), *after* marking it as executable (right click, properties, somewhere is a tab that contains something like that). The command to launch an executable file is (if you're in the same directory): ```
./executablefile
``` ...it's actually about the "./".

---

### Post by Jrdrag on 2012-08-22
"bash: no such file or directory"

---

### Post by alexftw. on 2012-08-22
Maybe you've got something like a different package...if that's the case, try finding the executable file (there might be just one), mark it as executable and launch it.

---

### Post by Jrdrag on 2012-08-22
There wasn't an executable, it was only a .rsf, .txt, and a .x86 file. The file is an updater which installs AND updates the game, in one file. I just don't know how to run that file. It's checked as an executable.

---

### Post by alexftw. on 2012-08-22
Where did you get it from? Doesn't look like the download provided by [http://www.urbanterror.info](http://www.urbanterror.info) .

*Checking Website*
Oh yeah, i get it, they've somehow changed it.

"...Then run the **UrTUpdater**, follow the instructions on screen and you should be downloading the latest version of Urban Terror 4.2 ...."

That .txt file might be something like a manual. This .x86 - file (never heard about that filetype before, though) has to be executable. Did you try double clicking it?

---

### Post by Jrdrag on 2012-08-22
> **alexftw. said:**
> Where did you get it from? Doesn't look like the download provided by [http://www.urbanterror.info](http://www.urbanterror.info) .

*Checking Website*
Oh yeah, i get it, they've somehow changed it.

"...Then run the **UrTUpdater**, follow the instructions on screen and you should be downloading the latest version of Urban Terror 4.2 ...."

That .txt file might be something like a manual. This .x86 - file (never heard about that filetype before, though) has to be executable. Did you try double clicking it?
It says there's no applications available to open the application.

---

### Post by 25tom on 2012-08-22
See if you can find the program you want in the Synaptic Package Manager or the Ubuntu Software Centre. Installing software from these usually works better than from other sources.
Hope this helps :)

---

### Post by Jrdrag on 2012-08-22
> **25tom said:**
> See if you can find the program you want in the Synaptic Package Manager or the Ubuntu Software Centre. Installing software from these usually works better than from other sources.
Hope this helps :)
It's not in there.

---

### Post by Jrdrag on 2012-08-22
bump?

---

### Post by synaptix on 2012-08-22
In terminal:

```
cd /path/to/download/directory
```As an example I will use my download directory:

```
cd ~/Downloads/UrTUpdater42
```After that, make it executable:
```
sudo chmod +x ./UrTUpdater.x86
```Then simply execute it with:

```
./UrTUpdater.x86
```

---

### Post by Jrdrag on 2012-08-22
> **synaptix said:**
> In terminal:

```
cd /path/to/download/directory
```As an example I will use my download directory:

```
cd ~/Downloads/UrTUpdater42
```After that, make it executable:
```
sudo chmod +x ./UrTUpdater.x86
```Then simply execute it with:

```
./UrTUpdater.x86
```
I get

bash: cd: /home/alstonm/Downloads/UrbanTerror42/UrTUpdater: No such file or directory

Gosh, why can't there be a .deb file for it? Sigh...

---

### Post by blueshead on 2012-08-22
I'm updating now.  

Open the tar and extract the x86 updater file and place it on your desktop.
Double click the x86 and your download will begin.


```
Urban Terror 4.2 Beta is provided using an extra executable called UrTUpdater.
This small software package will download the full game for you. 
It can also keep your Urban Terror game up to date.

To install Urban Terror 4.2, you just have to run UrTUpdater, 
and the download will start automatically.

```

---

### Post by Jrdrag on 2012-08-22
> **blueshead said:**
> I'm updating now.  

Open the tar and extract the x86 updater file and place it on your desktop.
Double click the x86 and your download will begin.


```
Urban Terror 4.2 Beta is provided using an extra executable called UrTUpdater.
This small software package will download the full game for you. 
It can also keep your Urban Terror game up to date.

To install Urban Terror 4.2, you just have to run UrTUpdater, 
and the download will start automatically.

```
I'm sorry to say, but did you read any of this? It's some weird format that isn't executable. I've double-clicked and tried through terminal. But if you insist, I'll try a fifth time.

---

### Post by blueshead on 2012-08-22
> **Jrdrag said:**
> I'm sorry to say, but did you read any of this? It's some weird format that isn't executable. I've double-clicked and tried through terminal. But if you insist, I'll try a fifth time.

It's working for me.. d/l ing now. Make sure the x86 file is extracted from the tar.  I'll check back in after d/l finished. I opened the tar and drag n dropped the x86 to my desktop.

---

### Post by Jrdrag on 2012-08-22
Apparently they changed it again, because now I get two UrTUpdater.x86's, and they both are 'unknown' file types.

What is this craziness!

oh, and if I extract it to my desktop I can't do ANYTHING with it, double-clicking used to tell me that I didn't have anything to open it with; now nothing happens at all. When I right click>properties>open with, it says "no applications available to open "executable"."

---

### Post by steeldriver on 2012-08-22
are you running a 64-bit system? if it's a 32-bit binary it may not run without 32-bit lib support

[http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di](http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di)

---

### Post by Jrdrag on 2012-08-22
> **steeldriver said:**
> are you running a 64-bit system? if it's a 32-bit binary it may not run without 32-bit lib support

[http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di](http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di)

I'm installing that now, thanks!

---

### Post by blueshead on 2012-08-22
> **steeldriver said:**
> are you running a 64-bit system? if it's a 32-bit binary it may not run without 32-bit lib support

[http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di](http://stackoverflow.com/questions/8752727/executing-32-bit-code-under-ubundu-64-bit-installation-error-no-such-file-or-di)


EDIT-- I made an empty folder-put the x86 in it.. Then it worked..

Maybe thats why it's working here. I'm 64 bit but I d/l ed the 32 bit binarys a long time ago. The game is still downloading.. It's a monster.


For those of you that get it running.. Look for a CTF server called "Fallen Angels"

Great map rotation and nice people (no bots)  my tag     drunk_rabbit

---

### Post by anewguy on 2012-08-22
Could you post the path on the net and file name you downloaded?  If so, we could look at the file(s).

---

### Post by Perfect Storm on 2012-08-22
Try use PLayDeb PPA instead for easy install. They got a lot of games ready for easy installation: [http://www.playdeb.net/updates/ubuntu/12.04/?q=urban](http://www.playdeb.net/updates/ubuntu/12.04/?q=urban)

---

### Post by blueshead on 2012-08-23
I'm up and running. It seems 4.2 is a beta and there are not many servers at all.

I'll stick with 4.1 for now.

---

### Post by alexftw. on 2012-08-23
If you really want UrbanTerror that much, try insalling Desura ([http://www.desura.com](http://www.desura.com)). It's a Steam like client that allows you to install many games with just a few clicks, Urban Terror too. Registration is free.

---

### Post by crisbermud on 2012-09-18
For Ubuntu 64 bits x86, install ia32-libs then extract the UrTUpdater.x86 file and execute it(double - click)

```
sudo apt-get install ia32-libs
``````
cd ~/Descargas/
``````
tar -xf UrbanTerror42.tar
``````
cd UrbanTerror42/
``````
./UrTUpdater.x86 
```then next next next.... bla bla 

enjoy :D

---

### Post by mips on 2012-09-19
> **Jrdrag said:**
> But anyway, I am downloading Urban Terror...

Any insight on what to do?

I dunno why people do this but I am gonna chip in with my 0.02c worth.

Downloading a app/package should be your second last resort, last being compiling from source.

In order:
1. Always check the repos first.
2. Have a look at GetDeb [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/) and see if they have what you need.
3. Search for a PPA, a simple google search for 'application-name PPA' should do the trick. If you find more than one PPA compare them to see which has the latest version of a package and how frequent activity is on the PPA.
4. Download a package from github/sourceforge etc.
5. Compile from source.

If you follow this order you will see that GetDeb has what you need [http://www.playdeb.net/updates/ubuntu/11.10/?q=urban+terror](http://www.playdeb.net/updates/ubuntu/11.10/?q=urban+terror) and the installation is as simple as clicking on a button.

The chances of getting to steps 4 & 5 are extremely rare.

---

### Post by Scott Harrison on 2012-09-19
> **mips said:**
> I dunno why people do this but I am gonna chip in with my 0.02c worth.

Downloading a app/package should be your second last resort, last being compiling from source.

In order:
1. Always check the repos first.
2. Have a look at GetDeb [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/) and see if they have what you need.
3. Search for a PPA, a simple google search for 'application-name PPA' should do the trick. If you find more than one PPA compare them to see which has the latest version of a package and how frequent activity is on the PPA.
4. Download a package from github/sourceforge etc.
5. Compile from source.

If you follow this order you will see that GetDeb has what you need [http://www.playdeb.net/updates/ubuntu/11.10/?q=urban+terror](http://www.playdeb.net/updates/ubuntu/11.10/?q=urban+terror) and the installation is as simple as clicking on a button.

The chances of getting to steps 4 & 5 are extremely rare.
In most cases but he's managed to work it out and he's learned something new. I often think the best part of linux is that it's not made for dummies, sometimes you just have to play around and fiddle until you get it right.

---

### Post by mips on 2012-09-19
> **Scott Harrison said:**
> In most cases but he's managed to work it out and he's learned something new.

Maybe so but a lot of people will eventually go "This is way to much effort to install something, linux sucks!" and back they go to windows. I see no reason to intimidate new users, as they get more comfortable I'm sure some will explore on their own.

---

