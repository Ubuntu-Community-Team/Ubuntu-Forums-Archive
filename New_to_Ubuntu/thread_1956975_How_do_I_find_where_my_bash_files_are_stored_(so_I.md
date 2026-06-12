---
title: "How do I find where my bash files are stored (so I can configure an upgrade)?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by jps2012 on 2012-04-11
I'm trying to upgrade my bash (I'm on an old Mac), with the end objective being ... mounting an external drive (I wanted to use the latest version) so I can copy over an iso file onto a disk that will then be used to edit the partitions on an UBUNTU machine. 

I downloaded the tar file, but ./configure doesn't work (I think) unless I'm in the correct bash directory. The ReadMe file for (the unarchived) BASH 4.2 says "To compile Bash, type `./configure', then `make'. " 

No such luck. Would someone tell me if I'm thinking about this wrong? Or how I should proceed (with configuring the upgrade)? Many thanks.

---

### Post by josephmills on 2012-04-11
> **jps2012 said:**
> I'm trying to upgrade my bash (I'm on an old Mac), with the end objective being ... mounting an external drive (I wanted to use the latest version) so I can copy over an iso file onto a disk that will then be used to edit the partitions on an UBUNTU machine. 

I downloaded the tar file, but ./configure doesn't work (I think) unless I'm in the correct bash directory. The ReadMe file for (the unarchived) BASH 4.2 says "To compile Bash, type `./configure', then `make'. " 

No such luck. Would someone tell me if I'm thinking about this wrong? Or how I should proceed (with configuring the upgrade)? Many thanks.

Could you please post errors that you are gettign form ./configure 

thanks

---

### Post by jps2012 on 2012-04-11
Thank you, Joseph. 

Here's my command, and the shell's response: 

sh-3.2# ./configure
sh: ./configure: No such file or directory

---

### Post by GoaTzaR on 2012-04-11
To find your bash, type "whereis bash" from a terminal without the quotes. Hope that helps.

---

### Post by josephmills on 2012-04-11
> **jps2012 said:**
> Thank you, Joseph. 

Here's my command, and the shell's response: 

sh-3.2# ./configure
sh: ./configure: No such file or directory

umm that is odd are you are sure you are in the correct directory ? 
where did you get bash from ? here ? [ftp://ftp.gnu.org/gnu/bash/](ftp://ftp.gnu.org/gnu/bash/)

lets see a ```
find / -name [bB]ash*tar.gz
```
or 
```
find / -type d -name *[Bb]ash*
```
thanks

---

### Post by jps2012 on 2012-04-11
Just FYI: I ran "ps x" because I was trying to kill an annoying calendar notification loop and saw this directory/file: "/usr/sbin/configd" 

Could it be that on this old version of bash (3.2) the configure command is actually called "configd"?

Or is the shell just telling me (past tense) that something was configured? (This is the kind of question we noobies ask to keep the rest of you laughing; we do our part.)

---

### Post by jps2012 on 2012-04-11
Joseph: I'm in my home directory: 

sh-3.2# pwd
/

I downloaded bash here: [ftp.cwru.edu]("ftp://ftp.cwru.edu/pub/bash/bash-4.2.tar.gz")

When I invoke 
find / -name [bB]ash*tar.gz
I get no response. Had to CNTL-c to kill the process. 

The same interminable wait happens when I invoke 

find / -type d -name *[Bb]ash*


The unarchived folder "bash-4.2" is sitting in my downloads folder.

---

### Post by jps2012 on 2012-04-12
Looks like I was too hasty. Even though I signaled end of input, the shells responded (some of these files are on an external harddrive, obviously): 

sh-3.2# find / -type d -name *[Bb]ash*
/Downloads/bash-4.2
/Downloads/bash-4.2/examples/obashdb
find: /net/localhost: Operation timed out
find: /net/broadcasthost: Operation timed out
/usr/share/doc/bash
/Volumes/JPSBackupDrive1/lost+found/dir_1436482/share/doc/bash
/Volumes/JPSBackupDrive1/lost+found/dir_1442260/share/doc/bash
/Volumes/JPSBackupDrive1/lost+found/dir_1571448/share/doc/bash
/Volumes/JPSBackupDrive1/lost+found/dir_1613502/share/doc/bash
/Volumes/JPSBackupDrive1/lost+found/dir_1688664/share/doc/bash

I executed (again) "sh-3.2# find / -name [bB]ash*tar.gz" 

and am waiting for the response.

---

### Post by jps2012 on 2012-04-12
Here's the response from the tar file search (sorry I jumped the gun; thought it was a hang): 

sh-3.2# find / -name [bB]ash*tar.gz
/Downloads/bash-4.2/examples/complete/bashcc-1.0.1.tar.gz
/Downloads/bash-4.2.tar.gz

---

### Post by jerome1232 on 2012-04-12
Okay, you need to run configure from within that bash folder

ie

```
cd Downloads/bash-4.2/
./configure
```

The errors configure throws at you (if any) will be key in figuring out what packages you need to make bash from source.

---

### Post by jps2012 on 2012-04-12
Thanks, Joseph. I'm making progress. But it looks like the lack of a C compiler is preventing configure from working. Here's the command and response (I guess my next question is how do I get and install a C compiler?): 

sh-3.2# ./configure
checking build system type... powerpc-apple-darwin9.8.0
checking host system type... powerpc-apple-darwin9.8.0

Beginning configuration for bash-4.2-release for powerpc-apple-darwin9.8.0

checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/Downloads/bash-4.2':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
sh-3.2# make
sh: make: command not found

I jumped the gun again, seeing all that text fly by, thinking bash had configured (and thus the 'make' command, and the response from the shell).

---

### Post by jps2012 on 2012-04-12
I did a little (very little, because its mostly gobbledygook to me) reading about c compilers, and read that the Intel C compiler won't work with bash 3.2. I found a reference to a tar file that supposedly works with 3.2: 

[I]cbc-2.0.3.tar.gz

[/I]But I've only been able to find one domain that lists that file as a download, and the domain is in Russia (it worries me that I can't find it associated with the search term 'Linux"). So ... I'm wondering whether my paranoia is appropriate. [I]Here's the link for the download:
[/I]
[http://panda.ispras.ru/~cbr/cbc-203.html](http://panda.ispras.ru/~cbr/cbc-203.html)

---

### Post by jps2012 on 2012-04-12
Arrrgh! I mean, thanks JEROME and GoTazR. And Joseph. And to anyone who comes along for the ride.

---

### Post by jerome1232 on 2012-04-12
Install build-essential and try again.

```
sudo apt-get install build-essential
```

---

### Post by jps2012 on 2012-04-13
Jerome and Joseph, I followed your advice, but the shell keeps rejecting the commands. 

Here's what's happening: I execute this" 
cd Downloads/bash-4.2/
./configure
The shell returns this: 

configure: error: no acceptable C compiler found in $PATH

I execute the following: 

apt-get install build-essential
The shell returns this: 

apt-get: command not found
sh-3.2# 

I also tried wget, but that command also isn't available. 

Still stuck (but thanks for the suggestions so far). _Is there another command I can use to find (and interact with) a repository for "build-essential"?_

---

### Post by qyot27 on 2012-04-13
If by "(I'm on an old Mac)" you mean that you're using OS X, there is no apt-get.  You need to install the version of the Xcode suite that goes with the version of OS X being used (which means either installing it from the OS X install disc or downloading it through the Apple Developer Connection; Lion users can get it through the App Store).  Xcode includes the necessary tools - gcc and so forth - to do the compiling.  There's also MacPorts, which could streamline the installation of a newer version of bash.

---

### Post by jerome1232 on 2012-04-13
O.o I had assumed the OP was on a powerpc running Ubuntu, come to think of it I believe Ubuntu dropped powerpc support awhile ago. So yeah oops, perhaps this belongs in the mac users or other os forum?

---

### Post by jps2012 on 2012-04-14
Jerome: It's a Mac problem, but it's also Linux problem, and getting solutions here will help me (given that the core solution is coming from bash) on both OS's.

---

### Post by jps2012 on 2012-04-14
qyot27: I downloaded Xtools yesterday and am working on getting Xtools installed. Thanks very much for the advice. 

I read on a forum yesterday (lost track of the URL) that Xtools would "exclusively" on the Mac for which it was purchased. I know that sounds confusing, but I think the author meant that Xtools had to come from the installation CD (I bought my Mac used, and don't have the CD). 

Again, I know this SOUNDS like an exclusively Mac issue, but the ultimate goal is for me to be able to use bash to help with writing an iso file that will be used to backup my Ubuntu machine. Honestly, the bash update/backup/gpartition issue has become so complicated (spread out over two OS's) that I'm not explaining this very well. But I appreciate folks helping me through it.

---

### Post by qyot27 on 2012-04-14
> **jps2012 said:**
> I read on a forum yesterday (lost track of the URL) that Xtools would "exclusively" on the Mac for which it was purchased. I know that sounds confusing, but I think the author meant that Xtools had to come from the installation CD (I bought my Mac used, and don't have the CD).
No it's not tethered to the install disc.  My parents have bought two iMacs so far, and neither one came with an install disc.  The first one (a 2006 model) originally ran Tiger, and for that I downloaded Xcode through the Apple Developer Connection - it worked fine (and Xcode is freely available from Apple, I didn't have to buy it).

We only got an actual install disc when they decided to upgrade that same computer to Snow Leopard, and it did have the package right there on the disc.



Basically, log into Apple Developer Connection from this page using your Apple ID (the one used for iTunes is fine):
[https://developer.apple.com/downloads/](https://developer.apple.com/downloads/)

In the search box, type 'xcode' and then search.  It'll show the results, like the attached image shows.


The important thing is to download the right version for the OS.  Newer versions of Xcode won't install on versions of OS X older than a certain point.  For instance, you can't install Xcode 3.2 on versions of OSX prior to 10.6 Snow Leopard.  Tiger and Leopard have similar restrictions, if memory serves.

---

### Post by jps2012 on 2012-04-17
Thanks, [qyot27]("http://ubuntuforums.org/member.php?u=59638"). Believe it or not, I'm still trying to figure it out. The download seems to decompress by default to Volumes/. After trying to install MacPorts, I got a response from bash, saying that Xcode wasn't found. 

Someone else told me that I should delete all the Xcode files and download and reinstall again (but if the default target director is Volumes/, I assume it's just going to land there again. 

Long story short: I'm feeling guilty taking this much time on a Mac issue (to ultimately work on an Ubuntu issue). I did post on mac-forums.com, but this forum is sooooooooo much better. It's soooo tempting to go to experts here. 

And I apologize.

---

### Post by qyot27 on 2012-04-17
Normally, .dmg files will automount after they're finished downloading.  That's probably why it 'decompresses' to /Volumes (an icon representing the mounted .dmg should probably also appear on the Desktop).

There should be a .pkg (I think that's it) file in the mounted directory.  If you open that file, it'll start the installation wizard and allow you to install Xcode.

---

### Post by jps2012 on 2012-04-30
Quot27 and others: I'm still trying to upgrade my bash (3.2) for a very long workaround on Ubuntu, for which I need an upgraded bash on a Mac with OS 10.5. I'm having some trouble copying files and would like to ask for command-line help.

I downloaded XCodeTools and am trying to install it in the right directory. It uncompressed into my Applications/ folder. I believe it is supposed to land in Developer/. 

I used mkdir to create a Developer folder, and then used the following command to copy the files over to Developer/. 

bash-3.2# cp -r /Applications/XCodeToolsPackages/* /Users/joel/Developer

There are hundreds (if not thousands) of files in the XCodeTools/Packages directory. But the copy command resulted in only one folder ("Extras") being copied, with one file inside it. 

Here's the response from Terminal: 

cp: /Applications/XCodeToolsPackages/Developer/Applications/Utilities/VisualVM.app: No such file or directory

One thing (among many) I don't understand is ... why would only one folder and one file be copied? Why not hundreds of error messages, instead of just one? 

Did I issue the command incorrectly? What SHOULD I do to copy the files correctly?

---

### Post by jps2012 on 2012-04-30
I think I figured out part of it. I can't copy a set of directories into a directory that doesn't have the same set of subdirectories (please, someone correct me if I'm wrong). 

I BELIEVE I have to use "mv." But here's what I don't understand: when I execute mv, when I'm specifying a path with subdirectories, am I telling bash to copy every directory in the path I've listed, or only the last named directory in the path I've listed? 

For example, if I issue the following command, is only the Developer directory going to be moved into my **joel/** folder (or am I also going to be moving my **Applications/** directory)? 

mv /Applications/XCodeToolsPackages/* /Users/joel/Developer

Many thanks.

---

### Post by qyot27 on 2012-04-30
After installing Xcode, all you have to make sure of is that gcc and the other build tools are on the $PATH, which is as simple as:
```
gcc --version
```
If it responds with a version number and copyright/build information, you're good to go.  If you've followed the install wizard that all installable Mac apps come with, there should be no fiddling over what folder it's in.  It installs the build system components to the standard /usr directory, just like in Ubuntu.  The graphical apps that land in Applications are irrelevant to this purpose.

Then you install MacPorts, as described here (steps 0-2 only):
[http://www.davidbaumgold.com/tutorials/wine-mac/#part-0](http://www.davidbaumgold.com/tutorials/wine-mac/#part-0)

Finally, you update bash:
```
sudo port install bash
```
Which should provide you with bash version 4.2.24, as long as the environment variable doesn't favor /usr/bin before /opt/bin (I think it's /opt/bin).

---

### Post by jps2012 on 2012-04-30
Thanks qyot: I seem to be getting stuck in a lot of endless loops (which I probably wouldn't descend into if I wasn't a beginner). 

I executed "gcc --version"

Response: "command not found" 

I executed "sudo port install bash" 

Response: "command not found"

While XCodeTools seems to be sitting in an XCodeTools directory, I think it's not being found (in the sense of "being read and executed"). 

Again, I'm wondering if the problem might be related to the fact that the files are not in my (newly created) Developer directory (the directory wasn't created during the decompression; I made it, after reading forums about the file hierarchy for XCode).

Maybe a script is telling bash to look in Developer for the files, but the files are in XCodeTools. Correct me if the logic is wrong. 

I'd use apt-get, configure and other commands to work through some of these problems, but bash 3.2 doesn't have those commands. I imagine they ARE in my system (after the download and decompression), but they're sitting outside the command loop that would reference them (so I suspect). 

I've also downloaded MacPorts (as you suggested), but MacPorts can't be installed (according to error messages I'm getting) until XCodeTools is installed. (There's one of the embedded endless loops.)

---

### Post by jps2012 on 2012-04-30
quyot: It's been about 9 days since I downloaded XCodeTools, but I don't believe an install wizard launched with it, during decompression. This might be due to my Finder being broken (not sure about that). That's one of the many problems I'm dealing with. I decompressed the file with the Archive Manager, and it landed in Applications.

---

### Post by jps2012 on 2012-04-30
qyot. SORRY!

---

### Post by qyot27 on 2012-04-30
> **jps2012 said:**
> Thanks qyot: I seem to be getting stuck in a lot of endless loops (which I probably wouldn't descend into if I wasn't a beginner). 

I executed "gcc --version"

Response: "command not found" 
Then you haven't actually installed Xcode.  Since you mentioned it was 10.5 (Leopard), then you'll need to download Xcode 3.1.4 (log into Apple Developer Connection and in the Downloads area, search for 'Xcode 3.1.4 Developer DVD', and download said DVD file - it's almost one gigabyte in size, so it'll be downloading for a while).  It'll automount and show you the contents in Finder.  Double-click on the .pkg file in that Finder window (it may be labelled 'Install Xcode' or some such) and follow the instructions given by the Wizard.  Then shut the Finder, unmount the .dmg file, and if need be, fully close the Terminal and re-open it (or just make the computer restart).  Then try running gcc --version again and see what you get.

```
I executed "sudo port install bash" 

Response: "command not found"
```
That's because MacPorts isn't installed, as you found out later.

> Again, I'm wondering if the problem might be related to the fact that the files are not in my (newly created) Developer directory (the directory wasn't created during the decompression; I made it, after reading forums about the file hierarchy for XCode).

Maybe a script is telling bash to look in Developer for the files, but the files are in XCodeTools. Correct me if the logic is wrong.
Forget about this Developer folder, you don't need it, and it seems to be making this process much more confusing than it has to be.  The tools you need for this do not go into any custom folder, they go into the standard system area that all Unix-like OSes have, as I'll explain a little bit more below.

> I'd use apt-get, configure and other commands to work through some of these problems, but bash 3.2 doesn't have those commands. I imagine they ARE in my system (after the download and decompression), but they're sitting outside the command loop that would reference them (so I suspect).
No, they aren't.  apt is a package management system, and to the best of my knowledge, is only available on Debian-based Linux OSes (like Ubuntu).  The ability for ./configure and what not to run is dependent on you having the right tools installed to the PATH, usually in the /usr/bin directory.  This is true of all Unix-like systems, Linux or Mac.  The tools to compile software in Ubuntu are in /usr/bin, the tools to compile (this kind of) software on Mac are also in /usr/bin.

---

### Post by jps2012 on 2012-05-01
Qyot: You obviously know A LOT about how the system is built and how it works. I'm learning a great deal from your responses, but I'm afraid I'm still stuck. My Finder is broken (see earlier messages--sorry; the 'upside' is that it's forced me to learn a lot of commands, and functions in bash, which I'm applying generously in Ubuntu). 

Do I HAVE to use Finder to do the install, or can I complete it from the command line. Many, many thanks.

---

### Post by jps2012 on 2012-05-01
I'm downloading Xcode 3.1.4 now. I'll see if I can figure out how to install it without being able to use Finder.

---

### Post by jps2012 on 2012-05-02
I downloaded Xcode Tools, mounted it, then copied the files into my Developer directory. But here's the problem: there are now 35 files in the directory, but all are packages. I've read online that I need (instead) to use an installer command in Terminal. But when I execute the following command, I get an error message: 

sudo installer "/Volumes/Xcode Tools" -target /Developer

Response from the shell: 

installer: invalid option /Volumes/Xcode Tools

I'm attempting the install from the command line because my Finder isn't working. 

Any suggestions as to how I should proceed (or observations about what I'm doing wrong)?

---

### Post by qyot27 on 2012-05-02
The installer probably needs the name of a specific package, not the directory it's in.  Alternatively, an asterisk might get it to recognize all the packages in the directory and install them as a group,

"/Volumes/Xcode Tools/*"
or possibly
"/Volumes/Xcode Tools/*.pkg"





Although quite honestly, I think a simpler solution would be to take the minor financial hit to take the machine to an Apple Store and have them fix the Finder and upgrade the machine to 10.6 Snow Leopard (to avoid them peddling more expensive ones at you, buy the $29.00 Snow Leopard upgrade disk and physically take said disk to them and ask them to do the upgrade for you), and then you can just use the App Store to install Xcode.  There'll also probably be a performance boost by going up to Snow Leopard, as it'll clear out some of the OS cruft and more than likely supports 64-bit hardware better than Leopard does.

If you don't care about having an install disk available to recover from, you could let them upgrade to Lion if the computer supports it, but I don't know if that would cost the price for both Snow Leopard and Lion (~$60, plus whatever they might charge for installation) or just Lion.  Lion does not have an install disk, although I seem to remember something about a USB version.

---

### Post by jps2012 on 2012-05-02
Thanks very much, qyot: It's done. Installed. Whew! I put it in a Developer directory. But you're absolutely right. I should have gone to a Mac Store. I didn't realize the upgrade was just $29. Foolish. (But I did learn a lot of new commands, and info about file hierarchies--a lot of that came from you. That's the upside.)

I don't know if the 10.6 upgrade would come with MacPorts. That's where I am now--getting read to install it. I've mounted the dmg file, but don't know what target to specify for the install (no Finder--no chance to click and install). 

The FAQ at [MacPorts Guide]("http://guide.macports.org/") says to install it in /opt/local, but I can't find an /opt directory (I'm on a PPC with OS 10.5). I do have a var/local/ directory.

Is there an optional location (one that would be found in PATH) where I  can install it (and not have to change the PATH variables in  "~/.bash_profile"?

---

### Post by qyot27 on 2012-05-02
> **jps2012 said:**
> Thanks very much, qyot: It's done. Installed. Whew! I put it in a Developer directory. But you're absolutely right. I should have gone to a Mac Store. I didn't realize the upgrade was just $29. Foolish. (But I did learn a lot of new commands, and info about file hierarchies--a lot of that came from you. That's the upside.)

I don't know if the 10.6 upgrade would come with MacPorts. That's where I am now--getting read to install it. I've mounted the dmg file, but don't know what target to specify for the install (no Finder--no chance to click and install). 

The FAQ at [MacPorts Guide]("http://guide.macports.org/") says to install it in /opt/local, but I can't find an /opt directory (I'm on a PPC with OS 10.5). I do have a var/local/ directory.

Is there an optional location (one that would be found in PATH) where I  can install it (and not have to change the PATH variables in  "~/.bash_profile"?
It's a PPC? (wow, did not notice that earlier...the 'powerpc-apple-darwin9.8.0' snippet was a dead giveaway)  Then the upgrade isn't an option at all.  10.5 was the last version of OSX to support PPC.  It would still be a good idea to have them fix the Finder, though.  That would vastly simplify some of these problems.




Perhaps a better route of attack here would be to describe exactly what it is you want to do with the Ubuntu part, because if it's for an entirely different computer (especially one that runs on an Intel processor) it would be easier to troubleshoot from that side.

From the OP, the issue is that there's an ISO file sitting on a partition that the Mac can't read?  So I'm guessing that the reason is that only this Mac can burn CDs, which you need to do so you can burn the disc, and use said disc to edit the partitions on the Ubuntu computer?

In that case, I'd recommend using a USB flash drive to transfer the ISO between the two computers rather than depend on messing with bash (which wouldn't give you the ability to read other filesystems; filesystem support is deeper than the Terminal, and if the ISO is on, say, an ext3 or ext4 partition, then support is really spotty - if not nonexistant - for OSX, even the Intel-supporting versions).  Flash drives usually use FAT as their filesystem, and OSX can handle that no problem, which should be true even for a PPC.

---

### Post by jps2012 on 2012-05-02
Qyot: It's kind of the other way around: my ubuntu machine can't write DVDs (only CDs). I wanted to backup my U machine, but to do that I first needed to use Clonezilla. 

- To do that, I needed then to transfer the dmg over to the Mac to burn a dmg to use as startup disk (I also wanted to create a new partition using Gparted on the U machine--again, another dmg that has to be burned on the Mac) 

- With the Mac Finder broken, I was having to manage all this through the command line. 

- I couldn't figure out how to mount a dmg in Disk Utilities, so my workaround was this: install Xcode Tools and MacPorts, which would allow me (according to some forums) to do autoupdates (and therefore possibly fix Finder) 

- Again, the upside is that I HAD to learn a huge (to me) number of commands and functions and basic info in order to make any progress. If I hadn't broken the Finder, I wouldn't have had much incentive to pick up these skills (and the info). 

- Meaning I've seen it as a positive experience (thanks mostly to help you and others have given me--especially you). But I might be at the point where I WILL just go into the Mac Store and see if I can recover the Frameworks folder I deleted (that contained the script that launches Finder). 

Still, I'd like to finish what I started, so if you know how to either find the opt/local folder that's SUPPOSED (according to the Mac FAQs) be on my system, then please (and pretty please) let me know. 

Or if I can put it in another directory and have that directory recognized by the startup scripts, please let me know that. 

So, right now I've got XCode Installed, but need to follow through with MacPorts (in some mystery directory).

---

### Post by qyot27 on 2012-05-03
Well, /opt may simply get created by the MacPorts installer as part of the install process.  Part of the installation is adding wherever MacPorts is installed to to the $PATH, so that shouldn't be an issue.  Otherwise,
```
sudo mkdir -p /opt/local
```

---

### Post by jps2012 on 2012-05-04
Thank you, qyot. You are AWESOME. I didn't know about the -p switch (and even if I'd read about it beforehand in the man pages, it wouldn't have made sense to me until I understood about the need to force the creation of 'obligatory' directories). 

MacPorts is installing at this moment. Lordie am I glad to get through this. Several folks were incredibly helpful. Hands down, this is the best tech forum I've ever seen--all the more reason to learn Linux: because this is a GREAT community to learn from.

---

### Post by jps2012 on 2012-05-04
And there it is--like a love letter from bash: "installer: The install was successful." 

Next: I learn how to use Clonezilla and Gparted! (God help us.)

---

