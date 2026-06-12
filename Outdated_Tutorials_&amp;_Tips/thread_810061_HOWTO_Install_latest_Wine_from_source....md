---
title: "HOWTO: Install latest Wine from source..."
date: 2008-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jimhap on 2008-05-27
This howto will show any user (including newbies) how to install WINE.

[B]
REMEMBER: THIS IS CUTTING EDGE SOFTWARE!! IT CAN CRASH AND NOT WORK![/B]

This is for people who want to install a newer Wine.
(preferably in Gutsy....
There is a Firefox bug in Hardy, and is very bad.
I had a feeling of not upgrading to Hardy, and that was why....
There is no more updates for wine packages for Gutsy.
So I wrote this. :)

The bug will not be discussed here....)

**DISCLAIMER:**
There is NO WARRANTY provided. Do not attempt to get me if you killed your PC. I can not help you.

I will try to answer questions if I have time. But, there is NO warranty.


**What is Wine?**

Wine is an Windows binary emulator.

(Translating that to understandable format: 
It lets you run most Windows apps on Ubuntu!)

**Why would you want it?**

If you have a favorite program (Photoshop, Dreamweaver, etc.) that is not available for Linux, you can use Wine to run the Windows versions of them in Linux.

(DO try the open source alternatives! They are as good as the others!:))

Now to compiling.....

[B]BEFORE DOING SO:
-------------------------------[/B]
You need:

tons of space (200-350 MB for compilation, 200 MB for install, total 400-550MB)
gcc (comes with ubuntu)
Internet (you should have it if you are seeing this ;))

If you have Wine installed:

Go to menu, click on System, Administration, Synaptic Package Manager.
Search for wine.

Click on wine checkbox, select Remove.

Click Apply.

Let it uninstall. Now you are done.

**----------------------------------------**

**1. Download the latest version!**

You can find them in [http://ibiblio.org/pub/linux/system/emulators/wine/]("http://ibiblio.org/pub/linux/system/emulators/wine/").

The latest version at the time of writing is 1.0-rc2.
Get it here:
[http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.0-rc2.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.0-rc2.tar.bz2)

**REMEMBER WHERE YOU SAVED IT!!!!**

**2. Download your dependencies...**

Open a terminal.
To do so, click Applications, point to Accessories, and click on Terminal.
If you have Kubuntu, just click the icon at the bottom left corner.
That refers to the "start" menu.
    **- FOR HARDY USERS:**
        **-> Have KDE 4**
        Point to the big Applications "button", point to Utilities, and
        click on Konsole.
        **-> Don't have KDE 4**
        Point to Utilities, and click on Konsole.

    **- FOR GUTSY USERS AND OTHERS:**
    Point to Utilities, and click on Konsole.

If you have no idea which step you should follow, refer to the
"What KDE Do I Have" section at the bottom.

Now copy and paste this exactly as is into the terminal:

```

sudo apt-get install libasound2-dev libaudiofile-dev libesd0-dev libaudio-dev libcapi20-dev liblcms1-dev libcupsys2-dev libsane-dev libhal-dev libdbus-1-dev freeglut3-dev libc6-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libglib1.2-dev libglib2.0-dev libgpg-error-dev libice-dev libieee1284-3-dev libjpeg62-dev libldap2-dev libltdl3-dev libmad0-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libpng12-dev libqt3-mt-dev libsm-dev libusb-dev libvorbis-dev libx11-dev libxcursor-dev libxext-dev libxft-dev libxi-dev libxml2-dev libxmu-dev libxrandr-dev libxrender-dev libxslt1-dev libxt-dev libxv-dev render-dev unixodbc-dev x-dev zlib1g-dev libxxf86dga-dev libxxf86vm-dev libjack0.100.0-dev libicu34-dev libungif4-dev libssl-dev lib32ncurses5-dev libldap-dev libsane-dev libhal-dev libgphoto2-dev libcapi20-dev libcupsys2-dev

```

Then press ENTER if needed.

Press y, and ENTER if ever prompted about if you want to install it or not.

If you are a dev, you may already have them. But do it to be safe.
The program WILL NOT install it if you already have it.

**3. Compiling**

While still in the terminal, do this:
```
cd [where you saved the file]
```

**If you have Firefox:**
   If you did not recieve a prompt on where to save the file, it is likely
   that it is saved on your Desktop. In that case, do
```
cd ~/Desktop
```
   Make sure it actually does save by default to your Desktop.
   Open Firefox, click Edit, and click Prefrences.
   It should look like this:

[[IMG]http://img140.imageshack.us/img140/7224/ubuntututorialfirefoxhy5.th.png[/IMG]](http://img140.imageshack.us/my.php?image=ubuntututorialfirefoxhy5.png)

   If you recieved a prompt on where to save the file, do
```
cd [where it was saved]
```

**If you have anything else:**

Just type
```
cd [where it was saved]
```

Now do this:

```
tar -xvf wine-1.0*.bz2
```

If you have more than one source archive (wine-1.0.....bz2), type

```
tar -xvf [archive file]
```

If there were any errors, your download is broken.
Redownload the file....

Now type:

```
cd wine-1.0*
```

Now type:

```
nano ./tools/wineinstall
```

Scroll down and find **CONFARGS=""**.

In the quotes ("") type

```
--prefix=/usr --localstatedir=/var --sysconfdir=/etc
```

If any wrapping occurs (as in some text comes down), remove them.

Now press CTRL-X, y, ENTER.

Now type in:

```
./tools/wineinstall
```

Let the thing run. When prompted, type yes and press ENTER.

Sit back and let it compile.

**4. Installation**

The script you ran will do that for you. 
You may need to type password to do so.

**5. YOU'RE DONE!! :)**

**OTHER STUFF:**

That was easy...
But if you want to do it the HARD way:

1. Do the steps all the was to 
```
cd wine-1.0*
```

Then type this:

```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

Then type 

```
make depend
```

When done, type

```
make
```

After that, do

```
sudo make install
```

Enter password if needed.

Volla! It is installed.


**What KDE Do I Have?**

If you have KDE 3, you have this kind of look on your desktop:

[[IMG]http://img132.imageshack.us/img132/1331/ubuntututoralkde3yt0.th.gif[/IMG]](http://img132.imageshack.us/my.php?image=ubuntututoralkde3yt0.gif)

If you have KDE 4, you have this kind of look on your desktop:

[[IMG]http://img140.imageshack.us/img140/9384/ubuntututoralkde4fc5.th.gif[/IMG]](http://img140.imageshack.us/my.php?image=ubuntututoralkde4fc5.gif)


That's the end! Hope this helps...

Any problems/adjustments are welcome. :)

---

