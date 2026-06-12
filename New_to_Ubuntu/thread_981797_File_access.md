---
title: "File access"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by spike240 on 2008-11-14
Hi  there - After  many  years  of  reliable  use  I tried mucking  about  with a  system  file (long story). Now when  booting, after the username password  have been given Ubuntu stays blank (crimson screen). Any of you guys know how I can gain access to my files?
TIA
regards
Brian

---

### Post by Crafty Kisses on 2008-11-14
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X server:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```
Once it's rebooted and you are able to log in again, make sure your video card drivers are installed, and if this doesn't work please let me know and I or someone else can help you with your current issue.

---

### Post by spike240 on 2008-11-14
OK thanks for that. Got to go to work now - will try later. Will let you know.
Regards
Brian

---

### Post by Crafty Kisses on 2008-11-14
Alright, thanks for letting me know.

---

### Post by spike240 on 2008-11-14
Hi  thanks  for  your  input.  I  tried  entering  the  code,  but  alas  same  outcome. Maybe  if  I  tell  you  what  i  did  while  Ubuntu  was  running  to  get  me  in  this  situation.
I  tried  installing  a  wireless  adapter,  which  involved  installing  er  is  it  nidiswrapper - which allows  the  installation  of  the  Windows  driver. This  resulted  in  the  wireless  adapter  not  working,  on  top  of  that  my  ethernet  connection  would  no  longer  work. I researched  on  internet  and  ended up  editing  the  interfaces file.  i deleted the first couple of lines from etc/network/interfaces 
auto lo
iface lo inet loopback

PS please  bear in mind all the years I have used Ubuntu I have only used GUI  and  not ventured into the terminal much,  so  plainspeak please.
Thanks  to  everyone.

Regards
Brian

---

### Post by spike240 on 2008-11-15
A  quick  bump. Can anyone help please?
Many thanks
Brian

---

### Post by cariboo on 2008-11-15
Create a new user. Start in recovery mode and at the menu drop to root prompt. At the prompt type:

```
useradd -m <newuser> 
```

then

```
passwd <newuser>
```

The useradd -m adds a new user and create his how directory. Passwd is self explanitory. Next reboot:

```
reboot
```

You should now be able to login is as the user you just created.

Once you are logged in as your new user, you can transfer your files from the old user to the new user.

This won't fix your network device problems, but we can work on that after you're up and running.

Jim

---

### Post by spike240 on 2008-11-15
Thanks for input. Tried  it  but  same  result. When  I  boot  ubuntu  I  do  reach  the  username & password  screen. I  can  therefore  access  the terminal.  Is  there  any  way  of  editing   system  files  from  there. 
Also when  booting  in  recovery  mode I  am informed that  there was  a fatal error  with ndiswrapper - maybe  this  is  a clue?
Thanks  again for responding.

regards
Brian

---

