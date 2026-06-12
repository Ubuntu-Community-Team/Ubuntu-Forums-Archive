---
title: "installing Matlab on 14.04"
date: 2016-08-30
forum: New to Ubuntu
---

### Post by lauriehurman on 2016-08-30
Hi All
 

 I bought Matlab home R2016a so that I can do an online course on programming in Matlab but now I don't know how to install it. I have Ubuntu 14.04 LTS. I downloaded the software to “Home/Downloads” and then “extract here” and now have a folder called “matlab_R2016a_glnxa64” in “Home/Downloads”. It contains a file called “install” but it's just a text file and is full of stuff that might as well be Chinese.
 

 The Matlab site says type sudo ./install in a command line but I have search everywhere and can't find a way of getting a command line, I haven't done that before in 14.04 (I think I did it once in 10 but can't remember how). I don't understand how the computer will know what to install if I do manage to type that.
 

 I used to use Octave in Ubuntu 10 but I thought I should buy Matlab so that it was identical to the lessons and coursework of the course. I seem to have failed the first test, I hope someone on here will take pity and help me get this installed.
 Thanks very much for your time.
 

 Laurie

---

### Post by howefield on 2016-08-31
> **lauriehurman said:**
>  The Matlab site says type sudo ./install in a command line but I have search everywhere and can't find a way of getting a command line, 

Try the keyboard shortcut Ctrl + Alt  T to open a terminal.

Or open the dash and search for terminal..

---

### Post by lauriehurman on 2016-08-31
Thanks
In the end I Googled and found out how to open a command window and typed sudo ./install but got the reply ./install command not found.

The Matlab site implies that I can click on a file in the unzipped folder in downloads but I have searched all the folders and the "install" file is just a text file and I can't find anything else that responds when I click it.

I tried sudo apt-get matlab-support but that failed when it found no matlab installed (hope I haven't screwed something up).

Appreciate anybody pointing towards any information so I can find out how to do this. Matlab implies it's easy but I'm obviously missing something.

Thanks
Laurie
P.S. don't know what a dash is.

---

### Post by howefield on 2016-08-31
> **lauriehurman said:**
> ....typed sudo ./install but got the reply ./install command not found.

When you open a terminal you will generally be in your /home folder. Using the command pwd will tell you exactly where in the file system you are.

You would need to navigate to the folder containing the file you want to use. In this case it would appear that..

```
cd /Downloads/matlab_R2016a_glnxa64/
```

would put you in the correct folder to run the command.

---

### Post by lauriehurman on 2016-08-31
Howefield, thanks very much. I now know how to find out where I am and get to where I want to be. Progress :-)

I still don't seem to be able to make the install command do anything:-

./install: 1: eval: /home/lauriehurman/Downloads/matlab_R2016a_glnxa64/bin/glnx86/install_unix: not found

Thanks very much for your time.
Laurie

---

### Post by howefield on 2016-08-31
OK, I have absolutely no knowledge of what Matlab is or what it is for, but downloaded a file called matlab_R2016a_glnxa64.zip and this is how I installed it, well, actually stopped at the point it wanted to download a shed load of stuff, I have no reason to think that it wouldn't continue successfully to conclusion.

Download the file to the ~/Downloads folder. Note : ~/ being a shortened way of typing your home folder, eg for me /home/hugh/Downloads/ is the same as ~/Downloads/

Open a terminal and create a new folder called matlab..

```
mkdir matlab
```

which can be confirmed with the ls command..

```
hugh@xenial-laptop:~$ ls
Desktop  Documents  Downloads  matlab  Music  ownCloud  Pictures  Public  Templates  Videos
hugh@xenial-laptop:~$
```

Then unzip the contents of the downloaded zip file with

```
hugh@xenial-laptop:~$ unzip ~/Downloads/matlab_R2016a_glnxa64.zip -d ~/matlab/
```

There are a lot of files to extract, so a load of text will scroll down the terminal.

Then cd to the matlab folder.

```
hugh@xenial-laptop:~$ cd matlab/
```

Then start the install process..

```
hugh@xenial-laptop:~/matlab$ ./install 
Preparing installation files ...
Installing ...
```

An installation window will pop up at this point and take you through the installation process....

One point of note, the default installation folder is /usr/bin, I think you'll get better results installing to your home folder, I overwrote the default with /home/hugh/matlab/R2016a/

Hopefully you might be able to pick through the bones of this and get it started. :)

---

### Post by lauriehurman on 2016-08-31
It was all going so well until ...

lauriehurman@lauriehurman-Satellite-L300:~/matlab$ ./install
./install: 1: eval: /home/lauriehurman/matlab/bin/glnx86/install_unix: not found
lauriehurman@lauriehurman-Satellite-L300:~/matlab$

Sigh :-(

---

### Post by howefield on 2016-09-01
OK, just to rule something out.. can you provide the output from 

```
uname -m && uname -r
```

If it returns for a 32 bit Ubuntu, you probably are trying to install a 64 bit MatLab on a 32 bit machine.

---

### Post by lauriehurman on 2016-09-01
lauriehurman@lauriehurman-Satellite-L300:~$ uname -m && uname -r
i686
3.13.0-66-generic
lauriehurman@lauriehurman-Satellite-L300:~$

---

### Post by howefield on 2016-09-01
Oh well, that seems to be the problem.

You are trying to install a 64 bit application into a 32 bit operating system, which won't work. You can usually install a 32 bit application into a 64 bit operating system, but not the other way round.

Is you machine capable of running 64 Ubuntu ? I fear that is what you will need to do.

---

### Post by lauriehurman on 2016-09-01
Hugh
Thanks so much for taking the trouble to sort this out for me.
I'll see if a previous 32 bit version of Matlab is available.

I'm guessing that Ubuntu 16 is 64 bit. Is that right?

How do I find out if my Toshiba satellite L300 can run a 64 bit OS?

Laurie

---

### Post by #&amp;thj^% on 2016-09-01
A quick way
```
inxi -C
```
Mine shows this
```
inxi -C
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2600 MHz 1: 1400 MHz 2: 800 MHz 3: 1400 MHz
           4: 800 MHz


```
Mine is 64 bit ready
Or
```
lscpu
```
And find the line that reads"Architecture: "
It will tell you something like
```
Architecture:          x86_64
```
Again a 64 bit CPU
Hope this is Clear.
But one word of Advice here...Unless you have upgraded your RAM (To at least 4 Gigs of RAM) you might want to stick to a 32bit OS...Most of the Toshiba Satellite Pro L300 only came with 2Gigs of Ram.
It will run but might be Sluggish and Choppy.

---

### Post by howefield on 2016-09-02
> **lauriehurman said:**
> I'll see if a previous 32 bit version of Matlab is available.

I don't believe it is, looking at the requirements for Matlab it appears to only support 64 bit.

> I'm guessing that Ubuntu 16 is 64 bit. Is that right?

Yes, for now Ubuntu is available in both 32 and 64 bit versions.

> How do I find out if my Toshiba satellite L300 can run a 64 bit OS?

All the stuff posted in 1fallen is good, I'd use..

```
cat /proc/cpuinfo  | grep 'name' && lscpu | grep "CPU op-mode(s)"
```

Having looked at the Toshiba satellite L300 specifications, it appears that you have a "*Intel® Pentium® Dual-Core Processor T2370*" which is 64 bit capable and the RAM is listed at 2 gigabytes which is about the limit below which I'd not install a 64 bit system. So all being well you should be able to install 64 bit Ubuntu.

---

### Post by lauriehurman on 2016-09-05
Thank so much guys. I was thinking that my old laptop would not run 64bit but that doesn't seem to be the case Hoorah :-) ( it took ages to find out how to type | . Yet another thing I've learned this week. )
Looks like I need to google "how to upgrade my RAM". I'll bet there's a Youtube video for that.
Thanks very much for all your help.
Laurie

```
lauriehurman@lauriehurman-Satellite-L300:~$ inxi -c 
The program 'inxi' is currently not installed. You can install it by typing: 
sudo apt-get install inxi 
lauriehurman@lauriehurman-Satellite-L300:~$ lscpu 
Architecture:          i686 
CPU op-mode(s):        32-bit, 64-bit 
Byte Order:            Little Endian 
CPU(s):                2 
On-line CPU(s) list:   0,1 
Thread(s) per core:    1 
Core(s) per socket:    2 
Socket(s):             1 
Vendor ID:             GenuineIntel 
CPU family:            6 
Model:                 15 
Stepping:              13 
CPU MHz:               1662.427 
BogoMIPS:              3324.85 
L1d cache:             32K 
L1i cache:             32K 
L2 cache:              1024K 
lauriehurman@lauriehurman-Satellite-L300:~$ cat /proc/cpuinfo  | grep 'name' && lscpu | grep "CPU op-mode(s)" 
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz 
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz 
CPU op-mode(s):        32-bit, 64-bit 
lauriehurman@lauriehurman-Satellite-L300:~$
```

---

### Post by mörgæs on 2016-09-05
I wouldn't begin buying extra memory or other hardware yet. Better to see how it all works in a 64 bit install of 16.04.1.

If you want something lighter (that is, faster) than Ubuntu then X/Lubuntu are good options.

---

### Post by howefield on 2016-09-05
> **lauriehurman said:**
> Thank so much guys. I was thinking that my old laptop would not run 64bit but that doesn't seem to be the case Hoorah :-) ( it took ages to find out how to type | . Yet another thing I've learned this week. )

You are welcome, the pipe symbol "|" is used here to take the output from one command and use it as the input for the next one, with the goal of the eventual output being easier to understand. Sorry the solution isn't a tad more simplistic than reinstalling the operating system, but there it is.

> Looks like I need to google "how to upgrade my RAM". I'll bet there's a Youtube video for that.

If you have 2 gigabyte of RAM (or more) I'd try it out first, older memory can be expensive and hard to find. I'm not sure how resource intensive Matlab is but you may well find that you are ok with what you have.

```
lauriehurman@lauriehurman-Satellite-L300:~$ inxi -c 
The program 'inxi' is currently not installed. You can install it by typing: 
sudo apt-get install inxi 
lauriehurman@lauriehurman-Satellite-L300:~$ lscpu 
Architecture:          i686 
CPU op-mode(s):        32-bit, 64-bit 
Byte Order:            Little Endian 
CPU(s):                2 
On-line CPU(s) list:   0,1 
Thread(s) per core:    1 
Core(s) per socket:    2 
Socket(s):             1 
Vendor ID:             GenuineIntel 
CPU family:            6 
Model:                 15 
Stepping:              13 
CPU MHz:               1662.427 
BogoMIPS:              3324.85 
L1d cache:             32K 
L1i cache:             32K 
L2 cache:              1024K 
lauriehurman@lauriehurman-Satellite-L300:~$ cat /proc/cpuinfo  | grep 'name' && lscpu | grep "CPU op-mode(s)" 
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz 
model name    : Genuine Intel(R) CPU           T1600  @ 1.66GHz 
CPU op-mode(s):        32-bit, 64-bit 
lauriehurman@lauriehurman-Satellite-L300:~$
```

The CPU op-mode is the line that you are looking for, the output basically means that you can install both 32 and 64 bit operating systems. The Architecture line in the inxi ouput refers to the installed software, not what can be installed.

---

