---
title: "Ubuntu Networking pls help.."
date: 2007-11-26
forum: Philippine Team
---

### Post by slaphoundz on 2007-11-26
guys paano ba i-network ang tatlong PC using ubuntu 7.10? san ako pupunta para magconfigure?

---

### Post by loell on 2007-11-26
na setup na ninyo po ba ang connection nang tatlong pc via a switch?

---

### Post by slaphoundz on 2007-11-26
Yes bro naka set-up na sya bali gusto ko lang magkita-kita sila within network.

---

### Post by loell on 2007-11-26
then its time to install and configure samba ;)

[samba guide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%28samba%29")

---

### Post by ichi_730 on 2007-11-27
wOW Samba config.. nahirapan kami jan sa samba server, apache and postgresql server configuration sa net01 namin before.. imagine mga newbie kami sa networking tapos icoconfigure namin.. heck! e active directory nga hindi namin alam yon pa kay.. kamote tuloy kami hehehe pero ayos lang exp din un.. ayos ahh may guide pa..:)

---

### Post by Pedro0727 on 2007-11-27
subay2x lng how to config ng samba :popcorn:

---

### Post by loell on 2007-11-27
in Hardy Heron , samba setup and configuration will be more simplified, so stay tuned :)

---

### Post by raxso on 2007-11-27
hope this helps.

Did you install samba, if not install samba.

1. sudo apt-get install samba samba-doc

Then set your smb users password.

2. sudo smbpasswd -a name-of-user

enter the password.

you may need to either modify or create the smbusers file

sudo gedit /etc/samba/smbusers

enter your password.

In the smbusers file, modify/add the following line:
USERNAME = "network username"

Modify the smb.configuration file

sudo gedit /etc/samba/smb.conf

enter your password.

Locate the section titled
[global]
If the following entries do not exist, add them. If they do exist and are set to something else, modify them to read:
workgroup = MSHOME (this is the name of your network)
security = user
username map =/etc/samba/smbusers

==== Share Definitions ===

[printers]

# My Shared Folders
[DRIVE1]
path = /media/DRIVE1/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = USERNAME

[DRIVE2]
path = /media/DRIVE2/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = USERNAME


Note: In place of the "USERNAME" entries above, make sure USERNAME is set to the same username you use to log into the system on both Windows and Linux.

save the the file and it is time to start samba and access the shares

3. sudo testparm
enter your password.

4. Then restart Samba
sudo /etc/init.d/samba restart

You should now be able to browse shared folders. let me know if it works for you..... :popcorn:

---

### Post by slaphoundz on 2007-11-27
@loell, ichi_730, pedro, raxso

   salamat sa mga binigay nyong tulong at inpormasyon, right now im downloading samba.

post back later for the result.....

---

