---
title: "Debugging script files"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by NormR2 on 2008-04-30
Hi,
I just spent a couple of hours trying to figure out why some Nautilus scripits weren't working. I had downloaded the scripts on a Windows system, looked at them and then copied them to the unbuntu system via a Floppy.
The first problem was that Nautilus didn't give any error message when I tried to use the script. So I opened a terminal and cd to the directory with the scripts. When I tried to run them, I got what appeared to be a syntax error. I manually entered a simple script and was able to get it to work from the commandline. I went back to the windows system and looked at the scripts that worked and those that didn't and saw that the bad ones had the Return character (hex 0D) at the end of each line (windows uses 0D0A to end a line).
When I removed the hex 0D from the script that failed, it then worked.

Question: Is there a hex editor that comes with the Ubuntu 7.10 distro?
Otherwise, how do I check for and remove the 0D characters?

2nd Question: When running a script in Nautilus, how do I find the error if there is no action/response when I click Open or chose a script on the right click/context menu?  Is there an error log that would have the text of an error message?  Right now it just seems to ignore my requests!!!

Thanks,
Norm

---

### Post by sdennie on 2008-04-30
1) It sounds like you want to use dos2unix (typing dos2unix from the commandline will tell you how to install it).  It should strip the ^M characters out of the doc.

2) You could try starting nautilus from the command line.  I would imagine that scripting errors would be printed to stdout but, I don't have any scripts to test this with.

---

### Post by NormR2 on 2008-04-30
When I entered dos2unix at the commandline I got instructions on how to install something like: sudo apt-get install tofrodos
When I typed that in, I get a message saying: 
Couldn't find package tofrodos

I tried starting nautilus from a Terminal commandline and then using the scripts. Nothing was shown on the terminal, the prompt continued to blink at its normal place.

Is there an editor that I can see the contents of files in hex?

Thanks,

Norm

---

### Post by wawadave on 2008-04-30
sudo apt-get install tofrodos worked for me in synaptic have you got all the update places added?

sudo apt-get install tofrodos
bash: dos2unix: command not found
bg@bg-desktop:~$ sudo apt-get install tofrodos
[sudo] password for billgates: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tofrodos
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.6kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main tofrodos 1.7.6-2 [16.6kB]
Fetched 16.6kB in 3s (4520B/s)  
Selecting previously deselected package tofrodos.
(Reading database ... 224912 files and directories currently installed.)
Unpacking tofrodos (from .../tofrodos_1.7.6-2_i386.deb) ...
Setting up tofrodos (1.7.6-2) ...

---

### Post by sdennie on 2008-04-30
I'm not sure why you can't install dos2unix but, an alternate way to remove the dos linefeeds is to do the following:

```

sed -e "s/\r//g" input_file > output_file

```

---

### Post by NormR2 on 2008-04-30
My Linux computer is NOT connected to the internet. 
So how can I find and download the needed file(s), copy them to my 
Linux system and have apt-get do an install from a local file?

Thanks for the sed edit command syntax.

Norm

---

