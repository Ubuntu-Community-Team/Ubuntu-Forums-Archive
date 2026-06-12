---
title: "Virtual Drive and WINE?"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by adventure man on 2012-03-11
I have a .bin file (old game) that I am trying to install.  I've tried furiusiso which recognizes the bin file and shows me the files on the image but when I go to install through wine (setup.exe), it tells me to "Please Insert cd".  This image file works fine in windows using magiciso or daemon tools.  

The only thing I can think of is that the virtual drive is not showing up as a cd drive but rather a hard drive (files), causing the issue.  Any clues guys on how to get a true virtual cd drive in xubuntu?  I'm a noob so please use simple language :confused:

OS: Xubunu 11.10

---

### Post by Toz on 2012-03-12
Try this:

1. Open the bin file with furiusiso (note: furiusiso will mount the bin file and will also place its contents in a folder in your home directory)

2. Run the "Configure Wine" program (from the Wine Menu) or from the command prompt:
```
winecfg
```

3. Go to the Drives tab and click on the "Add button" and add a cd drive ( I added D: ). Then click on the "Browse" button and select the directory in your home folder that furiusiso uses to mount the bin file in (sorry but don't have furiusiso installed to tell what the default folder name is). Click OK.

4. Then try running the setup file, or from the command line:
```
wine "D:\setup.exe"
```

---

### Post by adventure man on 2012-03-16
Steps 1 -3 went without a hitch.  Step 4 wine/terminal tells me "Command not found".  Am I possibly writing it wrong?

:confused:

So I opened up the folder where FuriusISO mounted the BIN to, double clicked the setup.exe file and it tells me again "Please Insert Ballance CD"  :mad:

Any ideas?

---

### Post by Toz on 2012-03-17
> **adventure man said:**
> Steps 1 -3 went without a hitch.  Step 4 wine/terminal tells me "Command not found".  Am I possibly writing it wrong?
Make sure the spelling of the setup file is correct. Linux is case sensitive. It could be Setup.exe, SETUP.EXE, etc...
Although the method mentioned above works for me, you can also try, in lieu of step 4, trying to start it the linux way:
```
wine /path/to/setup.exe
```

> So I opened up the folder where FuriusISO mounted the BIN to, double clicked the setup.exe file and it tells me again "Please Insert Ballance CD"  :mad:

Any ideas?
Type in the following command and post back the results:
```
ls -l ~/.wine/dosdevices
```

---

### Post by adventure man on 2012-03-17
I retried it, spelling everything perfectly.  No dice.

Here are the results from that code you told me to input into terminal:
zorfilak@ubuntu:~$ ls -l ~/.wine/dosdevices
total 0
lrwxrwxrwx 1 zorfilak zorfilak 10 2012-01-21 15:46 c: -> ../drive_c
lrwxrwxrwx 1 zorfilak zorfilak 25 2012-03-16 22:11 d: -> /home/zorfilak/Downloads/
lrwxrwxrwx 1 zorfilak zorfilak  1 2012-03-16 22:15 e: -> /
lrwxrwxrwx 1 zorfilak zorfilak 14 2012-03-16 22:15 h: -> /home/zorfilak

---

### Post by Toz on 2012-03-17
That should work - at least it works for me for isos and bins. Is it possible that there is copy protection preventing the install? Maybe its looking for a specific CD or signature on a CD? (Though that won't explain why it works on Windows and not here).

EDIT: Think I got it now. Here is mine that worked.
```
$ ll ~/.wineB/dosdevices/total 36
drwxrwxr-x 2 toz toz 4096 2012-03-17 22:39 ./
drwxrwxr-x 4 toz toz 4096 2012-03-17 22:39 ../
lrwxrwxrwx 1 toz toz   10 2012-03-17 22:36 c: -> ../drive_c/
lrwxrwxrwx 1 toz toz    8 2012-03-17 22:36 d:: -> /dev/sr0
lrwxrwxrwx 1 toz toz   53 2012-03-17 22:37 e: -> /home/toz/Downloads/Ballance/mnt/
lrwxrwxrwx 1 toz toz   62 2012-03-17 22:38 e:: -> /home/toz/Downloads/Ballance.iso
lrwxrwxrwx 1 toz toz    1 2012-03-17 22:36 z: -> //

```
...note the two entries for the drive ( e: & e:: )

I did this:

```

ln -s /home/toz/Downloads/Ballance/mnt/ /home/toz/.wineB/dosdevices/e\:
ln -s /home/toz/Downloads/Ballance/Ballance.iso /home/toz/.wineB/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

```
...and it installed. Doesn't work, but it installed.

EDIT2: Doesn't look good: [http://bugs.winehq.org/show_bug.cgi?id=23376]("http://bugs.winehq.org/show_bug.cgi?id=23376")

---

### Post by adventure man on 2012-03-18
> **Toz said:**
>  
  
[/code]...and it installed. Doesn't work, but it installed.

EDIT2: Doesn't look good: [http://bugs.winehq.org/show_bug.cgi?id=23376](http://bugs.winehq.org/show_bug.cgi?id=23376)

Thanks a bunch Toz! :guitar:
I'm just gonna leave it be then and not rip my hair out.  :KS

---

### Post by Toz on 2012-03-18
Well this is interesting. On a hunch, I went into winecfg and enabled the "Emulate a virtual desktop" option in the graphics tab, and now the game works (albeit in a window and not full screen).

---

### Post by adventure man on 2012-03-18
ln -s /home/zorfilak/Downloads/Ballance_bin/mnt/ /home/zorfilak/.wineB/dosdevices/e\:
ln -s /home/zorfilak/Downloads/Ballance_bin/Ballance.bin /home/zorfilak/.wineB/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

**^^^gives me the setup to start installing.  But then I get the same cd check error._  This is what terminal tells me_: **

fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002


[B]
_These are my devices from an earlier code you gave me_:[/B]
zorfilak@ubuntu:~$ ls -l ~/.wine/dosdevices
total 0
lrwxrwxrwx 1 zorfilak zorfilak 10 2012-01-21 15:46 c: -> ../drive_c
lrwxrwxrwx 1 zorfilak zorfilak 28 2012-03-18 14:23 e: -> /home/zorfilak/Ballance_bin/


**Where am I going wrong** :confused:

---

### Post by Toz on 2012-03-18
Oops, I'm using multiple wine prefixes. The one I used for testing this is called **.wineB** whereas yours is **.wine**.

Secondly, I'm using different locations for my files and mount.

In which directory is the Ballance iso located on your computer?
What is the name of the Ballance bin file?
In which directory does furiusiso extract the files to?

With this information, we can create the proper commands. Something like this:
```

ln -s <ballance_mount> /home/$USER/.wine/dosdevices/e\:
ln -s <ballance_iso> /home/$USER/.wine/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

```
...where:
   <ballance_mount> = the directory where furiusiso has extracted the bin file
   <ballance_iso> = the directory and file name of the ballance bin file

---

### Post by adventure man on 2012-03-18
> **Toz said:**
> Oops, I'm using multiple wine prefixes. The one I used for testing this is called **.wineB** whereas yours is **.wine**.
 
[B]Made the fix but it didn't change anything.
[/B] 
> **Toz said:**
> Secondly, I'm using different locations for my files and mount.

In which directory is the Ballance iso located on your computer? **It's still a bin file and it is located in the "Downloads" folder.**
What is the name of the Ballance bin file? **Ballance.bin**
In which directory does furiusiso extract the files to? **home/zorfilak/Ballance_bin**
> **Toz said:**
> 
With this information, we can create the proper commands. Something like this:
```

ln -s <ballance_mount> /home/zorfilak/Ballance_bin
ln -s <ballance_iso> /home/zorfilak/Downloads/Ballance.bin
wine "E:\Setup\Setup.exe"

``` 

**^^^I tried that but it did the same thing as before (need cd).**

---

### Post by Toz on 2012-03-18
Just to confirm the commands. 

First, remove any existing links that may be messing things up:
```

rm /home/zorfilak/.wine/dosdevices/e:\:
rm /home/zorfilak/.wine/dosdevices/e:\:\:

```
...then re-create the links:
```

ln -s /home/zorfilak/Ballance_bin /home/zorfilak/.wine/dosdevices/e\:
ln -s /home/zorfilak/Downloads/Ballance.bin /home/zorfilak/.wine/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

```

It might help if you posted back the results of all of those commands. Maybe copy/paste from the terminal when they're all done (to check to see if they were successful).

Also, my file is an .iso file and yours is a .bin. Might be a problem, but lets do the above first to see if it works.

---

### Post by adventure man on 2012-03-22
> **Toz said:**
> Just to confirm the commands. 

First, remove any existing links that may be messing things up:
```

rm /home/zorfilak/.wine/dosdevices/e:\:
rm /home/zorfilak/.wine/dosdevices/e:\:\:

```...then re-create the links:
```

ln -s /home/zorfilak/Ballance_bin /home/zorfilak/.wine/dosdevices/e\:
ln -s /home/zorfilak/Downloads/Ballance.bin /home/zorfilak/.wine/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

```It might help if you posted back the results of all of those commands. Maybe copy/paste from the terminal when they're all done (to check to see if they were successful).

Also, my file is an .iso file and yours is a .bin. Might be a problem, but lets do the above first to see if it works.

I converted the .bin file to an .iso file and will use the iso file from now on.  I get the same error though.  I configure wine, open terminal, pop in the code (slightly modified to reflect the .iso change), it  goes to install, then asks me for the cd. :confused:
Always the same thing :(
Here is what terminal gives me for error code:

```
zorfilak@ubuntu:~$ ln -s /home/zorfilak/Ballance_iso /home/zorfilak/.wine/dosdevices/e\:
ln: creating symbolic link `/home/zorfilak/.wine/dosdevices/e:/Ballance_iso': Function not implemented
zorfilak@ubuntu:~$ ln -s /home/zorfilak/Downloads/Ballance.iso /home/zorfilak/.wine/dosdevices/e\:\:
ln: creating symbolic link `/home/zorfilak/.wine/dosdevices/e::': File exists
zorfilak@ubuntu:~$ wine "E:\Setup\Setup.exe"
fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)

```

---

### Post by Toz on 2012-03-22
> zorfilak@ubuntu:~$ ln -s /home/zorfilak/Ballance_iso /home/zorfilak/.wine/dosdevices/e\:
ln: creating symbolic link `/home/zorfilak/.wine/dosdevices/e:/Ballance_iso': [COLOR="Red"]Function not implemented[/COLOR]
zorfilak@ubuntu:~$ ln -s /home/zorfilak/Downloads/Ballance.iso /home/zorfilak/.wine/dosdevices/e\:\:
ln: creating symbolic link `/home/zorfilak/.wine/dosdevices/e::': [COLOR="Red"]File exists[/COLOR]
It didn't work (I just realized I had an error in the rm commands from the previous post. sorry). Try it again with these commands: 
```

rm /home/zorfilak/.wine/dosdevices/e\:
rm /home/zorfilak/.wine/dosdevices/e\:\:
ln -s /home/zorfilak/Ballance_iso /home/zorfilak/.wine/dosdevices/e\:
ln -s /home/zorfilak/Downloads/Ballance.iso /home/zorfilak/.wine/dosdevices/e\:\:
wine "E:\Setup\Setup.exe"

```
Post back the results of all of those commands to confirm that they were successful.

---

### Post by adventure man on 2012-03-22
Well it managed to install ):P

BUT there is no sound :mad: (game plays fine though)

I copied this off of terminal as I installed and then started the program (there is a tidbit concerning audio if you scroll near the end of it, I couldn't understand it). I also changed the settings in wine config audio section, to no avail :(

```
zorfilak@ubuntu:~$ rm /home/zorfilak/.wine/dosdevices/e\:
zorfilak@ubuntu:~$ rm /home/zorfilak/.wine/dosdevices/e\:\:
zorfilak@ubuntu:~$ ln -s /home/zorfilak/Ballance_iso /home/zorfilak/.wine/dosdevices/e\:
zorfilak@ubuntu:~$ ln -s /home/zorfilak/Downloads/Ballance.iso /home/zorfilak/.wine/dosdevices/e\:\:
zorfilak@ubuntu:~$ wine "E:\Setup\Setup.exe"
fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
zorfilak@ubuntu:~$ fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ballance\\Bin\\InterfaceControls.dll") not found
err:module:import_dll Library InterfaceControls.dll (which is needed by L"C:\\Program Files\\Ballance\\Managers\\CK2UI.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ballance\\Managers\\CK2UI.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ballance\\Bin\\InterfaceControls.dll") not found
err:module:import_dll Library InterfaceControls.dll (which is needed by L"C:\\Program Files\\Ballance\\Managers\\CK2UI.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ballance\\Managers\\CK2UI.dll") not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33d968,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:win:EnumDisplayDevicesW ((null),0,0x33d954,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d85c,0x00000000), stub!
fixme:avifile:AVIFileExit (): stub!
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 6 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x2041c0,0x20393c): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting


```

---

### Post by Toz on 2012-03-22
Good news.

From your output:
> err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ballance\\Bin\\InterfaceControls.dll") not found

Try installing MFC42.dll via:
```
winetricks mfc42
```

---

### Post by adventure man on 2012-03-22
> **Toz said:**
> Good news.

From your output:


Try installing MFC42.dll via:
```
winetricks mfc42
```

Ok, I installed that. Install went smoothly.
I got sound to work after I played with the audio settings in wine.  It worked for a little bit, then I changed the audio settings in wine a second time (because the sound was a bit scratchy) and it stopped working, even after I switched it back. :confused:

Another thing I noticed, is that the game freezes after I grab the first extra life on stage 1. It freezes every single time. :mad:

**UPDATE: I restarted the computer and the sound works.  It doesn't work when the audio setting in wine config is "Full" only under "Emulation" mode.  But the sound is horrible with a loud hissing tv static sound and popping that makes it irritating to listen to.**

---

