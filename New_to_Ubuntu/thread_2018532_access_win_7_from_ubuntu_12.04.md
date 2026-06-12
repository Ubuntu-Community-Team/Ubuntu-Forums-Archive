---
title: "access win 7 from ubuntu 12.04"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by m3t3ors on 2012-07-06
ok ive set up a windoze 7 pc and need to access it from my ubuntu laptop and (if possible) vice versa. ive installed samba on ubuntu and set win 7 to share network. ive searched google and can only find info regarding earlier ubuntu releases.
any help appreciated

---

### Post by sandyd on 2012-07-06
> **m3t3ors said:**
> ok ive set up a windoze 7 pc and need to access it from my ubuntu laptop and (if possible) vice versa. ive installed samba on ubuntu and set win 7 to share network. ive searched google and can only find info regarding earlier ubuntu releases.
any help appreciated
you using homegroups?

---

### Post by m3t3ors on 2012-07-06
at moment yes

---

### Post by m3t3ors on 2012-07-06
ive now got ubuntu to see the win 7 pc but to connect it wants a password? ive deleted home network
cant see ubuntu in win 7 pc, 
uninstlled windows live sign in assistant

---

### Post by krustenBrot on 2012-07-06
Try disabling the password protected sharing in the Win7 settings. It was a common annoyance on LAN parties :)

Here is how: [Win7 disable password protected sharing]("http://www.sevenforums.com/tutorials/185429-password-protected-sharing-turn-off-windows-7-a.html").

Sorry I would have written it myself but i haven't been on a windows machine for a while :)

---

### Post by m3t3ors on 2012-07-06
thanks i now see my files but get the following error
"unable to mount location"
failed to mount windows share

---

### Post by NikTh on 2012-07-06
I am not sure but i think that password is not windows share password.. is your admin password in windows.. 
Enable again password protection and try it.

---

### Post by m3t3ors on 2012-07-06
i dont have admin password or admin, just 1 user etc

---

### Post by krustenBrot on 2012-07-06
> **NikTh said:**
> I am not sure but i think that password is not windows share password.. is your admin password in windows.. 
Enable again password protection and try it.

As far as i know it sometimes worked with the username (= Admin) and sometimes not.
Officially you have to create an user given the permission to access that specific folder, it might even be possible to grant the guest account the necessary rights. 
But to be clear - i am speaking of experiences and **not** consolidated knowledge.

):P

---

### Post by NikTh on 2012-07-06
> **m3t3ors said:**
> i dont have admin password or admin, just 1 user etc
How this happened ? 
When you install windows they prompt you for a password , when installation finish they promote you to administrator.
If you are not admin (in windows) i think you cannot do much.    
But again.. i am not sure

> **krustenBrot said:**
> As far as i know it sometimes worked with the username (= Admin) and sometimes not.
Officially you have to create an user given the permission to access  that specific folder, it might even be possible to grant the guest  account the necessary rights. 
But to be clear - i am speaking of experiences and **not** consolidated knowledge.

):P

I am speaking of experience too. When i hit "windows network" from  nautilus it request a password , i give windows password (not network  share password) user's password. 
Oh !! and a **note:** maybe important !! my windows and Ubuntu passwords are the same. (User passwords)

---

### Post by krustenBrot on 2012-07-06
> **NikTh said:**
> How this happened ? 
When you install windows they prompt you for a password , when installation finish they promote you to administrator.
If you are not admin (in windows) i think you cannot do much.    
But again.. i am not sure

Correct. I think he misunderstood you and meant there isn't a particular "Administrator Account". So his user account equals an admin account.

---

### Post by m3t3ors on 2012-07-06
> **krustenBrot said:**
> Correct. I think he misunderstood you and meant there isn't a particular "Administrator Account". So his user account equals an admin account.

when i install windows and it asks for a password i click next without giving a password. i use only 1 user account and no passwords
anyway since i unchecked network password it no longer is an issue now, my problem is unable to mount location failed to mount windows share. and i cant see ubuntu in win 7
 when i used xp it was so straight forward, but now im on win 7 its mental

---

### Post by critin on 2012-07-06
Try going to windows and disabling the firewall in network.

---

### Post by m3t3ors on 2012-07-06
already disabled

---

### Post by critin on 2012-07-06
Then it must be in Samba configs.  Have you done that?  Go to admin and apply permissions there.  You also might look over this info.

[http://www.liberiangeek.net/2012/04/quickly-share-your-documents-folder-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/quickly-share-your-documents-folder-in-ubuntu-12-04-precise-pangolin/)

Concerning the link:  For what it's worth, I didn't change these things in Windows.  From this line down:

*Finally, from your Windows system, go to **[I]Start &#8211;> All Programs &#8211; Accessories &#8211;> Run*** and type the commands then press Enter to open Ubuntu Documents folder.[/I]

**I did not do.  **

No matter what you do though, Samba preferences must be configured right or nothing will work consistently every time.  That same site, (liberiangeek) has some great tutorials on configuring Samba for simple networking sharing.

Don't give up- it can be done.

---

### Post by m3t3ors on 2012-07-07
thanks il have a play, but i had already done what was in the link

---

### Post by m3t3ors on 2012-07-07
all done , i created a password for windows user account and it worked, thanks to all for the help:p:p:p

---

### Post by a_z1_9scores on 2012-07-07
*edit* Glad to see you fixed your problem :D

---

### Post by krustenBrot on 2012-07-07
Please mark your thread as solved by clicking on **Thread Tools** on top and click **mark as solved**.

As mentioned [here]("http://ubuntuforums.org/showthread.php?t=1422475"):
> **Let us know when it's fixed.** When your problem is solved,  mark your thread  as [SOLVED] by using the Thread Tools menu near the  upper-righthand corner of the page, and remember to thank those who  helped fix your problem. This lets us know that we are doing some good  with our time, and encourages us to keep at it.

---

### Post by m3t3ors on 2012-08-25
im running ubuntu 12.04 on my laptop and windows 7 on the wifes pc, all networked through a d-link router. laptop is wireless the pc is ethernet.
i can access windows from ubuntu through samba but cant access ubuntu from windows?
now i need the access just for 1 shared folder and things for printing etc. and just to make things easier for me..
in my win7 pc i see the network, the laptop is there. if i click the icon it asks for username and network password
i enter my name and password for laptop and it errors?but the laptop is called john-ml3108b and username is john
now it errors if i type john and pwrd
but if i type laptop name and pwrd i get in but theres nothing there?
just a blank screen


any help appreciated

---

### Post by Mark Phelps on 2012-08-26
> **m3t3ors said:**
> im running ubuntu 12.04 on my laptop and windows 7 on the wifes pc, all networked through a d-link router. laptop is wireless the pc is ethernet.
i can access windows from ubuntu through samba but cant access ubuntu from windows? ... any help appreciated

Your problem is the OPPOSITE of the title of this thread.  You need to start your own thread to deal with this problem.

---

### Post by Buntu Bunny on 2012-08-26
> **NikTh said:**
> How this happened ? 
When you install windows they prompt you for a password , when installation finish they promote you to administrator.


When you first sign in to Windows 7 it recommends a password but does not require it.

---

