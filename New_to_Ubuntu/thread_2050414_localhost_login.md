---
title: "localhost login"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by desperate 101 on 2012-08-30
okay, so ive checked out multiple forums and none of their advice has helped me.


This is where i stand.  i just recentally installed ubuntu from a disk.  the install went fine.  went i went to reboot my computer it shows the ubuntu wallpaper, then goes to a black screen saying "localhost login".  i dont think i put a password on my user when i installed.


from what i read, im supposed to type in root, and change the root password, then type startx and it will startup.  i have tried this multiple times.  it doesnt matter what i type in the login still fails.  ive tried root, then root again as password,  also tried guest/guest and user/user nothing seems to work....  when i go recovery, and select the root option, a black screen appears asking for root password.  nothing i type i works and comes up incorrect password. idk what to do, but i am a basic computer user.  if u intend me to use command promt or any other advanced trick, youd better put step-by-step instructions, cuz i prolly couldnt even get the prompt open if i tried.  someone plz help me out.

idk if it helps, but at the localhost login area, i can see the user i type in, but the password appears blank.  it also doesnt give me any other options or errors with this.  id appreciate any helps possible

---

### Post by stmiller on 2012-08-30
During the ubuntu install you are required to make one user with a password. If data is no concern, best to just re-install at this point from the CD or DVD.

---

### Post by desperate 101 on 2012-08-30
okay, im pretty sure i can figurre out the password.  what would i type in as the username then? root??

---

### Post by desperate 101 on 2012-08-30
and actually, i think it asks for the password during install, but it also has the choice to automatically login.  im pretty sure i chose automatic loggin

---

### Post by NikTh on 2012-08-30
Hi , 
lets clarify some things. 

1st , Ubuntu will not let you to proceed with installation if you don't give a password for the user you created.

2nd Yes , it has this option for automatic login. 

3rd In recovery mode if you select the root option it will not ask you for a password. It just drop to a root's shell. 

Questions you must answer so we can proceed to a possibly solution:
1. Now , how did you install Ubuntu ? is this a regular installation of via wubi (from inside windows) ? 
2. What version of Ubuntu installed ? the number. 
3. Do you remember your username ? 

Thanks

---

### Post by desperate 101 on 2012-08-30
okay, just to clarify, i had downloaded pinguy os, but i was told it was an extension of ubuntu.  i installed with a dvd, and had my entire system wiped so pinguy would be my only os.  the first problems i had was it would not boot, but this was fixed by running the dvd live and goin thru boot repair.  thats when the login screen came up.

and you are right, in the recovery it does drop the shell, but it does still ask for a password.  and no matter what i type in it fails.  i do remember my user name was aaron, and i set password as aaron (u were right, it does make u put a password in).  i have tried aaron as user name and password and nothing.  root willnot login either with aaron or anything else as password. 

i have been able to use the terminal on the live boot, and change the root password.  this still does not help me on the login page

---

### Post by desperate 101 on 2012-08-30
im thinking the reason changing roots password on the live cd wont work because it is a live version, and the data/info will not hold once rebooted

---

### Post by NikTh on 2012-08-30
Hi , 
I don't know the interface of this Pinguy OS , but I assume is the same as Ubuntu (I mean recovery mode) , cuz this Pinguy OS is Ubuntu-based.

So , boot to recovery mode and click on Root. Then give bellow commands with order 

```
mount -o remount,rw /
passwd username
```where username you will replace it with your actual username (aaron?) 
It will ask you 2 times for a Unix password . Give the password carefully , same password 2 times. 2nd time is for confirmation. 
It will not show anything (like you not write) this is normal. Then reboot and at login screen give your username (aaron?) and the password you gave in root shell. 

  Bellow command ```
passwd username
``` lets you to change the password of the specified user.

Root's account is disabled by default in Ubuntu and I assume the same for Pinguy OS. 

Thanks

---

### Post by desperate 101 on 2012-08-30
okay, i apreciate the step by step instructions. lemme give it a try and ill let u know.  itd be nice if u cud reply tonight yet so i can get this done asap

---

### Post by desperate 101 on 2012-08-30
ok, so u are right about it being exactly like ubuntu.  but when i went to root what comes up is "give root password for maintenance". that was the password screen i said before.   after this didnt work, i loaded pinguy live off the disk again, somehow managed to get into the terminal and change the root password with "sudo bash" and still nothing.  none of the passwords that i think may fit will fit... any ideas?

---

### Post by NikTh on 2012-08-30
Hi , 
take a look here : [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) 

Is it the same ? 

Thanks

---

### Post by desperate 101 on 2012-08-30
yes everything is the same, except after root is selected.  then, as i said before, all that comes up is " give root password for maintenance".  when i type attempted passwords in, it seems like it doesnt even try  it, it just says password incorrect automatically

---

### Post by NikTh on 2012-08-30
> **desperate 101 said:**
> yes everything is the same, except after root is selected.  then, as i said before, all that comes up is " give root password for maintenance".  when i type attempted passwords in, it seems like it doesnt even try  it, it just says password incorrect automatically

Perhaps is this an extra safety in Pinguy OS ? Don't know for sure.  This not make sense.  Recovery Mode is there for you , to let you recover your system , even password in hard times (like yours) . 

I never faced a situation like this again. I've installed in my pc over 15 ubuntu and ubuntu-based disrtos , but never (none)  in recovery mode asked for a password for maintenance.  

Sorry, no more ideas for now. 

Thanks

---

### Post by desperate 101 on 2012-08-30
:/ that really sucks.  i think im gunna try booting into the terminal, and change to root password/ create a user thru that.  idk why pinguy would do that, especially since its supposed to be easier AND more user friendly than ubuntu.  passwords on random stuff is not user friendly...

can anybody else help me out plzzz?

---

### Post by NikTh on 2012-08-30
Found a thread in Pinguy OS forums , similar problem with yours. : [http://forum.pinguyos.com/Thread-Password-recovery](http://forum.pinguyos.com/Thread-Password-recovery) and as i read they don't even know what is this prompt for password in recovery mode. Pinguy OS must behavior like Ubuntu , cuz is Ubuntu-based. 
Take a look . 

Although the solution in this thread not match for you (cuz you don't have another linux OS installed)

My best advice would be to boot from LiveCD and backup (copy) somewhere (external HDD - Usb)  your personal files (music , photo etc) and install the OS from start. 

Thanks

---

### Post by desperate 101 on 2012-08-30
okay so i went to reinstall os,(had no personal files to backup) and it gets all the way thru the installer, and then at end of "almost done copying files" and error comes up sayin somethings not right. that the disk may be damaged or something.  the disk is fin, ive checked it and it is working on my other computer.

---

### Post by NikTh on 2012-08-31
Hi , 
try again , is the .iso Ok ? (check the .iso with MD5sum or/and SHA1sum)
Is the copy you've done ok ? (lower speed burned if is a CD) 

Try to erase everything from the disk , from a LiveCD , use Gparted partition editor , and erase everything first... then try to install again. 

Thanks

---

