---
title: "Parallel Port Control in Perl: ERRORS"
date: 2009-08-21
forum: Programming Talk
---

### Post by UnterDenLinden on 2009-08-21
[FONT=Arial,Helvetica, sans-serif][COLOR=black][FONT=Arial,Helvetica, sans-serif][COLOR=black]I'm trying to output to a parallel port on Ubuntu. I'm using the parport (Device::ParallelPort::drv::parport) driver because the Linux (Device::ParallelPort::drv::linux) driver has an error in it. It works fine until I ever stop a program while it is running, it won't let me create the parport driver again with this error: 
Device::ParallelPort unabel to create driver parport (see Device::ParallelPort::drv::auto for further information) - Failed to load partport driver for /dev/parport0 at (eval 1) line 3 at motortest.pl line 6 
 
A reboot won't fix it, but it will start working again a few days later. I have no idea. 
 
Here is the code I had written:

[/COLOR][/FONT][/COLOR][/FONT]```
#!/usr/bin/perl 
 
use Device::ParallelPort; 
 
 
my $parport = Device::ParallelPort->new('parport'); 
 
for ($c = 10; $ct >= 1; $c--) { 
$parport->set_bit(0,  0); 
select(undef,undef,undef, .1); 
$parport->set_bit(0,  1); 
$parport->set_bit(1,  0); 
select(undef,undef,undef, .1); 
$parport->set_bit(1,  1); 
$parport->set_bit(2,  0); 
select(undef,undef,undef, .1); 
$parport->set_bit(2,  1); 
$parport->set_bit(3,  0); 
select(undef,undef,undef, .1); 
$parport->set_bit(3,  1); 
}
```Thanks! Sorry I'm new at this.

---

### Post by DancingHippo on 2009-08-28
I got control (reading) of the parallel port in perl working on one computer and then recently had to do it again and made notes so I wouldn't forget. I'm thinking the last part (allowing user access) may help you and the rest may help others trying to get it to work. I'm new to Linux so my descriptions of why it works may not be right.

**Libraries Needed for perl parport module to work**:

Libraries libc6-dev and libstdc++6-4.3-dev  are needed to get the C and C++ headers and developer tools needed by CPAN to make a good install. (NOTE: Version numbers may be different these worked on Ubuntu 9.04)

```
sudo apt-get install build-essential
```This should install the libraries you need.

**Get CPAN modules**:

1) Get CPAN started and type in the following commands at the prompt and let it install the modules: 

```
install Device::ParallelPort

install Device::ParallelPort::drv::parport

get Device::ParallelPort::drv::linux
```NOTE: Don't install the Linux module as you need to modify the code. If you did do an install you will need to delete out all the directories that begin with "Device-ParallelPort-drv-linux-1.00-" and end with a random sequence see step below to find them.

2) Exit CPAN (q) and using the desktop gui navigate from your home directory (use ctrl-h to show hidden files) to ".cpan/build".

3) Open the directory that begins with "Device-ParallelPort-drv-linux-1.00-" and ends with a random sequence. (I'm sure someone can tell us the terminal entries to do this but this is how I got there).

4) Open the file "linux.xs" in a text editor and change the line that says

```
#include <asm/io.h>
```to 

```
#include <sys/io.h>
```I believe asm is defunct now on Ubuntu and replaced by sys but others would know better.

5) Go back into CPAN and 

```
install Device::ParallelPort::drv::linux
```which should use the modified file and now make a proper install. **Remember** that you can only use the Device:: ParallelPort::drv::linux module as root.

**Getting permission to use the parallel port**:

The final step before my Perl program would run without errors is getting permission to use parport0. If you want to temporarily assign permission and test your Perl program. Then you can use

```
sudo chmod 666 /dev/parport*
```If you want this to survive a reboot you could put it into a chron job and run it at each boot but there is another (maybe more proper) way of doing it using a udev rule file.
 
NOTE: Ubuntu 9.04 uses a udev rule file to set permissions now rather than the older /dev directory which was used to store file-like device nodes.

1) Open a terminal and type

```
sudo gedit /etc/udev/rules.d/10-local.rules
```2) Enter the following lines into the file:

```
# Change ownership of the parport device so it can be used in perl scripts
KERNEL=="parport[0-9]*", GROUP=="lp", MODE=="0666", OPTIONS+="last_rule
```3) Save and exit gedit then type 

```
sudo udevadm control --reload-rules
```[B]How I Load the Module in Perl:

[/B]```
# Load the Parallel Port Module.
use Device::ParallelPort;
my $parport = Device::ParallelPort->new('parport');
# Set the C5 bit high so that we can read the D0-7 lines.
$parport->set_bit(21,  1); 
```Hope this helps you or somebody else :)

---

### Post by DancingHippo on 2009-08-29
Okay I re-read your post and just realized you did get it working at one point so my first post proable isn't going to help you but maybe somebody else can use it. Could it be that you are trying to stop your perl program using ctrl-z instead of ctrl-c ? Ctrl+z actually pauses/suspends your job without terminating it which might explain why you can't regain access to parport0.

---

### Post by UnterDenLinden on 2009-08-30
Thanks for all the help! I think the control-z thing was my problem... I guess I am pretty new at this. But it's all working now, thankfully. Just in case, if I ever lose control of parport0 again, is there an easy way to regain it?
Thanks again!

---

### Post by DancingHippo on 2009-08-31
You can use the **jobs** command to see what jobs you are running and then the **fg *+ ***jobnumber command to being it to the foreground thus gaining control over it. Checkout [http://linuxreviews.org/beginner/jobs/](http://linuxreviews.org/beginner/jobs/) for a complete explanation on how to use job commands.

You can also use the  **ps** and **kill** commands to show the process status and it's associated PID (Process Identifier) and the **kill + **PID number to stop the process. For more help with these you can use the **man** command (ie. man ps) to display the manual pages.

---

### Post by UnterDenLinden on 2009-09-13
Ok, sounds good. Thanks for all the help!

---

