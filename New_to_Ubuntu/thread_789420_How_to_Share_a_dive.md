---
title: "How to Share a dive"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by scott@matheson.com on 2008-05-10
My son installed Ubuntu on an old PC and told my just to share the disk drive out to the home network (then went back to uni)

I was expecting to find a GUI like on XP to share a drive but I can not, is the a GUI I need to load that will help with shearing "mounting" a drive for network access 

or can some one point me at the command I would use to share a drive

---

### Post by Monicker on 2008-05-10
Which version of Ubuntu do you have?

Here are some instructions for 7.10

[https://help.ubuntu.com/7.10/internet/C/networking-shares.html]("https://help.ubuntu.com/7.10/internet/C/networking-shares.html")


For 8.04 you will need to look under Places -> Sharing Options.

---

### Post by benfindlay on 2008-05-10
Theres a really good guide here: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
And here are the highlights:
Enter these 2 commands into terminal
```
sudo apt-get install samba
```
```
sudo gedit /etc/samba/smb.conf
```
Now change the "workgroup" to whatever you want (MSHOME is default and fine to use)
Change the "server string" to whatever you want to call this particular computer on the network (for example ubuntu, or server)
Save and exit back to terminal
Now type```
sudo smbpasswd -L -a [your username]
```
Choose a password, then type```
sudo smbpasswd -L -e [your username]
```
This activates that user

Now you should reboot. Once everything is back up, log in, then you should simply be able to right click on folders that you want to share and choose "Sharing Options" and set things there

Hope this helps!

---

### Post by scott@matheson.com on 2008-05-10
Thanks in fact I had sharing installed I was thinking I had to share the drive link in XP not just the folder, this unix staff is realy good !!

I will give it a go in the tomorrow thanks

---

### Post by scott@matheson.com on 2008-05-11
I am using 8.1  when try and share a the folder /home/chris/share unix drive  I get the message 


net usershaer returned 255: net usershare: cannot open usershare directort /ver/lin/samba/usershare error premissions dened


but the user has root premisions

---

### Post by benfindlay on 2008-05-12
Open up a terminal and type ```
sudo smbpasswd -L -a [your username]
``` and choose a password for samba access.
Then type ```
sudo smbpasswd -L -e [your username]
``` to enable that samba account

Hope this helps!

---

### Post by scott@matheson.com on 2008-05-13
Hi
  I must be doing somethign work, I followed your steps but still get the same error message

so if i start fromt he top I have 3 uesres root, chris and scot
I have 1 disk drive that has both the OS and filesystem on it
i open the folder /home/chris/documents
I create a folder sharedunis
I right click on thefolder and select shasreing options
I follow the steps 
then I get the 255 premision error

if it help this is a test bix that I can let you have remort access to you can damage anything

---

### Post by scott@matheson.com on 2008-05-13
PS when i get the werror i am told that the user does not have premisions to write to /var/lin/sambo/usershare

this fodler does not exisit

---

