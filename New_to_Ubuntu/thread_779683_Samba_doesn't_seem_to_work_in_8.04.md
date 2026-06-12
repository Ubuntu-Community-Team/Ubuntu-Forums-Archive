---
title: "Samba doesn't seem to work in 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-05-02
Hi all,

I upgraded to 8.04 from 7.10 successfully and I'm currently using 8.04. But I have problem with samba in 8.04, that is:

I'm using a LAN with some colleagues, some of them use Windows and I want to access their shared files & folders. 

In 7.10, I just need to open any folder, press Ctrl + L, then type the LAN IP in the address bar (e.g "smb://192.168.222.77" ) but in 8.04 it doesn't seem to work anymore. I type the LAN IP in and nothing appeared. But if I add the drive letter in (e.g "smb://192.168.222.77/c$" ) then it required me to enter username and password to access the drive - does this mean samba still working?

And could anyone instruct me how to use cifs as well, because I remember reading somewhere that samba **might not** work with Windows Server whilst cifs does.

Thanks in advance :popcorn:

---

### Post by frup on 2008-05-02
Well first i'm going to guess you are on the same subnet as them?

Secondly I am going to guess that you entered their username and password on the prompt and the C was in fact shared and that they in fact allowed you to connect through their sharing settings?

I find it really funny how using samba between 2 linux devices is so much easier than using samba between to windows devices or a linux and windows device. Especially when the windows devices use XP home. 

Long story short, I was using 8.04 and samba 3 days ago. You might need to open system > administration > network and add yourself to the same workgroup as the windows machines though.

---

### Post by Dani Filth on 2008-05-02
Hi frup.

Yes, I'm in the same subnet as them. And I entered the username as password just to verify whether samba is still working or not. Normally, there are some shared folders & files which you don't need to enter any username & password to access, view & copy. That worked just fine for me in 7.10, but now in 8.04 nothing appears in the "Windows shares on 192.168.222.77" (just an example) anymore.

I'm no expert so I'm not sure if 8.04 replaced any configuration files during its installation. So I'll be very appreaciated if somebody can guide me through this problem.

Thanks!

---

### Post by Ghilteras on 2008-05-04
i can connect to windows computers but only by using their ip addresses, if I use their host name i cant, infact browsing my network->windows network i cant find my windows computers.

yes in the smb.conf i have the same workgroup of the windows machines


should I change the "DOMAIN" variable of my network to get it alike with the windows workgroup? are those names case sensitive?

---

### Post by bodhi.zazen on 2008-05-04
If you want to access your Windows machines by hostname add them to /etc/hosts

Format is :

ip_address   hostname

192.168.1.55  Windows1
192.168.1.66  Windows2

Go to "connect to Server" -> select windows share -> enter server name, domain, and share name -> connect -> Enter Windows username and password.

If you want the shares to mount at boot you will need to add an entry in /etc/fstab.

---

### Post by Dani Filth on 2008-05-04
I still cannot connect & access the shared files & folders from computers that I was able to connect via samba before in 7.10.
Could anybody please tell me how to solve this problem? Or any other changes should be made to the configuration file (smb.conf?)

Many thanks in advance

---

### Post by bodhi.zazen on 2008-05-05
Can you update us, what have you tried ?

If you updated your /etc/hosts you need to either reboot (windoz way) or re-start your network (linux way).

```
sudo /etc/init.d/networking force-reload
```

Then mount your shares.

---

### Post by jimv on 2008-05-05
I think he's saying that the problem is when he tries to browse for shares on those remote machines, he can't see them.  But he can access the shares if he types in the share names.

Right?

---

### Post by Dani Filth on 2008-05-05
Ok, I upgraded from 7.10 to 8.04, nothing seemed wrong as far as I know. I'm able to boot to 8.04, running stuffs, listen to the music, watch movies. etc.

Assuming the remote PC that I wanted to access has the LAN IP 192.168.222.77, and I'm in the same subnet.

The only problem is when I tried to use samba with "smb://192.168.222.77", I saw nothing in the browse shared folder - unlike 7.10. With 7.10, I just need to typed in the LAN IP with "smb://" then the shared stuffs will appear. I even tried to ask the owner of the PC to share a folder for testing but I couldn't see it too.

And when I wanted to verify if samba is actually working, I added "smb://192.168.222.77/c$" then a dialog pop-up asking me to enter username and password to access the C: drive in the remote PC.
Hope I provide enough details.

bodhi.zazen: I tried "sudo /etc/init.d/networking force-reload" and restarted as well but still cannot access the shared folders.

Thanks.

---

### Post by jimv on 2008-05-05
By the way, I'm having the same issue.  I just haven't really been bugged enough by it yet. If I just type in the address of my Vista machine, I don't see any shares.  If I type in the address of the Vista machine followed by a share's name, the share opens fine.

---

