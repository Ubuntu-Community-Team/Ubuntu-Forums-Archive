---
title: "Coming from Windows--how can I understand the Unix system?"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-22
Coming from Windows, I have a list of questions:

1. What is the bin folder I keep seeing? Are .sh files the .exe files of Windows?

2. Are the necessary files of an application all contained in a folder where it it is installed? I'm assuming not, so see #3.

 3. Home directory seems to be like the D drive. I know that Linux doesn't technically have registries--is it 100% problem-free to install any kind of application on the Home directory for the purpose of keeping the application *and *its settings fully functional if I were to reformat to a different Linux distro (or reformat to a newer version of the distro I'm using)? What if the application is dependent on certain files not installed in the Home directory and not present on the OS because the distro was reformated? I currently have JDK installed on the Home directory.

4. Will applications installed on the Home directory be fully compatible with all kinds of Linux distros? I see that certain applications are designed with KDE in mind--what does this mean and can I run that on GNOME or other environments?

5. What is the Program Files directory of Linux? What other directories should I know about? All I know is that root is at the very top and /home is like the D drive.

6. What are ways to optimize Linux? For example, what else besides the common clean/purge command to get rid of unnecessary files? Do these commands remove all relevant files of a program that is to be uninstalled? If not, is there a way to determine the list of all files associated with an application and delete those which are *not needed *in other applications installed? Is defragmenting necessary?

7. Even on highly supported distros like Ubuntu, it is recommended to fully reformat the system after every version (every 6 months I'm guessing)? Is it neccessary? I don't want to spend so much time configuring settings on Kubuntu only to have to reconfigure it again after updating.

8. How to automatically update the small system updates? It seems like I'm notified that there is a new update to something every time I boot the computer and I have to manually enter my password to update--it is tedious, but is it necessary?


I subscribed to this thread and will constantly check back until there are no more replies. Thanks.

---

### Post by Lars Noodén on 2015-01-22
1. /bin, /usr/bin, and /usr/local/bin are where most user-oriented executable files are stored.  If you want to see the official list of what goes where, then the manual page for [hier](http://manpages.ubuntu.com/manpages/trusty/en/man7/hier.7.html) is worth looking at.  .sh is a common file name extension for shell scripts, but in non-Windows systems, the name of a file is irrelevant, only what's in it.  So you will find shell scripts that end in .sh and shell scripts that don't.  The way to see what is in a script is to look at the first line and that will tell you what interpreter (bash, dash, perl, python, php, etc ) is being used for that script.  

The necessary files for an application are spread around, some in /usr/lib and maybe some other places.  This is due to dynamic linking and allows different applications to share the same libraries and such, saving space.  Now that disks are big and cheap, relatively speaking, maybe there is a case for static linking these days.

3. I wouldn't know about C:, D:, E:, etc. those labels seem from the CP/M days.  However, /home is where all of your user data and configurations go.  When you install an application, usually it goes in the main part of the system and leaves /home in peace.  Once you run a program, though, your configuration and data will be saved there.  So if you make a /home partition separate from the rest of the disk, you could if you wanted to reformat and reinstall the rest of the system without losing any of your data or personal configurations.  Usually manually added programs get put in /usr/local/bin or in ~/bin, where the tilde (~) is another shortcut for your home directory.

4.  You can run GNOME applications on KDE and KDE applications on GNOME.  However, the first time you install, the installer will pull in a massive amount of prerequisite libraries and supporting files.  You can also install multiple desktop environments (KDE, Unity, LXDE) on a single instance of Ubuntu and switch by logging out and back in again.

5.  The main directory to worry about is /home. That is where all your data and configurations are put automatically.  System-wide configurations go in /etc so if you install some server applications like nginx or Apache2, then you will find the configuration files for them in /etc.  Again see the manual page for hier for a too-detailed overview.  

6.  Ubuntu uses EXT filesystem which does not need to be defragmented, but if the disk is getting too full, then you may experience some improvement by getting a larger disk.  The package manager takes care to remove all files used by a package once they are no longer needed by any others.  Though sometimes things needed a nudge with 'sudo apt-get autoremove' to chase down loose ends.  See the manual page for apt-get for details.  I mention the manual pages a lot because they are the penultimate authority of what a program does, the source code being the ultimate authority.  Not all pages are of equal quality though and not all will make sense when you first start using a program but all are worth looking at when learning a program.

7.  Ubuntu does not accumulate a lot of cruft.  If you don't want to do much configuration after a wipe, then keep a separate /home partition and don't format it during the installation.  There is an option for this when setting up partitions manually during the installation.  Be sure to backup your directory anyway though.

8.  If you go to System Settings -> Software & Updates -> Updates you will have an option for automatic installation of updates.  Myself I prefer to be informed of what's going on, but that's more important on a server than a desktop maybe.

---

### Post by Mark Phelps on 2015-01-22
One thing you need to know immediately is that we here, deal with Linux.  That is NOT the same as UNIX.

---

### Post by buzzingrobot on 2015-01-22
> **garycheng12 said:**
> Coming from Windows, I have a list of questions:

1. What is the bin folder I keep seeing? Are .sh files the .exe files of Windows? 

The Unix/Linux file system is hierarchical.  It's usually portray as a tree. All directories, with one exception, are sub-directories of another directory. That one exception is the '/' directory. 

Unix indicates directory paths like this: /usr/bin/chmod. This means the 'chmod' program lives in the 'bin' directory which is contained within the '/' directory (as all other directories are).

The /usr/bin directory houses executables.  So do a number of other directories, including /bin, /sbin, etc. More here: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard).

'.sh' files are executable scripts, something like DOS/Windows .bat files or Powershell scripts.  A Windows .exe file is a compiled binary executable.

> 2. Are the necessary files of an application all contained in a folder where it it is installed? I'm assuming not, so see #3.

No. In any OS, all but the very simplest programs depend on some number of supporting libraries, etc.  In complex progams, these dependencies can number in the hundreds. Linux uses the concept of 'shared libraries'. This means that if Library A has been installed to support Program One, then any other program that is installed in the future that also depends on Library A will simply use the the copy that has already been installed rather than install another one, say, within its own directory.  

Linux distributions provide package managers and dependency resolvers that keep track of what has been installed and automatically identify, download and install only the dependencies that haven't been previously installed.

 >  3. Home directory seems to be like the D drive. I know that Linux doesn't technically have registries--is it 100% problem-free to install any kind of application on the Home directory for the purpose of keeping the application *and *its settings fully functional if I were to reformat to a different Linux distro (or reformat to a newer version of the distro I'm using)? What if the application is dependent on certain files not installed in the Home directory and not present on the OS because the distro was reformated? I currently have JDK installed on the Home directory.

Unix/Linux does not designate drives as C: or D:, etc.  Physical drives are partitioned.  Those partitions may or may not correspond to an entire physical drive. 

Best to avoid installing applications in /home. 

The /home directory contains the settings and configuration files used by the various applications, etc., installed by that user, and anything else that user wants to put there. While applications can be installed in /home, they should almost always be more properly installed in standardized locations in the filesystem. When you use a distribution's package manager, e.g., Ubuntu's Software Center, this is all done for you. Applications are built to expect to find the supporting libraries, etc., they depend on in these locations.

(BTW, avoid the Windows-esque habit of downloading and trying to install Linux software contained in '.tar.gz.' archives.)

Partitions that are not deleted will be preserved during installation of another distribution.  If directories on those partitions are not formatted during that install, their contents will be preserved. 

4. Will applications installed on the Home directory be fully compatible with all kinds of Linux distros? I see that certain applications are designed with KDE in mind--what does this mean and can I run that on GNOME or other environments?[/quote]

KDE and Gnome are two different GUI interfaces that are built using two fundamentally different supporting GUI libraries and tools. Both are very large and complex, containing hundreds of files. KDE programs can certainly run on systems using the Gnome interface, and vice versa.  However, installing a KDE package on a Gnome system, or a Gnome package on a KDE system, will trigger the installation of all the dependencies that package requires.  In either case, that may amount to many, many package.  E.g., if a Gnome package is installed on a KDE sytem on which no other Gnome packages have previously been installed, then all the packages from the Gnome environment that package depends on will be installed, and then all the packages each of those other packages depend on will be installed, and so forth. 

> 5. What is the Program Files directory of Linux? What other directories should I know about? All I know is that root is at the very top and /home is like the D drive.

No direct equivalent to the Program Files directory exists. See answer #1.

> 6. What are ways to optimize Linux? For example, what else besides the common clean/purge command to get rid of unnecessary files? Do these commands remove all relevant files of a program that is to be uninstalled? If not, is there a way to determine the list of all files associated with an application and delete those which are *not needed *in other applications installed? Is defragmenting necessary?

Defragmenting is typically not necessary. 

I'd suggest putting of thinking about playing with optimizations until you acquire a more thorough awareness of Linux. If nothing else, the web is full of bad advice about that.

The packaging system sees to adding needed packages and removing packages no longer needed. Attempts at manually installing software by extracting it from archives should be avoided, especially by inexperienced users. (And the packaging system will be unaware of their existence.)

> 7. Even on highly supported distros like Ubuntu, it is recommended to fully reformat the system after every version (every 6 months I'm guessing)? Is it neccessary? I don't want to spend so much time configuring settings on Kubuntu only to have to reconfigure it again after updating.

No, that isn't needed. I've never seen that recommendation. Properly administered, a Linux system can be updated and upgraded in place for years.

> 8. How to automatically update the small system updates? It seems like I'm notified that there is a new update to something every time I boot the computer and I have to manually enter my password to update--it is tedious, but is it necessary?

The system will alert you to the availability of updates, small or large.  You can also manually check for updates. Fresh installs typically require a good number of updates, especially if some time has passed since that version's initial release.  Updates are released as they are ready, not on a fixed schedule.

The password is required.  Among other reasons, Unix was created a multiuser system that allows multiple users to log on (with their own /home directories) to a single machine, simultaneously or otherwise. An individual user cannot make changes, like installing software into the file system, that might impact other users without temporarily acting as the root (think 'administrator') user.  Entering that password allows you to act as the root user temporarily, usually for that one command.

The 'root' user can do anything, including quickly and easily trashing a system thanks to a mistake or a typo. You will not be asked "Are You Sure?". Avoid urges to run as root.

You don't have to install updates, of course, but you won't be getting security patches, bug fixes, or updates to programs to ensure they work with updates to other components.

---

### Post by Impavidus on 2015-01-22
I'll try not to repeat all the good advice given already, but here are some additions:

1: .sh files usually denote shell scripts, which are somewhat comparable to .bat files in Windows. Extensions only exist on Linux as a convention. I can rename image.jpeg to image.sh and it will still be a jpeg image. Many executables don't have any extension at all. Shell scripts are just one class of executables.

2: -

3: -

4: -

5: There is no Program Files in Linux. Most files you find in Program Files on Windows systems can be found in /usr/bin (executables) and /usr/share (data files).

6: -

7: You can either move to the next (K-, X, L-)Ubuntu release every 6 months, or stick to the LTS releases for two years. Every April release in even years is an LTS (Long Term Support) release. Most people would do best sticking to LTS releases. When moving to the next release, you can either do a clean install or upgrade. This will keep most of your settings. Some people advise against release upgrades, as they sometimes go wrong, but in my experience they usually work. But if things go wrong, be prepared to do a clean install after all.

8: Security updates can be installed automatically, other updates are not that important. Updates that don't involve installation of new packages can be installed via the update manager without entering your password. These are most updates, except kernel updates. Updates come at random times, sometimes several days in a row, sometimes none in two weeks. You can set the update manager to check only once a week.

---

### Post by coldraven on 2015-01-22
Some config files live in your home directory but are hidden. To hide any file prefix it with a dot, for example .myconfig
To see them in the Nautilus file manager press Ctrl+H
To see them from the command line use ls with the "show all" argument -a  ```
~$ ls -a
```
The ~ shows that you are in the Home folder, the $ shows that you are logged in as a user.

---

### Post by mastablasta on 2015-01-23
unnatented upgrades: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

I don't want to sound rude but it might be good to read the community made manual first (see my signature). or at least glance through it. many things mentioned here are found there. also the stuff you mentioned are in no official documentation so I am not sure whose advice you are following.

things are much simpler than they seem at first. they are different, so some basic knowledge is needed to use them and to change the windows mind set a bit. i think Android OS works in a very similar way.

---

### Post by vasa1 on 2015-01-23
> **Impavidus said:**
> ... 
Extensions only exist on Linux as a convention. I can rename image.jpeg to image.sh and it will still be a jpeg image. ...
I find this business of file extensions a bit confusing, but can't say whether it's because of my operating environment, Openbox session of Lubuntu 14.04, or some other reason.

For example, I have two files with identical content but named differently: test.mkd and test.txt. If I double-click on the first in PCManFM, it will open in Geany. Double-clicking on test.txt opens the file in Mousepad.
```
$ file test*
test.mkd: UTF-8 Unicode text, with very long lines
test.txt: UTF-8 Unicode text, with very long lines
$
```I've given up trying to understand what's going but I gather that how a file is "handled" and "seen" by the system depends on various things such as: the magic number, the extension, the content of the first (few) lines of the file, and various "mime"-related lists.

Some Xubuntu users had [pdf files opening in gimp]("http://ubuntuforums.org/showthread.php?t=2250940") rather than evince. Then, there's a thread titled [How to open some files based on extension rather than mime type?]("https://lists.ubuntu.com/archives/lubuntu-users/2015-January/009232.html").

---

### Post by buzzingrobot on 2015-01-23
> **vasa1 said:**
> I find this business of file extensions a bit confusing, but can't say whether it's because of my operating environment, Openbox session of Lubuntu 14.04, or some other reason.

For example, I have two files with identical content but named differently: test.mkd and test.txt. If I double-click on the first in PCManFM, it will open in Geany. Double-clicking on test.txt opens the file in Mousepad.


If you right-click on a filename, does PCManFM offer an option to change the default tool used to open that file?

Seems to have to do with mime types: [https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes), something I've never been interested in enough to pursue. (That link says mime types do use file extensions.)

---

### Post by vasa1 on 2015-01-23
> **buzzingrobot said:**
> If you right-click on a filename, does PCManFM offer an option to change the default tool used to open that file?

Seems to have to do with mime types: [https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes), something I've never been interested in enough to pursue. (That link says mime types do use file extensions.)
Yes, there is an **Open with ...** option in the right-click context menu. I think what I was trying to get across is that the extension can matter, at least in the example I cited.

I've got into the habit of ensuring that my files have suitable extensions to "assist" the system as much I as I can.

---

### Post by pfeiffep on 2015-01-23
> **garycheng12 said:**
> Coming from Windows, I have a list of questions:
1. - 5.
6. What are ways to optimize Linux? For example, what else besides the common clean/purge command to get rid of unnecessary files? Do these commands remove all relevant files of a program that is to be uninstalled? If not, is there a way to determine the list of all files associated with an application and delete those which are *not needed *in other applications installed? Is defragmenting necessary?Yes there are ways to keep your Linux system running smoothly. I suggest using Synaptic Package manager (available in the Software center) to completely remove programs that you've installed and no longer use or need. I use BleachBit to periodically remove unwanted files. From what I've read and understood defrag in not required on ext file systems. Some folks suggest adjusting the swap use and paring the startup programs read [here]("https://sites.google.com/site/easylinuxtipsproject/first").

> 7. Even on highly supported distros like Ubuntu, it is recommended to fully reformat the system after every version (every 6 months I'm guessing)? Is it neccessary? I don't want to spend so much time configuring settings on Kubuntu only to have to reconfigure it again after updating.I installed multiple times when I was first adjusting my mentality to Linux, but I've found that not necessary after my learning curve. Many folks adopt the 'I want the latest and greatest position' and therefore install frequently. There are many posts about upgrade failures as opposed to fresh installs. I've tried once to to upgrade and failed miserably; consequently I don't upgrade the base Linux OS.If you plan on trying out different Ubuntu flavors you might consider using a separate [home partition]("http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/"). If you have a dual boot customizing [grub]("http://www.gnu.org/software/grub/manual/grub.html") presentation order and timeout might speed boot times.

> 8. How to automatically update the small system updates? It seems like I'm notified that there is a new update to something every time I boot the computer and I have to manually enter my password to update--it is tedious, but is it necessary?
One of Linux strenghts is it's inherent security. Installing a system altering modification requires a password - I strongly suggest that you adopt your thinking here. You may adjust the frequency of updates in system settings - software & updates - updates tab. I strongly also suggest that you maintain a daily update check for security updates.

---

### Post by SeijiSensei on 2015-01-23
> **garycheng12 said:**
> 4. Will applications installed on the Home directory be fully compatible with all kinds of Linux distros? I see that certain applications are designed with KDE in mind--what does this mean and can I run that on GNOME or other environments?

Unless absolutely necessary, you should only install applications from the Ubuntu repositories, or trusted third-party repositories called "[Personal Package Archives]("http://en.wikipedia.org/wiki/Personal_Package_Archive")." If you code your own applications, you can put them in $HOME/bin, or /usr/local/bin (need sudo to copy into this directory).

Most Linux distributions are designed so all the software you might need resides in the repositories or perhaps a PPA.  I haven't installed a program from any other location in years.

I run GNOME apps in KDE and have run KDE apps in GNOME.  Sometimes there are minor issues with the appearance of the program.

---

### Post by Bucky Ball on 2015-01-23
You can avoid upgrading every six months by using an LTS (long-term support) release. They are supported for five years. 12.04 LTS and 14.04 LTS are supported until April 2017 and 2019 respectively. LTS releases can upgraded 'in place' to the next LTS, leapfrogging the interim releases in between. Not true of the interim releases (to get to 16.04 LTS, for instance, from 14.10 would mean upgrading to 15.04>15.10>16.04 LTS, which could be problematic, not to mention tedious). ;)

---

### Post by Derrick_Katula on 2015-01-23
for me the one thing that i failed to put my hand around when i was transitioning from windows to linux was the case sensitive nature of the linux system as opposed to windows

---

### Post by oldrocker99 on 2015-01-23
Another thing Windows users have to get used to is file renaming from within a file manager. You don't click on a filename, hesitate and click again to rename. You have to select 'Rename' from the right-click menu. It did take me all of two days to get used to that, but I thought I'd mention it.

File renaming from the terminal uses the **mv** command, which is also used for moving files from one directory or drive to another. It takes some study of the commands to use, so many users just do those things from within a file manager.

And the earlier post is correct. Linux is **not** UNIX. Actually, the kernel is Linux, and the system it allows you to use is GNU (GNU's Not UNIX). GNU was designed from the ground up to be **better** than UNIX, and it is. It has a huge amount of compatibility with UNIX (in fact, there is a System V version 4 compatibilty standard built into GNU), but while UNIX is/was a proprietary, closed OS, GNU is a free (as in freedom) open source OS. That's a ***BIG*** difference.

---

### Post by Rick_Smith on 2015-02-23
While this does not directly answer any of your questions I have found that studying "The Lunix Command Line" by William E. Shotts to be very useful. I use the CL sparingly, on advice from those more knowledgeable than myself, but TLCL has given me more understanding of how a Linux system is structured and functions. This ebook is available for free in many different places, you should have no trouble finding it. 

edx also has a free and paid course called Introduction to Linux which is also useful to a newbie like me. There is plenty of free info around and is easy to find. Hope this is of some help to you.

---

