---
title: "&quot; 'gdm' does not exist &quot;"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by CyberDean on 2008-04-23
I added a quest user last evening to my Ubuntu 7.10 laptop. Immediately after I was unable to boot up to the login screen.  Instead I get the following message.

     The GDM user 'gdm' does not exist.  Please correct GDM configuation and restart GDM.

Ok, I believe I have figured out what it is, but being a Linux user for 3 months I have no idea how to correct it.  And with the new "Forum" configuation I do not know how to search the forum for assistance.

Somehow, some way, in my adding a new user, something happened to the gdm user.  In a terminal window I checked users and only my user name shows up.

Now what?  I have a remastered CD of my laptop software as of last month, will that help?

---

### Post by phidia on 2008-04-23
How did you add the "Guest user"? To create an alternate account on your install one usually does sudo adduser in a shell/terminal. Doing it that will will create all the files needed and ask you for a password and other user info.

Also if the only user shown is you then the attempt to add another account didn't work. 
For your specific problem see the thread [here]("http://www.linuxquestions.org/questions/debian-26/gdm-fails-to-start-on-boot-618057/?highlight=The+GDM+user+%27gdm%27+does+-exist.+Please+correct+GDM+configuation+restart+GDM.")
The linuxquestions.org site is a good alternative place to look particularly while the ubuntu forum is reconfiguring this week.

---

### Post by CyberDean on 2008-04-23
I found a GUI under Admin, I believe it was called "User Management".  In the GUI it asked for new user name and password, I let the other options go to default. After saving and the GUI disappeared I attempted to test it by logging out and rebooting, and that is when I got the error.

I will look into the link you gave me, Thanks.

---

### Post by CyberDean on 2008-04-23
For phidia,

Went to the link suggested and tried the only thing I could find, to reconfigure gdm, and here is what I got:

XXXX is not in the sudoers file.  This incident will be reported. ~$ exim: failed to find uid for user name "Debian-exim"

I have no idea what the error means and I am currently the only user on my laptop and I don't understand why I would not have sudoers rights and be in the sudoers file.  Of course there is allot I don't understand at this stage.

I do have access to the laptop in terminal mode only.

Someone, any help?  :confused:

---

### Post by phidia on 2008-04-23
> **CyberDean said:**
> For phidia,

Went to the link suggested and tried the only thing I could find, to reconfigure gdm, and here is what I got:

XXXX is not in the sudoers file.  This incident will be reported. ~$ exim: failed to find uid for user name "Debian-exim"

I have no idea what the error means and I am currently the only user on my laptop and I don't understand why I would not have sudoers rights and be in the sudoers file.  Of course there is allot I don't understand at this stage.

I do have access to the laptop in terminal mode only.

Someone, any help?  :confused:

Is Debian-exim your user and also the 1st account you created when installing Ubuntu?

Added Later: Did you have a different user account when you installed Ubuntu and did you delete that account and create a new user?

It seems like you lost admin privledges somehow. Check out this [post]("http://ubuntuforums.org/showthread.php?t=107940")
 Please read the whole thread it isn't very long-often it's easier to reference the ways to a solution than to recreate the wheel. Hope that Helps!

---

### Post by CyberDean on 2008-04-27
[QUOTE=phidia;4773340]Is Debian-exim your user and also the 1st account you created when installing Ubuntu?

Added Later: Did you have a different user account when you installed Ubuntu and did you delete that account and create a new user?



I've only had one user since installing till this problem, have not changed user names or deleted.  I do not understand what Debian-exim is, sorry for ignorance, checked Wiki but no go.

I checked the latest link, but I can not get logged in to do anything, don't know how it would help me at this point.

I do appreciate all you are trying to do, thanks.

---

