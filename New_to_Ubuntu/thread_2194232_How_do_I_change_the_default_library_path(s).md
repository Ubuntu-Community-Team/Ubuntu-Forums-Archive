---
title: "How do I change the default library path(s)?"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by wpbdry on 2013-12-17
Hi All,

I am completely new to ubuntu so please be patient with me :P :) I recently installed ubuntu 13.01 on my Dell Inspirion laptop alongside the already installed Windows 8.1. Both 64bit.

I made a separate partition on my hard drive called "Shared" for all my movies, music etc. so that I can easily access them from both OS's. In windows this drive shows up as "Shared(A:)". I managed to change the library path in windows so that when I click on the "Music" library icon it goes to **A:\Music** and the same for Documents etc. How do I do the same thing in ubuntu? If I right click on the Shared drive in ubuntu and select properties is says "Location: **media/myname**". This would indicate that I need to change the path of the Music library, for example, to **media/myname/Shared**. The current location of the Music library is "**home/myname**". How do I change it?

I tried clicking Files>Bookmarks in the Files title bar. This brought up a "Bookmarks" window where I could edit the names and locations of Documents, Music, Pictures, Videos and Downloads. Surely this is exactly what I'm looking for? However I tried it with Music first and typed in** /media/myname/Shared/Music** where it currently said** /home/myname/Music** but all it did was create a new bookmark that never existed before under the heading Bookmarks in the navigation pane on the left. Is my computer malfunctioning or is this supposed to happen? When I click on this new bookmark it goes to the correct location but I haven't changed the destination location of the system library which is what I want to do.

Any help would be appreciated :)

Thanks in advance.

---

### Post by theDaveTheRave on 2013-12-17
hi wpbdry,

welcome to the world of linux.

the 'music'. location points to the following path on my system
```

/home/{myName}/Music

```

you will access your shared drive with a path such as
```

/media/{yourName}/{nameOfDevice}/
[code]
or
[code]
/media/{nameOfDevice}/
[code]
This seems to be a 'default' location inside the media folder. note that ubuntu doesn't see 'hard drives' it considers everything as a folder (or ultimately a file), if you insert a USB key it will likely appear in the [code]/media/{yourName}/{diskLabel}/
``` folder. it is possible to make it appear elsewhere, (I won't go into that now suffice to say look up fstab and mount points).

So when you navigate to the media folder you should be seeing your shared drive as a sub directory in here, again possibly inside the ```
{yourName}
``` sub folder.
Alternatively if you are using nautilus file browser (or similar) you will likely have the little icon for your disk, if you click on it you will see the full path to this disk.

Now that you are well located inside your shared drive, and you can see your ```
/Music
``` sub folder, navigate your way inside.

In nautilus, or your prefered file browser, you will have an option to 'add to bookmarks' your current location, or you should be able to simply drag the folder into your bookmarks toolbar.

Once the bookmark is added you can right click to modify the name of the item.

You should now be good. If not shout back into this thread with what went wrong.

David

---

### Post by howefield on 2013-12-17
You could remove your existing ~/Music folder (making sure there is nothing in it that you want to keep) and replace it with a link to the folder on the shared drive, eg

```
rm -r ~/Music
```

```
ln -s /pathtomusicfolder
```

---

### Post by theDaveTheRave on 2013-12-17
@howefield,

I was going to suggest that, but I got the impression that the exact location of the shared drive wasn't certain, also I wanted to avoid the use of the terminal.

If you wanted to be really clever, the OP could make a the disk mount directly into his ~home/{userName}/Music folder. But again, I figured that was going to be doing too much terminal, and file modifications for something that didn't require that level of expertise.

David

---

### Post by ajgreeny on 2013-12-17
Using the above as an example, and assuming that all your music is now on the shared partition which you mount automatically at boot it is easiest to remove the empty Music folder from your current ubuntu home, and then make a soft link from the shared partition Music folder to your ubuntu home with the command
```
ln -s /media/username/sharedpartition/Music /home/username/Music
```
This does depend on the shared partition being mounted all the time when you boot or you will get error messages when you login to your user-session.  Also if you do not remove your empty Music folder in ubuntu's home first you will end up with all the music appearing in a /Music/Music folder which is not particularly helpful.

Any problems or uncertainties, come back and ask again.

---

### Post by wpbdry on 2013-12-17
Hi theDaveTheRave, that sounds good but I think that is what I already did when I created that bookmark I was talking about (I'm not sure) which is not what I wanted because it is not tidy. I didn't realise that I can delete the folders in **/home **but even so it would still be down at the bottom below all my drives, including my windows drives which I never look at, and not at the top like the original folders.

However ajgreeny, I followed your suggestion and it worked perfectly :) I have not yet tried rebooting my system to see if it still works but the drive is always there so I think it should. If not I'll be right back.

Thanks all for your help!

---

### Post by ajgreeny on 2013-12-17
> **wpbdry said:**
> However ajgreeny, I followed your suggestion and it worked perfectly :) I have not yet tried rebooting my system to see if it still works but the drive is always there so I think it should. If not I'll be right back.

Thanks all for your help!
If the partition with all the data files is not mounted at boot we can quickly tell you how to ensure it is with an edit of the /etc/fstab file, so come back again if necessary.

---

### Post by wpbdry on 2013-12-17
After I rebooted my computer the links in the navigation pane listed under "Places" have disappeared.

It now reads:

[B]Places
[/B]Recent
Home
Desktop
Downloads
Trash

It used to read:

[B]Places
[/B]Recent
Home
Desktop
Documents
Music
Pictures
Videos
Downloads
Trash

Presumably this is because there is no longer a folder called "Documents" or "Music" etc in the folder **/home **but there is a soft link. Is there not a way that I can create a link under "Places" that goes to this soft link? Ideally with the specialized icons for documents or music or whatever so it looks the same as it did before I started any of this? If I create bookmarks they go under a new heading called "Bookmarks"and I can't find any way of dragging them to under the heading "Places".

As before any help will be appreciated :)

Thanks.

---

### Post by ajgreeny on 2013-12-17
As I said, you will need to edit fstab, but for now you can just mount the partition with all your data on it and all the soft links should mend again.  It is too late at night here to answer in detail, but  will.come back again tomorrow morning and try to help sort this out for you.

---

### Post by ajgreeny on 2013-12-18
OK, I'm back.  Are you now sorted or does the problem of broken links happen every time?

What we will need to sort this out is the output of command ```
sudo blkid -c /dev/null
``` which will give us the UUID and labels of all your partitions.  If the partition we are trying to deal with is not labelled, I suggest you give it one that tells you what it is (use gparted) as it can make life a lot easier when it needs mounting; you will recognise it much easier than a long alphanumeric string.

Now we know what the partition UUID is we can make a mountpoint folder in media or mnt, I prefer mnt but it's up to you, with command sudo mkdir /mnt/LABEL[/code] where LABEL is the label you gave the partition earlier (eg **storage**).  Now backup then edit fstab with ```
sudo cp /etc/fstab /etc/fstabbak
``` then ```
gksudo gedit /etc/fstab
``` and add a line similar to ```
UUID=66E53AEC54455DB2 /mnt/storage/    ntfs-3g        auto,user,rw 0 0
``` where you will use the UUID gleaned from the blkid command earlier.  Finally to check all is well run command ```
sudo mount -a
``` and if there is no output and the terminal goes straight back to the prompt, everything is OK.

Now when you boot the machine the storage partition will be automounted and all those links should work, but bear in mind that the original links you made may now be to the wrong source folders so you may need to delete them and make new ones with ```
ln -s /mnt/storage/Music Music
```

I hope this all makes sense to you.  Good luck!

---

### Post by wpbdry on 2013-12-18
When I entered command sudo mkdir /mnt/Label[/code] [COLOR=#000000]the output said [/COLOR]mkdir: cannot create directory &#8216;/mnt/Label[/code]&#8217;: No such file or directory. Is this a problem? I tried using /mnt and /media but both said No such file or directory. I'm sure I typed the UUID code correctly.

---

### Post by ajgreeny on 2013-12-18
> **wpbdry said:**
> When I entered command sudo mkdir /mnt/Label[/code] [COLOR=#000000]the output said [/COLOR]mkdir: cannot create directory &#8216;/mnt/Label[/code]&#8217;: No such file or directory. Is this a problem? I tried using /mnt and /media but both said No such file or directory. I'm sure I typed the UUID code correctly.
Whoops ! ! !  Mea culpa !

Sorry I added the code tags manually when I replied and forgot the one at the start of the command as I typed it.

Try ```
sudo mkdir /mnt/Label
``` where Label is of course whatever label you gave the partition, eg as in my example, "storage".

---

### Post by wpbdry on 2013-12-18
When I type that is says Cannot create directory "mnt/Shared": File exists. My Shared drive is definitely still located in **media/userName **because that's what it says if I right click on it and click properties.

---

### Post by ajgreeny on 2013-12-18
OK, so you have already made the mountpoint /media/Shared; correct?  Have a look at the output of **ls /media**

If so, add a line in fstab ```
UUID=66E53AEC54455DB2 /media/Shared/    ntfs-3g        auto,user,rw 0 0
``` changing the UUID to that of your partition, and then run ```
sudo mount -a
``` What happens?

---

### Post by theDaveTheRave on 2013-12-19
Hi all, and especially wpbdry

Having re-read the original post, I am wondering why this is as difficult as it is to configure?

I get the impression that wpbdry is not a 'computing green apple', he was able to perform this action on his windows partition apparently with ease.

So this does beg the following observations and comments.

[LIST]
[*]Should this be easier in Linux (General), Ubuntu (specifically) ?
[*]Should this functionality be enabled during install, with information that this can also be performed later?
[*]Should it be available from special tools (eg gparted) only ~ does such a tool already exist ?
[/LIST]

I'm pointing this request at all those who are following this thread, but particularly I would like wpbdry's feedback.

I wonder if it is something we should add to a 'bug' report or improvement request for the next versions.

David

---

### Post by wpbdry on 2013-12-19
Hi ajgreeny, the output of that is bash: "ls/media: No such file or directory". (I hope I am doing it right, I just typed ls/media in the terminal and pressed enter [that is a lower case L not a upper case i])

theDaveTheRave, I think that in windows the "visual" settings (if I can call them that) are a lot more developed than in linux hence being more user/noob friendly and a lot less is needing to be done with command prompt (windows version of terminal). The only thing I have ever used command prompt for is to set up my computer as a Wifi hotspot (ironically the one thing that is built in to linux's settings) but even that you can download a program that does it for you. So for example to do this in windows I simply right clicked on the library in "My PC" (windows equivalent of "Home") and clicked on properties bringing up a small window with about 8 tabs, licked on the location tab, typed in the new location and clicked the apply button. A popup came up saying "Would you like to move all the files currently in this library to the new location so as not to confuse programs?" I clicked "Yes" and Done! In linux the "Properties" window doesn't even give you the option of changing anything.

Briefly looking over the settings in linux (brought up by clicking on the settings icon in the launcher) they look very limited compared to windows although I would imagine that a lot more is possible using terminal. So I think when it comes to command line work I am a "green apple".

I don't think it is necessary to have this option during install but it would be good to have it somewhere in the settings as is the same with many other  things. although I find it fun using terminal it would be nice if I understood it a bit more because at the moment I am just following other people's instructions letter for letter. But I don't think that most people just wanting an easy to use computer, not interested in development at all, would want to start using terminal to customise their computer. So if we are talking about reporting a "bug" to linux we should ask for a general overhaul of the settings making them a lot more detailed.

---

### Post by theDaveTheRave on 2013-12-19
@wpbdry

Thanks for the response to my question. Not having had to do this ever on windows I wasn't aware of the extra available tabs in the 'properties' pop-up.

here is the [ question on launchpad]("https://answers.launchpad.net/ubuntu/+question/241028"), so as it can be followed by any others that are out there.


David

ps. OT : re : learning the command line.
Don't worry too much if you feel that you are just 'copy / pasting' commands into the terminal, I suspect that is how we all started!
if you want to look into the available commands, I have  [www.die.net/]("http://www.die.net/") bookmarked on my pc it is basically easier to search than the normal 'man' pages.

D

---

### Post by wpbdry on 2013-12-19
Hi theDaveTheRave,

Thanks for that die.net link I think/hope that will help me a lot. Your link to the launchpad question didn't work for me but I found it here: [https://answers.launchpad.net/ubuntu/+question/241028](https://answers.launchpad.net/ubuntu/+question/241028) I am interested to see what other people think about this.

---

### Post by ajgreeny on 2013-12-19
Hi again wpbdry.

You missed a space in that **ls /media** command, so try again **ls** *space* **/media** or just copy it, which is easiest done by highlighting the command in my post then middle click (or if a laptop click left and right together) with the cursor in the terminal; that will paste the buffer contents immediately, a brilliant linux facility which you will get used to doing very quickly.

What you are trying to do is not really as difficult as theDaveTheRave seems to think, but it does demand that the commands are correct.  NTFS partitions are not mounted by default in a Linux OS, nor are other ext4 partitions, unless you add them to the fstab file which instructs the OS to mount them at boot time with appropriate mount options.  Follow what I said and it should mount your shared partition and allow you to make links to the data folders in that partiton.

Apologies for my slip earlier with a missing code tag, which I hope you are now able to overcome.

---

### Post by wpbdry on 2013-12-19
Hi ajgreeny,


Sorry about that slip and thanks for that copying trick, it should make stuff a lot easier. I have managed to get everything working now and it still works even after I rebooted (I checked). So thanks for that and thanks for your patience! But I still don't have the libraries listed under the **Places** heading in the navigation pane which, if you remember, is what I wanted. It is not serious if it can't be done, or if it is very difficult perhaps not worth it, but it would make it a bit easier to navigate my libraries and look more familiar. So any ideas would be appreciated but as I said not the end of the world.


However, when I first tried to mount the drive and then ran the command "sudo mount -a" there was an output message that said something along the lines of "cannot mount Shared. Drive in use by another OS. Windows in hibernation" I can't remember the exact message but that was the gist of it. It is true that the last time I used windows I hibernated it and then booted into ubuntu. So I rebooted into windows and shut down windows completely and then rebooted back into ubuntu and tried the whole thing again and it worked fine. Does that mean that every time I hibernate windows and boot into ubuntu it will fail to mount the drive? Or is it just that it cannot set the mount point when windows is in hibernation?

---

### Post by theDaveTheRave on 2013-12-19
> **ajgreeny said:**
> 
What you are trying to do is not really as difficult as theDaveTheRave seems to think

I didn't intend to imply it was difficult, I just believe the the 'terminal' is scary for 'newbies' ~ even windows power users almost never go anywhere near the windows equivalent.

I remember using the windows dos prompt in front of my then sys admin, and he had a horrified look on his face when I shoved in a few commands to get the info he wanted.

> **ajgreeny said:**
> but it does demand that the commands are correct..

which is probably more my point, a newb could get the commands wrong, and decide that linux was too 'unfriendly' spitting out seemingly cryptic messages about mount points and missing file systems, especially when they just did this in windows with 'a couple of clicks' 

@wpbdry
thanks for pointing out the bad link I've corrected it now. I got over zealous with the clever 'middle click' thing that ajgreeny mentioned. which is probably one of the most usefull things in linux, but can catch you unawares sometimes if you aren't carefull I just wish you could do a middle mouse click and the scroll backwards through the previous possible items.... especially as the middle button is now often a scroll wheel also.

Davi

---

### Post by ajgreeny on 2013-12-19
It can be very dangerous, as well as giving the problem you saw, to hibernate Windows and start another OS such as Ubuntu so I very strongly recommend that you should not do it again. You are perhaps lucky that when hibernating the ntfs partition will be flagged as still in use and Linux will not mount a partition flagged in that way unless you force the mount operation; not something I ever recommend.

I don't have windows so can not help you with configuring how to get windows to shutdown fully each time, but you may already know how to do that.

You should be able to get the libraries, as you call them, that is, the folders with your data files in to show in Places by adding them to the nautilus bookmarks.  That certainly works in nautilus from 12.04 but I know nautilus has changed in several ways since then, but I assume bookmarks will still work in the same way.

@theDaveTheRave
I did not intend to give the impression that what you said was silly or incorrect, merely to suggest that copy & paste is the easiest way to proceed, and there are some things that are so much easier to explain how do in terminal with a copied command from someone you trust than trying to explain how to do it with a GUI that, in this case, I don't use, so don't really know what it may look like.

Any way it looks as if the OP has now got most of what is needed working; let's hope that the Places/bookmarks answer I gave is correct

@wpbdry
Do not be too afraid of the terminal.  It may look quite scary, and I know it was something I shied away from when I started with Ubuntu back at version 5.04, but it fairly quickly became my friend and is something I use for many things these days without so much as a second thought.  Using an alias, a simple easy to remember command in place of a complicated command-string can also be extremely useful, and is something I use a lot.  I have a hidden file in my home called .bash_aliases, which is a default for them and anything contained in that will be used by your user terminal, though not by a root terminal if you ever use one.  Here are my additions to the file, which I think is present at installation, though most of the content is commented out (line starts with #).
```
# some more ls aliases

alias am='alsamixer'
alias addppa='sudo add-apt-repository'
alias autoclean='sudo apt-get autoclean'
alias blk='sudo blkid -c /dev/null'
alias blank='wodim -vv dev=/dev/cdrw blank=all'
alias c='clear'
alias cp='cp -i'
alias cron='gedit Quicknotes/Cron_Commands.txt & crontab -e'
alias db='sudo updatedb'
alias df='df -hT'
alias dl='vnstat -d'
alias dll='vnstat -l'
alias dldays='vnstat -d > /tmp/$(date +%F-%T)-DLs && gedit /tmp/*DLs & exit'
alias effects='eog Pics/Effects.png'
alias eo='exo-open'
alias xo='xdg-open'
alias fdisk='sudo parted -l'
alias free='free -m'
alias fsck='sudo touch /forcefsck'
alias fstab='cat /etc/fstab'
alias gip='get_iplayer'
alias gipc='get_iplayer --category'
alias gipg='cd Videos/BBC_iPlayer && get_iplayer -g'
alias gipghd='get_iplayer --vmode=flashhd --get'
alias gipi='get_iplayer --info'
alias gipr='get_iplayer --type radio'
alias gpgupdate='sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys'
alias hw='sudo lshw -html > $(date +%F-%I%M)hw.html'
alias install='grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log'
alias remove='grep -iw remove /var/log/dpkg.log.1 && grep -iw remove /var/log/dpkg.log'
alias upgrade='grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log'
alias la='ls -Ap --group-directories-first'
alias ll='ls -lhp --group-directories-first'
alias lla='ls -alhp --group-directories-first'
alias l='ls -CFp --group-directories-first'
alias ls='ls -p --color=auto --group-directories-first'
alias lshw='sudo lshw -html > hardware.html'
alias menu='grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100'
alias mv='mv -i'
alias nano='nano -B'
alias parted='sudo parted -l'
alias ping='ping -c 5'
alias q='exit'
alias rm='rm -i'
alias scanhome='sudo tune2fs /dev/sda4 -l'
alias scan='sudo tune2fs /dev/sda2 -l'
alias server='python -m SimpleHTTPServer 1111'
alias session='nano .xsession-errors'
alias shred='shred -vzu'
alias ssh+='sudo service ssh start'
alias ssh-='sudo service ssh stop'
alias temp='mbmon -A -c 2 && hddtemp /dev/sda /dev/sdb'
alias version='lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -a'
alias xorg='cat /etc/X11/xorg.conf'
alias cleanhistory='grep -v '^q$' .bash_history > .bash_history2 && mv .bash_history .bash_historybak && mv .bash_history2 .bash_history'
alias ag='sudo apt-get update'
alias agu='sudo apt-get upgrade'
```
Many of these will not apply to your system, but try the ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` to see how useful they can be.  In my case I simply type **menu** and that longer command is executed.

---

### Post by wpbdry on 2013-12-19
Thanks @ajgreeny for those aliases. I think they will help me even though I don't know what half of them mean (yet) - I'm sure I will learn. Now that I know that file exists I can also create my own. But why do you say it is dangerous to hibernate Windows and run Ubuntu? What might happen? Is it also dangerous the other way around? ie. to hibernate Ubuntu and boot into Windows? Would it be dangerous if I didn't have a "Shared" hard drive partition?

---

### Post by ajgreeny on 2013-12-19
> **wpbdry said:**
> Thanks @ajgreeny for those aliases. I think they will help me even though I don't know what half of them mean (yet) - I'm sure I will learn. Now that I know that file exists I can also create my own. But why do you say it is dangerous to hibernate Windows and run Ubuntu? What might happen? Is it also dangerous the other way around? ie. to hibernate Ubuntu and boot into Windows? Would it be dangerous if I didn't have a "Shared" hard drive partition?
I can not really answer that question as I don't run windows any more.  I do know, however, that many threads on this forum and other places say that it is a "very bad thing to do" and here is a lot of info from another thread (thanks to oldfred)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enab...p-in-windows-8]("http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8")
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/...rid-sleep.html]("http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html")
[http://superuser.com/questions/14472...te-w-dual-boot]("http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot")
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials...ndows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mo...u-hybrid-boot/]("http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/")

To get the Places showing as you want again you may need to add the full pathway to the Music, Videos etc etc folders rather than just the home folders, which as you said earlier, do not actually exist any more.  I don't use nautilus any more so will have to leave you to figure out how to add bookmarks, but I will be very surprised if it can not be done.

---

### Post by wpbdry on 2013-12-19
Ok, Thanks a  lot @ajgreeny! You have been very helpful in many ways!

---

