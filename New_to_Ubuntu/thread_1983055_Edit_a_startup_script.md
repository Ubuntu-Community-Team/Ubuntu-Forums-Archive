---
title: "Edit a startup script"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by brandonwarrington on 2012-05-19
Using VirtualBox on Windows 7 Home, with an Ubuntu 64 guest

Trying to have a PERMANENT windows shared folder between my Windows 7 host and Ubuntu Guest

Got the shared folder to work, using:

sudo mkdir /media/windows-share

then:

sudo mount -t vboxsf folder-name /media/windows-share

Don't understand how to edit this rc.local script in /ect/init.d/rc.local so it starts automatically.

---

### Post by cryptotheslow on 2012-05-19
I'd have thought you could add it to /etc/fstab rather than rc.local

Try adding this line to the end of /etc/fstab
```
folder-name /media/windows-share vboxsf defaults 0 0
```

** obviously changing '*folder-name*' to suit your setup.

Once you've save the changes restart the VB and it should mount automagically.

---

### Post by brandonwarrington on 2012-05-19
> **cryptotheslow said:**
> I'd have thought you could add it to /etc/fstab rather than rc.local

Try adding this line to the end of /etc/fstab
```
folder-name /media/windows-share vboxsf defaults 0 0
```

** obviously changing '*folder-name*' to suit your setup.

Once you've save the changes restart the VB and it should mount automagically.



The /etc/fstab folder does not exist. I have an /etc/fstab.d but there are no files in it..

_

---

### Post by Lisiano on 2012-05-19
/etc/fstab is not a folder, it's a file. Similar to how C:\Windows\System32\drivers\etc\hosts doesn't have an extension, fstab doesn't have an extension, but they both are mere text files.

---

### Post by brandonwarrington on 2012-05-19
> **Lisiano said:**
> /etc/fstab is not a folder, it's a file. Similar to how C:\Windows\System32\drivers\etc\hosts doesn't have an extension, fstab doesn't have an extension, but they both are mere text files.

=0

I see 

How do I get permissions to modify this file?

I guess its read only, in the properties the option to get rid of read only is greyed out.

_

---

### Post by Lisiano on 2012-05-19
Open a terminal (Ctrl+Alt+T) and type ```
gksudo gedit /etc/fstab
```This will let you edit the file temporarily

DO NOT modify permissions for system files if you are unsure of what they are and what they are responsible for.

I repeat: ***_[SIZE="4"][COLOR="Red"]DO NOT MODIFY PERMISSIONS OF SYSTEM FILES[/COLOR][/SIZE]_***

Sorry if it sounds offensive.

---

### Post by brandonwarrington on 2012-05-19
That worked, thank you.

+1 for cryptotheslow and Lisiano

---

### Post by Lisiano on 2012-05-19
If you have no more questions (Like why not to modify permissions or about fstab, or what the command I gave you did) then please mark the thread as solved in the thread tools above.

---

### Post by brandonwarrington on 2012-05-19
I am a Windows user and am not used to having to enter all this code into terminal to get things done. 

Is there a list of commands somewhere??

---

### Post by Lisiano on 2012-05-19
There is no giant list of what every command does, but you can do this if you wish to find out about what a command does.
Open a terminal and type ```
man command
```where command is what you want to find out about, for example ```
man man
```
Or use Google and search for the same thing, for example [man gedit](https://www.google.com/search?q=man+gedit)

There is also a good compilation of resources in the stickies here
[Linux Command Line Learning Resources](http://ubuntuforums.org/showthread.php?t=1909108)


Note, you can do most stuff without a command line, but most administrative stuff use a terminal. We suggest it early on so you will not have to get used to it later on and won't be as intimidated. And it's also easier to tell you exactly what command to type instead of listing multiple ways how to do it in a GUI.

Again, if you want to know more about the commands we suggest you, you can always ask before or after you use them. We will always warn if they are destructive for example using tools to partition your disk.

---

### Post by brandonwarrington on 2012-05-19
Thanks

---

### Post by Lisiano on 2012-05-19
Your welcome.
A quick tip, to auto complete stuff you can use tab, you can also use it to see how many commands you can run from the terminal. In my case it's 3263. Just open one and double press tab. Simple reason why there ain't  no giant list.

---

