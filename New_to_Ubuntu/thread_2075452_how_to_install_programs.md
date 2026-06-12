---
title: "how to install programs"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by Cu Rua on 2012-10-23
I don't know how to install programs in Linux without the Synaptic Package Manager. Could somebody give me a tutorial?

---

### Post by Frogs Hair on 2012-10-23
What kind of programs ? It is possible to install programs from the command line if you know the package name and they are in the repository. Methods for installing may vary depending on the package type.

---

### Post by mardybear on 2012-10-23
Hi.

Welcome to Ubuntu Linux.

Via terminal you would typically type 'sudo apt-get <program name>'
...not including the quotes...replace program name with the program you wish to install.

A forum or google search will provide all the information you would ever want to know.

mardybear

---

### Post by mag1strate on 2012-10-23
This is a pretty useful guide that will get you to know the ins and outs of apt-get:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by oldos2er on 2012-10-23
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by newb85 on 2012-10-23
> **mardybear said:**
> Via terminal you would typically type 'sudo apt-get <program name>'
...not including the quotes...replace program name with the program you wish to install.

Should actually be 'sudo apt-get **install** <program name>'  ;)

---

### Post by Cu Rua on 2012-10-24
The problem with trudging all over Google is they assume I have a clue. I need something very general and dumbed-down, particularly for somebody who's hopelessly dependent on GUIs and Windows install wizards. 

Also, not all the programs I want are in the repositories, though I try to use them as much as I can. What would I do with old Windows discs? 

I keep getting zips or tarballs, as soon as I extract them, I have no idea what to do next. Is there a command-line incantation for that? 

Finally, all Linux distros have the same command-line system, right?

---

### Post by mardybear on 2012-10-24
> **newb85 said:**
> Should actually be 'sudo apt-get **install** <program name>'  ;)
Sorry...that's what i meant...only an Ubuntu wizard would be able to install software via terminal without using the install command :)

mardybear

---

### Post by oldfred on 2012-10-24
If you want synaptic:

sudo apt-get install synaptic

You can also use Ubuntu Software Center.

I almost never install from a deb which is complied for Debian distributions. 

And I do not think I have ever installed from zips or tar-bells. They usually have compile instructions in a text file, but may have dependency issues. Or the old dependency hell that used to be common before repositories and their managers. 


Terminal may be similar, but there even different terminals by distribution, several optional in Ubuntu.
Only Debian based Linux use apt, the other major distributions use different managers for software repositories. 
[http://en.wikipedia.org/wiki/Package_management_system](http://en.wikipedia.org/wiki/Package_management_system)

---

### Post by mardybear on 2012-10-24
Hi again...

As synaptic usually works well, rarely do i install software via command line. The repositories are so vast (can't remember how many thousands of available packages), rarely have i ever needed/wanted to install software that wasn't already in the repository. Additonal repositories are also available via syanptic if you can't find the specific software you're looking for.

There's lots to learn with Ubuntu Linux, one step at at time. As mentioned, there's lots of reading available on this forum and via google, such as:

[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)

[http://www.google.ca/search?client=ubuntu&channel=fs&q=how+to+install+ubuntu+software+zip+or+tarball&ie=utf-8&oe=utf-8&redir_esc=&ei=VJSIUIGxM4nKiwK40oCYCA](http://www.google.ca/search?client=ubuntu&channel=fs&q=how+to+install+ubuntu+software+zip+or+tarball&ie=utf-8&oe=utf-8&redir_esc=&ei=VJSIUIGxM4nKiwK40oCYCA)

Have fun with it and don't let yourself get too frustrated. Linux has a steep learning curve. Don't expect to figure everything out right away. It's taken me years and i'm just starting to feel like i'm getting a handle on it.

mardybear

---

### Post by squakie on 2012-10-24
Most programs that what come in a zip or tarball usually have a "readme" file of some sort describing how to install them.  A lot of these are source code and require some additional packages be installed first.  Without a specific example, it would be difficult to give you meaningful instructions.  

As far as Windows disks go, Ubuntu isn't Windows and as such does not used the same internal interfaces (libraries, GUI development, etc.) as most Windows programs.  A .bat, .com or .exe file will not run or work in Linux.  If you have specific Windows applications that you MUST have that you have not found a Linux equivalent for, you can try installing the wine package and perhaps playonlinux (a front end for installation).  Wine tries to provide a means to run a Windows program.  By far, not all will run.  Unless something has changed you also can't use USB devices (outside of keyboard, mouse and maybe your printer).  USB flash drives, wireless adapters, etc., will not be accessable.

Depending on the specifications of your PC you may also be able to install something like VirtualBox (free, but get the download from Oracle's site) and run Windows in a virtual machine in Linux.  This will have access to your devices and wireless.  You'll need some sort of Windows installation disk to install Windows as a virtual machine.

---

### Post by newb85 on 2012-10-25
> **squakie said:**
> USB flash drives, wireless adapters, etc., will not be accessable.

Really?  Flash drives have always been plug-and-play for me.

> **squakie said:**
> Depending on the specifications of your PC you may also be able to install something like VirtualBox (free, but get the download from Oracle's site)

Is there something wrong with the version in the repositories?

---

### Post by squakie on 2012-10-25
Well, I don't know if it's still true, especially with Oracle having bought Sun and doing their own thing now, but it at least *used* to be that the version in the repositories was the open user version, but you had to go to Sun (now Oracle) to get the version of VirtualBox that included USB support.

For Wine, it always used to be a restriction that USB devices wouldn't work.  It had been that way for years (excluding keyboards, mice and some printers) but I never personally tried a flash drive with it just simply because I didn't need to.  I dumped wine in favor of VirtualBox and Windows in a VM years ago - much more flexible and all Windows programs will run without restrictions.  Yes, there is a trade off if you run games.  I don't.

So, the last I knew, yes there were differences.  If a USB flash drive now works in Wine it is news to me - being a USB device - and that USB devices weren't supported in Wine.  Same with VirtualBox.  Perhaps the version now in the repositories is now what used to be called the peul (I might have a letter swapped there) version, and that version you always had to download from Sun/Oracle.  The last I checked Oracle's site it appeared they only had 1 version there now.  Perhaps that is what is included now in the repositories - if so, it's new since Oracle took over Sun.

So perhaps things have changed.  These things at least used to be, not that long ago, facts.

---

### Post by newb85 on 2012-10-25
> **squakie said:**
> Well, I don't know if it's still true, especially with Oracle having bought Sun and doing their own thing now, but it at least *used* to be that the version in the repositories was the open user version, but you had to go to Sun (now Oracle) to get the version of VirtualBox that included USB support.

Ah, yes.  It looks like the repository version requires that an Extension Pack be installed from the Oracle website to use USB 2.0.  (The USB 2.0 option is present in the settings, but when you click it, it gives you a message about installing the Extension Pack.)

> **squakie said:**
> For Wine, it always used to be a restriction that USB devices wouldn't work.

Wow, I should probably start drinking my coffee before I start posting.  When I read your first comment about USB devices, I didn't catch that you were talking about their (not) working with Wine.  Don't know why that wasn't obvious to me.

---

### Post by squakie on 2012-10-25
> **newb85 said:**
> ....Wow, I should probably start drinking my coffee before I start posting.  When I read your first comment about USB devices, I didn't catch that you were talking about their (not) working with Wine. 

I love the smell of coffee but for some reason hate the taste - but I get the same way if I don't have my diet coke.  Oh heck, who am I fooling - it's my darn age!  Things don't seem to swing around in the noggin like they used to!

Have a good one! ;)

---

