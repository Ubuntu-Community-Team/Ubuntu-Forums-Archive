---
title: "Installing Java Download Manager, JRE, Java?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by mjmark223 on 2008-10-22
How do you guys know all of these codes and directory locations and when to use them?

My current example is trying to install the Java JRE. I read that Java is an easy programming language and I am interested in learning how to program. 

I download it and when I want to open it a box pops up saying I don't have the helper application. I went to Java's site and read the instructions but I don't understand them. It says...

1. Download and check the download file size to ensure that you have downloaded the full, uncorrupted software bundle.
***You can download to any directory you choose***; it does not have to be the directory where you want to install the Java SE Runtime Environment.
Before you download the file, notice its byte size provided on the download page on the web site. Once the download has completed, compare that file size to the size of the downloaded file to make sure they are equal.

2. [COLOR="red"]***Make sure that execute permissions are set on the self-extracting binary.***Huh?[/COLOR]
Run this command:
[[COLOR="red"]I]**chmod +x 6<version>-linux-i586.bin**[/I][/COLOR]
3. Change directory to the location where you would like the files to be installed.

The next step installs the Java SE Runtime Environment into the current directory.
4. [COLOR="Red"]***Run the self-extracting binary***[/COLOR].

[COLOR="red"]Execute the downloaded file, prepended by the path to it. For example, if the file is in the current directory, prepend it with [I][B]"./" (necessary if "." is not in the PATH environment variable):
./jre-6<version>-linux-i586.bin[/B][/I][/COLOR]

The binary code license is displayed, and you are prompted to agree to its terms.

The Java SE Runtime Environment files are installed in a directory called [COLOR="Red"]***jre1.6.0_<version>[/COLOR] in the current directory***.


I am loving Ubuntu and I don't want to go back to Windows. I want to learn about codes and programming but I am very confused/aggravated.:confused::mad:


I my question is too involved I apologize. Just some guidance or some search terms to help me understand the basics would be greatly appreciated.

Thanks

Mark

---

### Post by fooman on 2008-10-22
did you try installing java jre from synaptic (system > administration > synaptic package manager) or in a terminal?

in synaptic,  search for "sun-java6-jre",  right click on it and choose mark for installation,  then click "apply".  it will install a couple of other packages as dependencies,  thats ok.

or do it in a terminal (applications > accessories > terminal),  type or copy/paste the following:

```
sudo apt-get install sun-java6-jre
```

---

### Post by mjmark223 on 2008-10-22
Thanks for the help

I'm at work right now so I can't try anything.

One other thing. 

If I hit CTRL+C to copy something from a website
how come CTRL+V won't paste it in the terminal. But if I right click and choose paste it will.

---

### Post by fooman on 2008-10-22
try ctrl-shift-v

see if that works.

---

### Post by Nepherte on 2008-10-22
> **mjmark223 said:**
> Thanks for the help

I'm at work right now so I can't try anything.

One other thing. 

If I hit CTRL+C to copy something from a website
how come CTRL+V won't paste it in the terminal. But if I right click and choose paste it will.
Shift + Insert will work.

---

### Post by Teamgeist on 2008-10-22
Install the Package ubuntu-restricted-extras via the Package Manager or with ```
sudo apt-get install ubuntu-restricted-extras
```

This will pull a lot of codecs and other multimedia-stuff for you automagically.

Also have a look at [www.medibuntu.org](www.medibuntu.org) afterwards.

---

