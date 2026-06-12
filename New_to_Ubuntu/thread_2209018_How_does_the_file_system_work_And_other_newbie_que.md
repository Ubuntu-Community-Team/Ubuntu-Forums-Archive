---
title: "How does the file system work? And other newbie questions"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by ankit7 on 2014-03-03
I have some basic idea about the file system since i studied about it a bit , but only recently have i started using ubuntu . 
I am a little puzzled about the file system as i have forever been a windows user in the past. 

1. Are there no volumes in this OS?? I find it hard to imagine the whole OS being indexed w/o them . 
2. Is there some place i can learn what each folder in the computer folder does ?? 



-----

Onto the more nooby questions : 
1. How do i put direct shortcuts on the desktop ?? I have only been able to create folders on it and save files in the folders nothing more . 
2. My knowledge of the grub is very limited and google isnt giving me good results , so can someone please link me to some good webpage that could help me ?? 
3. Could you suggest me some must have softwares??? The software center was very useful , but i wanna know if i missed something . 

Thanx in advance.

---

### Post by Lars Noodén on 2014-03-03
The system itself follows the layout described in [hier](http://manpages.ubuntu.com/manpages/saucy/en/man7/hier.7.html).  That's fairly similar across distros.  Most of your programs will be found in /usr/bin

Inside the home directories is more unique to each distro, but the folder names should give a strong clue as to their default contents.

---

### Post by grahammechanical on 2014-03-03
You asked for it and here it is

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

My advice would be to first learn to be a Ubuntu user. Otherwise, the first thing you will learn is how to break Linux. In Linux we do not have volumes but Devices. And it all depends upon how Ubuntu was installed.

If Ubuntu is the only OS and if you have a BIOS boot system then there will be but three partitions. One primary partition in which Ubuntu is installed; one extended partition second partition) in which one logical partition is created (the third partition) and used as swap. But you will not see these in File Manager as volumes or devices. You will see the Ubuntu partition in File Manager under Places with nine default named folders.

Additional formatted partitions show up in File Manager as Devices and in the Launcher as hard disk icons. You can also open the Disks utility and that will show you the partition layout of the hard disk. Everything is there for the Ubuntu user.

Regards.

---

### Post by diesch on 2014-03-03
> **ankit7 said:**
> 
1. Are there no volumes in this OS?? I find it hard to imagine the whole OS being indexed w/o them . 


In Ubuntu like in any other Unix-like system you have just one folder tree that can span multiple file systems. If you want to access a file system you just mount it to a folder in the system's file system tree so it becomes a subtree.

---

### Post by ajgreeny on 2014-03-03
A good general view of the filestsrem layout at [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)
More here [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

A general google search will find hundreds more, I am sure.

---

### Post by endlessinstant on 2014-03-03
You will see from these links that while Linux and other Unix-like systems use a hierarchical directory system like Windows, the entire structure is much more organized than in Windows.  Windows will install its key folders like \Program Files\ etc. but what and where you put things doesn't really matter because the registry pretty much figures all of that out.   It's good to muck around in your system folders to learn how your system is laid about, but don't start editing things there, especially as root, because you're curious.   Personal data should all go in the \home\ folder.   You can pull apps off the Ubuntu Software Center and doing it this way will install everything where it needs to be without you having to mess with it (unlike Windows where you might have to specify the file path or something).  There are various ways to install packages manually (and various reasons you would want to do this) but at first it is good to just rely on the Software Center to keep your system tidy for you.

---

### Post by mastablasta on 2014-03-04
about the programs - what are you into? do you have any special things you need to do in the OS?

Aside form software center Ubuntu (using official archive/repository) has PPA (personal package archives) -these include form various games and programs (see playdeb, getdeb) as well as more up-to-date/beta drivers and some other things. Ubutnu can also install .deb files which act similar to .exe files in windows.

also if you are seeking desktop environment that is more similar to windows i suggest you look into KDE (found in Kubuntu)

---

### Post by ankit7 on 2014-03-05
First of all, I'd like to thank everyone for their replies. 

Yes, I have a special purpose for shifting to this OS . I wanted to learn Setting up Havana andtry out other cloud related EMC softwares. 

-----

While i posted for problems in that in a different thread , [http://ubuntuforums.org/showthread.php?t=2209021](http://ubuntuforums.org/showthread.php?t=2209021)

I have one more question , I wanted to learn for my CCNA certfication as well. For that I wished to try my hand on with Cisco Packet Tracer. I installed it [i did sh install_file_name] , but when I click its icon to lauch it post install , nothing happens, ny suggestions ? 
----------

Thanx again

---

### Post by Lars Noodén on 2014-03-05
> **ankit7 said:**
> First of all, I'd like to thank everyone for their replies. 

Yes, I have a special purpose for shifting to this OS . I wanted to learn Setting up Havana andtry out other cloud related EMC softwares. 

-----

While i posted for problems in that in a different thread , [http://ubuntuforums.org/showthread.php?t=2209021](http://ubuntuforums.org/showthread.php?t=2209021)

I have one more question , I wanted to learn for my CCNA certfication as well. For that I wished to try my hand on with Cisco Packet Tracer. I installed it [i did sh install_file_name] , but when I click its icon to lauch it post install , nothing happens, ny suggestions ? 
----------

Thanx again

You should probably start a new thread for your new question.  I'm not into networking but did read about GNS3, maybe it would be useful in your case?
[http://www.gns3.net/](http://www.gns3.net/)

---

