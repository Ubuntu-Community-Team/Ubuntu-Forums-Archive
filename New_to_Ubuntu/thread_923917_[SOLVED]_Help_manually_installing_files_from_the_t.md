---
title: "[SOLVED] Help manually installing files from the terminal"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by semitone36 on 2008-09-18
Hi there everyone

I would like to say that I am far from a beginner but this seems like a beginner question so Ill put it here.  Ive learned a ton about Ubuntu since I switched to it a while ago but there is one thing that has me totally in the dark that I really need to figure out how to do. 

Installing without Synaptic.:confused:  Ive downloaded a ton of things like .tar .zip files roms and other programs.  But I can NEVER figure out how to get them from my desktop to my applications menu.  Ive looked at the README files but I might as well be reading chinese.  I understand a lot of commands and uses for the terminal but Im not advanced enough to know how to install downloaded packages manually.

Is there anyone who can explain to me this process?  Just so we're on the same page lets use Azureus Vuze for example.  I downloaded a tar file from their website to my desktop.  It's full of .jar .png and .txt files and plugins for the program.  How do I combine all of this into an executable file with all the plugins installed and with the .png as the launcher on my desktop?

Haha sorry I realize thats kind of a lot to ask but is there anyone up to the challege?  Thank you very much in advance:)

---

### Post by Gannon8 on 2008-09-18
.tar.gz files are usually source archives. You probably need to compile them. You should really prefer apt-get though.

To compile something, first install build-essentials
```
sudo apt-get install build-essentials
```
Then most source archives use a file called configure to set the source code up. After navigating to the directory of the source, run:
```
./configure
```
Then:
```
make
```
and finally:
```
make install
```

If there still isn't a menu, you can manually add in an entry.

Edit: Oh it is a jar file? That means it is a java file. Install java and run it like that.

---

### Post by tuxxy on 2008-09-18
Think you would be best with this for the last option

```
sudo make install
```

---

### Post by Pro-reason on 2008-09-18
> **semitone36 said:**
> Ive downloaded a ton of things like .tar .zip files roms and other programs.  But I can NEVER figure out how to get them from my desktop to my applications menu.  Ive looked at the README files but I might as well be reading chinese.

If that's the case, then frankly you shouldn't try.  It will just be frustrating.  Look for stuff in Synaptic instead.  For example, you are trying to install Azureus, which is a Bittorrent client.  There are several excellent Bittorrent clients available in Synaptic, including Azureus.

If you Google for &#8220;compiling Linux source code&#8221;, you will find everything you would possibly need to know about compiling, but you really ought to take advantage of all the hard work that has gone into creating the software repositories used by Synaptic to give you access to many thousands of bug-tested programs.

We could naïvely tell you to type &#8220;./configure&#8221;, then &#8220;make&#8221; then &#8220;sudo make install&#8221;, but what if there is no configure script?  What if it is a static binary?  What if it is Java-based?  What if there are unsatifiable dependencies?  There is no substitute for actually knowing what you are doing.

Just use Synaptic.

---

### Post by semitone36 on 2008-09-18
apt-get looks files up through Synaptic though doesnt it?  I wanted to use Azureus because I couldnt find it in the repositories so I figured it would be a good learning device.  Thanks for the reply though! Ill try it out in a second here...

---

### Post by mc4100 on 2008-09-18
> **tuxxy said:**
> Think you would be best with this for the last option

```
sudo make install
```
Or possibly
```
sudo checkinstall
```
Yes it's hack-ish, but usually it works, and means the package can be easily removed.

---

### Post by semitone36 on 2008-09-18
> **Pro-reason said:**
> If that's the case, then frankly you shouldn't try.  It will just be frustrating. 

haha thanks for the support lol.  

Im actually in my freshman year of CompSci and I would really like to get some background in Linux.  Trust me I am willing to learn

---

### Post by tuxxy on 2008-09-18
> **mc4100 said:**
> Or possibly
```
sudo checkinstall
```
Yes it's hack-ish, but usually it works, and means the package can be easily removed.

heh nice, also you may need to install the package 

```
sudo apt-get nstall checkinstall
```

---

### Post by Pro-reason on 2008-09-18
> **semitone36 said:**
> apt-get looks files up through Synaptic though doesnt it?  I wanted to use Azureus because I couldnt find it in the repositories so I figured it would be a good learning device.  Thanks for the reply though! Ill try it out in a second here...

It's the other way round.  Synaptic uses the APT system.

Azureus and several excellent Bittorrent clients are available in the repositories.  

If a program you really need (not Azureus) is not in the repositories, then the next step is to find a repository that contains it.

In Synaptic, there are several extra repos that you can enable, if they are not already (e.g. proposed, backports, etc).

If that's still not enough, then find a third-party repo and it to yout repository list.  [Launchpad]("https://launchpad.net/ubuntu/+ppas") is a great place to look for these.

The next stage, if that doesn't work out, is to find a .deb file on the web somewhere and install that.

If even that fails, then look for an .rpm file, convert it to .deb (using Alien), and install that.

The absolute last resort is to download some random tarball and try to work out whether it requires compilation of some sort.

> haha thanks for the support lol.

Im actually in my freshman year of CompSci and I would really like to get some background in Linux. Trust me I am willing to learn

Heh, I didn't mean to imply that you were totally clueless, just that you are needlessly jumping into the deep end.

---

### Post by semitone36 on 2008-09-18
Whoa whoa whoa... one at a time please! haha okay so what is the difference between "make" "make install" and "checkinstall"? What do these commands do?  Should I still use the first few commands gannon sugested?

---

### Post by T3h_Dohtem on 2008-09-18
It depends on what you're downloading. Sorry, I'm not familiar with the program you mentioned. There are basically 3 different types of files that you will get online for linux.

Package Files - These are packs of files, set to install on your computer, and are usually distribution specific. They often come with a .deb extension, but not always. They are by far the easiest to intall, usually you can just double click them and your package manager will install them for you.

Precompiled Binaries - These can be exectuable installers, or just the program itself, they will generally have an extension of .bin or .sh and can be run from the command line by typing ./filename (you will need to make sure that the file is executable, try typing 'chmod 700 filename' if it is not). These may come in zip or tar files, so look around for a .bin or .sh file in the directory if you're not sure what you downloaded. If it is an installer, and needs to install to a common directory (such as /bin) you may need to run the command with sudo, just be careful that you know what you're getting!

Source Code - Source almost always comes in tar files, and is a bit harder to give generic instructions for. They generally need to be installed from the command line, once you extract the tar, move to the directory, and you can start building. There are several different ways that it could go from here, depending on the files, and most places will have instructions on how to build, but basically, it *may* go like this.

The first thing you need to do if you are going to compile is run this command to install the most common programs needed for building programs:
sudo apt-get install build-essential make

Some sources have an auto config script in the source directory and can be run with: ./configure
Watch the output here, because it may give errors, or it may tell you you need to install different libraries. If it says, for example, you need libgtk5.0, you can simply type: sudo apt-get install libgtk5.0
and in most cases, aptitude will find and install the library. Sometimes you will need to open synaptic and search for the right one, the names are not always the same, and sometimes version numbers can cause problems as well.

If your source doesn't have a config script, or you've made it past that step successfully, you will then need to compile. While you're still in the directory you ran ./configure in, type: make
That will start the compile, and may take a while depending on the program.

Generally, you will need to install the compiled files afterwards, and again, if it wants to install to common folders such as /bin you may need to run the command with sudo: make install

Once the program is installed...
You have to figure out what the command is! It's usually fairly self explanitory, lets say you downloaded a file called superpaint-i386-2.0.5.tar.gz you can pretty much count on the binary being 'superpaint'. It's just a matter of finding it. If you had to run the installer with sudo, then you can probably just type 'superpaint' anywhere in a shell and it will run. If you ran the install without sudo, it may have put the binaries in the source directory, or may have made a subdirectory with the install files in it. Look for a new subdirectory named 'bin' or 'superpaint'. The installer will generally create all the files with the proper permissions, so 'ls' will show the files names in green if they are executable.

Now, there are plenty of other variables that may come into play, but for most of your source installs, this should get you through it. If it doesn't then the site that you got the program from will usually have the details of their specific install. If you have any questions, I'll try to answer them as best I can, hopefully, I've at least come CLOSE to what you were looking for. ;) Oh, and if you have a link to the program you were using for an example, me, or somebody, may be able to take a look at it to get a better idea of what it is you're dealing with.

---

### Post by T3h_Dohtem on 2008-09-18
Haha, this post blew up fast, but:

`make` compiles the program
`make install` moves the compile files around on your harddrive to the proper locations.

basically, running one and then the other creates a binary, and puts it in the binaries directory, although it's a bit more complicated than that (for one, there are usually many more than 1 files)

---

### Post by semitone36 on 2008-09-18
> **Pro-reason said:**
> It's the other way round.  Synaptic uses the APT system.

Azureus and several excellent Bittorrent clients are available in the repositories.  

If a program you really need (not Azureus) is not in the repositories, then the next step is to find a repository that contains it.

In Synaptic, there are several extra repos that you can enable, if they are not already (e.g. proposed, backports, etc).

If that's still not enough, then find a third-party repo and it to yout repository list.  [Launchpad]("https://launchpad.net/ubuntu/+ppas") is a great place to look for these.

The next stage, if that doesn't work out, is to find a .deb file on the web somewhere and install that.

If even that fails, then look for an .rpm file, convert it to .deb (using Alien), and install that.

The absolute last resort is to download some random tarball and try to work out whether it requires compilation of some sort.



Heh, I didn't mean to imply that you were totally clueless, just that you are needlessly jumping into the deep end.

Huh that makes a lot more sense.  Your talking about System -> Administration -> Software Sources right?

Backports and proposed look a little iffy to me and from my understanding theyre only for updates, Im more looking for actual software progams (I guess Im still thinking like I was with Windows:roll: )

How do I go about the Third party repos though? That sounds like its more what im after.

---

### Post by semitone36 on 2008-09-18
Thanks for the explanation T3h_Dohtem.  As for the link here it is: [http://www.vuze.com/Download.html](http://www.vuze.com/Download.html)

Things are starting to make a lot more sense, I should have posted this thread weeks ago :lolflag:

---

### Post by nowshining on 2008-09-18
when u checkinstall - to create a deb do

sudo checkinstall -D make install

---

### Post by Pro-reason on 2008-09-19
Out of curiosity, I've been to that site, and downloaded Vuze.  I didn't know that Azureus had come out with stuff other than their core program.

Vuze comes as a bzip2ed tarball containing Java software.  There is a README.txt file that says:

```

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

```

I don't see how this is Chinese. You need only the most basic command-line knowledge to follow these instructions.

What it means is that you download the file to your home directory, then open a terminal and do these three commands:

```

tar -xvzf Vuze_linux.tar.bz2
cd vuze
./azureus

```

You have to have done the first two to even read the README.txt file, so the last one is a piece of cake!

However, I don't find that it is good software.  It has trouble finding my Java installation, etc.

---

### Post by semitone36 on 2008-09-22
Thanks for the help Pro Reason.  The Vuze README probably wasnt the best example for READMEs that have confused me, I should have used Mupen64plus -that one was ridiculous.

Just so that I know what Im doing from now on, say, if I wanted to download and install something from Google codes, how would I add any programs located at Google to my repos?

---

### Post by Pro-reason on 2008-09-22
> **semitone36 said:**
> 
Just so that I know what Im doing from now on, say, if I wanted to download and install something from Google codes, how would I add any programs located at Google to my repos?

I presume you're talking about a page for a project that provides only source code.  In that situation, I would Google for a site that provides a repo containing that software ([Launchpad]("https://launchpad.net/ubuntu/+ppas") is good for that) or at least a site that provides a [.deb]("http://en.wikipedia.org/wiki/Deb_(file_format)") file ([GetDeb]("http://GetDeb.net") sometimes has one, and there are [various]("http://rpm.pbone.net/") [sites]("http://rpmfind.net/") with [.rpm]("http://en.wikipedia.org/wiki/RPM_Package_Manager") files).

If that fails, then I would compile the source code and make a .deb package out of it for my repository, so that others don't have to compile it.

P.S.: If you want Mupen64plus, [do a GetDeb search for it]("http://www.getdeb.net/search.php?keywords=Mupen64plus"), or do a [Launchpad PPA search for it]("https://launchpad.net/ubuntu/+ppas?name_filter=mupen64plus"), and add one of the PPAs that come up, as a third-party repo.

---

### Post by semitone36 on 2008-09-23
Thanks so much for the feedback everyone! This helped me install a couple apps that Ive been trying to get for weeks. If I need any more help Ill post a new thread.

---

