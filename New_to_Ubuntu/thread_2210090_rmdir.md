---
title: "rmdir"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by thomas-ahlborn on 2014-03-08
Somehow I've created a directory titled ~ as you can see here:
> eric@xxx:~$ ls -l
total 48
drwxrwxr-x 3 eric eric 4096 Mar  8 19:00 ~
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Desktop
drwxr-xr-x 3 eric eric 4096 Mar  8 19:29 Documents
drwxr-xr-x 3 eric eric 4096 Mar  8 18:50 Downloads
-rw-r--r-- 1 eric eric 8942 Mar  3 16:07 examples.desktop
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Music
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Pictures
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Public
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Templates
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Videos



Now how do I remove this directory without screwing myself? I don't think the command is:
> $ sudo rmdir ~
I am more leaning towards:
> $ sudo rmdir /home/eric/~
I'm so scared right now. I will not try to remove it until I know what I think will work actually is confirmed to work. Thanks for your help.

---

### Post by panorain on 2014-03-08
**How do I remove a full directory in Linux?**

 When attempting to remove a [directory]("http://www.computerhope.com/jargon/d/director.htm")  using a command such as the rmdir command, you may receive a prompt  such as "rmdir: 'dir': Directory not empty" and be unable to delete the  directory. To remove a directory that is full with other files or  directories, use the below command.
 ```
rm -r directory


```  In  the above example, you would replace "directory" with the name of the  full directory you wish to delete. So if the directory was named files,  you would type: rm -r files
   Doing the above command would delete the files and directories, but  would require a prompt for each of the files. If you also don't want to  receive a prompt use the command below.
   ```
rm -rf example


```   In the above example, the "example" directory would be deleted with no prompt or message.

Thank you,

---

### Post by thomas-ahlborn on 2014-03-09
Not really sure you answered my question panorain but thank you anyways. I've figured it out! Here's what I did:
As you saw above my problem was that I had created a folder titled ~
When ls-ing my home directory, there was this directory inside:
> [COLOR=#000000]*drwxrwxr-x 3 eric eric 4096 Mar 8 19:00 ~*[/COLOR]
Inside this directory were some things I wanted. I successfully copied those items recursively into the correct location. Then tested things:
> eric@xxx:~$ ls -l ~/
total 48
drwxrwxr-x 2 eric eric 4096 Mar  8 21:30 ~
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Desktop
drwxr-xr-x 3 eric eric 4096 Mar  8 19:29 Documents
drwxr-xr-x 3 eric eric 4096 Mar  8 18:50 Downloads
-rw-r--r-- 1 eric eric 8942 Mar  3 16:07 examples.desktop
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Music
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Pictures
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Public
drwxr-xr-x 2 eric eric 4096 Mar  3 16:09 Templates
drwxr-xr-x 3 eric eric 4096 Mar  8 21:24 Videos



Notice above how the relative path gives me the contents of my home directory including the folder titled '~'
Now I will do ls with an absolute path:
> eric@xxx:~$ ls -l /home/eric/~
total 0
-rw-rw-r-- 1 eric eric 0 Mar  8 21:31 things


See that strange difference? I didn't try it but I'm guessing if I had done rm -r ~ my entire user folder would have been blasted away. SO use absolute paths when rm-ing :idea:

---

### Post by Impavidus on 2014-03-09
Either absolute paths or quoting, which disables expansion of leading ~ into the path to your home directory, or any other way to put the ~ not in leading position:```
rmdir ~/~
#OR
rmdir "~"
#OR
rmdir ./~
```assuming the directory is empty. Don't lean towards using sudo to do things in your home directory. You never need it (except for recovering from earlier errors), so the only cases where adding sudo has any effect are the cases where it does something you don't want.

BTW, **rm -r ~** won't delete your home directory, as you don't have permissions for that. It will delete all it's contents though.

---

### Post by panorain on 2014-03-09
How can a person protect their home directory then from some other person that doesn't like you from walking up and entering rm -r in your home directory and walking away? Always make sure you lock your screen or logout when not at your computer?

Thank you,

---

### Post by Irihapeti on 2014-03-09
> **panorain said:**
> How can a person protect their home directory then from some other person that doesn't like you from walking up and entering rm -r in your home directory and walking away? Always make sure you lock your screen or logout when not at your computer?

Thank you,

Yes, always logout or lock the screen, unless perhaps you live on your own in a secure building and you don't take the computer anywhere else.

---

### Post by Vaphell on 2014-03-09
screen lock is like having locks in your door. It will stop the cases of 'opportunity makes a thief' but won't stop a dedicated attacker from intruding.

physical access = root, in other words all bets are off.

If some other person can just walk up to your computer, not only he can wipe your home, he can also restart, which gives him power to do anything with the computer. He can simply boot his own system from USB which gives him root right off the bat and then he's free to plant bad stuff on the hdd mounted with full access if the hdd is not encrypted. Your filesystems don't care, root is root.

---

### Post by panorain on 2014-03-09
Can a person set a 'boot password' in bios that would help the situation of someone accessing root? Is it easy to 'encrypt' a harddisk that already has an operating system installed? This has me concerned now even more because I have logged in with an .iso image to edit a file I messed up.. What can a beginner do to lock down root filesystem in Ubuntu?

Thank you,

---

### Post by Vaphell on 2014-03-09
No need to become paranoid, it's unhealthy ;-)

yes, usually you can set up a bios password to to prevent changing boot priority from hdd to usb... unless the attacker has means and time to reset bios (eg by using a jumper or by removing the battery for few seconds), which could take the pw down ;-)

As for encryption, you can encrypt some/all partition(s) so booting some other system doesn't give access to them. Sadly i think encrypting them in place is impossible and you need to dump the data somewhere else, recreate the partition with encryption and move the data back.
To minimize risk the system shouldn't have the pw anywhere (ie has to be typed in every time) and your most sensitive data should only be decrypted for immediate use, never unlocked for hours just because. Encryption becomes rather worthless if you leave it opened for extended periods.
There are some NSA level attacks against such encryption that exploit physics of RAM etc, but if the attackers are so skilled and determined to hack you, you have much bigger problems ;-)


You can encrypt everything (safest), or only /home in case of separate partition (safe data but allows planting malware on unencrypted / so at runtime your data could be intercepted once you decrypt it to use it). There is a performance hit, because the CPU needs to encode/decode data with each hdd access.

The same thing that works against attackers works against the ease of data recovery and general problem fixing. They become much more annoying and personally i wouldn't commit to full encryption before learning on some test partition everything that needs to be known about the use and maintenance of these things.
There are plenty of stories of noobs who didn't pay attention when the installer said "better remember this pw or else". They reinstalled without backing up first and lost access to their data because they couldn't remember the passphrase. Sloppiness with encryption means kissing your data goodbye.
Once the know-how is nailed down, one can think about locking his computer down tightly.



now from philosophical angle:
Security is a spectrum. The more layers you use, the more secure the system is, but perfect safety is a pipe dream. Perfect safety would require something like an airgapped computer in a lead screened vault in a basement of a fortress built at the ocean floor, but the utility of such a machine would be nonexistent, who would want to use a computer like that?
You need to pick a point on the spectrum where the ease of use and the safety strike perfect balance.

---

