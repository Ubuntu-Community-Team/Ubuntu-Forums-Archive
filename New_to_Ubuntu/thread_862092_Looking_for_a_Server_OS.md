---
title: "Looking for a Server OS"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by ngreenwood6 on 2008-07-17
Hello all,

I am new to the whole server operations. I want to set-up a home server. I am looking for the right operating system to do what i need to do with an easy to use GUI. Basically all I want to be able to do is file sharing, authentication to the network(domain controller), remote access, backups, and push out installs to workstations for software upgrades and OS reinstalls. I want the user profiles stored on the server so that no matter which computer i log into, my desktop and favorites are always there. If anyone knows of a good os for what I have described please let me know with maybe some set-up information.

Thanks

---

### Post by t0p on 2008-07-17
Seeing as you're in an ubuntu forum... how about ubuntu?

If for some reason you don't want to use ubuntu, I've heard good things about CentOS

---

### Post by Dedoimedo on 2008-07-17
Hello,

Actually, anything will do, although I'd personally recommend CentOS for a server. And even though you may like GUI, I STRONGLY recommend against using GUI for server configurations.

1. Using CLI, you'll actually understand what you do.
2. It's way faster.
3. Less bugs.

4. Most people, including myself, will be able to help you with command line, but not with GUI, as very few users use GUI for their servers. GUI is clunky, complicated and relies on memory rather than knowledge. Like Windows, you REMEMBER the options you need to tick, but you don't see the insides of the system pumping. Frankly, I'm not sure I can help you configure much (anything) with GUI, as I'm only using it for desktop use.

Dedoimedo

---

### Post by ngreenwood6 on 2008-07-17
First of all thanks for the quick reply,

top - I was looking into ubuntu as being my server. I installed the ubuntu server last night but it is all text base. I am not that familiar with the commands so I require something with a gui until i can learn a little more about the server side of things. If you know of a method please let me know. I have clients that will be running windows xp and clients running ubuntu will i be able to manage them and complete the other tasks required in my previous post with the ubuntu server. Can you also provide some resources where i can get some help or some information?

Dedoimedo - Can you provide some more information about the CentOS? Will it do all the tasks in my previous post? Will it handle different users on different platforms (ex. windows and ubuntu)? I would require a gui because I am not very good at command line and i think a gui is way easier for right now. Any links to useful information would be great.

---

### Post by benfindlay on 2008-07-17
I personally use ubuntu desktop as a server. It's important to remember that each and every version of ubuntu is built from the same foundation, and they differ merely on what extra packages are installed.

I installed ubuntu desktop edition then added stuff like openssh-server, ftp server, samba server etc manually afterwards.
> **Dedoimedo said:**
> I STRONGLY recommend against using GUI for server configurations.

1. Using CLI, you'll actually understand what you do.
2. It's way faster.
3. Less bugs.


I agree with Dedoimedo that CLI is better, purely because you understand more about the inner workings that way!

I also am a big fan of webmin for administering a server. If you're not familiar with webmin, it is a web-browser interface (tick boxes, drop down menu options etc) that provides a more graphical interface, without being a full blown GUI.

Personal needs and preferences are the most important factor in choosing your own implementation (in my opinion), but Ubuntu is a great place to start!

Hope this helps!

Ben

---

### Post by ngreenwood6 on 2008-07-17
benfindlay the main thing that i want to be able to do is set up shared folders on the server. I want the users "documents and settings" (ex. desktop, favorites, etc.) to be shared on this server as well. I want the users to login to the network through the server and get their desktop, favorites, etc. from the server. This way whatever computer I am on the desktop and favorites are there. I also want to do backups and have remote access. The clients will be windows and ubuntu users. I want to be able to control their access to their computer and the network. Is this possible with ubuntu?

---

### Post by LowSky on 2008-07-17
ubuntu server edition can have a GUI very easily, at the prompt type one of these three commands

```
Sudo apt-get install ubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop
```

---

### Post by hyper_ch on 2008-07-17
I prefer Debian as server ;)

---

### Post by ngreenwood6 on 2008-07-17
I have seen that before but my main question is, is it capable of doing what I need it to do?

---

### Post by benfindlay on 2008-07-17
Shared folders are fairly easy to do, you can specify guest access or proper authentication as required.

In terms of storing windows documents and settings on an ubuntu server, I'm not sure, it's something I've never tried but I should imagine that it will take quite a bit of jiggery pokery to sort! One thing you could try with your windows machines is manually setting their user folders to a specific folder shared via samba across the network (right click my docs, properties, specify the folder you want in "Target"). The ubuntu machines could simply function as thin clients, or connect to the main server remotely as a session at logon.

Controling the access to the ubuntu server is doable, just use firestarter (a GUI for the firewall) to set up access rules, but in terms of controlling access to their own computer, that would likely be handled by specific user privilidges

Hope this helps!

Ben

---

### Post by ngreenwood6 on 2008-07-17
when i say controlling access to their computer I mean like limiting the permissions on it. like whether they can access the control panel, add/remove programs, etc. do you think that his is possible.

---

### Post by ngreenwood6 on 2008-07-17
also would i be able to remotely access this machine via a windows pc.

---

### Post by hyper_ch on 2008-07-17
yes, of course...

install openssh-server on the server, get putty on windows, connect through putty to the server and you have a cli that you can work in.

---

### Post by ngreenwood6 on 2008-07-17
No i dont want to be able to manage it from the command line. I want to be able to access the physical server gui from a remote location. If I am out of town and need to access something at home I would want to remote in through the server and find what i need or access other computers from there. I would be using a windows workstation though and want to know if it is possible to remote into a ubuntu server with a gui from windows.

---

### Post by steveneddy on 2008-07-17
Try looking here.

[http://ubuntuforums.org/showthread.php?t=765695](http://ubuntuforums.org/showthread.php?t=765695)

It's a start.

---

### Post by benfindlay on 2008-07-17
For GUI admin, try [here]("http://ubuntuforums.org/showthread.php?t=122402")
I personally use this in addition to plain old SSH with great results!

Hope this helps!

P.S. You can also use webmin

---

### Post by hyper_ch on 2008-07-17
if you just want to get files, use WinSCP (and install openssh-server and denyhosts) and forward port 22 from your router to your server('s static IP)

---

### Post by the_darkside_986 on 2008-07-17
VNC server should work for graphically logging into the remote Ubuntu machine, even on Windows. However, I highly doubt it is possible to do a Windows domain login into an Ubuntu server because Windows lacks an ext3 driver and wouldn't know what to do with the files.  (I also don't think Ubuntu can log into Windows domains the way XP Pro logs into one, because I haven't found anything that even mentions it, but that's beside the point).

---

### Post by Dedoimedo on 2008-07-17
Hi,
Any Linux distro can do anything. That said, CentOS comes with GUI and can do everything you asked for. Then again, all distros can.
Dedoimedo

---

