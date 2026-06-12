---
title: "ubuntu - how install skype via GUI?"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by slmehl on 2012-12-25
Hello --

I attempted to install Skype using Terminal, but it failed on 32-bit; it also failed on 64-bit.

Chrome installed fine using the Ubuntu Software Center.  I think that is the limit of my skills now.

Can I install Skype using GUI like the Ubuntu Software Center?

Thanks in advance for any help.

Larry Mehl

---

### Post by papibe on 2012-12-26
Hi slmehl. Welcome to the forums ):P

Sure you can. Take a look at this instructions: [Install Skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype").

Let us know how it goes.

Merry Christmas.

---

### Post by slmehl on 2012-12-26
> **papibe said:**
> Hi slmehl. Welcome to the forums ):P

Sure you can. Take a look at this instructions: [Install Skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype").

Let us know how it goes.

Merry Christmas.
papibe --

That was a fast Christmas present.  Thank you,

I will give it a go soon.

Larry

---

### Post by slmehl on 2012-12-26
pabibe --

I have Ubuntu version 12.107.  I found the Other Software tab (although the interface did not look as it did in the screen shots) and I think I designated Canonical Partners as a source.

But, I did not see the family of 4 checkboxes below it.

I guess that is the problem ... searching for Skype resulted in 5 German links, none of which include the word Skype.

So, I tried the 4 terminal steps in
[http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/](http://www.tecmint.com/install-skype-4-1-in-ubuntu-xubuntu-linux-mint/)

$ sudo apt-get install libxss1 
$ cd /tmp 
$ wget [http://www.skype.com/go/getskype-linux-ubuntu-32/skype-ubuntu-precise_4.1.0.20-1_i386.deb](http://www.skype.com/go/getskype-linux-ubuntu-32/skype-ubuntu-precise_4.1.0.20-1_i386.deb)
$ sudo dpkg -i skype-ubuntu*.deb

This process failed on the last one, saying
dpkg: error processing skype-ubuntu-precise_4.1.0.20-1_amd64.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 skype-ubuntu-precise_4.1.0.20-1_amd64.deb

Can you or someone else help me through this, 
OR
point me to a GUI method that describes what I will see in 12.107?

Thanks for any further help.

Larry Mehl

---

### Post by fantab on 2012-12-26
If you don't have already install 'Synaptic Package Manager' (Its a more detailed than Software Center). 

Check your software sources at /etc/apt/sources.list. You MUST have the 'Universe' and 'Multiverse' sources enabled... you can use Synaptic to do this. AFAIK 'Skype' is not available for linux in 64bit, so it runs on 64bit  using 32bit libraries/dependencies. Having Universe, Multiverse and  Backport repos/sources this is make easier. 

remember, after you make any changes to sources and BEFORE you install anything you have to run:
```
$ sudo apt-get update
```in the Terminal.

And carefully look at the output of the above command and see if you get any errors. If not, you are good to proceed to install any package.

---

### Post by slmehl on 2012-12-27
fantab --

Thanks.  I installed Synaptic.
I like the look of it mubh better.
I am ready to 
"Check your software sources at /etc/apt/sources.list"
but I don't know how to do that.
I have very little experience at the command line, but much experience in DOS.
I found it is not a "cd" or "dir" in Ubuntu.
Can you tell me how to "Check ..."?

I am taking a dual-boot laptop on a long trip and will need Skype.  Windows audio drivers are broken.  Ubuntu's work fine.  So, I want to install Skype on Ubuntu.

I appreciate the help.

Larry

---

### Post by JHawk56 on 2012-12-27
> **slmehl said:**
> 
I am ready to 
"Check your software sources at /etc/apt/sources.list"
but I don't know how to do that.Click the "Origin" button in Synaptic and scroll through the list of sources.

If you want to install Skype from Software Center rather than Synaptic (it should now appear in Software Center's Search), close Synaptic first.

---

### Post by fantab on 2012-12-27
> **slmehl said:**
> I am ready to 
"Check your software sources at /etc/apt/sources.list"
but I don't know how to do that.
I have very little experience at the command line, but much experience in DOS.
I found it is not a "cd" or "dir" in Ubuntu.

With Synaptic it is as easy as:

Open Synaptic- Settings - Repositories (aka Software Sources)- Other Software

You have to 'check' **Canonical Partners** and also **Independent** (no need to activate the 'Source Code' repos). 'Closed Source' software is not directly provided by Ubuntu. Applications like Skype and Adode Reader are not provided by Ubuntu- main. We can only install such software through these repos.

After you have enabled the said repos, from Synaptic **RELOAD** the repos. After this **Search** for Skype in the Synaptic and it will show. Right click on it and 'Mark for installation' then hit 'Apply' to install the selected/Marked software.

You can also achieve the above goal through the Terminal:

```
$ sudo gedit /etc/apt/sources.list
```Gedit will open the file sources.list (which lists all your software sources). Check the file for these lines:

```
deb http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe
deb http://archive.ubuntu.com/ubuntu quantal multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
deb http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse
```If any of the above lines is preceded by **#** then **remove #** to activate that repo. And SAVE the file.

Then :

```
$ sudo apt-get update
$ sudo apt-get install skype

```Always pay attention to the output of apt-get update if there are any errors in sources.list it will show.

If you come across any 'Broken Packages' then use Synaptic to fix them:

Synaptic- Edit- Fix Broken Packages.

Good Luck..

---

