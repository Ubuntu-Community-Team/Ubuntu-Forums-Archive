---
title: "Tinyos Tossim Not Working"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by brucemonty on 2008-07-21
I'm doing research with my school and it involves using TinyOS on mica2 motes. Ive never used linux before and Im not sure exactly whats happening.  I was able to install TOS on my laptop but Im not sure that Ive done it correctly.

whenever I try

make micaz sim

I get this long list of output and at the end it says

...
In component `CounterToLocalTimeC':
/opt/tinyos-2.0.2/tos/lib/timer/CounterToLocalTimeC.nc:38: syntax error before `uint32_t'
/opt/tinyos-2.0.2/tos/lib/timer/CounterToLocalTimeC.nc:42: syntax error before `LocalTime'
In component `HilTimerMilliC':
/opt/tinyos-2.0.2/tos/platforms/mica/sim/HilTimerMilliC.nc:47: no match
/opt/tinyos-2.0.2/tos/platforms/mica/sim/HilTimerMilliC.nc:48: cannot find `TimerFrom'
/opt/tinyos-2.0.2/tos/platforms/mica/sim/HilTimerMilliC.nc:49: cannot find `Alarm'
/opt/tinyos-2.0.2/tos/platforms/mica/sim/HilTimerMilliC.nc:51: no match
/opt/tinyos-2.0.2/tos/platforms/mica/sim/HilTimerMilliC.nc:52: cannot find `Counter'
In component `TimerMilliP':
/opt/tinyos-2.0.2/tos/system/TimerMilliP.nc:42: cannot find `SoftwareInit'
In component `TimerMilliC':
/opt/tinyos-2.0.2/tos/system/TimerMilliC.nc:44: too many arguments
In component `BlinkAppC':
BlinkAppC.nc:51: cannot find `Boot'
make: *** [sim-exe] Error 1
root@bacmnix:/opt/tinyos-2.0.2/apps/Blink#


Is there anyone that can help me?

---

### Post by farahijahromi on 2008-09-04
I am not sure if its too late for you to answer or not but today I was trying to figure out the problem and finally I could!
As a new Linux user, I have installed hardy Unubtu. I was able to compile successfully using  mica2, micaz, or telosb but not micaz sim. The same bunch of error messages was printing in my screen. After hours and hours searching in the different websites I could solve the problem (thanks to forums!).
This may solve yours as well:
1- Install tinyos 2.1.0 as this link guides you:
Many thanks to [Gireesh]("http://mythicalcomputer.blogspot.com/2008/08/installation-of-tinyos-in-ubuntu.html"), 
check carefully so that everything is according to his guides.
Just the html codes made the instructions a little tricky!
while setting the .bashrc each line starts with an "export" and no space after each line!!!
2- Then you have to install the standard c development library 
(many thanks to [Phil]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2007-August/027530.html") )
the command is:                                               
sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential  
(Thanks to this [tutorial]("www.cs.wustl.edu/~lu/cs520s/slides/tinyos_tutorial.pdf")!) 

3- Third and the last one!!! You have to install the Python development 
headers which is python2.5-dev (or any other version) from

System -> Administration -> Synaptic Package Manager

(Thanks to [Greg Hackmann]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2008-March/031763.html"))

That's it! Now you should be able to compile Blink or any other app with the Tossim!

By the way! I already noticed that after compiling the Blink with Tossim, it would write "*** Successfully built micaz TOSSIM library"; however, too many warnings come to the existence. I used a Xubuntu live CD and compare these two together. while searching the web, I noticed that the gcc version 4.2 + is more strict about the conversions between char and string compared to gcc 4.1 . I don't know if its an important issue for the real programs but I found out that in the error lines of the mentioned files (/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c and /opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx) if a " (char*) " be added after the * = * it would solve the problem. 
It may sound a ridicules or even a dangerous method to solve the problem like that! But as far as I experienced it removed the warnings. Just in case I did backup my original files.

Regards,
Mohsen

---

### Post by sahyagiri on 2008-09-17
Thanks for the appreciations put for my blog
I am working on simple programs to help tinyos beginners mostly tinyos 2.10.
Please keep visiting and please add your suggestions in my blog/here

---

### Post by ki_ha1984 on 2009-02-09
hello i dry to install the tinyos like the above guide and when i try to install from the synaptic package manager 

it give me this error any help please .



 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to tinyos.stanford.edu:80 (171.67.76.65). - connect (111 Connection refused)

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/or/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/or/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/for/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/for/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/a/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/a/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/different/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/different/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/distribution/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/distribution/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/of/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/of/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/Ubuntu/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/Ubuntu/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/(deb/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/(deb/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/http://tinyos.stanford.edu/tinyos/dists/ubuntu/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/http://tinyos.stanford.edu/tinyos/dists/ubuntu/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/*/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/*/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/ma/binary-i386/Packages.gz](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/hardy/ma/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.




thanks

---

### Post by replikanxxl on 2009-12-13
> **farahijahromi said:**
> I am not sure if its too late for you to answer or not but today I was trying to figure out the problem and finally I could!
As a new Linux user, I have installed hardy Unubtu. I was able to compile successfully using  mica2, micaz, or telosb but not micaz sim. The same bunch of error messages was printing in my screen. After hours and hours searching in the different websites I could solve the problem (thanks to forums!).
This may solve yours as well:
1- Install tinyos 2.1.0 as this link guides you:
Many thanks to [Gireesh]("http://mythicalcomputer.blogspot.com/2008/08/installation-of-tinyos-in-ubuntu.html"), 
check carefully so that everything is according to his guides.
Just the html codes made the instructions a little tricky!
while setting the .bashrc each line starts with an "export" and no space after each line!!!
2- Then you have to install the standard c development library 
(many thanks to [Phil]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2007-August/027530.html") )
the command is:                                               
sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential  
(Thanks to this [tutorial]("www.cs.wustl.edu/~lu/cs520s/slides/tinyos_tutorial.pdf")!) 

3- Third and the last one!!! You have to install the Python development 
headers which is python2.5-dev (or any other version) from

System -> Administration -> Synaptic Package Manager

(Thanks to [Greg Hackmann]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2008-March/031763.html"))

That's it! Now you should be able to compile Blink or any other app with the Tossim!

By the way! I already noticed that after compiling the Blink with Tossim, it would write "*** Successfully built micaz TOSSIM library"; however, too many warnings come to the existence. I used a Xubuntu live CD and compare these two together. while searching the web, I noticed that the gcc version 4.2 + is more strict about the conversions between char and string compared to gcc 4.1 . I don't know if its an important issue for the real programs but I found out that in the error lines of the mentioned files (/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c and /opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx) if a " (char*) " be added after the * = * it would solve the problem. 
It may sound a ridicules or even a dangerous method to solve the problem like that! But as far as I experienced it removed the warnings. Just in case I did backup my original files.

Regards,
Mohsen

Thanks a lot for this clear explanation . nice day

---

### Post by 7ayala on 2010-03-25
> **farahijahromi said:**
> I am not sure if its too late for you to answer or not but today I was trying to figure out the problem and finally I could!
As a new Linux user, I have installed hardy Unubtu. I was able to compile successfully using  mica2, micaz, or telosb but not micaz sim. The same bunch of error messages was printing in my screen. After hours and hours searching in the different websites I could solve the problem (thanks to forums!).
This may solve yours as well:
1- Install tinyos 2.1.0 as this link guides you:
Many thanks to [Gireesh]("http://mythicalcomputer.blogspot.com/2008/08/installation-of-tinyos-in-ubuntu.html"), 
check carefully so that everything is according to his guides.
Just the html codes made the instructions a little tricky!
while setting the .bashrc each line starts with an "export" and no space after each line!!!
2- Then you have to install the standard c development library 
(many thanks to [Phil]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2007-August/027530.html") )
the command is:                                               
sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential  
(Thanks to this [tutorial]("www.cs.wustl.edu/~lu/cs520s/slides/tinyos_tutorial.pdf")!) 

3- Third and the last one!!! You have to install the Python development 
headers which is python2.5-dev (or any other version) from

System -> Administration -> Synaptic Package Manager

(Thanks to [Greg Hackmann]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2008-March/031763.html"))

That's it! Now you should be able to compile Blink or any other app with the Tossim!

By the way! I already noticed that after compiling the Blink with Tossim, it would write "*** Successfully built micaz TOSSIM library"; however, too many warnings come to the existence. I used a Xubuntu live CD and compare these two together. while searching the web, I noticed that the gcc version 4.2 + is more strict about the conversions between char and string compared to gcc 4.1 . I don't know if its an important issue for the real programs but I found out that in the error lines of the mentioned files (/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c and /opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx) if a " (char*) " be added after the * = * it would solve the problem. 
It may sound a ridicules or even a dangerous method to solve the problem like that! But as far as I experienced it removed the warnings. Just in case I did backup my original files.

Regards,
Mohsen
Hello.. I am a new Ubuntu user and I am working on Tiny-OS 2 and I faced the same errors: make micaz sim errors.. I did all what you said and it didn't work. No problem with the paths all are correct.. What shall I do?? If you can help me its urgent..Thanks in advance

---

### Post by 7ayala on 2010-05-12
Hi all.. I am trying to compile a TinyOS 2 application on UBUNTU to use it either in Simulation or in Experiments and in the two (make micaz sim  and make tmote) I had these errors:
...
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:99: no match
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:100: cannot find `SubSend'
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:101: cannot find `Send'
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:102: cannot find `Send'
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:103: cannot find `SubSend'
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:106: no match
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:107: cannot find `Receive'
/opt/tinyos-2.1.0/tos/chips/cc2420/CC2420ActiveMessageC.nc:108: cannot find `Receive'
...
make: *** [sim-exe] Error 1
 
I tried all whta you talked about and by the way TOSSIM works properly for other applications..Is it a problem of makefile or what ? So if some hints guys.. Thanks in advance :)

---

### Post by bharani16 on 2010-05-16
i installed Tinyos ..Tossim yesterday...it didnt work fine..It had some installation problems...

But when i rebooted i got this unique problem..

It booted well but when i entered terminal following happened on own

[FONT=Century Gothic]$command not found
connecting to Tinyos[/FONT]

Then all themes got disabled..basic ubuntu came but couldn open any application until i put my visual effects to normal...The same happened repatedly...

Now i am unable to enter terminal itself..

Please help soon

These were the steps i followed to install tossim

1) add bellow repository to your [FONT=courier new]/etc/apt/sources.list[/FONT]  though it is for hardy, it is working for intrepid also

deb  [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) hardy main

2) with  following commands you can update the apt-cache and search the required  packages thin you can install the required version and all.

apt-get  update
apt-cache search tinyos
apt-get install tinyos-2.1.0

3)  then install python development package (headers)

apt-get  install python-dev

4) Edit /opt/tinyos-2.1.0/tinyos.sh  and change the CLASSPATH env-variable as bellow

CLASSPATH=$CLASSPATH:$TOSROOT/support/sdk/java/tinyos.jar:.

4)  Import /opt/tinyos-2.1.0/tinyos.sh  in your .bashrc; include bellow code snippet to ~/.bashrc

[FONT=courier new]if [ -f /opt/tinyos-[/FONT][FONT=courier new]2.1.0[/FONT]/tinyos.sh ] ; then
.  /opt/tinyos-[FONT=courier new]2.1.0[/FONT][FONT=courier new]/tinyos.sh[/FONT]
[FONT=courier new]fi[/FONT]

5) Now  execut bash again or restart the terminal and chech your enviorenment  with bellow command. It will check the enviorenment and report you the  status. (Ignore the WORNING returned due to graphvis version)

tos-check-env

6)  Lets compile the first application

cd $TOSROOT/apps/Blink
[FONT=courier new]make micaz[/FONT]

for  simulator

make micaz sim

Please help soon 

Thanks in advance

---

### Post by raihanrcc on 2010-06-14
Thanks for nice guides, specially for the warnings TOSSIM generates, thanks...

> **farahijahromi said:**
> I am not sure if its too late for you to answer or not but today I was trying to figure out the problem and finally I could!
As a new Linux user, I have installed hardy Unubtu. I was able to compile successfully using  mica2, micaz, or telosb but not micaz sim. The same bunch of error messages was printing in my screen. After hours and hours searching in the different websites I could solve the problem (thanks to forums!).
This may solve yours as well:
1- Install tinyos 2.1.0 as this link guides you:
Many thanks to [Gireesh]("http://mythicalcomputer.blogspot.com/2008/08/installation-of-tinyos-in-ubuntu.html"), 
check carefully so that everything is according to his guides.
Just the html codes made the instructions a little tricky!
while setting the .bashrc each line starts with an "export" and no space after each line!!!
2- Then you have to install the standard c development library 
(many thanks to [Phil]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2007-August/027530.html") )
the command is:                                               
sudo apt&#8208;get &#8233;install &#8233;build&#8208;essential  
(Thanks to this [tutorial]("http://www.cs.wustl.edu/%7Elu/cs520s/slides/tinyos_tutorial.pdf")!) 

3- Third and the last one!!! You have to install the Python development 
headers which is python2.5-dev (or any other version) from

System -> Administration -> Synaptic Package Manager

(Thanks to [Greg Hackmann]("http://mail.millennium.berkeley.edu/pipermail/tinyos-help/2008-March/031763.html"))

That's it! Now you should be able to compile Blink or any other app with the Tossim!

By the way! I already noticed that after compiling the Blink with Tossim, it would write "*** Successfully built micaz TOSSIM library"; however, too many warnings come to the existence. I used a Xubuntu live CD and compare these two together. while searching the web, I noticed that the gcc version 4.2 + is more strict about the conversions between char and string compared to gcc 4.1 . I don't know if its an important issue for the real programs but I found out that in the error lines of the mentioned files (/opt/tinyos-2.1.0/tos/lib/tossim/tossim.c and /opt/tinyos-2.1.0/tos/lib/tossim/tossim_wrap.cxx) if a " (char*) " be added after the * = * it would solve the problem. 
It may sound a ridicules or even a dangerous method to solve the problem like that! But as far as I experienced it removed the warnings. Just in case I did backup my original files.

Regards,
Mohsen

---

