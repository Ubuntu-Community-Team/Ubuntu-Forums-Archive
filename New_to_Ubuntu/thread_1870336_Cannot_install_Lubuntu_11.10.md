---
title: "Cannot install Lubuntu 11.10"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by inger on 2011-10-27
I have a PC with these specifications:
CPU 1.6 GHz
RAM 1GB 
Disk 8GB PSSD
 
I have tried to install Lubuntu 11.10. The md5sums value for the Lubuntu is: a0307761af5a0e3374f65959366d1dcb (Just what it should be). Then I choose language and select Install Lubuntu. After doing this, I got this message from the PC:
>  
Welcome to Ubuntu 11.10(GNU/Linux 3.0.0-12-generic i686)
To run a command asAdministrator (user "root"), use "Sudo <command>".
ubuntu@ubuntu:~$

 
What may I do to install Lubuntu 11.10.
I have used Lubuntu 11.04 before on the same PC. I wanted to install the new version because on 11.04 I had some troubles. the PC did not start every time.
 
Can anyone help me?

---

### Post by mörgæs on 2011-10-27
See 'Desktop ISO boot to a terminal prompt' in
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot)

---

### Post by inger on 2011-10-27
I have tried to write: sudo start lxdm. 
The answer then is: lxdm start/running, process 3106
 
I don't get a close button when trying to install. I tried to press Esc, but I got stdin error.
 
Any other ideas?

---

### Post by westie457 on 2011-10-27
> Welcome to Ubuntu 11.10(GNU/[COLOR="Red"]Linux 3.0.0-12-generic i686[/COLOR])
To run a command asAdministrator (user "root"), use "Sudo <command>".
ubuntu@ubuntu:~$

Hi, the above is from your first post. Is your machine capable of running a 64bit OS? 

To chech, if unsure run ```
lshw
``` in a terminal. Look at the first instance of a line starting 'width =' the number given should be either 32 or 64.

If it is 32 you are trying to install the wrong one and should try dl'ing one for 32bit architecture. it will have [COLOR="Blue"]i386[/COLOR] for the download link.

---

### Post by amjjawad on 2011-10-27
> **inger said:**
> I have a PC with these specifications:
CPU 1.6 GHz
RAM 1GB 
Disk 8GB PSSD
 
I have tried to install Lubuntu 11.10. The md5sums value for the Lubuntu is: a0307761af5a0e3374f65959366d1dcb (Just what it should be). Then I choose language and select Install Lubuntu. After doing this, I got this message from the PC:

 
What may I do to install Lubuntu 11.10.
I have used Lubuntu 11.04 before on the same PC. I wanted to install the new version because on 11.04 I had some troubles. the PC did not start every time.
 
**Can anyone help me?**

Definitely :)

Please check this thread: [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

You'll find ALL what you need. If you didn't, let me know. I'm a member of Lubuntu Team and it's a pleasure to help!

Please check the Release Notes so you can get to the Live Desktop. It's in that thread above.

Thank you for choosing Lubuntu :)

---

### Post by amjjawad on 2011-10-27
> **inger said:**
> I have tried to write: sudo start lxdm. 
The answer then is: lxdm start/running, process 3106
 
I don't get a close button when trying to install. I tried to press Esc, but I got stdin error.
 
Any other ideas?

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot#Desktop_ISO_boot_to_a_terminal_prompt)

> In some cases, Lubuntu desktop ISO boots to a terminal prompt instead of  the desktop session when "Try Lubuntu without installing" is chosen.  You can manually start the session by typing "sudo start lxdm" ([854837]("https://bugs.launchpad.net/bugs/854837")). Or you can choose "Install Lubuntu" and once the installer starts, click "Close" then "Close" and you'll get the live desktop. 

When you see this:
[IMG]http://i53.tinypic.com/2cql5de.jpg[/IMG]

Select "Install Lubuntu" then when you'll see this:

[IMG]http://i52.tinypic.com/v7s1e9.jpg[/IMG]

Click Quit then confirm that (Quit again) and you'll get the Live Desktop.
[IMG]http://tinypic.com/usermedia.php?uo=aA1TvidBoMhkFAC7Vom6NIh4l5k2TGxc[/IMG]

---

### Post by amjjawad on 2011-10-27
> **mörgæs said:**
> See 'Desktop ISO boot to a terminal prompt' in
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot)

Thank you :)

I guess I'll write that in a better way so everyone can see it clearly.
I'll write that on my thread and add the link to the index and also add that to the Wiki Pages. What do you think?

---

### Post by mörgæs on 2011-10-27
Yes, we need to get more attention to this (and to the other workaround you suggested).

Does the alternate ISO have the same problem, by the way?
[http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/)

---

### Post by amjjawad on 2011-10-27
> **mörgæs said:**
> Yes, we need to get more attention to this (and to the other workaround you suggested).

[http://ubuntuforums.org/showpost.php?p=11398602&postcount=35](http://ubuntuforums.org/showpost.php?p=11398602&postcount=35)

> 
Does the alternate ISO have the same problem, by the way?
[http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/)

I need to test that but I don't have time :(

---

### Post by inger on 2011-10-27
Thanks.
 
My problem is that I don't get a new GUI after chosing "Install Lubuntu" I only get to a black terminal and logged in as user. There I can put my commands. the Welcome-screen never appears.
 
I have tried to install Lubuntu with two several screens. Same problem.
I think it is very strange because I could install Lubuntu 11.04 in same PC.

---

