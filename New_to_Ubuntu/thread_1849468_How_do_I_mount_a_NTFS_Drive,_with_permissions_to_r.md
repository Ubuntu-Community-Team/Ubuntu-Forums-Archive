---
title: "How do I mount a NTFS Drive, with permissions to run .BIN and Linux executables?"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by Conzeit on 2011-09-24
Hey all, glad to be in this very heplful "ubuntu", this community.

I've already posted this issue in Launchpad and I got some help, but I still dont know how to fix it I guess I'm the kind of guy that needs guides for this :p 

[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/171724](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/171724)

Basically it goes like this, I got a NTFS drive from which I want to run .BIN .JAR and other linux executables, I have tried changing permissions in the right click > permissions menu, but it simply doesnt allow me to change them and if it does they dont stick. I've also done it in terminal with sud chmod +x file.bin but that doesnt seem to work either. help?

---

### Post by Lisiano on 2011-09-24
```
sudo mount -o fmask=000,dmask=000 /dev/sdx /mnt
```
Replace sdx with the actual partition, if you don't know it, mount it using Nautilus and look at the output of this command```
mount
```
To launch .jar files, run ```
java -jar file.jar
```
The executable bit is not needed in this case.
I don't know what you might have in the .bin files, Windows files? In that case ```
wine file.bin
```
And for ELF files, ```
./file
```

EDIT: Noticed about the bin files, same story as ELF files then.

EIDT2: To make that permanent, create a folder where you will usually mount the disk
```
sudo mkdir /media/Data
```
Now edit fstab
```
gksudo gedit /etc/fstab
```
And add this line to the very end
```
/dev/sdx       /media/Data       auto        defaults,noauto,users,rw,fmask=000,dmask=000  0   2
```
Remove noauto if you want it to mount on boot, change rw to ro if you want it to be read-only.

---

### Post by Morbius1 on 2011-09-24
[COLOR=Blue]**Pre-step**[/COLOR]: If you currently have the partition mounted - unmount it.

[1] Run the following command to find out how your system sees the partitions:
```
sudo blkid -c /dev/null
```For the purposes of this example let's say it comes back with something like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" [2] Create a permanent home for the partition:
```
sudo mkdir /media/WinXP
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=DA9056C19056A3B3 /media/WinXP ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```[5] Run the following command that will test for errors and if there are none mount the partition:
```
sudo mount -a
```

---

### Post by Morbius1 on 2011-09-24
@Lisiano,  I seem to be going out of my way to step on your posts. That is not my intent. My apologies.

---

### Post by Lisiano on 2011-09-24
Hey, the more options the better, no? Freedom of choice, hehe. Although why the nocache on blkid?

---

### Post by Morbius1 on 2011-09-24
bklid remembers and stores the information from the last time it's used ( like during the install ). If you manipulate your partitions ( resize, reformat, etc.. ) it's output [COLOR=Blue]**may**[/COLOR] not be accurate. For the average new linux user it's overkill. 

I've gotten into the habit of using it because I'm constantly trying out new distros plus I don't know the history of what the user's done to his machine so it's best to start with a clean view.

---

### Post by Conzeit on 2011-10-01
Ok guys, first I want to thank you all for the advice, this thread helped me understand fstab better and made me more comfortable with Linux, 

I read your advice, went and read some fstab guides and while the executable files still only work in my Linux system drive, I felt like I had learnt enough about this and I could learn how to manage executables later.

I ended up mounting the drive in the best way I saw from the advice here and in the guides ```
/dev/sda3 /media/DitYself auto user,rw,dev,exec,auto,async,uid=myuserlogin  0   0 
``` The reason I'm coming back now, is that when I make a change to the NTFS hard drive in linux and go to WinXP it will try to run a checkdisk, which reads changes made in linux as an error, sometimes sending the files to a hidden found000 folder, sometimes even turning folders into unusable files by removing their extension.

 I'm getting a bit tired of this whole thing, can I get some advice about the best way to share files between narwhal and XP? I've read about [http://www.fs-driver.org/](http://www.fs-driver.org/) programs which allow XP to read Linux HDs and after all this I'm not sure which way is best

I have no idea why every time I edit my post this weird barrage of text appears, but I cant help it so here it goes =/

here comes ******** 
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by Lisiano on 2011-10-01
This is probably due to the async option you gave it. It means that any changes you do will be written LATER, as in if you ever hard-reboot or get a power loss, the changes will not be made, try using sync instead or use this argument instead ```
defaults,nls=utf8,rw,users,sync,umask=000
```Hybrid on my suggestion and Morbius1 suggestion

---

### Post by Conzeit on 2011-10-02
Oh? I did that because I thought this was the standard fare for hard drives! a guide I read said sync was only common for floppy disks. I read that the "default" option included async actually.  Thanks for your help, I WILL try your suggestion =)

EDIT: that worked wonders Lisiano! thank you so much for your help and to everybody else too. 
EDIT: Actually I just realized what was key in getting this working was adding "ntfs-3g" to the fstab options, since this is the driver that supports ntfs properly in Ubuntu.

get ready for senseless code O_Oimg, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

