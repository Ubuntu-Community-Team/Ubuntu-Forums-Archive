---
title: "install and run .tar.gz application"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-28
Hi,
I am having trouble with a program I downloaded as a tarball. I can extract the files OK but can't find a way of running the app. The program in question is the Metasploit app, Framework-3.1.tar.gz. I am unable so far to find among the files, an executable. 
I've attached a thumbnail of the extracted files. I run Hardy Heron 8.04
Thanks
philk949

---

### Post by perlluver on 2008-07-28
The main way to install is, ./configure, then type make, then run make install.  Check out the link, how to install anything.  It should offer more help.

---

### Post by steveneddy on 2008-07-28
How to install anything in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ramjet_1953 on 2008-07-28
Did you read the installation instructions on the SoftPedia website?

[http://linux.softpedia.com/get/System/Logging/ProM-Import-Framework-7822.shtml](http://linux.softpedia.com/get/System/Logging/ProM-Import-Framework-7822.shtml)

Regards,
Roger :cool:

---

### Post by BLTicklemonster on 2008-07-28
INSTALL TAR.GZ:

tar zxvf filename.gz
cd file
./configure
make
sudo make install

---

### Post by philk949 on 2008-07-28
To:
ramjet_1953
I am not trying to install that app. I am using the Metasploit Framework and as this is a forum for Absolute Beginners, it would have been too obscure antway(I _did_look at it), but thanks anyway.

To all other repondents:
I find the monkeyblog site and the 'install anything' guide unclear. I am not overly proficient with the terminal yet and the guide seems to be offering me advice on compiling from source code.
Did anyone look at the thumbnail I provided in my post? Is there any file in there I can use to execute the program or must I go to the command line?
If the latter, could someone please offer me some clear, detailed assistance and not a reference to something else?

To: BLTicklemonster
tried that, but get 'No such file or directory. Could you flesh out your advice a bit more please?
Phil

---

### Post by philetus on 2008-07-28
I found this, Hope it helps.

Here's a little step-through to get Metasploit running. Version 0.1

1. Download the framework 3 tarball from [http://www.metasploit.com/](http://www.metasploit.com/) into a folder

2. use tar -xvzf to open the tarball. Metasploit is written in Ruby, so it doesn't need installing per se, but you will need a load of Ruby stuff in order to run it.... So here goes.

3. Head over to [http://pierre.droids-corp.org/maemo/](http://pierre.droids-corp.org/maemo/) and download the .debs you'll find there into a new folder. (Actually you don't need to download the scapy .deb so you only need to download four)

4. Next, click on the gems folder on that page, which will take you to [http://pierre.droids-corp.org/maemo/gems/](http://pierre.droids-corp.org/maemo/gems/) , and download the 7 .gem files.

Pause here to thank Pierre for his sterling work - cheers, French geezer!

5. Alright. Enough silliness. Here's where the hard work starts. Go to the N800's application manager, and on the Application menu find the option to Install from file..., and install ruby_1.8.5-p3_armel.deb and rubygems_0.9.2_armel.deb from the folder into which you just downloaded them.

6. At this point some sages suggest you update rubygems. If you want to do this, open a terminal window and type gem update --system. (Note: there's a space between update and --system. You may need to be root to do this, I can't remember)

7. OK. Now it's time to install the gems, and it it's rather important that you do so in the right order. That's because some people have reported that you'll bugger the installation if you get it wrong. Personally I have done it twice in the following order and had no problems, so I recommend you do so too.

What you want to do is go back to your terminal session, and go to the directory into which you downloaded the gems onto your N800. If you don't do this your N800 will try to get them off the Internet and fail. Now you're going to type gem install followed by the name of the gem you want to install.

So, first of all, type:
gem install activesupport-1.4.1.gem

Then go and have a cup of tea and a bun, because it takes about 10 to 20 minutes to install the gem plus its accompanying ri and rdoc files.

When you get back your command prompt, type

gem install activerecord-1.15.2.gem

repeat this gem install procedure for the following gems in the following order:

actionpack-1.13.2.gem
actionmailer-1.3.2.gem
actionwebservice-1.2.2.gem
rake-0.7.1.gem
rails-1.2.2.gem

(thanks go to negen for publising this installation order)

If all goes well then welcome aboard - you're riding the rails!


8. A few more things to install: go to the App manager again and install from file the following debs you downloaded earlier:
sqlite3-ruby_1.2.1_armel.deb
and
nmap_4.20_armel.deb

9. Now you should be done, unless I have forgotten anything. Using your terminal, as root, head over to the folder where you put Metasploit - probably called something like framework3 inside a Metasploit3 directory, and run ./msfweb to run the web interface, or ./msfconsole for the console.

It all runs slooow on the N800, so be patient when waiting for thing to happen.

10. If you want to check out the auto_pwn feature you need to do this after having run ./msfconsole

>load db_sqlite3
>db_create pentest (or evilhacker or any other name you want to use in place of pentest)
>db_nmap 192.168.0.* (or whatever network you want to test. You do have permission don't you?)

>db_autopwn -t

The -t option will just test the autopwn feature. Change that to -e if you want to carry out any possible exploits and face the consequences if you bring down any machines....

That's about it. I am bound to have forgotten something but I'll correct and update as necessary. Thanks to all the various people who left enough info on the web and especially Internettablettalk for me to compile this.

---

### Post by philk949 on 2008-07-28
Thanks for this detailed response, philetus - I'm sure it will prove very helpful once I can get a run at it, but for now, I've fallen at the first hurdle. When I run tar -xvzf, I get this: 

tar: option requires an argument -- f
Try `tar --help' or `tar --usage' for more information.

 I know I'm a klutz, but this is what I was instructed to type, isn't it, or am I just too thick to live?

Phil

---

### Post by philk949 on 2008-07-28
N800? What the....

---

### Post by philk949 on 2008-07-28
Okay, as you were. Tarball opened, likewise synapses to brain. Have also downloaded all files from the supplied links (gems etc). But I must repeat - N800? 
What is that, please?

Phil

---

### Post by forger on 2008-07-28
He copy-pasted from a Nokia mobile phone (N800) blog :lolflag:
[http://mfresh-n800.blogspot.com/2007/07/installing-metasploit-framework-3-on.html](http://mfresh-n800.blogspot.com/2007/07/installing-metasploit-framework-3-on.html)

Here's a more ubuntu-related guide to install it:
[http://www.ubuntu-unleashed.com/2008/04/howto-install-metasploit-31-svn-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-metasploit-31-svn-in.html)
[http://metasploit.com/dev/trac/wiki/Metasploit3/InstallUbuntu](http://metasploit.com/dev/trac/wiki/Metasploit3/InstallUbuntu)
[http://linuxbasement.com/content/metasploit-ultimate-hacker-tool](http://linuxbasement.com/content/metasploit-ultimate-hacker-tool)
[http://www.howtoforge.com/installing-metasploit-3.0-on-ubuntu-7.10](http://www.howtoforge.com/installing-metasploit-3.0-on-ubuntu-7.10)

Support info:
[http://www.metasploit.com/framework/support/](http://www.metasploit.com/framework/support/)

If you can't manage to compile it, then I why not use a virtual machine, windows xp and the windows compiled installer?
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
[http://www.metasploit.com/framework/downloader/?id=framework-3.1.exe](http://www.metasploit.com/framework/downloader/?id=framework-3.1.exe)

---

### Post by philk949 on 2008-07-28
I've downloaded Virtualbox to my Hardy 8.04. Can anyone tell me how to open and run it please?

Phil

---

### Post by eightmillion on 2008-07-28
What kind of file is it? Did you download the .deb file? If so, just double click it and it should install.

---

### Post by philk949 on 2008-07-28
I wish it were that simple. Double-clicking on the downloaded Debian file reveals two .tar files, Control.tar and Data.tar plus a debian-binary file with nothing in it but the numeral 2

---

### Post by philk949 on 2008-07-28
Hi,
First, let me say thanks for the help with Metasploit. I've got it all downloaded but don't know how or if I can use a GUI to run it, or if I'll be able to get it back once I quit the terminal. I've included a screenshot of where I'm up to.
Phil

---

### Post by forger on 2008-07-28
"If you would like to use the experimental GUI, you will need to install the following packages:"
```
sudo apt-get install libgtk2-ruby libglade2-ruby
```

Then execute:
```
./msfgui
```

You have msfgui, msfconsole and msfweb :)

---

### Post by forger on 2008-07-28
May I ask why you need it? You seem to be really unrelevant to console and building applications

---

### Post by steveneddy on 2008-07-28
I realize this is a little late, but you are correct when you say that when you DL a .tar.gz file, you will probably be compiling from source.

Not every time, but most likely you will.

Just DL to the desktop, right click and select Extract.

Find the Read Me file if it is available and the instructions should be in there.

Just FYI

---

### Post by philk949 on 2008-07-28
Forger, 
please rest easy. I have no intention of trying to exploit any vulnerabilities anywhere, even if I had the expertise.
I'm studying for my Diploma in IT and we are currently undergoing an assessment in Security, which requires us to locate and demonstrate vulnerabilities, exploits and fixes.
For this I need to use a virtual machine, for safety's sake, and getting that installed and running is a whole other saga.
BTW, any advice on that? It's another stoush with tarballs, I bet.
Thanks again for all your help. Really appreciate it.

Phil

---

### Post by forger on 2008-07-29
I don't really care what you do with it, I was just curious on the purpose :)
Ok, about virtual machine, you could use virtualbox from innotek(sun), or virtual server from vmware, or kvm.

If you need networking, use vmware server:
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

If you don't need networking (I don't mean simple internet browsing), use virtualbox (its networking needs some reading to be set up properly) you can grab a deb package for your version of ubuntu from here: [http://tinyurl.com/virtualboxdownload](http://tinyurl.com/virtualboxdownload)
(or [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) -> Binaries)

I must warn you that the ubuntu repositories have a similar version called virtualbox-ose (open source edition), which does not have all the goodies. Use the binary version provided from the website, since it's easier and has "guest additions".

Virtual-machine-wise, guest o/s (operating system) is the one in your virtual machine, host o/s is the one that you currently have.

You just choose your platform (o/s) in that site, agree to the license and download it. Double click on the deb package, it will open the gdebi. If you don't have it install it:
```
sudo apt-get install gdebi
```
..then try to double click again, it should ask you to install the .deb package.

More info: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Sef on 2008-07-29
> please rest easy. I have no intention of trying to exploit any vulnerabilities anywhere, even if I had the expertise.
I'm studying for my Diploma in IT and we are currently undergoing an assessment in Security, which requires us to locate and demonstrate vulnerabilities, exploits and fixes.

Moved to Security Discussions.

---

### Post by philk949 on 2008-08-31
Could someone please give me a clear and detailed method for installing a .tar.gz file downloaded from the internet? I've launched this post in a new thread because my previous attempts to elicit coherent responses from contributors have failed.
Thank you

Phil

---

### Post by Bachstelze on 2008-08-31
A .tar.gz is just an archive, like a ZIP file. It can cotain anything so we can"t give general instructions about how to install stuff from one. However, they most often contain a README which will explain it very well.

---

### Post by alienexplorers on 2008-08-31
If you have archive manager running it will un tar your file and place it in a directory of your choosing.  From there if you need to compile you would do:
> ./configure
sudo make
sudo make install


---

### Post by Bachstelze on 2008-08-31
**Never** run [font="Courier New"]sudo make[/font]! [font="Courier New"]make[/font] alone will do.

---

### Post by InfinityCircuit on 2008-08-31
> **philk949 said:**
> Could someone please give me a clear and detailed method for installing a .tar.gz file downloaded from the internet? I've launched this post in a new thread because my previous attempts to elicit coherent responses from contributors have failed.
Thank you

Phil

If the normal ./configure && make && sudo make install does not succeed, then please post do the following and post the result of the last command:

```
tar zxf filename.tar.gz
cd filename/
ls -l .

```

---

### Post by philk949 on 2008-08-31
Thanks for your replies, but they only serve to highlight my point - neither of you agrees on how to do it.

Phil

---

### Post by mikewhatever on 2008-08-31
> **philk949 said:**
> Thanks for your replies, but they only serve to highlight my point - neither of you agrees on how to do it.

Phil

As noted above, we don't know what's in the archive, hence the disagreement.

---

### Post by philk949 on 2008-08-31
Okay, I'll be more specific:
Dissatisfied with the performance of Firefox 3 (which has been hanging and freezing), I decided to re-install Firefox 2.0.0.16. I downloaded the file and extracted it to my desktop, where it now sits with the simple filename, Firefox. How do I now install this program from here, please?

Phil

---

### Post by youngalfred on 2008-08-31
just try something?  if it fails it will tell you.  most probably you'll have wrong dependencies and it wont install.  if it does, then great!  everyones trying to contribute to help you.  the most common way to install is to ./configure && make && sudo make install.  But as hymntolife said, it could contain anything in the tar.gz.  why dont you point us to where you downloaded it so we have a batter idea what's in it?  Or search the wiki or google your problem, it is probably one of the most asked (and detailed) questions.

---

### Post by philk949 on 2008-08-31
> ./configure
sudo make
sudo make install 

I'm afraid that these instructions in the raw, without explanation or detail do not help very much. They are described as normal, but nothing of this kind is normal to an absolute beginner - configure (then what?)
                                            - make (make what?)

I'm not trying to be difficult and I'm not ungrateful, but as I said in my first post, could you please make your replies coherent?

---

### Post by alienexplorers on 2008-08-31
./configure sets up your files in preperation for building.
make is used to build the files (Compile Them)
sudo make install installs your files to the /usr directory.
You can then run your program once you know the start name of the program.

---

### Post by aysiu on 2008-08-31
The reason you don't get a consistent set of instructions for .tar.gz is that there *isn't* a consistent way to install a program that comes as .tar.gz.

A .tar.gz extension indicates that the file is a compressed archive of a large file or set of files. That's all it means.

If I see a .tar.gz, I don't know if it's a bunch of pictures, a program's source code, a program with a precompiled binary, a theme, or an icon set.

It's like seeing a .zip or .rar file.

You really should be installing from .tar.gz as only a last resort. The standard way to install software is through the repositories. This guide will show you how to do that. Don't skip down to the bottom part about .rpm and .tar.gz. Those are *last resorts*. Read the top bit first.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Irihapeti on 2008-08-31
I'm assuming you downloaded Firefox from the Mozilla site or similar. In that case, it's not a source code archive and the ./configure, make and make install commands won't work.

Instructions for installing Firefox manually are here:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Where the instructions mention firefox-3.0.tar.bz2, change it to firefox.2.0.0.16.tar.bz2 (or whichever version you have).

Irihapeti

---

### Post by aysiu on 2008-08-31
> **philk949 said:**
> Okay, I'll be more specific:
Dissatisfied with the performance of Firefox 3 (which has been hanging and freezing), I decided to re-install Firefox 2.0.0.16. I downloaded the file and extracted it to my desktop, where it now sits with the simple filename, Firefox. How do I now install this program from here, please?

Phil Delete the .tar.gz of Firefox 2.0.0.16 and then use Add/Remove or Synaptic Package Manager to remove the package called *firefox-3.0* and install the package called *firefox-2*. More details here:
[http://psychocats.net/ubuntu/firefox2hardy](http://psychocats.net/ubuntu/firefox2hardy)

---

