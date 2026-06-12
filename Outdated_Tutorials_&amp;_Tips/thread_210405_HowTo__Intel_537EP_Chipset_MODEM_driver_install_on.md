---
title: "HowTo:  Intel 537EP Chipset MODEM driver install on Ubuntu Dapper."
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by chuckman78 on 2006-07-06
[B][U][COLOR="Red"][SIZE="4"]FOR A CLEARER GUIDE, PLEASE USE THE INFORMATION IN THE WIKI AT:

[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP]("https://help.ubuntu.com/community/DialupModemHowto/Intel537EP")

THIS THREAD SHOULD BE USED JUST AFTER CHECKING THE GUIDE IN THE WIKI.[/SIZE][/COLOR][/U][/B]


[COLOR="Black"][SIZE="4"]*** EDIT: THERE IS INSTALLATION INFORMATION FOR DAPPER 6.06.0, DAPPER 6.06.1 AND EDGY 6.10. SEARCH THROUGH THE THREAD TO FIND OUT ****

THERE IS ALSO SOME INFO ON FEISTY FAWN 7.04 DEVELOPMENT ON THE TOPIC - LOOK FOR NEWEST POSTS.[/SIZE][/COLOR]

First of all: I am a new Linux, and subsequently Ubuntu, user. The following information is a blend of steps from various sources with the purpose of installing the driver for a dial up MODEM with Intel 537EP Chipset. 

The principal sources of info for this little guide are:

[<http://www.ubuntu-es.org/comment/reply/5503/40456>]("http://www.ubuntu-es.org/comment/reply/5503/40456")

<[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")>

I have got also lots of help from the guys at <[http://linmodems.org/]("http://linmodems.org/")> and their discussion list, specially Marv and Jaques. Last, but not least, the people at <[http://www.ubuntuforums.org/]("http://www.ubuntuforums.org/")> , with special acknowledgement to zxee, azz and Matchless.

Now, let&#8217;s get to business.

0.- I did this on a fresh new install, but I think It could work even after some kernel updates. More on this later.

You will need to use a computer with internet connection to get these files:

<[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1230&DwnldID=9284&strOSs=39&OSFullName=Linux*&lang=eng")>

This is the driver from Intel. Don&#8217;t worry if it says &#8220;suse&#8221; in its name.

Also, let&#8217;s get these:
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb")>
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb")> 
<[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb")> 

These are the files for the C compiler needed to create the driver.

1.- We need to install some things first, the linux-headers and the build-essential packages. They are in the Dapper installation CD, so pop it in and type at the terminal:


```
sudo apt-get install linux-headers-386 build-essential
```

(I am assuming that you are using the same architecture as I am, x86. If not, change 386 with yours).

It is a good idea to put all the downloaded files in the previous step in your Desktop, just to keep then handy.

On the terminal lets cd to Desktop and execute the following three commands (The order is important):

```
sudo dpkg -i gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb
sudo dpkg -i gcc-3.4_3.4.4-6ubuntu8_i386.deb
```

This installs the gcc packages, needed for the compilation of the driver. 

Now lets unpack the MODEM driver:

```
tar xzf Intel-537EP-2.70.95.0-suse9.3.tgz
```

This will create a folder called Intel-537. We will need to rename it with the result of doing:

```
uname -r
```

In my case I got &#8220;***2.6.15-23-386***&#8221; so I renamed the directory **Intel-537** to&#8230;. yes, you got it ***2.6.15-23-386***. This step will be addressed and explained later.  For simplicity in this tutorial I will call this directory &#8220;**modem_source**&#8221;. 

2.- Let&#8217;s cd to **modem_source**. Now, we will need root privileges so:

```
sudo su
```

And, now let&#8217;s compile:


```
make clean
make 537
make install
```

At this point, hopefully, we got the driver compiled.

3.- To make things easier lets open nautilus (I assume you are using Gnome) from the terminal still having root privileges:

```
nautilus
```

Now, from nautilus copy the **modem_source** folder to **/etc/init.d.** 

4.- At the **/etc/init.d** directory you will also find the **537_boot **shell script. Double click on it to open it in your text editor. We will replace the content of the script with the following:

[COLOR="Blue"]#!/bin/sh
kernel=`uname -r`
serial="/etc/init.d/$kernel/Intel537.ko"
device="537"
registry="hamregistry"
group="root"
mode="664"
if [ -a /etc/SuSE-release ]; then
{
group="dialout"
}
fi
case "$1" in
start | b)
if ! ( modprobe -f $serial 1>/dev/null 2>/dev/null ); then
{
if ! ( insmod -f $serial 1>/dev/null 2>/dev/null ); then
{
echo error loading $serial
rmmod $serial
exit 1
}
fi
}
fi
major=`cat /proc/devices | awk "\\$2==\"Intel537\" {print \\$1}"`
echo major="($major)"
rm -f /dev/$device
mknod /dev/$device c $major 1 2> /dev/null 1> /dev/null
chgrp $group /dev/$device
chmod $mode /dev/$device
ln -sf /dev/Intel5370 /dev/modem 1> /dev/null 2> /dev/null
if ! ps -C $registry 1> /dev/null 2> /dev/null; then
{
if ! ( /usr/sbin/$registry 2> /dev/null 1> /dev/null & ); then
{
echo "Modem registry ($registry) could not start."
echo "Please see international users secion in readme.txt for more info."
}
fi
}
fi
exit 0
;;
stop)
rmmod 537 1> /dev/null 2> /dev/null
rmmod 537_core 1> /dev/null 2> /dev/null
rmmod $serial 1> /dev/null 2> /dev/null
;;
restart | reload)
/bin/bash "$0" stop
/bin/bash "$0" start
exit 0
;;
status)
if lsmod | grep "$serial " >/dev/null; then
{
lsmod | grep "$serial " > /dev/null
}
else
{
echo "$serial NOT loaded"
}
fi
if ps -C $registry 1> /dev/null 2> /dev/null; then
{
ps -C $registry
}
else
{
echo "$registry NOT running"
}
fi
exit 0
;;
*)
echo unknown $serial script parameter
exit 1
esac
exit 0[/COLOR]
################# End of script ##################

This script is executed on boot, looks for the directory with the same name as the kernel version (that&#8217;s why we renamed the directory on step 1), installs the module for the modem and creates the link to /dev/modem from /dev/537. If you update your kernel you should repeat steps 0 to 3 (it worked for me when I updated to 2.6.15-25-386).

5.- Configure your favorite dial up utility (I use gnome-ppp). In my case I had to uncheck the &#8220;Abort if busy&#8221;, &#8220;Abort if no dial tone&#8221; and &#8220;Carrier check&#8221; check boxes.

6.- Restart or type:

```
sudo bash /etc/init.d/537_boot start
```


And that's pretty much it.  

Right now I've been having trouble to use gnome-ppp when I restart the machine so I have to type in terminal before using the modem (but just once per session), this:

```
sudo /etc/init.d/537_boot restart
```

Enjoy!

Regards,

Carlos Marcano.

P.S: Please, I would like to read your suggestions and improvement to this little guide. We all most try to make this as painless as possible for all the dialup users out there using winmodems. I still have a faboulus USrobotics external modem lying on the top of my desk with out use with Ubuntu, thats my next goal. Meanwhile, I have my 537 to help me! :D

---

### Post by Marvin Stodolsky on 2006-07-07
The gcc-4.0 related packages are included on the Dapper install CD.
Thus they need not be downloaded.  Just with the CD in place.
$ sudo apt-get install gcc-4.0 
will load the three required packages.

It may be additionally necessary to make a symbolic link:
$ sudo ln -sf /usr/bin/gcc-4.0  /usr/bin/gcc
Check afterwards with:
$ ls -l /usr/bin/gcc*
whose output should include
   /usr/bin/gcc-4.0 --> /usr/bin/gcc

---

### Post by chuckman78 on 2006-07-07
Hi, Marvin.

> **Marvin Stodolsky said:**
> The gcc-4.0 related packages are included on the Dapper install CD.
Thus they need not be downloaded.  Just with the CD in place.
$ sudo apt-get install gcc-4.0 
will load the three required packages.

Yes, this is right. The problem is (or at least the problem that **I had**) that the driver did not compile untill I got the gcc 3.4 packages stated upthere.

> **Marvin Stodolsky said:**
> 
It may be additionally necessary to make a symbolic link:
$ sudo ln -sf /usr/bin/gcc-4.0  /usr/bin/gcc
Check afterwards with:
$ ls -l /usr/bin/gcc*
whose output should include
   /usr/bin/gcc-4.0 --> /usr/bin/gcc

Ummm... so this would make the install scripts call the gcc 4.0? I assume that anyhting that can be compiled with gcc 3.4 could be compiled with 4.0, am I right? If true, then the symbolic link you proposed would be everything needed, I guess. Thanks for your reply!

Regards,

Carlos.

---

### Post by nrayever on 2006-07-08
> **chuckman78 said:**
> **[SIZE="4"]HowTo:  Intel 537EP Chipset MODEM driver install on Ubuntu Dapper.[/SIZE]**

First of all: I am a new Linux, and subsequently Ubuntu, user. The following information is a blend of steps from various sources with the purpose of installing the driver for a dial up MODEM with Intel 537EP Chipset. 

Enjoy!

Regards,

Carlos Marcano.

P.S: Please, I would like to read your suggestions and improvement to this little guide. We all most try to make this as painless as possible for all the dialup users out there using winmodems. I still have a faboulus USrobotics external modem lying on the top of my desk with out use with Ubuntu, thats my next goal. Meanwhile, I have my 537 to help me! :D

carlos:

if this howto works, i will take care of your children for a month!! i was looking all over the web for a solution like this! i will try it and i will let you know if it works!!:D :D 

nrayever

---

### Post by chuckman78 on 2006-07-09
Nrayever, my fingers are crossed! (no children but a very demanding wife!!)

Regards,

Carlos.

---

### Post by nrayever on 2006-08-04
> **chuckman78 said:**
> Nrayever, my fingers are crossed! (no children but a very demanding wife!!)

Regards,

Carlos.

sorry carlos i wouldn't take care of your children, because i got some problems with the intel 537. i followed step by step your how to but when i tried to start the modem i got this message:

```
aranza@pakiel:~$ sudo bash /etc/init.d/537_boot start
Password:
error loading /etc/init.d/2.6.15-26-386/Intel537.ko
ERROR: Module Intel537 does not exist in /proc/modules
aranza@pakiel:~$

```

i hope you could help me with this. then i may take care of your children.

nrayever

---

### Post by Rakeris on 2006-08-05
Great guide! Thanks a lot, been trying for a while to get my connection set up but just couldn't. Thanks to you I was able to!

---

### Post by nrayever on 2006-08-05
> **Rakeris said:**
> Great guide! Thanks a lot, been trying for a while to get my connection set up but just couldn't. Thanks to you I was able to!

rakeris: 

did you follow step by step this howto?? didn't you get the same error as i received??

am i missign something??

nrayever

---

### Post by Rakeris on 2006-08-06
Yeah, followed it to the letter.

I did get a few errors but they didn't matter in the long run. But the one you got was not one of them. I'm quite new to linux as is, so I can't offer much help...sorry.

One thing in the guide is some of the commands used the wrong "–" so if you copy/paste they won't work. Othe than that not a clue. =(

---

### Post by nrayever on 2006-08-11
finally it worked!!! but i had to try with a new fresh install of dapper. thanks for this howto carlos!!

nrayever

---

### Post by Mazehero55 on 2006-08-18
Hey i'm having a big problem, when I try to compile the driver I get a message saying I don't have the kenel source, But I installed it like you said. I don't know whats going on. I'm going to try with a fresh install and see if that works.

---

### Post by Coburn on 2006-08-20
Carlos--

I installed the SuSE driver, and it worked for me--so I didn't change /etc/init.d/modem_source.

In fact, when I added the /modem_source file to /etc/init.d, I had a little premonition of alarm.  All the files in the folder were single executables (binaries).  I was adding a folder.

I had also followed some other advice and added the line "Intel537" and some symlinks to my /etc/modules.

When I rebooted, the computer would not finish loading hald.  It hung on "too many options" somewhere. ](*,) 

I removed all three--the lines from /modules and the folder--(and actually while I was working in rescue mode the modem kept dialing and disconnecting)--and finally made it to the blessed shore of my login screen. :-D

It was probably the Intel537 line in /modules combined with a new, different install that did it, judging by the behavior--but that was a little freaky. :-({|=

So, yeah, I'm running without the updated /etc/init.d for now.  I will look at it more in-depth later and see if it warrants changing.

As always, I am very appreciative of the hard work you put in to make the Internet available for all of us.  Ubuntu works because users keep polishing off the rough edges. :-)

Thanks

---

### Post by chuckman78 on 2006-08-21
> **Coburn said:**
> Carlos--

I installed the SuSE driver, and it worked for me--so I didn't change /etc/init.d/modem_source.



Hi, Coburn. Great news it worked! I have a few questions so we can improve the Howto. What exactly you mean by "didn´t change /etc/init.d/modem_source"? **modem_source** is a directory containing the result of the compilation of the modem driver and it should be renamed with the result of executing "$ uname -r".

> **Coburn said:**
> In fact, when I added the /modem_source file to /etc/init.d, I had a little premonition of alarm.  All the files in the folder were single executables (binaries).  I was adding a folder.

Yes, that is right. You were adding a folder containing, as I wrote before, the result of the compilation. The important thing here is to rename it properly **and** to change the content of the **537_boot** shell script in the **/etc/init.d** directory with the one in the Howto (section 4).

> **Coburn said:**
> I had also followed some other advice and added the line "Intel537" and some symlinks to my /etc/modules.

When I rebooted, the computer would not finish loading hald. It hung on "too many options" somewhere.

I removed all three--the lines from /modules and the folder--(and actually while I was working in rescue mode the modem kept dialing and disconnecting)--and finally made it to the blessed shore of my login screen.

It was probably the Intel537 line in /modules combined with a new, different install that did it, judging by the behavior--but that was a little freaky.

I really don´t know what could be happening, but as I have said in the Howto: there is a lot of things I don´t know! :) 

> **Coburn said:**
> So, yeah, I'm running without the updated /etc/init.d for now. I will look at it more in-depth later and see if it warrants changing.

One question: Is the modem working inmediatly after you turn on the computer? Or do you need to issue any command before you can use it?

> **Coburn said:**
> As always, I am very appreciative of the hard work you put in to make the Internet available for all of us. Ubuntu works because users keep polishing off the rough edges.

Thanks

We are a big Ubuntu family, helping each other to get our systems up and running as we want! Thanks for your feedback.

Regards,

Carlos.

---

### Post by Steed on 2006-09-23
I just got into Ubuntu a few weeks ago. I'm still on dialup but was hoping to get a headstart before DSL gets here in a few months and I can experiment with a small webserver. I tried this tutorial and the steps I found on the DialupModemHowto but neither worked with my Intel537EP modem.

In the end I found that a much simpler way is to follow steps in the "readme.txt" that is included with the Intel-537EP-2.70.95.0-suse9.3.tgz download.

I downloaded the driver .tgz using my Windows partition and copied it to a FAT32 partition I created during installation which I then copied over to my /home directory. It can also be burned to a CD and retrieved by mounting the CD in Ubuntu. In a nutshell this is how I established my connection using the terminal. 
```

sudo apt-cdrom add (insert your Dapper CD)
sudo apt-get install linux-headers-386
sudo apt-get install build-essential

sudo su  (login as root)
tar -zxvf Intel-537EP-2.70.95.0-suse9.3.tgz  (creates Intel-537 folder)
cd Intel-537   
make clean
make 537
make install

```
```

pppconfig

```  (setup your ISP connection - I used the default name "provider") I use Dynamic, PAP settings
For the part where is asks to set up your port, enter **/dev/modem**

To start the connection 
```

pon provider

```
("provider" or whatever name you used during the pppconfig setup)

When I do this the modem starts to connect even though the terminal doesn't indicate anything is happening. If you type 

plog

you will get an update on what the connection is doing. About 30-45 seconds later I'm connected.

poff provider (to terminate the connection)

---

### Post by chuckman78 on 2006-09-23
Hi, Steed.

   I am glad to know you got your system working! And yes, you are right, that is the way to go for Ubuntu Dapper **6.06.1 LTS**. The solution I posted initially was needed for the 6.06.0 LTS, or at least it was the way I got it to work then. 

   The good thing is that things looks to be getting easier in this way, let´s hope that this trend keeps going!

Regards,

Carlos.

---

### Post by Steed on 2006-10-01
Anyone else seeing slow speeds with this modem on Ubuntu? On the same system running Windows 98 I get 5 KB per sec on downloads. Now it starts out around 3, then immediately plunges to around 1.8.

Are there any tricks I can use to help boost the speed, like modem init strings in pppconfig for instance? Thanks.

---

### Post by chuckman78 on 2006-10-04
Hi, Steed.

> **Steed said:**
> Anyone else seeing slow speeds with this modem on Ubuntu? On the same system running Windows 98 I get 5 KB per sec on downloads. Now it starts out around 3, then immediately plunges to around 1.8.

   I ussually get 3 Kb/s sustained under Ubuntu and 5 Kb/s under Windows XP PRO. I think it is got to do with an inferior performance of the driver under linux.

> **Steed said:**
> Are there any tricks I can use to help boost the speed, like modem init strings in pppconfig for instance?

   I don´t know. I believe this could be possible. I am try to get some help on that sense with another [modem problem I have]("http://www.ubuntuforums.org/showthread.php?p=1579298#post1579298").


Regards,
Carlos.

---

### Post by kellard on 2006-10-15
Hi
I have followed the howto and it worked until step 5. I used System > Administration > Networking as dial up utility. Modem port was autodetected and I was able to activate the connection. So far so good. After reboot I tried to type pon (I'm not sure if this is how to connect to internet) in the terminal window.
This is the answer: 
"/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem' "
Then i opened the Network settings again and now the Modem connection wasn't active and I wasn't able to autodetect the modem either?
I have a fresh installation of Ubuntu Dapper and I didn't see any errors when I installed the drivers.

Du you know what I should do? It feels like I'm almost there but still so far away when I'm a novice at Linux.

Thanks!

---

### Post by chuckman78 on 2006-10-15
Hi kellard.

I mainly use gnome-ppp for conection and have little experience with pon. I think you must use "sudo pppconfig" to create the conection account for your modem. I would prefer to use gnome-ppp it is simpler. If you want a terminal utility you could use wvdial, it is the tool that gnome-ppp uses, I think. At any time you can type:

```
sudo /etc/init.d/537_boot restart
```

 to restart the modem modules.

Regards,

Carlos.

---

### Post by Mazehero55 on 2006-10-19
I just have a quick question, How can you know if you have version 6.06.0 LTS or 6.06.1 LTS? All my CD's just have 6.06 LTS on them, and that's what the main site says is the current verion too.

---

### Post by Mazehero55 on 2006-10-19
Okey I reinstalled ubuntu and now when I try to do make 357 it does this.

> 
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.15-23-386
make[1]: Entering directory `/home/rave/Desktop/Linux modem/2.6.15-23-386/coredrv'
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/rave/Desktop/Linux modem/2.6.15-23-386/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
make[2]: *** No rule to make target `modem/2.6.15-23-386/coredrv'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/rave/Desktop/Linux modem/2.6.15-23-386/coredrv'
2.6.15-23-386
Failed to build driver


Why isn't it working, does anyone know how to kix it?

---

### Post by chuckman78 on 2006-10-19
Hi Mazehero55.

Just checking, did you follow the firts steps of the Howto? Looks like there are some files missing, headers and make stuff...

Regards,

Carlos.

---

### Post by Mazehero55 on 2006-10-19
Yes I believe I did. I even saved the whole how-to on my computer so I could follow it step by step.

I had other trouble before this as it wouldn't even recognize the make command! But I installed the make package and that was fixed. I downloaded every package you put a link to and to keep it precise I copied every command into the terminal from the how-to. 

I thought it was missing files too. But I've got all the things you said was needed.

any insight

Edit{also I had to install I think it was called the binutil package or one the sounds like that.

---

### Post by chuckman78 on 2006-10-19
Hi Mazehero55.

I have just done a fresh install of Dapper and installed my 537EP and everything went ok.

I must point out that basically you just need the next steps to get the modem working:

First you need to get some files so, in a terminal type:

> sudo apt-cdrom add

It will ask for your cd, so put in your cdrom drive the Ubuntu Dapper one, then press enter.

Then type

> sudo apt-get update

Then, assuming your computer architecture is x386, type:

> sudo apt-get install linux-headers-386 build-essential

That will get ALL the necessary files for building the driver. Now, go to the directory where you extracted the driver you got from Intel's site and simply type:

> sudo make clean

then

> sudo make 537

then

> sudo make install

And that is it. I hope this work.

Regards,

Carlos.

---

### Post by Mazehero55 on 2006-10-20
Okey I have just done that, I still get the same thing when I "make 537" it though. It's like nothing changed. Do you have any other ideas? Could there be something else that I may be missing? 

Thank you for the help, I'd be nowhere without this community.

Isaiah,

---

### Post by chuckman78 on 2006-10-20
Hi Mazehero55.

Uhmm, I am loosing options here... Let´s try another approach:

1.- Get this driver:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz")

Now follow this steps from the Howto (take in count I changed it to what exactly you should need to do):

1.- We need to install some things first, the linux-headers and the build-essential packages. They are in the Dapper installation CD, so pop it in and type at the terminal:


Code:

sudo apt-get install linux-headers-386 build-essential

(I am assuming that you are using the same architecture as I am, x86. If not, change 386 with yours).

It is a good idea to put all the downloaded files in the previous step in your Desktop, just to keep then handy.

On the terminal lets cd to Desktop and unpack the MODEM driver:

Code:

tar xzf intel-537EP_secure-2.60.80.1_21_09_2006.tgz

This will create a directory that for simplicity in this tutorial I will call “modem_source”.

2.- Let’s cd to modem_source. Now, we will need root privileges so:

Code:

sudo su

And, now let’s compile:


Code:

make clean

make 537

make install

At this point, hopefully, we got the driver compiled.

I hope this work for you. Tell us how did it go.

Regards,

Carlos.

---

### Post by Mazehero55 on 2006-10-20
hurray!!! it compiled!!

Okey but where do I go from here? I can't use the script from the first tutorial because that's for the susie one right?

I can't help but wonder why the susie one wouldn't compile...

Edit:{by the way I just have a quick question, why didn't you use this driver before? is it not as good as the susie one?}

---

### Post by chuckman78 on 2006-10-21
> **Mazehero55 said:**
> hurray!!! it compiled!!

Great news!

> **Mazehero55 said:**
> Okey but where do I go from here? I can't use the script from the first tutorial because that's for the susie one right?

I think you can use it. But first, did you have to use this command,

> export MODEM_TYPE=537EP

to get the compilation done? (just curious about that because I forgot to tell you to do it).

Another question, did you use the "make install"? Did everything go right with that?

I believe that if the "make install" worked, you are already done! Use wvdial (I prefer to use gnome-ppp but it is just a front end for wvdial) to test your modem. If everything goes fine reboot your computer and try wvdial again. If it doesn`t work now, you need to use the script from the Howto.

> **Mazehero55 said:**
> I can't help but wonder why the susie one wouldn't compile...

It is "suse" (the linux distro). I am not pretty sure why it didn`t work for you, it did work for me!

> **Mazehero55 said:**
> Edit:{by the way I just have a quick question, why didn't you use this driver before? is it not as good as the susie one?}

No, it is as good as the other, maybe better. It is an updated version from Philippe Vouters, an HP France employee (I think) and volunteer in the linmodems field. I just recently got to know this driver, that is the reason I did not use it before.

By the way, I recommend to anyone trying to get their modems to work under linux to get to [http://linmodems.org]("http://linmodems.org") it is the best place on the web to get the info to get the modem working.

Regards, 

Carlos.

---

### Post by Mazehero55 on 2006-10-21
Yes I had to make that command, it just took me a sec to figure that out. It mentioned it in the terminal and I read through the docs and files and I found it out.
It's done now! *happy dance*

Okey I try those and edit this post to let you know.

EDIT{ Okey even when I get the script and try wvdial I get

initializing modem
sending: ATZ
sending:ATQU
Re-sending:ATZ
Modem not responding

What about the networking in the administraion menue? It kept saying connection active but I couldn't use internet?

Also I would want to ask how to creat a conection with wvdial or something?

---

### Post by chuckman78 on 2006-10-21
Hi Mazehero55.

I would recommend you to use gnome-ppp. Download this:

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-0ubuntu2_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-0ubuntu2_i386.deb")

Double click it and install it. Now, DO THIS:

1.- Open a terminal.

2.- Type "sudo su"

3.- Input the root password.

4.- Type "gnome-ppp" (Always be sure to run gnome-ppp from a superuser terminal) You can create a launcher for your desktop with the command "gksudo gnome-ppp" to try it with out going to a terminal.

5.- There will appear a dialog box.

6.- Type in your data (login, password, dialing number).

7.- Configure your modem data:

Modem : /dev/modem

Don´t use carrier detect, abort on busy.

8.- Try  to connect.

9.- If this doesn´t work, try to change the different settings at gnome-ppp.


Regards,

Carlos.

---

### Post by paulgir on 2006-10-25
Will this driver work with the 536EP modem?
Intel don't seem to have 536 drivers for Dapper.

---

### Post by chuckman78 on 2006-10-25
> **paulgir said:**
> Will this driver work with the 536EP modem?

I don´t think so.

> **paulgir said:**
> Intel don't seem to have 536 drivers for Dapper.

You can find linux drivers for the 536EP at:

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

I think you should try:

[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=6497&strOSs=39&OSFullName=Linux*&lang=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=6497&strOSs=39&OSFullName=Linux*&lang=eng")

This **might** work with the Howto but I have not tried.

I would recommend you to go to:

[http://linmodems.org]("http://linmodems.org")

This guys are the best to try to find solutions for winmodems on linux.

Regards,

Carlos.

---

### Post by BoredOutOfMyMind on 2006-10-29
Here is link to version 4.71 driver for 536EP modem-

[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=977&DwnldID=9266&strOSs=39&OSFullName=Linux*&lang=eng)

Both the 536 and 537 are in the DialupModemHowto page.

Carlos, thanks for the imput of this thread also!

---

### Post by quasarhu on 2006-11-10
Thanks Carlos, very good guide, I have changed 3 times the kernel in Ubuntu 6.06.1 and any problems, only compiling the new kernel. My question is, this guide working in Ubuntu Edgy 6.10?

Thanks a lot.

---

### Post by chuckman78 on 2006-11-13
> **quasarhu said:**
> Thanks Carlos, very good guide, I have changed 3 times the kernel in Ubuntu 6.06.1 and any problems, only compiling the new kernel.

Hi, quasarhu.

I am glad this guide has been usefull for you!
 
 > **quasarhu said:**
> My question is, this guide working in Ubuntu Edgy 6.10?

It is even simpler:

1.- Put in the drive the Edgy disc and type:

```
sudo apt-get install linux-headers-386 build-essential
```

2.- Get the driver and untar it to a directory.

3.- Get into that directory and simply do:

```
sudo make clean
sudo make 537
sudo make install
```

 And that´s it.

If for any reason this doesn´t work, try again with this other driver:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz")


> **quasarhu said:**
> Thanks a lot.

Nothing to thank, we are all in the same road!

Regards,

Carlos.

---

### Post by quasarhu on 2006-11-16
Hi, Carlos:

Change Ubuntu 6.06 to Edgy 6.10 and I can´t use my modem, this is the information:

edgar@edgar-desktop:~/Desktop/Intel-537$ sudo apt-get install linux-headers-generic build-essential

Leyendo lista de paquetes... Hecho
Creando Ã¡rbol de dependencias       
Leyendo informaciÃ³n de estado... Hecho
linux-headers-generic ya estÃ¡ en su versiÃ³n mÃ¡s reciente.
build-essential ya estÃ¡ en su versiÃ³n mÃ¡s reciente.
0 actualizados, 0 se instalarÃ¡n, 0 para eliminar y 0 no actualizados.

edgar@edgar-desktop:~/Desktop/Intel-537$ sudo make clean

cd coredrv; make clean
make[1]: se ingresa al directorio `/home/edgar/Desktop/Intel-537/coredrv'
rm -f *.ko *.o *~ core
make[1]: se sale del directorio `/home/edgar/Desktop/Intel-537/coredrv'
rm -f *.o *.ko

edgar@edgar-desktop:~/Desktop/Intel-537$ sudo make 537

   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No existe el fichero Ã³ directorio
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No existe el fichero Ã³ directorio
   version.h matches running kernel
2.6.17-10-generic
make[1]: se ingresa al directorio `/home/edgar/Desktop/Intel-537/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/edgar/Desktop/Intel-537/coredrv modules
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/edgar/Desktop/Intel-537/coredrv/coredrv.o
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:73: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_NOVERSâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: In function â€˜softcore_init_structâ€™:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: In function â€˜openâ€™:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:407: warning: implicit declaration of function â€˜pm_registerâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:408: warning: assignment makes pointer from integer without a cast
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: In function â€˜closeâ€™:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:439: warning: implicit declaration of function â€˜pm_unregisterâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: In function â€˜send_data_to_userâ€™:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:587: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:592: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:593: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:595: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:596: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:597: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: At top level:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:665: error: expected â€˜)â€™ before string constant
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: In function â€˜hamproc_writeâ€™:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:684: warning: ignoring return value of â€˜copy_from_userâ€™, declared with attribute warn_unused_result
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c: At top level:
/home/edgar/Desktop/Intel-537/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/edgar/Desktop/Intel-537/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/edgar/Desktop/Intel-537/coredrv] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [537core_26] Error 2
make[1]: se sale del directorio `/home/edgar/Desktop/Intel-537/coredrv'
2.6.17-10-generic
Failed to build driver


Any idea??

---

### Post by chuckman78 on 2006-11-16
Hi, Edgar.

Try this:

Download this driver:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz")

Untar it an get to its directory.

Type:

```
sudo make clean
```

Then:

```
export MODEM_TYPE=537EP
```

Then:

```
sudo make 537
```

Then:

```
sudo make install
```


I hope this works!

Regards,

Carlos.

---

### Post by quasarhu on 2006-11-16
Thanks Carlos:

I have Ubuntu Edgy working with modem Intel 537, your second solution option is excelent for Edgy. Now, the name of Thread is, HowTo: Intel 537EP Chipset MODEM driver install on Ubuntu Dapper and Edgy.

Regards.

Edgar

---

### Post by jdawgnc82 on 2006-11-23
Hi everybody!,
   I'm pretty new to the whole Linux thing.  I've been playing around with Kubuntu 6.06.01 LTS and I am having some trouble trying to install the modem driver for my Intel 537EP modem.  I have used the driver: Intel-573EP-2.70.95.0-suse9.3.tgz

I then open terminal and type:

sudo apt-cdrom add
sudo apt-get install linux-header-386
sudo apt-get build-essential

sudo su
tar -zxvf Intel-573EP-2.70-95.0-suse9.3.tgz
cd Intel-537
make clean
make 537

Here is where I can my error:

ubuntu@ubuntu:~/Intel-537$ make 537
   Module precompile check
   Current running kernel is: 2.6.15-26-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
ubuntu@ubuntu:~/Intel-537$     

Does anybody have any idea what is going on?  I would really like to start converting away from Windows and to Linux; however, I have to have my internet connection before I do.

Also, I am running Kubuntu 6.06.01 LTS from the live cd.  Do you have to install the OS in order to do this?  Any help would be greatfully appreciated!  Thanks!

---

### Post by chuckman78 on 2006-11-23
> **jdawgnc82 said:**
> Hi everybody!,
   I'm pretty new to the whole Linux thing.  I've been playing around with Kubuntu 6.06.01 LTS...

Welcome jdawgnc82!

> **jdawgnc82 said:**
> ...and I am having some trouble trying to install the modem driver for my Intel 537EP modem.  I have used the driver: Intel-573EP-2.70.95.0-suse9.3.tgz

I then open terminal and type:

sudo apt-cdrom add
sudo apt-get install linux-header-386
sudo apt-get build-essential

sudo su
tar -zxvf Intel-573EP-2.70-95.0-suse9.3.tgz
cd Intel-537
make clean
make 537

Here is where I can my error:

ubuntu@ubuntu:~/Intel-537$ make 537
   Module precompile check
   Current running kernel is: 2.6.15-26-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
ubuntu@ubuntu:~/Intel-537$     

Does anybody have any idea what is going on?  I would really like to start converting away from Windows and to Linux; however, I have to have my internet connection before I do. 

Try this:

Get this driver:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_21_09_2006.tgz")



Type:

```
tar -zxvf intel-537EP_secure-2.60.80.1_21_09_2006.tgz
```

Then:

```
cd intel-537EP_secure-2.60.80.1
```

Then: 

```
sudo make clean
```

Then:
```

export MODEM_TYPE=537EP
```

Then:

```
sudo make 537
```

Then:

```

sudo make install
```


I hope this works!

> **jdawgnc82 said:**
> Also, I am running Kubuntu 6.06.01 LTS from the live cd.  Do you have to install the OS in order to do this?  Any help would be greatfully appreciated!  Thanks!

The only problem will be that you will need to repeat this guide every time you reboot your machine. Why don´t you install (K)Ubuntu? It´s great! I use Ubuntu Edgy myself because I don´t like KDE too much.

Regards,

Carlos.

---

### Post by nrayever on 2006-11-23
> **chuckman78 said:**
> **[COLOR="Red"][SIZE="4"]*** EDIT: THERE IS INSTALLATION INFORMATION FOR DAPPER 6.06.0, DAPPER 6.06.1 AND EDGY 6.10. SEARCH THROUGH THE THREAD TO FIND OUT ****[/SIZE][/COLOR]**

hi chuckman78!!!

seem that now you have made it work with edgy. i will try it and then again i will ask you for some help. you know sometimes this things don't your at the first try. ;) ;) 

i will post if it works or if i have any problem.

sincerly nrayever

---

### Post by chuckman78 on 2006-11-23
My fingers are crossed!

Regards,

Carlos.

---

### Post by jdawgnc82 on 2006-11-25
chuckman,
  I tried what you said to do, and this comes up when I run 'pon provider' to connect.

root@ubuntu:/home/ubuntu/Intel-537# plog
Nov 23 22:47:02 ubuntu chat[7946]: send (ATZ^M)
Nov 23 22:47:02 ubuntu chat[7946]: expect (OK)
Nov 23 22:47:47 ubuntu chat[7946]: alarm
Nov 23 22:47:47 ubuntu chat[7946]: send (AT^M)
Nov 23 22:47:47 ubuntu chat[7946]: expect (OK)
Nov 23 22:48:32 ubuntu chat[7946]: alarm
Nov 23 22:48:32 ubuntu chat[7946]: Failed
Nov 23 22:48:32 ubuntu pppd[7945]: Connect script failed
root@ubuntu:/home/ubuntu/Intel-537#  

I have the modem set to ttyS0 using the 'pppconfig' tool.  Any ideas?

---

### Post by chuckman78 on 2006-11-25
> **jdawgnc82 said:**
> chuckman,
  I tried what you said to do, and this comes up when I run 'pon provider' to connect.

root@ubuntu:/home/ubuntu/Intel-537# plog
Nov 23 22:47:02 ubuntu chat[7946]: send (ATZ^M)
Nov 23 22:47:02 ubuntu chat[7946]: expect (OK)
Nov 23 22:47:47 ubuntu chat[7946]: alarm
Nov 23 22:47:47 ubuntu chat[7946]: send (AT^M)
Nov 23 22:47:47 ubuntu chat[7946]: expect (OK)
Nov 23 22:48:32 ubuntu chat[7946]: alarm
Nov 23 22:48:32 ubuntu chat[7946]: Failed
Nov 23 22:48:32 ubuntu pppd[7945]: Connect script failed
root@ubuntu:/home/ubuntu/Intel-537#  

I have the modem set to ttyS0 using the 'pppconfig' tool.  Any ideas?

I am not very familiar with that (I use wvdial for connection) but you should set the modem to /dev/modem or /dev/537.

Regards,

Carlos.

---

### Post by lime4x4 on 2006-12-26
can't get this ep537 modem to work.Fresh install of edgy on a dell dimension 3000 when i go to use gnome-ppp and select detect modem  it tells me i don't have a modem installed.Here is the output of the commands to install the driver

megan@megan-desktop:~$ cd Desktop/intel-537EP_secure-2.60.80.1
megan@megan-desktop:~/Desktop/intel-537EP_secure-2.60.80.1$ sudo -s
root@megan-desktop:~/Desktop/intel-537EP_secure-2.60.80.1# export MODEM_TYPE=537EP
root@megan-desktop:~/Desktop/intel-537EP_secure-2.60.80.1# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd Modules.symvers
rm -rf .tmp_versions
make[1]: Leaving directory `/home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv'
rm -f *.o *.ko
root@megan-desktop:~/Desktop/intel-537EP_secure-2.60.80.1# make 537
   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.17-10-generic
make[1]: Entering directory `/home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/coredrv.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/clmmain.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/rts.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/task.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/uart.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/wwh_dflt.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/locks.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/softserial_io.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/softserial_ioctl.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/softserial.o
  CC [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/afedsp_int.o
  LD [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/.537core.lib.cmd for /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/537core.lib
  CC      /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/Intel537.mod.o
  LD [M]  /home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/megan/Desktop/intel-537EP_secure-2.60.80.1/coredrv'
root@megan-desktop:~/Desktop/intel-537EP_secure-2.60.80.1# make install
rm -f /usr/sbin/hamregistry.bin
bash 537_inst
running kernel 2.6.17-10-generic
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install DEBIAN 537 boot script and links
starting module and utilities
done

---

### Post by chuckman78 on 2006-12-26
Hello.

 Could you please post your gnome-ppp options? A hint: remember to set your modem option in gnome-ppp to ***/dev/modem***.

Regards,

Carlos.

P.S: I don't use gnome-ppp, I prefer to use plain ***wvdial***.

---

### Post by lime4x4 on 2006-12-27
megan@megan-desktop:~$ sudo wvdialconf /etc/wvdial.conf
Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by chuckman78 on 2006-12-29
Hi.

 Sorry for the delay. You should try this:

1.-

```
sudo gedit /etc/wvdial.conf
```

2.-

Erase its content and copy the following lines into this file, change the phone number, username and password to the right ones for your case:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=3D
Init3 = ATM1L3
Carrier Check = no
FlowControl = CRTSCTS
**Phone = <your ISP phone number>**
**Username = <your username>**
**Password = <your password>**
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

3.-

Save and close.

4.- 

```
sudo wvdial

```

Luckily after a while you will be connected.

Regards,

Carlos.

---

### Post by teamr on 2007-01-27
Hi Guy's/guyettes,

Posted in 64 forum but will repeat here as it is similar.

I have a amd64 system with a Intel 536EP modem that I can't get to work. I followed the stepps in this tread but at make 536 I get the following

root@bigtoot:/home/garry/Desktop/Intel-536# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/garry/Desktop/Intel-536/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/garry/Desktop/Intel-536/coredrv'
rm -f *.o *.ko
root@bigtoot:/home/garry/Desktop/Intel-536# make 536
   Module precompile check
   Current running kernel is: 2.6.15-23-amd64-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed  to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTAR GET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname  -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/v ersion.h;\
        fi
2.6.15-23-amd64-generic
make[1]: Entering directory `/home/garry/Desktop/Intel-536/coredrv'
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/home/garry/Desktop/I ntel-536/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/coredrv.o
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: type defaults to â€˜i ntâ€™ in declaration of â€˜EXPORT_SYMBOL_NOVERSâ€™
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: parameter names (wi thout types) in function declaration
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:73: warning: data definition has  no type or storage class
/home/garry/Desktop/Intel-536/coredrv/coredrv.c: In function â€˜closeâ€™:
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:439: warning: implicit declarati on of function â€˜pm_unregisterâ€™
/home/garry/Desktop/Intel-536/coredrv/coredrv.c: At top level:
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:880: warning: initialization mak es integer from pointer without a cast
/home/garry/Desktop/Intel-536/coredrv/coredrv.c:289: warning: â€˜power_callbackâ€™ d efined but not used
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/clmmain.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/rts.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/task.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/uart.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/wwh_dflt.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/locks.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial_io.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial_ioctl.o
  CC [M]  /home/garry/Desktop/Intel-536/coredrv/softserial.o
  LD [M]  /home/garry/Desktop/Intel-536/coredrv/Intel536.o
ld: Relocatable linking with relocations from format elf32-i386 (/home/garry/Des ktop/Intel-536/coredrv/536core.lib) to format elf64-x86-64 (/home/garry/Desktop/ Intel-536/coredrv/Intel536.o) is not supported
make[3]: *** [/home/garry/Desktop/Intel-536/coredrv/Intel536.o] Error 1
make[2]: *** [_module_/home/garry/Desktop/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/garry/Desktop/Intel-536/coredrv'
2.6.15-23-amd64-generic
Failed to build driver
root@bigtoot:/home/garry/Desktop/Intel-536# make clean

Any ideas?

teamr.

---

### Post by chuckman78 on 2007-01-28
Hi.

I think there is no driver for 64 bits. You could try to find info about that joining the discussion list on [http://linmodems.org]("http://linmodems.org").

Regards,

Carlos.

---

### Post by teamr on 2007-01-28
Blast, I think your right.

Do you think if I loaded the 386 Dapper the drivers might work.

Cheers.

teamr

---

### Post by chuckman78 on 2007-01-28
Yes, I think it is very possible. Make sure to check the whole thread to find out on the latest driver tweak by Mr. Vouters, It will work better.

Regards,

Carlos.

---

### Post by thorosius on 2007-02-01
Hello
                Thanks for this guide. This thread has been very helpful to me. I need a couple confirmations and have some questions:

1. I have run scanmodem tool and I have read ModemData.txt it has a section that says:

For candidate modem in PCI bus:  02:02.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
            
                 I have tried the driver from Mr. Vouters. Am I correct at choosing this driver?


2. Now am I right if I replace "537" instead of "537EP" in the step: "export MODEM_TYPE=537EP" ? because If I enter 537EP, command "make install" fails and it succeeds, if I write only 537.

3. Do I have to follow the initial steps as-it-is (On the first page) or any editing is needed? I have Ubuntu 6.10.

Thanks! 
Fahd

---

### Post by chuckman78 on 2007-02-02
> **thorosius said:**
> Hello
                Thanks for this guide. This thread has been very helpful to me. I need a couple confirmations and have some questions:

1. I have run scanmodem tool and I have read ModemData.txt it has a section that says:

For candidate modem in PCI bus:  02:02.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
            
                 I have tried the driver from Mr. Vouters. Am I correct at choosing this driver?

Hi Fahd, glad to know the guide have been helpfull for you. It is correct to use Mr. Vouters driver althought you should use the last update of it, get it at:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_16_07_2006.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_16_07_2006.tgz")

> **thorosius said:**
> 2. Now am I right if I replace "537" instead of "537EP" in the step: "export MODEM_TYPE=537EP" ? because If I enter 537EP, command "make install" fails and it succeeds, if I write only 537.

That is perfect.

> **thorosius said:**
> 3. Do I have to follow the initial steps as-it-is (On the first page) or any editing is needed? I have Ubuntu 6.10.

If you are using Edgy Eft (Ubuntu 6.10) all you may need is to do is:

```
sudo apt-get install linux-headers-386 build-essential
```

Then untar the driver and do this in its directory:

```
sudo make clean
```

Then:

```
export MODEM_TYPE=<*your modem type*>
```

In your case would be:


```
export MODEM_TYPE=*537*
```

Then:

```
sudo make 537
```

And last but not least:

```
sudo make install
```

I hope this works. Sorry for the late reply!

Regards,

Carlos.

---

### Post by thorosius on 2007-02-03
Thanks for the reply!

I dont have access to internet so I cant issue this : "sudo apt-get install linux-headers-386 build-essential" is it alright if I download these in WindowsXP and install them with package manager?

Thank You!
Fahd

---

### Post by thorosius on 2007-02-03
I have tried your indicated steps and the driver successfully installed. "Intel537" in "lsmod" output. But wvdial indicates "No dial Tone" please look at the output below.

**************************************************************************
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

**************************************************************************
WVDIAL.CONF CONTENTS
**************************************************************************
[Dialer Defaults]
Modem = /dev/modem
Baud = 57600
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=84
Init3 = ATM1L3
Carrier Check = no
Phone = 13198765
Username = cstb
Password = cstb

**************************************************************************
WVDIAL OUTPUT
**************************************************************************
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=84
AT+GCI=84
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
NO DIALTONE
--> No dial tone.
--> Disconnecting at Sat Feb  3 15:14:26 2007

I must add that when wvdial starts I hear a click sound from my modem (its buzzer I think) but when wvdial says its dialing I picked the phone but there was no dialing going on just the dial tone.

---

### Post by chuckman78 on 2007-02-03
Fahd,

Right now I can´t help because I am leaving on a business trip and wont be at computer until next Monday 12. Sorry for the incovenience. Meanwhile you could check at [http://linmodems.org]("http://linmodems.org"), and join their mailing list for help.

Regards,

Carlos.

P.S: Maybe someone else could help Fahd in the meanwhile? Thanks in advance.

---

### Post by thorosius on 2007-02-03
No problem I will wait. Can anyone else please help?

---

### Post by directcharitycontribution on 2007-02-05
driver re-compilation had been the next step considered, with error risk and traceability issues entailed,  but now system status has moved to post-driver installation stage following your suggestion. 

triple beans for that! do you need any money for that good work?

now with gnome ppp system dials sometimes but no follow through when password sends. the sometimes means as i change phone numbers/userpass it sometimes says no modem. if i quit and start again it manages dialout dialog but not completing connecting stage. this is the dialog [http://ubuntuforums.org/showthread.php?t=244824&highlight=modem+initialized+please+enter+password]("http://ubuntuforums.org/showthread.php?t=244824&highlight=modem+initialized+please+enter+password")

i am now looking for the solution to that next obstacle. think i have seen it spread around the forums before.

maybe we shall come through the whole connection problem together!

now, what are the names of the problems?

---

### Post by thorosius on 2007-02-16
Please Please Please can anyone help?

---

### Post by sayal on 2007-02-20
Hi!
        I am stuck. Please get me out of this trouble.
When I try to extract modem drivers using this command
tar -zxvf Intel-537EP-2.70.95.0-suse9.3.tgz
it gives me error.Then I extract drivers manually. But When I perform this command
make 537
it says unable to build drivers. Please help me. I am a new user of linux.

---

### Post by chuckman78 on 2007-02-22
Thorosius,

Have you tried this? Add this line to your **wvdial.conf** file:
[B]
Abort on No Dialtone = no[/B]


Hope this helps.

Regards,

Carlos.

---

### Post by chuckman78 on 2007-02-22
> **sayal said:**
> Hi!
        I am stuck. Please get me out of this trouble.
When I try to extract modem drivers using this command
tar -zxvf Intel-537EP-2.70.95.0-suse9.3.tgz
it gives me error.

Hi sayal.

Please could you elaborate on which is the error you are getting?

Also, what is your kernel? (Use the command ```
**uname -r**
``` to find out that).

I see you are using a fairly old driver. You should check through the thread and find out the evolution of it to a newer one. In fact, up to today the newest driver from Mr. Vouters is:

[http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_19_01_2007.tgz]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/intel-537EP_secure-2.60.80.1_19_01_2007.tgz")



> **sayal said:**
> Then I extract drivers manually. But When I perform this command
make 537
it says unable to build drivers. Please help me. I am a new user of linux.

Sayal,  in order to help you we need as much information as possible. Did you do this steps (inside the directory of the extracted files):

1.- ```
sudo make clean
```

2.- ```
export MODEM_TYPE=537EP       *-assuming you have a 537EP modem-*
```

3.- ```
sudo make 537
```

4.- ```
sudo make install
```

Please check all these steps and the thread. I know it is a little bit time consuming but I think you could get the most from that. I hope I can get the time to update it in to a new decently layered HOWTO for easier reading but it is in my never ending todo list!

Regards,

Carlos.

---

### Post by thorosius on 2007-03-03
I apologise for not posting sooner. I was away. 

chuckman78 >> Yes I have tried it. And with no results.

---

### Post by thorosius on 2007-03-10
I have installed genome-ppp and it has a button in its settings to detect my modem. And when I click it, it doesnt detect my modem, although the driver module is loaded. What is the problem? Any ideas?

---

### Post by Wake Rider on 2007-03-20
I got up to the code make 537 when it came up with a whole pile of errors and said failed to build driver! HELP!!:confused: :(

---

### Post by thorosius on 2007-03-20
Please make sure you are entering the correct modem type of your modem in the command 
"export MODEM_TYPE = <modem type>". Modem type can be determined from scanmodem tool.

---

### Post by m10 on 2007-05-09
is there any chance at all that i get the modem somehow working on Feisty?

---

### Post by chuckman78 on 2007-05-09
Sure, you will. Mr. Vouters is working on an updated version of the driver. It wil be available soon, I will post info about it as soon as posible.

Regards,

Carlos.

---

### Post by m10 on 2007-05-11
i read somewhere that it is possible by appling some *.patch ...
anyone heared about it?

---

### Post by chuckman78 on 2007-05-11
Yes, there is been a discussion on that matter at the mailing list on [http://linmodems.org]("http://linmodems.org"). I have gotten my hands, throught Marvin Stodolsky one of the list's moderators, on a working driver, I am waiting to get a reply from Marvin for getting it available to the public.

Regards,

Carlos.

---

### Post by chuckman78 on 2007-05-11
This is a temporary link to a working driver for Intel-537 modems on Ubuntu Feisty Fawn:

[http://www.marcano-balza.com/intel-537/feisty/Intel-537.tar.gz]("http://www.marcano-balza.com/intel-537/feisty/Intel-537.tar.gz")

It will be available soon on its "official" site from Mr. Vouters.

Regards,

Carlos.

---

### Post by m10 on 2007-05-12
Hi
Do I need to do:
```
 export MODEM_TYPE=<your modem type>
```
on this new driver?

P.S. on Feisty the headers are installed by default, aren't they?

---

### Post by m10 on 2007-05-12
Hi,
I'm coming to the conclusion that I'm either to stupid to get this f****** driver compiled or it just doesn't work.

here is the output in the terminal there are quite some warnings but in the end there is written done so what does it mean should it work?I'm dubious:

```
mio@mydesk:~$ sudo su
Password:
root@mydesk:/home/mio# cd Intel-537
root@mydesk:/home/mio/Intel-537# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/mio/Intel-537/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/mio/Intel-537/coredrv'
rm -f *.o *.ko
root@mydesk:/home/mio/Intel-537# make 537
   Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: [B]No such file or directory
   autoconf.h matches running kernel[/B]
diff: /boot/vmlinuz.version.h: [B]No such file or directory
   version.h matches running kernel[/B]
2.6.20-15-generic
make[1]: Entering directory `/home/mio/Intel-537/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/mio/Intel-537/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/mio/Intel-537/coredrv/coredrv.o
/home/mio/Intel-537/coredrv/coredrv.c: In function â&#8364;&#732;softcore_init_structâ&#8364;&#8482;:
/home/mio/Intel-537/coredrv/coredrv.c:341:** warning: assignment from incompatible pointer type**
/home/mio/Intel-537/coredrv/coredrv.c: In function â&#8364;&#732;openâ&#8364;&#8482;:
/home/mio/Intel-537/coredrv/coredrv.c:397: **warning: passing argument 2 of â&#8364;&#732;request_irqâ&#8364;&#8482; from incompatible pointer type**
/home/mio/Intel-537/coredrv/coredrv.c:409:** warning: â&#8364;&#732;pm_registerâ&#8364;&#8482; is deprecated (declared at include/linux/pm_legacy.h:15)**
/home/mio/Intel-537/coredrv/coredrv.c: At top level:
/home/mio/Intel-537/coredrv/coredrv.c:770: **warning: initialization from incompatible pointer type**
/home/mio/Intel-537/coredrv/coredrv.c:771:** warning: initialization from incompatible pointer type**
/home/mio/Intel-537/coredrv/coredrv.c:872:** warning: initialization makes integer from pointer without a cast**
  CC [M]  /home/mio/Intel-537/coredrv/clmmain.o
  CC [M]  /home/mio/Intel-537/coredrv/rts.o
/home/mio/Intel-537/coredrv/rts.c:80:** warning: initialization from incompatible pointer type**
  CC [M]  /home/mio/Intel-537/coredrv/task.o
  CC [M]  /home/mio/Intel-537/coredrv/uart.o
  CC [M]  /home/mio/Intel-537/coredrv/wwh_dflt.o
  CC [M]  /home/mio/Intel-537/coredrv/locks.o
  CC [M]  /home/mio/Intel-537/coredrv/softserial_io.o
  CC [M]  /home/mio/Intel-537/coredrv/softserial_ioctl.o
  CC [M]  /home/mio/Intel-537/coredrv/softserial.o
/home/mio/Intel-537/coredrv/softserial.c: In function â&#8364;&#732;softserial_register_ttyâ&#8364;&#8482;:
/home/mio/Intel-537/coredrv/softserial.c:127: **warning: assignment from incompatible pointer type**
/home/mio/Intel-537/coredrv/softserial.c:128: **warning: assignment from incompatible pointer type**
/home/mio/Intel-537/coredrv/softserial.c:151: **warning: assignment from incompatible pointer type**
/home/mio/Intel-537/coredrv/softserial.c: At top level:
/home/mio/Intel-537/coredrv/softserial.c:190:** warning: initialization from incompatible pointer type**
  CC [M]  /home/mio/Intel-537/coredrv/afedsp_int.o
/home/mio/Intel-537/coredrv/afedsp_int.c:39: **warning: initialization makes integer from pointer without a cast**
/home/mio/Intel-537/coredrv/afedsp_int.c:48: **warning: function declaration isnâ&#8364;&#8482;t a prototype**
/home/mio/Intel-537/coredrv/afedsp_int.c:60: **warning: initialization from incompatible pointer type**
/home/mio/Intel-537/coredrv/afedsp_int.c:61: **warning: initialization from incompatible pointer type**
/home/mio/Intel-537/coredrv/afedsp_int.c:65: **warning: function declaration isnâ&#8364;&#8482;t a prototype**
/home/mio/Intel-537/coredrv/afedsp_int.c:446:** warning: initialization from incompatible pointer type**
  LD [M]  /home/mio/Intel-537/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/mio/Intel-537/coredrv/.537core.lib.cmd for /home/mio/Intel-537/coredrv/537core.lib
  CC      /home/mio/Intel-537/coredrv/Intel537.mod.o
  LD [M]  /home/mio/Intel-537/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/mio/Intel-537/coredrv'
root@mydesk:/home/mio/Intel-537# make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.20-15-generic
chmod: cannot access `usrsound': [B]No such file or directory
installing hamregistry, used for persistant storage[/B]
installing usrsound, a soft buzzer
install: cannot stat `usrsound': **No such file or directory**
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities
**done**
```
i did reboot and there was a notification of restricted drivers for intel537 so something did work.. but it won't connect...
i looked in the readme in the source of the driver and there was written:

> ATTENTION:  if the driver compiles but the script just wont work for you.
   Here are the bare minimum steps to get your modem to work.

   0.  log in as root.
   1.  insmod -f Intel537.o    (Intel537.ko for kernel 2.6)
   2. you can start "hamregistry &" at this point if you wish.
   3.  rm /dev/537
   4.  mknod /dev/537 c 240 1   (note "240" is the default, if it does not 
       work see what /proc/devices says 537's major number is)
   5.  ln -s /dev/537 /dev/modem
   6.  start a comm application like minicom and use the modem.
   7.  see section 3 (International Users) for info on setting the correct 
       country settings.

i did it (note: i didn't do point 7 ...) but still nothing. I went back to win downloaded gnome-ppp (maybe i had have done it before)
back to feisty i installed it played a bit with the options but:
> --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT7020187187
--> Waiting for carrier.
ATM1L1DT7020187187
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM1L1DT7020187187
--> Waiting for carrier.
** Ascend TNT Terminal Server **
System Password: 
System Password: 
System Password: 
**NO CARRIER**
--> No Carrier!  Trying again.

i'm slowly going depressed and i don't wonna use windoze any more!!but without connection...:( :(

P.S. i did not install the linux headers because it seems that they are installed by default, at least they are marked green(in synaptic)... so I just installed the build-essentials..

---

### Post by chuckman78 on 2007-05-13
m10,

   The driver seems to be installed. Coud you pleas post your **wvdial.conf** file?

Regards,

Carlos.

---

### Post by m10 on 2007-05-14
oh, i did never looked at that 
here is it:
```

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes   [COLOR="Silver"]<<what's this for?[/COLOR]

```

i did look at the ubuntu help and changed it like this:

```

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
ISDN = 0
Modem Type = Analog Modem
Phone = 7020187187
Username = telecom
Password = telecom
Carrier Check = no
Abort on No Dialtone = off  [COLOR="SeaGreen"]<<< afterwards i changed this to "no" but still nothing[/COLOR]

```

but (i'm shure i managed to do something wrong) on dial with gnome-ppp (should i use directly wvdial?):
```

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  [COLOR="Silver"]<<<< what's this?[/COLOR]
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0                       [COLOR="Silver"]<<<<[/COLOR]
OK
--> Modem initialized.
--> Sending: ATM1L3DT7020187187
--> Waiting for carrier.
ATM1L3DT7020187187
CONNECT 40000       [COLOR="Silver"]   <<<< that looks good[/COLOR]
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)  [COLOR="Silver"]  <<<< how many times is it request that pw and what's about login anyway?[/COLOR]
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon May 14 15:45:02 2007
--> Pid of pppd: 5812
--> Using interface ppp0
--> Disconnecting at Mon May 14 15:45:35 2007
--> The PPP daemon has died: Loopback detected (exit code = 17)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 17)

```
it seems all a bit better (but my stupid comments) but still no connection......
help!

Mio

P.S. i did a clean ubuntu install(again) and recompiled the driver (got the same warnings) before playing around with wvdial.conf and posting my results here..

edit{i read throu the posts in this thread and saw that you ( chucman78 ) did mention before how to set wvdial.conf i did everythink like you sayed but no luck :(}

---

### Post by chuckman78 on 2007-05-15
Hi, m10.

  Right now I can´t answer all your question, but I can suggest something:

 0.-  Open a terminal box.

1.- Type:

```
sudo gedit /etc/wvdial.conf
```

2.- A window with the **wvdial.conf** file will open. Replace its content with this:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=B5
Init3 = ATM1L3
Carrier Check = no
FlowControl = CRTSCTS
Phone = ***<your ISP phone number>***
Username = ***<your username>***
Password = ***<your password>***
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

3.- Save and close the file.

4.- Type in the terminal:

```
sudo wvdial
```

5.- Keep the terminal window open and let´s expect the connection takes place.

Hope this helps, please report back.

Regards,

Carlos.

P.S1.: Some lines of this configuration are suposing you live in USA. Please report back if this is not true.  (Line ***Init2 = AT+GCI=B5*** would be ***Init2 = AT+GCI=BB*** as I live in Venezuela).

P.S2.: Sometimes it helps to change the line ***Carrier Check = no*** to ***Carrier Check = yes***.

P.S3.: If you get a NO DIAL TONE message, you could add this line: ***Init4 = ATX3***.

---

### Post by m10 on 2007-05-15
i live in italy so should it be** Init2 = AT+GCI=59**, shouldn't it?

---

### Post by m10 on 2007-05-15
sigh 8-[  ](*,)  it id not work:
first try:
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=59
Init3 = ATM1L3
Carrier Check = no
FlowControl = CRTSCTS
Phone = 7020187187
Username = telecom
Password = telecom
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

gave me this:
```
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
NO CARRIER
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 15:45:44 2007
--> Pid of pppd: 6776
--> Using interface ppp0
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> Disconnecting at Tue May 15 15:46:44 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 37333
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 15:47:55 2007
--> Pid of pppd: 6833
--> Using interface ppp0
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> Disconnecting at Tue May 15 15:49:29 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 15:52:03 2007
--> Pid of pppd: 6934
--> Using interface ppp0
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> Disconnecting at Tue May 15 15:53:15 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
NO DIALTONE
--> No dial tone.  Trying again in 5 seconds.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 16:00:45 2007
--> Pid of pppd: 7147
--> Using interface ppp0
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> pppd: 8 [06][08]
--> Disconnecting at Tue May 15 16:01:16 2007
--> The PPP daemon has died: Loopback detected (exit code = 17)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 17)

```

second:
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=59
Init3 = ATM1L3
Init4 = ATX3
Carrier Check = no
FlowControl = CRTSCTS
Phone = 7020187187
Username = telecom
Password = telecom
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

gave me this:
```
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Sending: ATX3
ATX3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 40000
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 15:39:24 2007
--> Pid of pppd: 6614
--> Using interface ppp0
--> pppd: 8 [06][08]X [06][08]
--> pppd: 8 [06][08]X [06][08]
--> pppd: 8 [06][08]X [06][08]
--> pppd: 8 [06][08]X [06][08]
--> Disconnecting at Tue May 15 15:39:58 2007
--> The PPP daemon has died: Loopback detected (exit code = 17)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 17)

```

third and last:
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=59
Init3 = ATM1L3
Init4 = ATX3
Carrier Check = yes
FlowControl = CRTSCTS
Phone = 7020187187
Username = telecom
Password = telecom
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

this:
```

--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Sending: ATX3
ATX3
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 38666
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT7020187187
--> Waiting for carrier.
** Ascend TNT Terminal Server **
System Password: 
System Password: 
System Password: 
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
DELAYED CALL
--> Timed out while dialing.  Trying again.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 44000
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT7020187187
--> Waiting for carrier.
** Ascend TNT Terminal Server **
System Password: 
System Password: 
System Password: 
NO CARRIER

```

i hope you can find any other possible solution....
Mio


edi{should i post /var/log/messages?  it's quite huge}

---

### Post by chuckman78 on 2007-05-15
Hi, m10.

   I am running out of options here. Try this: Use the second wvdial.conf configuration you last posted and add this line to it:

```
Init5 = AT+MS=V90
```

If this does not work I would recommend to you to take a look to this site:

[http://linmodems.org]("http://linmodems.org")

They run the best mailing list regarding winmodems on linux. You should suscribe to the list and run the tool they use (scanModem) and send the results to them. Additionally you should attach all the information you posted in your last post, including the information of your location. 

Regards,

Carlos.

---

### Post by m10 on 2007-05-15
again, no luck..

wvdial.conf:
```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=59
Init3 = ATM1L3
Init4 = ATX3
Init5 = AT+MS=V90
Carrier Check = no
FlowControl = CRTSCTS
Phone = 7020187187
Username = telecom
Password = telecom
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```


on dial:
```
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=59
AT+GCI=59
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Sending: ATX3
ATX3
OK
--> Sending: AT+MS=V90
AT+MS=V90
OK
--> Modem initialized.
--> Sending: ATDT7020187187
--> Waiting for carrier.
ATDT7020187187
CONNECT 40000
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
System Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Tue May 15 22:23:14 2007
--> Pid of pppd: 5521
--> Using interface ppp0
--> pppd: H [06][08]h [06][08]ï¿½ [06][08]ï¿½ [06][08]
--> pppd: H [06][08]h [06][08]ï¿½ [06][08]ï¿½ [06][08]
--> pppd: H [06][08]h [06][08]ï¿½ [06][08]ï¿½ [06][08]
--> pppd: H [06][08]h [06][08]ï¿½ [06][08]ï¿½ [06][08]
--> pppd: H [06][08]h [06][08]ï¿½ [06][08]ï¿½ [06][08]
--> Disconnecting at Tue May 15 22:25:29 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

```


thank you alot for your help and effort anyway
i'll try now on linmodems.org but i've not much hope 
i'm considering to get another modem (maybe a 536ep) and trying my luck with it
thx again

---

### Post by chuckman78 on 2007-05-16
Hi m10.

Let's try one last thing:

  Add to **wvdial.conf** the following line:

```
Stupid Mode = yes
```

 Then execute **sudo wvdial** as usual.

Please, report back.

Regards,

Carlos.

P.S: I don't think you have to switch to another modem yet. I own an Intel 537EP based modem and it has worked in all versions of Ubuntu, even on Feisty Fawn.

---

### Post by m10 on 2007-05-16
hi!
i did just tried that before reading your post (i did read it in some ScanModem file) and it worked:biggrin: :mrgreen: :D ;) :popcorn: 
but we could have thinked of it befor, couldn't we?
anyway i'm happy that it finally worked and that it wasn't anything worse
i thank you so much! Grazie mille (a thousand of thanks)!
Mio
P.S. is it normal that it's so much sloooower compared to windows?(it has a download rate between 1 and 3 Kb/s while under win it's between 5 and 8 Kb/s)
P.P.S. Thx again

---

### Post by chuckman78 on 2007-05-17
Congratulations!

  I believe we could have got this working before but I just didn't remember it. This lines refers to an "issue" during the data exchange between your modem and your ISP modem, but we were trying to make an effect just on your modem.

  I also have a slower connection on linux than windows, I think this could be somehow improved tweaking wvdial.conf. If you find out any improvement on this regard please report back.

Regards,

Carlos.

P.S1.: ¡Felicitaciones! (that is "Congratulations" in spanish).

P.S2.: Please share your recently gained knowledge on this topic with any other in the need of it, we need reinforces!

---

### Post by chuckman78 on 2007-05-18
This is the place where any Feisty Fawn user on kernel 2.6.20 can find the driver for the Intel 537 chipset:

 [http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz]("http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz")


Regards,

Carlos.

---

### Post by m10 on 2007-05-23
is there any documentation abaut (only) wvdial?
i couldn't find any..

---

### Post by chuckman78 on 2007-05-23
Hi m10.

  Besides of the man page for wvdial (which you can acces by typing **man wvdial** in a terminal box), you can find more info on this link:

[http://www.freeos.com/articles/2452/]("http://www.freeos.com/articles/2452/")


Regards,

Carlos.

---

### Post by markomg on 2007-05-24
I have a filling that i did everything right but i am lost. Yesterday i instaled linux for the first time so i am absolute noob.
First problem is modem.
Folowed the instructions from [https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)  and impression is that it should work.
 Think that all steps went ok, no errors (that i notice) and when i tipe sudo pppconfig  i get this 4 options (new connection, delete connection, edit conn. and exit) but i have no idea is the modem working, how to set the parameters there and how to connect (command or what)

Ubuntu 7.04

---

### Post by chuckman78 on 2007-05-25
Hi.

Are you completely sure you have an **Intel 536EP** modem?

I would recommend to you (and to anyone starting on linux and trying to get a *winmodem* working on it) to go to:

[http://linmodems.org]("http://linmodems.org")


There you will have access to a very good tool: **scanModem**. It will help you correctly identify your modem and mght suggest the proper configuration for it.

Next step will be to suscribe to their mailing list and post the result from scanModem.

On another topic, you should use **wvdial** for setting up and running your dialing account. It is a way better tool than others.

Please report back.

Regards,

Carlos.

---

### Post by JGT on 2007-05-29
Hi

Hoe you can help. I'm a complete novice to Linux - this is my first post. I installed (dual-boot with XP) Feisty Fawn last week and, after reading the thread, have installed 6.06 over the top of it in order to get my winmodem to work.

I have no experience using a terminal type input other than very basic MS-DOS in about 1993. 

Alternating between Windows XP and Ubuntu to search for answers is getting to be exhausting.

Basically, I think I'm following the instructions but hit a wall using the "make" command. I will post my pasted terminal input here. I apologise for its presentation and my laboured navigation.

john@john-desktop:~$ ls
Desktop  Examples
john@john-desktop:~$ cd Desktop
john@john-desktop:~/Desktop$ $ sudo apt-get install gcc-4.0
bash: $: command not found
john@john-desktop:~/Desktop$ cd ..
john@john-desktop:~$ sudo apt-get install gcc-4.0
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  gcc-3.4: Depends: binutils (>= 2.16.1-2ubuntu3) but it is not going to be inst alled
  gcc-4.0: Depends: cpp-4.0 (= 4.0.3-1ubuntu5) but it is not going to be install ed
           Depends: binutils (>= 2.16.1cvs20051214) but it is not going to be in stalled
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a s olution).
john@john-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
john@john-desktop:~$ sudo su
root@john-desktop:/home/john# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  binutils cpp-3.4 gcc-3.4 gcc-3.4-base
Suggested packages:
  binutils-doc gcc-3.4-doc libc6-dev-amd64 lib64gcc1
Recommended packages:
  libc6-dev
The following NEW packages will be installed
  binutils
The following packages will be upgraded:
  cpp-3.4 gcc-3.4 gcc-3.4-base
3 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3752kB of archives.
After unpacking 7131kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 69593 files and directories currently installed.)
Preparing to replace gcc-3.4 3.4.4-6ubuntu8 (using .../gcc-3.4_3.4.6-1ubuntu2_i386.deb) ...
Unpacking replacement gcc-3.4 ...
Preparing to replace cpp-3.4 3.4.4-6ubuntu8 (using .../cpp-3.4_3.4.6-1ubuntu2_i386.deb) ...
Unpacking replacement cpp-3.4 ...
Preparing to replace gcc-3.4-base 3.4.4-6ubuntu8 (using .../gcc-3.4-base_3.4.6-1ubuntu2_i386.deb) ...
Unpacking replacement gcc-3.4-base ...
Selecting previously deselected package binutils.
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-1ubuntu2) ...
Setting up cpp-3.4 (3.4.6-1ubuntu2) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2) ...

Setting up gcc-3.4 (3.4.6-1ubuntu2) ...
root@john-desktop:/home/john# ls
Desktop  Examples
root@john-desktop:/home/john# cd desktop
bash: cd: desktop: No such file or directory
root@john-desktop:/home/john# cd Desktop
root@john-desktop:/home/john/Desktop# ls
2.6.15-23-386                    gcc-3.4_3.4.4-6ubuntu8_i386.deb       intel.txt
cpp-3.4_3.4.4-6ubuntu8_i386.deb  gcc-3.4-base_3.4.4-6ubuntu8_i386.deb  linux.txt
desperate.txt                    Intel-537EP-2.70.95.0-suse9.3.tgz
root@john-desktop:/home/john/Desktop# cd 2.6.15-23-386
root@john-desktop:/home/john/Desktop/2.6.15-23-386# make clean
bash: make: command not found
root@john-desktop:/home/john/Desktop/2.6.15-23-386# clean
bash: clean: command not found
root@john-desktop:/home/john/Desktop/2.6.15-23-386# cd ..
root@john-desktop:/home/john/Desktop# cd ..
root@john-desktop:/home/john# cd ..
root@john-desktop:/home# cd ..
root@john-desktop:/#  sudo apt-get install gcc-4.0
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp-4.0
Suggested packages:
  gcc-4.0-locales gcc-4.0-doc libc6-dev-amd64 lib64gcc1
Recommended packages:
  libc6-dev libmudflap0-dev
The following NEW packages will be installed
  cpp-4.0 gcc-4.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2499kB of archives.
After unpacking 5947kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package cpp-4.0.
(Reading database ... 69680 files and directories currently installed.)
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
root@john-desktop:/# ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
root@john-desktop:/# cd root
root@john-desktop:~# ls
root@john-desktop:~# ls
root@john-desktop:~# cd ..
root@john-desktop:/# cd home
root@john-desktop:/home# cd Desktop
bash: cd: Desktop: No such file or directory
root@john-desktop:/home# ls
john
root@john-desktop:/home# cd john
root@john-desktop:/home/john# cd ..
root@john-desktop:/home# ls
john
root@john-desktop:/home# cd john
root@john-desktop:/home/john# ls
Desktop  Examples
root@john-desktop:/home/john# cd Desktop
root@john-desktop:/home/john/Desktop# ls
2.6.15-23-386                    gcc-3.4_3.4.4-6ubuntu8_i386.deb       intel.txt
cpp-3.4_3.4.4-6ubuntu8_i386.deb  gcc-3.4-base_3.4.4-6ubuntu8_i386.deb  linux.txt
desperate.txt                    Intel-537EP-2.70.95.0-suse9.3.tgz
root@john-desktop:/home/john/Desktop# cd 2.6.15-23-386
root@john-desktop:/home/john/Desktop/2.6.15-23-386# ls
537_boot  537_inst  config_check  coredrv  hamregistry  license.txt  makefile  readme.txt
root@john-desktop:/home/john/Desktop/2.6.15-23-386# make clean
bash: make: command not found
root@john-desktop:/home/john/Desktop/2.6.15-23-386# ls
537_boot  537_inst  config_check  coredrv  hamregistry  license.txt  makefile  readme.txt
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo su
root@john-desktop:/home/john/Desktop/2.6.15-23-386# make clean
bash: make: command not found
root@john-desktop:/home/john/Desktop/2.6.15-23-386#


Why can't I compile? Can anyone help?

(Also, do I need to carry out the earlier steps again when I boot back into Ubuntu - or is it already "done"?)

Apologies again - I'm usually fairly self-sufficient but I think I'm beaten!

Cheers

John

---

### Post by JGT on 2007-05-30
Been trying various combos of earlier methods.

I think I might give up with Ubuntu. Are there any other distros that have cracked this problem? One reason I chose Ubuntu was for its automatic detection and migration of internet settings! Someone must have cracked this - any suggestions?

John

---

### Post by chuckman78 on 2007-05-30
John:

   Sorry for the delay on answering. Please try this:


0.- Download this driver for your modem (I am assuming you have an INTEL 537EP based modem, it could be other, more on this later).

[http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz]("http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz")

1.- In a terminal box type:

```
sudo apt-get install build-essential
```

2.- Then get to where you copied and extracted the driver downloaded in step 0. Type:

```
sudo make clean
```

   Then:

```
export MODEM_TYPE=537EP
```

   Then:
```

sudo make 537
```

   Then:

```
sudo make install
```

  Please report back.

Regards, 

Carlos.

P.S:  I would recommend in any case that you visiti this site:

[http://linmodems.org]("http://linmodems.org")

They are very competent in helping out with these issues.

---

### Post by JGT on 2007-05-30
Hi  Many thanks for your interest. I made a bit of progress (I think) with your help, but I'm not quite there. Previous I got stuck with the "make" command.

I'm pretty sure I've got a 537EP, as Windows reports my hardware profile as "Intel(R) 537EP V9x DFV PCI Modem". It's a completely "off-the-shelf" Dell 3100 Dimension, which seemed to be Dell's low-to-medium spec standard desktop model in the UK last year. Unfortunately, due to geography, broadband is not an option for me.


```
john@john-desktop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp dpkg-dev g++ g++-4.0 gcc libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  cpp-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf automake1.9 libtool flex bison gcc-doc
  glibc-doc libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed
  build-essential cpp dpkg-dev g++ g++-4.0 gcc libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8096kB of archives.
After unpacking 34.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package linux-kernel-headers.
(Reading database ... 70229 files and directories currently installed.)
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu6) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
```

For some reason I couldn't seem to unpack, but might just be an oversight on my part.

```
john@john-desktop:~$ tar -zxvf Intel-537EP-2.70.95.0-for-2.6.20.tar.gz
tar: Intel-537EP-2.70.95.0-for-2.6.20.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
john@john-desktop:~$ tar -zxvf Intel-537EP-2.70.95.0-for-2.6.20.tar.gz
tar: Intel-537EP-2.70.95.0-for-2.6.20.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

At this point I unpacked the driver by using the GUI rather than the terminal! I renamed its directory "2.6.15-23-386" following the earlier process. Not sure it this was necessary, but couldn't see any harm in it. So to continue...

```
root@john-desktop:/home/john# cd
root@john-desktop:~# ls
root@john-desktop:~# ls
root@john-desktop:~# ls
root@john-desktop:~# cd -
/home/john
root@john-desktop:/home/john# ls
Desktop  Examples
root@john-desktop:/home/john# cd Desktop
root@john-desktop:/home/john/Desktop# cd 2.6.15-23-386
```

Now, this is progress:

```
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make clean
cd coredrv; make clean
make[1]: Entering directory `/home/john/Desktop/2.6.15-23-386/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/john/Desktop/2.6.15-23-386/coredrv'
rm -f *.o *.ko
root@john-desktop:/home/john/Desktop/2.6.15-23-386# export MODEM_TYPE=537EP
```

But alas...

```
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make 537
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.15-23-386
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
install: cannot stat `Intel537.ko': No such file or directory
make: *** [install] Error 1
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make 537
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
root@john-desktop:/home/john/Desktop/2.6.15-23-386#
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.15-23-386
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
install: cannot stat `Intel537.ko': No such file or directory
make: *** [install] Error 1
```

From this point I'm just repeating the process.

```
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@john-desktop:/home/john/Desktop/2.6.15-23-386# dir
537_boot  537_inst  config_check  coredrv  hamregistry  license.txt  makefile  readme.txt
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make clean
cd coredrv; make clean
make[1]: Entering directory `/home/john/Desktop/2.6.15-23-386 original/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/john/Desktop/2.6.15-23-386 original/coredrv'
rm -f *.o *.ko
root@john-desktop:/home/john/Desktop/2.6.15-23-386# export MODEM_TYPE=537EP
root@john-desktop:/home/john/Desktop/2.6.15-23-386# sudo make 537
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
root@john-desktop:/home/john/Desktop/2.6.15-23-386#
```

Is this progress?

John

---

### Post by chuckman78 on 2007-05-30
Hi John.

I am not sure if you downloaded **this** driver:

[http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz]("http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz")

I am pretty sure you are trying to use the olde driver you previously had. Please download this one in your windows session and copy it on your Ubuntu desktop. Extract it using the graphical interface (it is the same) and get through the terminal box to your desktop and try from **STEP 2** from my previous post.

Regards,

Carlos.

---

### Post by JGT on 2007-05-30
Hiya Carlos

Nope, same thing happened. I rechecked - I even put a dummy Here_I_am file in there just to be sure I was in the right place using the new folder.

```
john@john-desktop:~/Desktop$ cd 2.6.15-23-386
john@john-desktop:~/Desktop/2.6.15-23-386$ ls
537_boot  537_inst  config_check  coredrv  hamregistry  Here_I_am.txt  license.txt  makefile  readme.txt  ReadPatched.txt
john@john-desktop:~/Desktop/2.6.15-23-386$ sudo make clean
Password:
cd coredrv; make clean
make[1]: Entering directory `/home/john/Desktop/2.6.15-23-386/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/john/Desktop/2.6.15-23-386/coredrv'
rm -f *.o *.ko
john@john-desktop:~/Desktop/2.6.15-23-386$ export MODEM_TYPE=537EP
john@john-desktop:~/Desktop/2.6.15-23-386$ sudo make 537
   Module precompile check
   Current running kernel is: 2.6.15-23-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source
make: *** [check] Error 1
john@john-desktop:~/Desktop/2.6.15-23-386$
```

I also rechecked the "2.6.15-23-386" number in case that was relevant.

Would this process work under another build of Ubuntu (I'm on 6.06)?

Bit of a vertical learning curve, this!

Cheers 

John

---

### Post by JGT on 2007-05-31
Hi Carlos

Please disregard my posts now. I'm bidding on a Plug 'n' Pray external modem from eBay, which I'll install under Windows. Hopefully a Linux re-install will carry my settings across.

Thanks for all your time

John

---

### Post by MRL on 2007-06-11
hi guys,

    I have an intel 537 modem

    I did whatever was written in the howto on the first page,, but when i typed

                             sudo bash /etc/init.d/537_boot start

  the following error occured

                            error loading /etc/init.d/2.6.15-26-386/Intel537.ko
                            ERROR: Module Intel537 is in use

    What should i do to get my modem working on Ubuntu............
    Please, please, please helpppppp....

---

### Post by zanoman on 2007-06-12
Hi,

I also have a problem with the last driver from Chuckman78 (Carlos) well from Philippe Vouters). (Man, [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) is highly unaccessible most of the time)
I want to use this card as fax.

I'm on Ubuntu 7.04 (2.6.20.16) and have a digium x100p card, which is tiger3xx (tiger jet) based on intel 537.
It WORKED on WinXP with Intel 537 drivers from tjnet.com, I still have the drivers somewhere.

Now, scanModem see my soundcard as modem (snd-intel8x0m) and also see the Tiger3xx card but cannot propose a driver for it. Didn't go through Windows to check it cause I totally dumped Windows :) from my computer and AFAIK a VM cannot access PCI cards.

After downloading [http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz](http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz)
I followed instructions and "make install" failed :

```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make 537
   Module precompile check
   Current running kernel is: 2.6.20-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-16-generic
make[1]: Entering directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:341: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘open’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:397: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:409: warning: ‘pm_register’ is deprecated (declared at include/linux/pm_legacy.h:15)
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:770: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:771: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:872: warning: initialization makes integer from pointer without a cast
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/clmmain.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.c:80: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/task.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/uart.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/wwh_dflt.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/locks.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_io.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_ioctl.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function ‘softserial_register_tty’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:127: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:128: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:151: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:190: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:39: warning: initialization makes integer from pointer without a cast
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:48: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:60: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:65: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:446: warning: initialization from incompatible pointer type
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/.537core.lib.cmd for /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/537core.lib
  CC      /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.mod.o
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make installrm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.20-16-generic
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.942972] Oops: 0000 [#1]

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.942974] SMP 

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943049] CPU:    0

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943050] EIP:    0060:[_proxy_pda+0/1024]    Tainted: PF     VLI

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943052] EFLAGS: 00010286   (2.6.20-16-generic #2)

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943059] EIP is at 0x0

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943062] eax: ffffffff   ebx: fc4bf880   ecx: 00000046   edx: ffffffff

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943065] esi: fc4bf880   edi: e2891560   ebp: d225fec8   esp: d225feac

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943068] ds: 007b   es: 007b   ss: 0068

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943072] Process modprobe (pid: 5792, ti=d225e000 task=f5ced560 task.ti=d225e000)
537_boot: line 48:  5792 Segmentation fault      ! ( modprobe -f $serial > /dev/null 2> /dev/null )
error loading Intel537
ERROR: Module Intel537 is in use
done
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# 
Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943074] Stack: fc1629f7 fc4251ef d225fec0 fc15f6f4 fc428d44 fc424ec1 fc4c5064 00000033 

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943082]        fc15f11f f89e9018 c014422d fc4bf8c8 c036522a fc4bf88c 00000012 fc4bf8c8 

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943089]        fc4bf88c fc4bf880 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943095] Call Trace:

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943097]  [<fc1629f7>] ham_proc_shutdown+0x11/0x35 [Intel537]

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943312]  [<fc15f6f4>] get_pci_info_537+0x72/0x3f7 [Intel537]

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943485]  [<fc15f11f>] core_cleanup_module+0x5/0x11 [Intel537]

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943637]  [<f89e9018>] init_serial+0x18/0x74 [Intel537]

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943788]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.943959]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.944015]  =======================

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.944017] Code:  Bad EIP value.

Message from syslogd@pm-desktop at Tue Jun 12 12:28:05 2007 ...
pm-desktop kernel: [14138.944021] EIP: [_proxy_pda+0/1024] 0x0 SS:ESP 0068:d225feac


```

There's no /dev/modem
Do you have an idea what went wrong?

---

### Post by chuckman78 on 2007-06-13
Hi MRL.

Sorry for the late reply. Please help us with this info:

0.- What is your current version of Ubuntu?

1.- Type in a terminal box the following command and give us the result:

```
uname -r
```


Regards,

Carlos.

---

### Post by chuckman78 on 2007-06-13
Hi, Phil, (zanoman):

As far as I can see you did everything ok, so I wolud consider redoing it again. Please follow this **exact** order:

0.- Go  to the directory where you extracted and previously compiled the driver and execute this:

```
sudo make uninstall
```

1.- Now execute:

```
sudo make clean
```

Then:

```
export MODEM_TYPE=**<Here goes your modem type>**
``` 

Please be sure about your modem type. In my case I use:

```
export MODEM_TYPE=***[B]537EP***[/B]
```

But there are others (like just **537**)

Then:

```
sudo make 537
```


Then:

```
sudo make install
```

Realize that it is just that, no need for touching hamstring and so.

Please report back.

Regards,

Carlos.

---

### Post by zanoman on 2007-06-13
Hi Carlos,

Thanks for your replies.
kernel is 2.6.20-16-generic

When I booted this morning, I found that it added Intel537 restricted driver in the list (with Nvidia) but /dev/modem didn't exist so it's useless.

Now, I followed what you said and got:
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make uninstall
Uninstalling on system V boot like only.
ERROR: Module Intel537 is in use

usrsound: no process killed

Uninstalling done.

```

then
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
rm -f *.o *.ko
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# export MODEM_TYPE=537

```

and
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make 537
   Module precompile check
   Current running kernel is: 2.6.20-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-16-generic
make[1]: Entering directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:341: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘open’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:397: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:409: warning: ‘pm_register’ is deprecated (declared at include/linux/pm_legacy.h:15)
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:770: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:771: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:872: warning: initialization makes integer from pointer without a cast
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/clmmain.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.c:80: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/task.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/uart.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/wwh_dflt.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/locks.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_io.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_ioctl.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function ‘softserial_register_tty’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:127: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:128: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:151: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:190: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:39: warning: initialization makes integer from pointer without a cast
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:48: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:60: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:65: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:446: warning: initialization from incompatible pointer type
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/.537core.lib.cmd for /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/537core.lib
  CC      /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.mod.o
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

```

but install fails, it never gives back prompt:
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make installrm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.20-16-generic
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities

```

Should I reboot after uninstall? Then try to reinstall?

---

### Post by chuckman78 on 2007-06-13
Hi, Phil.

By writing this:

> but install fails, it never gives back prompt:

do you mean **sudo make install** fails?

Is that why you execute? > make installrm -f /etc/hamregistry.bin

The response you get from this indicates the driver is getting installed. I assume you could make a symbolic link for the /dev/537 to /dev/modem.

You could try to connect using **/dev/537** or **/dev/intel537** or **/dev/Intel537**. What will you use to connect, **wvdial**? If this is the case just configure the **wvdial.conf** file to one of the options I mentioned (I can't recall the right one and I am not at my ubuntu box at this moment).

Please report back. 

Regards,

Carlos.

---

### Post by zanoman on 2007-06-13
> do you mean sudo make install fails?
It just hanged, never coming back to prompt.
with 0% use of CPU
only ctrl-c worked to come back to prompt.

> Is that why you execute?
Quote:
make installrm -f /etc/hamregistry.bin
I didn't added any instruction to procedure, it should be in makefile, I didn't check.

Well, meanwhile, I uninstalled it, rebooted and checked:
```
philmanzano@pm-desktop:~/Intel-537EP-2.70.95.0-for-2.6.20$ sudo su
Password:
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make uninstall
Uninstalling on system V boot like only.
ERROR: Module Intel537 does not exist in /proc/modules



usrsound: no process killed

Uninstalling done.

```
so 537 is really uninstalled
then
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make clean
cd coredrv; make clean
make[1]: Entering directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
rm -f *.o *.ko

```
sounds correct
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# export MODEM_TYPE=537

```
no message sent back
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make 537   Module precompile check
   Current running kernel is: 2.6.20-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-16-generic
make[1]: Entering directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:341: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function ‘open’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:397: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:409: warning: ‘pm_register’ is deprecated (declared at include/linux/pm_legacy.h:15)
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:770: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:771: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:872: warning: initialization makes integer from pointer without a cast
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/clmmain.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.c:80: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/task.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/uart.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/wwh_dflt.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/locks.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_io.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_ioctl.o
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function ‘softserial_register_tty’:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:127: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:128: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:151: warning: assignment from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: At top level:
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:190: warning: initialization from incompatible pointer type
  CC [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.o
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:39: warning: initialization makes integer from pointer without a cast
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:48: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:60: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:65: warning: function declaration isn’t a prototype
/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:446: warning: initialization from incompatible pointer type
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/.537core.lib.cmd for /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/537core.lib
  CC      /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.mod.o
  LD [M]  /home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'

```

Now to make it clear, here is my input:
```
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# make install
```

and the result:
```
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.20-16-generic
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965305] Oops: 0000 [#1]

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965306] SMP 

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965376] CPU:    0

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965377] EIP:    0060:[_proxy_pda+0/1024]    Tainted: PF     VLI

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965378] EFLAGS: 00010286   (2.6.20-16-generic #2)

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965386] EIP is at 0x0

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965389] eax: ffffffff   ebx: fc4bf880   ecx: 00000046   edx: ffffffff

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965393] esi: fc4bf880   edi: f7a08d60   ebp: f54b7ec8   esp: f54b7eac

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965396] ds: 007b   es: 007b   ss: 0068

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965399] Process modprobe (pid: 11421, ti=f54b6000 task=f6617560 task.ti=f54b6000)
537_boot: line 48: 11421 Segmentation fault      ! ( modprobe -f $serial > /dev/null 2> /dev/null )
error loading Intel537
ERROR: Module Intel537 is in use
done
root@pm-desktop:/home/philmanzano/Intel-537EP-2.70.95.0-for-2.6.20# 
Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965401] Stack: fc1629f7 fc4251ef f54b7ec0 fc15f6f4 fc428d44 fc424ec1 fc4c5064 00000033 

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965409]        fc15f11f f88c9018 c014422d fc4bf8c8 c036522a fc4bf88c 00000012 fc4bf8c8 

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965415]        fc4bf88c fc4bf880 00000000 00000000 00000000 00000000 00000000 00000000 

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965421] Call Trace:

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965423]  [<fc1629f7>] ham_proc_shutdown+0x11/0x35 [Intel537]

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965634]  [<fc15f6f4>] get_pci_info_537+0x72/0x3f7 [Intel537]

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965809]  [<fc15f11f>] core_cleanup_module+0x5/0x11 [Intel537]

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.965961]  [<f88c9018>] init_serial+0x18/0x74 [Intel537]

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.966111]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.966345]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.966422]  =======================

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.966424] Code:  Bad EIP value.

Message from syslogd@pm-desktop at Wed Jun 13 12:44:50 2007 ...
pm-desktop kernel: [  247.966427] EIP: [_proxy_pda+0/1024] 0x0 SS:ESP 0068:f54b7eac

```
and it hangs there

CTRL-C to exist

No dev/modem made in the process, neither /dev/537 or /dev/intel537 or /dev/Intel537.

Do you think this file works also for 537??, it says 537EP.
Readme or another file inside says it works for any 537, but I really wonder.
Or is it kernel version?

What's the instruction when driver IS installed to check which /dev it uses?

 I post this one and reboot, and check your reply.

Thanks

---

### Post by zanoman on 2007-06-13
I don't want to use this modem to connect to the net, just for fax (efax).

---

### Post by zanoman on 2007-06-13
just checked syslog:

```
Jun 13 12:44:50 pm-desktop kernel: [  247.950919] Intel537: no version for "struct_module" found: kernel tainted.
Jun 13 12:44:50 pm-desktop kernel: [  247.950930] Intel537: no version magic, tainting kernel.
Jun 13 12:44:50 pm-desktop kernel: [  247.965002] sound disabled
Jun 13 12:44:50 pm-desktop kernel: [  247.965266] Intel 537 card found
Jun 13 12:44:50 pm-desktop kernel: [  247.965270] This Intel(R) 537EP Modem driver won't install on Intel 537 card, please download the right driver
Jun 13 12:44:50 pm-desktop kernel: [  247.965294] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Jun 13 12:44:50 pm-desktop kernel: [  247.965298]  printing eip:
Jun 13 12:44:50 pm-desktop kernel: [  247.965300] 00000000
Jun 13 12:44:50 pm-desktop kernel: [  247.965301] *pde = 00000000
Jun 13 12:44:50 pm-desktop kernel: [  247.965305] Oops: 0000 [#1]
Jun 13 12:44:50 pm-desktop kernel: [  247.965306] SMP 
Jun 13 12:44:50 pm-desktop kernel: [  247.965309] Modules linked in: Intel537(PF) nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm l2cap bluetooth vmnet(P) vmmon(P) ppdev cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sony_acpi tc1100_wmi pcc_acpi dev_acpi battery video container dock sbs button i2c_ec asus_acpi backlight ac af_packet lp fuse snd_hda_intel snd_hda_codec snd_usb_audio snd_usb_lib snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_hwdep pcspkr snd_seq_midi snd_rawmidi parport_pc parport snd_seq_midi_event snd_seq snd_timer snd_seq_device xpad gspca usblp psmouse serio_raw videodev v4l2_common v4l1_compat k8temp snd hisax crc_ccitt isdn slhc soundcore snd_page_alloc nvidia(P) agpgart shpchp pci_hotplug i2c_nforce2 i2c_core tsdev ipv6 evdev usb_storage ext3 jbd mbcache sg usbhid hid sd_mod ide_cd cdrom generic amd74xx ata_generic libusual floppy ohci_hcd forcedeth sata_nv libata scsi_mod ehci_hcd usbcore thermal processor fan fbcon til
Jun 13 12:44:50 pm-desktop kernel: blit font bitblit softcursor vesafb capability commoncap
Jun 13 12:44:50 pm-desktop kernel: [  247.965376] CPU:    0
Jun 13 12:44:50 pm-desktop kernel: [  247.965377] EIP:    0060:[_proxy_pda+0/1024]    Tainted: PF     VLI
Jun 13 12:44:50 pm-desktop kernel: [  247.965378] EFLAGS: 00010286   (2.6.20-16-generic #2)
Jun 13 12:44:50 pm-desktop kernel: [  247.965386] EIP is at 0x0
Jun 13 12:44:50 pm-desktop kernel: [  247.965389] eax: ffffffff   ebx: fc4bf880   ecx: 00000046   edx: ffffffff
Jun 13 12:44:50 pm-desktop kernel: [  247.965393] esi: fc4bf880   edi: f7a08d60   ebp: f54b7ec8   esp: f54b7eac
Jun 13 12:44:50 pm-desktop kernel: [  247.965396] ds: 007b   es: 007b   ss: 0068
Jun 13 12:44:50 pm-desktop kernel: [  247.965399] Process modprobe (pid: 11421, ti=f54b6000 task=f6617560 task.ti=f54b6000)
Jun 13 12:44:50 pm-desktop kernel: [  247.965401] Stack: fc1629f7 fc4251ef f54b7ec0 fc15f6f4 fc428d44 fc424ec1 fc4c5064 00000033 
Jun 13 12:44:50 pm-desktop kernel: [  247.965409]        fc15f11f f88c9018 c014422d fc4bf8c8 c036522a fc4bf88c 00000012 fc4bf8c8 
Jun 13 12:44:50 pm-desktop kernel: [  247.965415]        fc4bf88c fc4bf880 00000000 00000000 00000000 00000000 00000000 00000000 
Jun 13 12:44:50 pm-desktop kernel: [  247.965421] Call Trace:
Jun 13 12:44:50 pm-desktop kernel: [  247.965423]  [<fc1629f7>] ham_proc_shutdown+0x11/0x35 [Intel537]
Jun 13 12:44:50 pm-desktop kernel: [  247.965634]  [<fc15f6f4>] get_pci_info_537+0x72/0x3f7 [Intel537]
Jun 13 12:44:50 pm-desktop kernel: [  247.965809]  [<fc15f11f>] core_cleanup_module+0x5/0x11 [Intel537]
Jun 13 12:44:50 pm-desktop kernel: [  247.965961]  [<f88c9018>] init_serial+0x18/0x74 [Intel537]
Jun 13 12:44:50 pm-desktop kernel: [  247.966111]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0
Jun 13 12:44:50 pm-desktop kernel: [  247.966345]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Jun 13 12:44:50 pm-desktop kernel: [  247.966422]  =======================
Jun 13 12:44:50 pm-desktop kernel: [  247.966424] Code:  Bad EIP value.
Jun 13 12:44:50 pm-desktop kernel: [  247.966427] EIP: [_proxy_pda+0/1024] 0x0 SS:ESP 0068:f54b7eac
```

so 2 things:
if 537 driver exist, I need it.

if it doesn't exist, I'll give 537EP a try :)
what's the risk?

---

### Post by zanoman on 2007-06-13
Now I uninstall and reinstall with logs in mind.

At "make uninstall", here's xsession log message:
```
modinfo: could not open /lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko: No such file or directory
```

I reboot and come back

Phil

---

### Post by chuckman78 on 2007-06-13
Hi Phil.

 I am replying now because I wont be able to do it maybe until tomorrow.  Your problem is getting out of my limited knowledge. You should consider signing in to the 

[http://linmodems.org/]("http://linmodems.org/")

mailing list. Use their recommended tool **scanModem** and post the result at the mailing list. There are a few very proficient guys there which might give us a light on the problem. Please report back.

Regards,

Carlos.

P.S: I think this driver wont work for faxing, but I might be wrong.

---

### Post by zanoman on 2007-06-13
here I am

rebooted and tried 537EP and got syslog:
```
Jun 13 13:28:27 pm-desktop kernel: [  258.579560] Intel537: no version for "struct_module" found: kernel tainted.
Jun 13 13:28:27 pm-desktop kernel: [  258.579571] Intel537: no version magic, tainting kernel.
Jun 13 13:28:27 pm-desktop kernel: [  258.597142] sound disabled
Jun 13 13:28:27 pm-desktop kernel: [  258.597413] Intel 537 card found
Jun 13 13:28:27 pm-desktop kernel: [  258.597418] This Intel(R) 537EP Modem driver won't install on Intel 537 card, please download the right driver
Jun 13 13:28:27 pm-desktop kernel: [  258.597442] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Jun 13 13:28:27 pm-desktop kernel: [  258.597446]  printing eip:
Jun 13 13:28:27 pm-desktop kernel: [  258.597447] 00000000
Jun 13 13:28:27 pm-desktop kernel: [  258.597449] *pde = 00000000
Jun 13 13:28:27 pm-desktop kernel: [  258.597452] Oops: 0000 [#1]
Jun 13 13:28:27 pm-desktop kernel: [  258.597454] SMP 
Jun 13 13:28:27 pm-desktop kernel: [  258.597456] Modules linked in: Intel537(PF) nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm l2cap bluetooth vmnet(P) vmmon(P) ppdev cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sony_acpi tc1100_wmi pcc_acpi dev_acpi battery video container dock sbs button i2c_ec asus_acpi backlight ac af_packet lp fuse snd_hda_intel snd_hda_codec ide_cd snd_seq_dummy snd_seq_oss snd_usb_audio snd_pcm_oss snd_mixer_oss cdrom gspca snd_pcm snd_usb_lib pcspkr videodev v4l2_common v4l1_compat parport_pc parport usbhid hid usblp snd_hwdep snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device xpad hisax crc_ccitt isdn psmouse serio_raw k8temp nvidia(P) snd soundcore snd_page_alloc slhc agpgart shpchp pci_hotplug i2c_nforce2 i2c_core ipv6 tsdev evdev ext3 jbd mbcache usb_storage sg sd_mod libusual amd74xx generic ata_generic floppy forcedeth sata_nv libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbcon til
Jun 13 13:28:27 pm-desktop kernel: blit font bitblit softcursor vesafb capability commoncap
Jun 13 13:28:27 pm-desktop kernel: [  258.597526] CPU:    0
Jun 13 13:28:27 pm-desktop kernel: [  258.597527] EIP:    0060:[_proxy_pda+0/1024]    Tainted: PF     VLI
Jun 13 13:28:27 pm-desktop kernel: [  258.597529] EFLAGS: 00010286   (2.6.20-16-generic #2)
Jun 13 13:28:27 pm-desktop kernel: [  258.597535] EIP is at 0x0
Jun 13 13:28:27 pm-desktop kernel: [  258.597538] eax: ffffffff   ebx: fc4bf880   ecx: 00000046   edx: ffffffff
Jun 13 13:28:27 pm-desktop kernel: [  258.597542] esi: fc4bf880   edi: f79e5560   ebp: f6259ec8   esp: f6259eac
Jun 13 13:28:27 pm-desktop kernel: [  258.597545] ds: 007b   es: 007b   ss: 0068
Jun 13 13:28:27 pm-desktop kernel: [  258.597548] Process modprobe (pid: 11627, ti=f6258000 task=f6a2c030 task.ti=f6258000)
Jun 13 13:28:27 pm-desktop kernel: [  258.597551] Stack: fc1629f7 fc4251ef f6259ec0 fc15f6f4 fc428d44 fc424ec1 fc4c5064 00000033 
Jun 13 13:28:27 pm-desktop kernel: [  258.597558]        fc15f11f f8c0d018 c014422d fc4bf8c8 c036522a fc4bf88c 00000012 fc4bf8c8 
Jun 13 13:28:27 pm-desktop kernel: [  258.597565]        fc4bf88c fc4bf880 00000000 00000000 00000000 00000000 00000000 00000000 
Jun 13 13:28:27 pm-desktop kernel: [  258.597571] Call Trace:
Jun 13 13:28:27 pm-desktop kernel: [  258.597573]  [<fc1629f7>] ham_proc_shutdown+0x11/0x35 [Intel537]
Jun 13 13:28:27 pm-desktop kernel: [  258.597778]  [<fc15f6f4>] get_pci_info_537+0x72/0x3f7 [Intel537]
Jun 13 13:28:27 pm-desktop kernel: [  258.597949]  [<fc15f11f>] core_cleanup_module+0x5/0x11 [Intel537]
Jun 13 13:28:27 pm-desktop kernel: [  258.598101]  [<f8c0d018>] init_serial+0x18/0x74 [Intel537]
Jun 13 13:28:27 pm-desktop kernel: [  258.598251]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0
Jun 13 13:28:27 pm-desktop kernel: [  258.598408]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Jun 13 13:28:27 pm-desktop kernel: [  258.598459]  =======================
Jun 13 13:28:27 pm-desktop kernel: [  258.598460] Code:  Bad EIP value.
Jun 13 13:28:27 pm-desktop kernel: [  258.598464] EIP: [_proxy_pda+0/1024] 0x0 SS:ESP 0068:f6259eac
```

So it founds the 537 card even if I say it's a 537EP. Well it leave one option:
Get the 537 driver for 2.6.20

When I visit technicon.il I don't see the file I used in Philippe's files index.
Any idea where to find this rare pearl??

---

### Post by zanoman on 2007-06-13
ok I'll switch to linmodems.org mailing list and ask Philippe for help.
:cry:
just for search engine tracking (other people with same problem in the future):
In Ubuntu, with GUI, to check vendor id:
go in system>preference>hardware information
scroll to PCI bridge (mine is MCP51)
it says Tiger Jet Tiger3xx Modem/ISDN
click "advanced" tab
last line is: pci.vendor_id int 57689 (0xe159)
and a few line above is: pci.product_id int 1 (0x1)

in [http://www.pcidatabase.com/search.php?vendor_search_str=tiger+jet&vendor_search=Search](http://www.pcidatabase.com/search.php?vendor_search_str=tiger+jet&vendor_search=Search) database when entering "tiger jet" as vendor [http://www.pcidatabase.com/vendor_details.php?id=1310](http://www.pcidatabase.com/vendor_details.php?id=1310) it says for Device 0x0001 (product_id is 0x1 which is equiv to 0x0001) it's a:
Ambient MD3200 A - Intel 537

vendor_id match
product_id match
this is it

I tried to find a linux driver but couldn't so far (but I found my windows drivers that make it worked as FAX, dial-up, and answering machine since it has phone and lines plugs).

BTW, thanks Carlos

scanmodem just found my NVidia soundcard as modem and couldn't guess who's "Tiger Jet", so it's useless I think, but will post to mailing list still.

---

### Post by zanoman on 2007-06-14
Good news for ubuntu 7.04 feisty fawn with tiger jet tiger3xx PCI modem and fax card (Intel 537, the old X100p card from Digium, NOT 537EP)

Thanks to Philippe Vouters it does the job!

Here is the procedure:
download Ubuntu driver from [http://vouters.dyndns.org:8080/Intel/](http://vouters.dyndns.org:8080/Intel/)

At this time, this specific file doesn't exist but [http://vouters.dyndns.org:8080/Intel/intel-537EP_secure-2.60.80.0_2007_06_14.tar.bz2](http://vouters.dyndns.org:8080/Intel/intel-537EP_secure-2.60.80.0_2007_06_14.tar.bz2) with a trick does the job, but I think that a new file will be written.

Here's the trick (due to gcc4.2 in ubuntu different from fedora!):
in expanded folder
as root, edit coredev/clmmain.c line 86 and remove (work_func_t) from
```
static DECLARE_WORK(clm_rx_task, (work_func_t)clm_rx_int);
```

then the casual procedure:

```
make clean

export MODEM_TYPE=537

make 537

make install
```

TADA! you should have /dev/modem present now.
read intel-readme.txt file for details and help for dial-up.

---

### Post by chuckman78 on 2007-06-14
Phil, thanks a lot for the info! This should be useful for others.

Regards,

Carlos.

---

### Post by zanoman on 2007-06-14
You're welcome.

Philippe helps me a lot to make it work.
Feel free to update your specific page.

---

### Post by chuckman78 on 2007-06-14
I have the idea of creating specific Howtos for different Ubuntu versions using this chipsets so it could be easier for users to find the right answer to their problem and not having to roll through all this long thread. I just can't find the time to do this. Any takers? :)

Regards,

Carlos.

---

### Post by Sepero on 2007-06-15
chuckman78, I'd like to help the community, but I don't care for "howto"s very much. If you wanna work with me, I'd like to make a 537 deb package for Feisty 7.04 (and possibly Dapper).

I've done this for the Intel 536ep modem, and I think it's nicer for the user to just be able to install&go. Let me know what ya think.
[http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)

---

### Post by jdogzilla on 2007-06-16
Hello, I followed the instructions for the latest driver and got the following problem:

starting module and utilities
FATAL: Error inserting Intel537 (/lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko): Operation not permitted
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules
done

Any suggestions?

---

### Post by JGT on 2007-06-19
Thanks for all your help earlier Carlos

I got my cheap-but-lucky modem earlier,

"Posting from Linux"

John GT

---

### Post by Sepero on 2007-06-20
> **jdogzilla said:**
> Hello, I followed the instructions for the latest driver and got the following problem:

starting module and utilities
FATAL: Error inserting Intel537 (/lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko): Operation not permitted
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules
done

Any suggestions?
What does this return:
```
ls -l /lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko
sudo modprobe Intel537
```

---

### Post by jdogzilla on 2007-06-25
$ ls -l /lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko
-rwxrw-r-- 1 root root 4217656 2007-06-16 00:01 /lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko

$ sudo modprobe Intel537
Password: XXXXX
FATAL: Error inserting Intel537 (/lib/modules/2.6.20-16-generic/kernel/drivers/char/Intel537.ko): Operation not permitted

Any suggestions?

---

### Post by Sepero on 2007-06-26
The only thing that I can think is that there was a problem in compiling your module. So the only thing I can suggest is to try clean, and compile it again.

Unfortunately, I don't have a 537ep modem, I have a 536ep. The size of your module looks extremely large at 4.2MB. My 536ep driver is just over 1MB. Without actually having a 537ep module, I can't tell you for certain if the size is to big.

If recompiling doesn't work for you, hopefully chuckman78 can get back in here and help out.

---

### Post by chuckman78 on 2007-06-26
Hi jdogzilla.

  It would be very helpfull if you could provide us with a step by step log of the procedure you did to compile and install the driver.

Also, provide the result of entering:  **sudo uname -r**


Regards,

Carlos.

---

### Post by Sepero on 2007-06-26
chuckman78, I sent you back a private message a few days ago and you haven't answered back yet.

---

### Post by alroc_18 on 2007-07-22
> **chuckman78 said:**
> Hi jdogzilla.

  It would be very helpfull if you could provide us with a step by step log of the procedure you did to compile and install the driver.

Also, provide the result of entering:  **sudo uname -r**


Regards,

Carlos.

Hello everyone, I follow the steps to install the 537 but fail, here is my complete code:

[COLOR="DarkGreen"]gonzalo@aresbuntu-desktop:~$ sudo -s -H
Password:

root@aresbuntu-desktop:/home/gonzalo# cd intel-537EP_secure-2.60.80.0

root@aresbuntu-desktop:/home/gonzalo/intel-537EP_secure-2.60.80.0# make clean
cd coredrv; make clean
make[1]: se ingresa al directorio `/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.ko *.o .*.o.cmd *.mod.c *~ core .*.ko.cmd Module.symvers
rm -rf .tmp_versions
make[1]: se sale del directorio `/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv'
rm -f *.o *.ko

root@aresbuntu-desktop:/home/gonzalo/intel-537EP_secure-2.60.80.0# export MODEM_TYPE=537

root@aresbuntu-desktop:/home/gonzalo/intel-537EP_secure-2.60.80.0# make 537
   Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No existe el fichero ó directorio
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No existe el fichero ó directorio
   version.h matches running kernel
2.6.20-15-generic
make[1]: se ingresa al directorio `/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv modules
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/coredrv.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/clmmain.o
/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/clmmain.c:86: aviso: el tipo de dato por defecto es &#8216;int&#8217; en la declaración de &#8216;DECLARE_WORK&#8217;
/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/clmmain.c:86: aviso: nombres de parámetros (sin tipos) en la declaración de la función
/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/clmmain.c:86: aviso: &#8216;DECLARE_WORK&#8217; se declaró &#8216;static&#8217; pero nunca se definió
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/rts.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/task.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/uart.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/wwh_dflt.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/locks.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/softserial_io.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/softserial_ioctl.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/softserial.o
  CC [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/afedsp_int.o
  LD [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/.537core.lib.cmd for /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/537core.lib
  CC      /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/Intel537.mod.o
  LD [M]  /home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv/Intel537.ko
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: se sale del directorio `/home/gonzalo/intel-537EP_secure-2.60.80.0/coredrv'

root@aresbuntu-desktop:/home/gonzalo/intel-537EP_secure-2.60.80.0# make install
rm -f /usr/sbin/hamregistry.bin
bash 537_inst
running kernel 2.6.20-15-generic
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install DEBIAN 537 boot script and links
starting module and utilities
FATAL: Error inserting Intel537 (/lib/modules/2.6.20-15-generic/kernel/drivers/char/Intel537.ko): Operation not permitted
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules
done[/COLOR]

Also ScanModem tells me I have an Old Ambient HaM Modem with the following on ModemData.txt

[COLOR="#006400"]------------ --------------  System information ------------------------
Ubuntu 7.04 
 on System with processor: i686
 currently under kernel:   2.6.20-15-generic
 The kernel was assembled with compiler:  4.1.2
 with current System compiler GCC=4.1.2
    /usr/bin/gcc -> gcc-4.1

Checking for kernel-headers needed for compiling.

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  00:09.0
    
Providing detail for device at PCI_bus 00:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 1813:4000   Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
  SubSystem   
00:09.0 0780: 1813:4000 (rev 02)
	Flags: medium devsel, IRQ 3
	Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c400 [size=256]
	Capabilities: <access denied>
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1813:4000  debian 2.6.20-15-generic 4.1.2 4.1.2    i686

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=1813 Ambient Tech was acquired by Intel with its HaM (Host assisted Modem) chipsets.
 Intel-v92ham-453.tgz is the most recent update, available at:
    [http://linmodems.technion.ac.il/packages/Intel/ham/](http://linmodems.technion.ac.il/packages/Intel/ham/)
    [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)
 The 453 code release is also the last for this older chipset (relates Intel maintainer Dorian Araneda).
 It is NOT functional when compiled under 2.6.n kernels.
 But under the 2.4.nn kernels, all HaM chipsets are supported,
 with a single EXCEPTION: the odd PCI_ID 1813:4100 modems.  For the explanation, see message:
     [http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:9448:200210:fbhcoigfcimgkjdedjad](http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:9448:200210:fbhcoigfcimgkjdedjad)


 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
 and AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download available drivers through:  [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)  with Intel-537 types at:
 [http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2](http://downloadfinder.intel.com/scripts-df/Filter_Results.asp?selCat=all&strOSs=39&ProductID=1230&page_nbr=2)
 Also check at: [http://linmodems.technion.ac.il/packages/Intel/537/](http://linmodems.technion.ac.il/packages/Intel/537/)  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 A very detailed installation report cogent to 537 type modems is at:
                  [http://linmodems.technion.ac.il/archive-fifth/msg00541.html](http://linmodems.technion.ac.il/archive-fifth/msg00541.html)
 Setup call id with:
 	Type 1 : When the phone line is not in use                    at+vcid=1
	Type 2 : When the phone line is already in use on a call      at+pcw=0
 ---------------------

  ======= PCI_ID checking completed ====== 
[/COLOR]

I install Feasty (ubuntu 7.04) just yesterday, and I have a Kubuntu Feasty install as the main system, a Edubuntu desktop installed over Kubuntu (for the Gnome and the Compiz ;) ), the modem works fine on my WinXP SP2.

What could be wrong??

please help! I want to have multimedia support, but is a pain in the **** to get the packages one-by-one with windows try on ubuntu back to windows, back to ubuntu... you get picture right.


Greetings from La Paz, Bolivia

---

### Post by jdogzilla on 2007-07-22
OK ... its working for me now ... just compiled ... now to try to setup a hylafax server ...

---

### Post by alroc_18 on 2007-07-23
Hello Carlos, and hello to everyone again.

I still have no idea of what could be the problem I search for Intel537.ko on /lib/modules/2.6.20-15-generic/kernel/drivers/char/ and is there, why can't be set on /proc/modules.

What did I do wrong, you can find the complete result of my terminal on my first post.

Please Help!!!

---

### Post by goatboy22 on 2007-07-30
Thanks to this great guide my driver is compiled!  But when I try wvdial, I get the following:

--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I have tried gnome-ppp with the same result.  Here is the wvdial.conf contents:

[Dialer Defaults]
Modem = /dev/modem
Baud = 57600
SetVolume = 3
Init1 = ATZ
Init2 = AT+GCI=14
Init3 = ATQ0 V1 E1 SO=O &C1 &D2 +FCLASS=O
Dial Command = ATDT
Carrier Check = no
FlowControl = CRTSCTS
Phone = ###
Username = ###
Password = ###
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes

I edited wvdial.conf manually because it says 'modem not found' when I type 

sudo wvdialconf /etc/wvdial.conf

Also, the Auto Detect feature in Networking Utility doesn't detect anything.

Is something wrong with my install?  I didn't use the script provided in this thread because it returned a syntax error.  So I am using the script provided with the driver.

(This is with ver. 6.06)

Any suggestions?

---

### Post by cratshak on 2007-07-30
need help on Ambient/Intel MD 5628 modem installation 

the output of scanModem tool
---------------------------------------------------------------------------------------
 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_Feb_21


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:0a.0	1813:4000		Communication controller: Ambient Technologies Inc HaM controllerless modem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 02:0a.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

PCIbus=02:0a.0
02:0a.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
	Flags: medium devsel, IRQ 11
	Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a000 [size=256]
	Capabilities: [60] Power Management version 2

 For candidate modem in PCI bus:  02:0a.0
   Class 0780: 1813:4000 Communication controller: Ambient Technologies Inc HaM controllerless modem
      Primary PCI_id  1813:4000
 Support type needed or chipset:	AmbientTech
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read InfoGeneral.txt about alternatives.


 Vendor=1813 Ambient Tech was acquired by Intel with its HaM (Host assisted Modem) chipsets.
 There is no support under 2.6.n kernels!!
 Intel-v92ham-453.tgz 2.4.n kernels was the FINAL 2.4.n update for HaM modems, available at:
    [http://linmodems.technion.ac.il/packages/Intel/ham/](http://linmodems.technion.ac.il/packages/Intel/ham/) 
    [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)
    It is NOT functional when compiled under 2.6.n kernels.
 But under the 2.4.nn kernels, all HaM chipsets were supported,
    with a single EXCEPTION: the odd PCI_ID 1813:4100 modems.  For the explanation, see message:
    [http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:9448:200210:fbhcoigfcimgkjdedjad](http://linmodems.org/cgi-bin/ezmlm-cgi?1:mss:9448:200210:fbhcoigfcimgkjdedjad)
 ====== end AmbientTech section =======


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 03:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1 eth0:avah eth1:avah
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


PCIDEV=1813:4000
CLASS="Class 0780: 1813:4000"
NAME="Communication controller: Ambient Technologies Inc HaM controllerless modem "
Vendor=1813
Device=4000
SUBSYS=none
SUBNAME=""
SUBven=
IRQ=11
Test="./scanModem test 1813:4000 none"
IDENT=AmbientTech
TST=

---

### Post by Sepero on 2007-08-01
To goatboy22:
Try this for your wvdial.conf.
```

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = off
#Carrier Check = no
Dial Attempts = 1

# MODIFY THE FOLLOWING 3 SECTIONS FOR YOUR CONNECTION
Phone = 1234567
Username = ExampleName
Password = ExamplePassword

```

If you continue to get "Modem not responding.", then try changing the modem to your actual device (Modem = /dev/537?).

---

### Post by goatboy22 on 2007-08-03
Sepero, I tried your suggestions, but when I try to dial, same output "Modem not responding".

Could it have anything to do with the 537_boot script?  I am using the one for Suse as I can't get the script supplied here to work.  When I type /etc/init.d/537_boot start,   with the ubuntu version of the script, it says "no such file or directory", but with the suse version, it starts.  Perhaps this is not related at all.

---

### Post by Sepero on 2007-08-03
To: goatboy22

I do not know what the problem is with getting your modem working. Does the modem work fine in any other operating systems? If not, then the modem itself may be broken.

---

### Post by goatboy22 on 2007-08-07
After running the scan modem tool there is a file Intel.txt in /home/Modem.  I used the wvdial.conf file suggested in there and the modem connects fine.  I don't know what the difference is, but it's sure nice to have it working!

---

### Post by Sepero on 2007-08-08
To goatboy22:

Could you please post that wvdial.conf script that you used.

---

### Post by goatboy22 on 2007-08-12
Sure, here it is:

```
[Modem0]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=3D
Init3 = ATM1L3
Carrier Check = no
FlowControl = CRTSCTS
#Stupid Mode = yes
[Dialer tiscali]
Username = <your ISP provided user name>
Password = <your ISP provided password>
Phone = <your ISP phone number>
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Inherits = Modem0

#tiscali is my Internet provider. You may replace the
string [Dialer tiscali] by
[Dialer <your provider name>].


```

This is copied directly from the Intel.txt file in /home/yourname/Modem created by the scanmodem tool.  It worked fine, I changed only the line AT+GCI=3D to AT+GCI=14 because I live in Canada.  I also uncommented "Stupid Mode = yes".  Later, I changed the file to this:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=14
Init3 = ATM1L3
Init4 = ATS11 = 20
Carrier Check = no
FlowControl = CRTSCTS
Stupid Mode = yes
Username = ###
Password = ###
Phone = ###
Auto DNS = yes
Check DNS = yes
Auto Reconnect = yes
Idle Seconds = 0
Abort on Busy = no
Abort on No Dialtone = no
Dial Attempts = 0
New PPPD = yes
```

So I do not need to type "wvdial tiscali", just "wvdial".  As a side note, changing the mru and mtu values in /etc/ppp/options resulted in faster modem operation.  I found the value of 642 to give the fastest download rate for me (average about 4 kbps).

---

### Post by autocrosser on 2007-09-04
Just a note: I have got the Intel-537EP_secure-2.60.80.0_07_05_2007 driver to work with Gutsy's newest Kernel---2.6.22-10-generic. Involved installing the driver twice--first time Almost everything installed--needed to see some elements already installed to install the rest......:)

More info---yes it works---but I found that it was using almost 100% of one of my cpus---back to the external Zoom Modem :(  I'll try it again with the next kernel release.

---

### Post by chuckman78 on 2007-09-05
> **autocrosser said:**
> Just a note: I have got the Intel-537EP_secure-2.60.80.0_07_05_2007 driver to work with Gutsy's newest Kernel---2.6.22-10-generic. Involved installing the driver twice--first time Almost everything installed--needed to see some elements already installed to install the rest......:)

More info---yes it works---but I found that it was using almost 100% of one of my cpus---back to the external Zoom Modem :(  I'll try it again with the next kernel release.

Hi, autocrosser.

 Thanks a lot for the info. Please keep us updated with your experiences and if you want please update the wiki with information for Gutsy. The link for the wiki is:

[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP]("https://help.ubuntu.com/community/DialupModemHowto/Intel537EP")

Thanks again for your help.

Regards,

Carlos.

---

### Post by Sepero on 2007-09-05
Hello again, I am the author of the prepackaged driver for Intel 536EP modems on Feisty.

I am happy to announce that chuckman78 and I have corresponded and are currently working on an Intel 537EP prepackaged binary driver for Feisty. Chuckman78 has modified the instructions on the Ubuntu 537 Wiki page to help those who are currently using Feisty and need the driver immediately.
[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

Hopefully, we should be able to release the prepackaged 537EP driver for Feisty this month.

I have intentions of creating more prepackaged drivers. When Gutsy is officially released, I want to begin preparations to have a driver for it. I would also like to have a driver for the other 537* modems.

For anyone wanting to help:
If you are able to compile the driver or having deb packaging experience, please contact me.
Everyone else, please check out the wiki page, it can always use helpers.

---

### Post by m10 on 2007-09-21
hi i did change my mru and mtu in  /etc/ppp/options to 642 like suggested above but my speed hasn't really got better: while before i did have between 2.0 KB/s and 2.5KB/s  now i get between 0.1KB/s and 3.5KB/s.
note: in both 'configurations' i had cases where the speed got up to 6-7KB/s but only for a few seconds...
may you suggest an other value?
note2: i use a sort of ?panel applet?(you add it to a panel) called (i think) netspeed that i installed some weeks/monthes ago..

---

### Post by Sepero on 2007-09-22
m10:
Try 552
If that doesn't work, you can always set it back to the default of 1500

---

### Post by Sepero on 2007-09-22
The Intel 537EP driver that chuckman78 and I were working on has been released. Follow this link to download it.
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

---

### Post by m10 on 2007-09-22
now with mru and mtu at 552 it's better (it could be better though) between 2.5KB/s and 3.5KB/s
thanks for the help

---

### Post by jdogzilla on 2007-09-25
> **Sepero said:**
> The Intel 537EP driver that chuckman78 and I were working on has been released. Follow this link to download it.
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)
Hello, thanks very much for this.  

It would also be helpful if you could post a sample but comprehensive wvdial.conf file, as well as the right parameters to use in eFax.  

Also, are there any plans to make a driver for 64bit gutsy?  I am planning on moving over to 64bit when gutsy is released, and having a working driver for this would be really appreciated. 

Regards

---

### Post by Sepero on 2007-09-25
> **jdogzilla said:**
> It would also be helpful if you could post a sample but comprehensive wvdial.conf file, as well as the right parameters to use in eFax.I'm not currently able to be very active on the project, but when the next release comes out, I will definitely include it.



> **jdogzilla said:**
> Also, are there any plans to make a driver for 64bit gutsy?To my knowledge, Linux Intel drivers will not work with 64bit. For Linux, I don't know of Any software modems that work on 64bit. (If anyone knows different, please tell me.)

---

### Post by m10 on 2007-10-30
will there be any time soon a package for gutsy?
or else referring to:
> **autocrosser said:**
> Just a note: I have got the Intel-537EP_secure-2.60.80.0_07_05_2007 driver to work with Gutsy's newest Kernel---2.6.22-10-generic. Involved installing the driver twice--first time Almost everything installed--needed to see some elements already installed to install the rest......:)

More info---yes it works---but I found that it was using almost 100% of one of my cpus---back to the external Zoom Modem :(  I'll try it again with the next kernel release.
will the mentioned driver work properly on a bit slower pc(single core 1.3Ghz 384mb ram)?

---

### Post by Sepero on 2007-10-30
If chuckman is willing, we will make a package for gutsy. I currently do not yet have the time though.

---

### Post by chuckman78 on 2007-10-30
I have donew some initial testing of Mr. Vouters driver on Gutsy and things are working right. We might build a package for Gutsy soon.

Regards,

Carlos.

P.S.: You might try *AT YOUR OWN RISK* the Feisty Fawn package on Gutsy, it *MIGHT* work.

---

### Post by Sepero on 2007-10-31
> **chuckman78 said:**
> P.S.: You might try *AT YOUR OWN RISK* the Feisty Fawn package on Gutsy, it *MIGHT* work.
Just to input my opinion, I do Not think the driver will work.

Anyway, the good news is that we have corresponded, and with any luck, we might be able to release a driver for Gutsy in the next few weeks.

---

### Post by m10 on 2007-11-01
I can't wait upgrading! (I like solving problems  and finding out new things and upgrading might bring new knowledge)
I really appreciate your work here! Thank you!

---

### Post by Sepero on 2007-11-12
537EP Driver for Gutsy Gibbon 7.10 has been released:
[http://ubuntuforums.org/showthread.php?p=3372887](http://ubuntuforums.org/showthread.php?p=3372887)

---

