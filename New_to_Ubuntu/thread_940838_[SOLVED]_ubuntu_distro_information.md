---
title: "[SOLVED] ubuntu distro information"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-07
Dear Forum users,

I would appreciate if somebody can guide me how to find Distro information on my desktop running on xubuntu, whether it is 32-bit or 64-bit?

I am new to linux and uname -i command does not return the bit information.

I need bit information for correct ver of software I need to download.

Thank you.
mrm0607

---

### Post by jerome1232 on 2008-10-07
This  one gives you the architecture (32bit or 64bit)
```
uname -m
```

This one will return more info
```
uname -a
```

---

### Post by AndyCooll on 2008-10-07
```
uname -a
```

:cool:

---

### Post by Ryadt on 2008-10-07
The commands above will give you the result.
If it returns i386 then it's 32bits. Otherwise it is 64 bits (x86_64).

---

### Post by Thelasko on 2008-10-07
[Here's]("http://ubuntuforums.org/showthread.php?t=921081&highlight=uname") how to figure out what you version your running.

More importantly, what software are you installing?  If your installing from the Ubuntu repositories, Ubuntu will pick the correct software version for you.

[I really think you need to read this.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by MRM0607 on 2008-10-07
> **Ryadt said:**
> The commands above will give you the result.
If it returns i386 then it's 32bits. Otherwise it is 64 bits (x86_64).

Dear User,

Thank you for your response.

uname -a returns result

Linux requiem 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

and uname -m returns result 'i686'

So I would understand that it is 64 bits (x86_64)

Also could you please guide me to understand the file system in ubuntu. I would appreciate a link. I am really new to linux and trying to install software on my machine. It is a presumption on most software venders part that person is familiar with linux operating system, so installation guide can be some time confusing to me.

Another important thing that I must stress is that I do not want to use gui interface (even though it will make things easier for me). I would like to use command interface primarily. I understand this will slow me down but eventually I will be quite independent.

Thank you.
mrm0607

---

### Post by jerome1232 on 2008-10-07
actually i686 is a 32bit arch. i386, i486, i586, i686 are all 32bit

---

### Post by Thelasko on 2008-10-07
> **MRM0607 said:**
> Also could you please guide me to understand the file system in ubuntu. I would appreciate a link. I am really new to linux and trying to install software on my machine. It is a presumption on most software venders part that person is familiar with linux operating system, so installation guide can be some time confusing to me.

What are you trying to install?  You shouldn't need to know all of this information for 90% of software!  To install software from the command line use:
```
sudo apt-get install *programname*
```
Where *programname* is the name of the program you are trying to install.

[I also think you should read this again.]("http://www.psychocats.net/ubuntu/installingsoftware")  **Installing software in Ubuntu is very different than in Windows!**

---

### Post by MRM0607 on 2008-10-08
> **Thelasko said:**
> What are you trying to install?  You shouldn't need to know all of this information for 90% of software!  To install software from the command line use:
```
sudo apt-get install *programname*
```
Where *programname* is the name of the program you are trying to install.

[I also think you should read this again.]("http://www.psychocats.net/ubuntu/installingsoftware")  **Installing software in Ubuntu is very different than in Windows!**

Dear UBUNTU user,

I would agree with you that majority software install do not require this information but in my case I do need this information.

I am trying to install scientific software (NAMD and VMD) which comes already in binary for 32-bit and 64-bit. So I have to download correct version depending the Distro information I have.

Thank you.
mrm0607

---

### Post by MRM0607 on 2008-10-08
> **jerome1232 said:**
> actually i686 is a 32bit arch. i386, i486, i586, i686 are all 32bit

Dear UBUNTU user,

Thank you for the response.

There is a response before you and I will qoute the response below:

 Re: ubuntu distro information
Quote:
Originally Posted by Ryadt View Post
The commands above will give you the result.
If it returns i386 then it's 32bits. Otherwise it is 64 bits (x86_64).

This response tells me things otherwise.

I would appreciate if somebody can verify which of the two is the one I shall go with.

Thank you.
mrm0607

---

### Post by Ryadt on 2008-10-08
Hi..
If I read right your output of > uname -m was *i686*
This means that you have a 32 bits system.

---

### Post by jerome1232 on 2008-10-08
> **MRM0607 said:**
> Dear UBUNTU user,

Thank you for the response.

There is a response before you and I will qoute the response below:

 Re: ubuntu distro information
Quote:
Originally Posted by Ryadt View Post
The commands above will give you the result.
If it returns i386 then it's 32bits. Otherwise it is 64 bits (x86_64).

This response tells me things otherwise.

I would appreciate if somebody can verify which of the two is the one I shall go with.

Thank you.
mrm0607

That's why it's often called x86, it usually doesn't matter as long as your some variant of i386-i686.

For 64 bit OS it shows up as x86_64.

---

### Post by Thelasko on 2008-10-08
> **MRM0607 said:**
> Dear UBUNTU user,

I would agree with you that majority software install do not require this information but in my case I do need this information.

I am trying to install scientific software (NAMD and VMD) which comes already in binary for 32-bit and 64-bit. So I have to download correct version depending the Distro information I have.

Thank you.
mrm0607

Good, many new users try to install from source instead of using the repositories.  The repositories are usually the best option it's available.

Please let us know if you need any more help with installing.  Don't forget to mention that your software isn't available from the repositories.

---

### Post by MRM0607 on 2008-10-08
Dear UBUNTU forum user,

Thank you for your help.

It is clear to me now.

I think I would install 64-bit on my machine.

Should I be concern with some details about machine. I have DELL 8200 dimension with INTEL pentium processor.

---

### Post by germanix on 2008-10-08
In your last post above you wrote:
It is clear to me now.

I think I would install 64-bit on my machine.

No! No! You seem to have misunderstood! You have a 32-bit machine. 
Your output from uname -m was i686 and not i686_64
SO PLEASE MAKE SURE YOU INSTALL THE 32 BIT!!!

---

### Post by Thelasko on 2008-10-08
> **MRM0607 said:**
> Should I be concern with some details about machine. I have DELL 8200 dimension with INTEL pentium processor.

I don't know if that will work.  From the [64-bit area]("http://ubuntuforums.org/showthread.php?t=765428"):> 
Intel users with EM64T processors eg: Pentium D/Celeron D/Core2-Duo/Core2-Quad/Xeon processors/and certain Pentium4's

If you have a spare CD and enough bandwidth to download the iso quickly, the easiest way to find out, is to try it.  It will give you a pretty clear message that your processor isn't 64-bit.

---

### Post by MRM0607 on 2008-10-08
> **germanix said:**
> In your last post above you wrote:
It is clear to me now.

I think I would install 64-bit on my machine.

No! No! You seem to have misunderstood! You have a 32-bit machine. 
Your output from uname -m was i686 and not i686_64
SO PLEASE MAKE SURE YOU INSTALL THE 32 BIT!!!

Dear UBUNTU forum user,

Thank you for the response.

I missed to mention that I meant install 64-bit for ubuntu. 

The software for VMD I downloaded is: 
[COLOR="DarkSlateBlue"]LINUX AMD64 OpenGL (Linux (64-bit AMD or Intel EM64T x86) with hardware OpenGL[/COLOR]

VMD software has 32-bit for windows but I cannot seem to see in download list binary for 32-bit linux. I could be mistaken being so new to the whole thing. I am listing the site name below in case anyone want to take a look at it.

[http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD](http://www.ks.uiuc.edu/Development/Download/download.cgi?PackageName=VMD)

So I think the other option I would have is to upgrade ubuntu from 32-bit to 64-bit and download the correct software and try to install it. Because of this I mentioned in my mail that shall I be concern about anything since I have machine which is dell dimension 8200 pentium processor.

While on the subject I have another question about openGL runtime libraries. Do they come bundled with the ubuntu software or do I have to install them separatly. The software uses them. It also uses PERL, Python and TCL/Tk. I think TCL/Tk I have to download. I am not sure about PERL though.

I tried to find Information about OpenGL Libs on UBUNTU website but could not find it.

The reason I am writing all this questions because by blindly downloading and installing software will not help me rather I would have these issues later.

I would truly appreciate your time and help.

---

### Post by MRM0607 on 2008-10-08
Thank you.

I will try that.

mrm0607

---

### Post by Thelasko on 2008-10-08
OpenGL should be on your machine when you install Ubuntu/Xubuntu Desktop Edition.

---

### Post by jerome1232 on 2008-10-08
> **germanix said:**
> In your last post above you wrote:
It is clear to me now.

I think I would install 64-bit on my machine.

No! No! You seem to have misunderstood! You have a 32-bit machine. 
Your output from uname -m was i686 and not i686_64
SO PLEASE MAKE SURE YOU INSTALL THE 32 BIT!!!

Just an fyi, that's just what he has installed, it may be that his processor is 64bit, and he installed a 32 bit OS, in that case uname -m will report i686.

I built my computer 4-5 years ago and it's 64bit, all modern cpu's are 64bit. If you try to install the 64bit OS onto a 32bit machine the cd will outright fail to load the kernel so there's no worries in trying to install the 64bit version if you desire a 64bit OS. (faster compile times and video/audio encoding times are the biggest advantage) oh and 4+GB of ram are possible.

---

### Post by MRM0607 on 2008-10-08
> **Thelasko said:**
> OpenGL should be on your machine when you install Ubuntu/Xubuntu Desktop Edition.

Thank you for your response.

how can I find that out. Is there a command or directory I can take a look at it?

mrm0607

---

### Post by Thelasko on 2008-10-09
> **MRM0607 said:**
> Thank you for your response.

how can I find that out. Is there a command or directory I can take a look at it?

mrm0607

There are many ways to determine if you have OpenGL on your system.  The simplest way I can think of is to open the terminal and type:
```
glxgears
```
If you see [three gears turning]("http://www.ncsa.uiuc.edu/UserInfo/Resources/Hardware/CommonDoc/glxgears.jpeg") you have OpenGL installed and it is functioning properly.

---

### Post by MRM0607 on 2008-10-09
Thank you.

I see the gears running. So I would understand that OpenGL is installed and functioning correctly.

---

### Post by MRM0607 on 2008-10-09
> **Thelasko said:**
> I don't know if that will work.  From the [64-bit area]("http://ubuntuforums.org/showthread.php?t=765428"):
If you have a spare CD and enough bandwidth to download the iso quickly, the easiest way to find out, is to try it.  It will give you a pretty clear message that your processor isn't 64-bit.

Dear User,

I truly feel grateful for your help.

I am going to try to install 64-bit ubuntu os. I appreciate the link you included.

Thank you.
mrm0607

---

### Post by roger_1960 on 2008-10-09
Hi

i686 is 32 bit.  64 bit returns x86_64

---

