---
title: "The same external HDD on Windows and Ubuntu?"
date: 2017-12-15
forum: New to Ubuntu
---

### Post by noxvirtox on 2017-12-15
I know it may sound a little silly, but it's something I really need to know and I haven't found another topic asking the exact same question. (only other topics about external hard drives and Ubuntu) The thing is, I have an external HDD that I have used for years to store all my pictures, music etc. But recently I made a switch from Windows 7 to Ubuntu 16.04 and I wanted to know, can I now save new files on the same hard drive using Ubuntu, or would there be any problems? Does it make a difference if the file is downloaded from the Internet or created on Ubuntu (i.e. with Gimp) I know that Linux and Windows use different file systems and I've heard somewhere about people having problems with disks used on different OSs, and since I have all my important data in there, I'd like to make sure I don't risk anything.

---

### Post by greyfaux01 on 2017-12-15
Yes most likely you should not have any problems what so ever.

If you want, you can plug the HDD into ubuntu, and run gparted, this is a graphical utility that will show you info about the HDD.. you could also run a default ubuntu program called 'disks', which will pretty much do the same thing.. IMPORTANT: dont make any changes with these programs, just look around and see what filesystem you are using..

From what i remember, if the external is using FAT32/NTFS it will work totally plugNplay.. some distros you have to install a 3rd party tool to read ntfs, but thats usually installed by default now.. I cant imagine your external being any other filesystem, unless you purposely changed it cuz you know what your doing.. even so, im pretty sure linux can read almost any filesystem, either natively, or after installing a 3rd party tool.. if you have a more obscure, or proprietary filesystem (HFS for example), just google that specific file system, for example 'HFS external drive work with ubuntu' ..

Now as far as saving files from gimp, it doesnt matter where you get the files, it matter what format their saved in.. IIRC gimp allows you to save files in jpeg as well as its standard format, of course any pc can read jpegs.. and most likely whatever gimp saves it as can be opened in windows, if not natively, then with the right plugin or viewer.. its been awhile since ive used gimp, but just search for 'gimp default file format windows' and you should get your answer...

And just to add, feel free to back up that entire hard drive somewher else too, like on a bunch of DVD's.. or at least back up the very important files.. i learned in school you generally want to have at least 3 backups of important stuff, 2 on site, and 1 remote.. now im not saying i follow that with everything, but generally speaking i back up my important stuff to mega, and have it at least on 1 external, and whatever computer i happen to be using.. i try at least..

---

### Post by HermanAB on 2017-12-15
Howdy,

Both FAT (in all its variants) and NTFS are cross platform and work on Windows, Linux, BSD and Mac.  However, if NTFS would develop a problem, then it can only be fixed on a Windows computer.  So, while NTFS is the better choice (since it has a journal), you should always keep at least a Windows virtual machine around for those odd occasions when you need to do your taxes with a Windows only program, or fix a NTFS disk.

---

### Post by DuckHook on 2017-12-15
I have a different take on all of the above.

Most of the Microsoft file systems have appreciable limitations. Both FAT and NTFS fragment severely. Moreover, as HermanAB observes, if you ever need to repair such a file system, Windows must be used. MS file systems are also not built to accommodate Linux permissioning philosophy, so security and compatibility suffer. In the final analysis, even though Linux will read and write to NTFS file systems transparently, this is to Linux's credit and should not be confused for real compatibility.

Though this matter is largely one of personal choice, my own (very personal) recommendation is this: If you are completely committed to only using Ubuntu, then I would convert that external HDD to a file system native to Linux. The obvious candidate is EXT4. EXT4 is more robust, highly resistant to fragmentation, supports the permissions that Linux expects and, not least, is fixable and maintainable with a wealth of Linux tools and apps.

And finally: if these files are as important to you as you state, then lack of backups is by far your number one risk—not the nature of your file system. Even if you do nothing more than occasionally mirror the contents of that HDD, this means using another HDD of similar size. This in turn means that you could easily change your file system into EXT4, simply by formatting your new HDD as such, copying your files over, then reformatting your old HDD to same, etc.

---

### Post by leunam12 on 2017-12-15
I pretty much agree with DuckHook, if you are going to use your external HDD on a Windows Machine you need NTFS or FAT32. If you are using only Linux it is better to have ext4 filesystem. Now, if you decide to keep NTFS and you are planning to use that drive to backup your home directory I strongly suggest that you make an ext4 partition for that purpose.

---

### Post by noxvirtox on 2017-12-15
Thank you for all your replies, I am mostly planning to use this HDD on Ubuntu but sometimes I will also plug it on the laptop with Windows 10 so I think I will leave everything as it is, as long as I know it won't cause any damage that's all that matters to me. (though I still make backups on DVDs occassionally)

---

