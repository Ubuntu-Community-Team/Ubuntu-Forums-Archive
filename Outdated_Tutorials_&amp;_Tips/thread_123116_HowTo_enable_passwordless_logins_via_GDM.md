---
title: "HowTo: enable passwordless logins via GDM"
date: 2006-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by darkfox on 2006-01-29
Given that this seems to me like a fairly simple and common objective, and seeing as how I have not been able to find a solution till now, I thought I'd make a start on a mini-howto. The below instructions work in fair conditions but I am a newbie, so it may be full of holes. Perhaps someone with a bit more technical knowledge could take a look at this for me and see if it can be improved?
   
   (MINI) HOW TO ALLOW SPECIFIC USERS TO LOG ON VIA GDM LOCALLY WITHOUT ENTERING A PASSWORD
   
   [1] Why Bother?
Well, partly because its just more convenient in some cases. If you are on a local network that is secure from remote access, where a machine is shared by multiple desktop users and where you trust some of them at least, why not let them have the benefits of their own account without the inconvenience of entering a password in GDM to log in? I know its no real hassle, but it is an extra step nonetheless. Anyway, choice is what we're all about, right? Partly also because Windows (and KDM!) lets you do this, and as a part of migrating folk over from Windows it is critical to not underestimate how important it is to minimise how much you take folk out of their familiarity zone. Even in small things like this. If you use a user browser in GDM, this will allow the user to click on the picture representing them and they're in!
   
   [2] Have a word with PAM!
PAM is the authentication model employed in Ubuntu. The first thing to do is to edit the PAM file that specifies how authentication should work with GDM. Open the file /etc/pam.d/gdm using your favorite text editor, in my case:
   $ sudo nano /etc/pam.d/gdm
Add lines that specify a password is not required for the users who are listed in a file that you are going to make later on. The new line in the file example comes between the #start and #end comments, all the other lines were there anyway and remain untouched:
   ----------------------
      #%PAM-1.0
      auth    requisite    pam_nologin.so
      auth    required    pam_env.so
# start
      auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers.txt onerr=fail
      # end
      @include common-auth
      @include common-account
      session    required    pam_limits.so
      @include common-session
      @include common-password
   ----------------------
   
   [3] Tell PAM who to let in without a pass
   Go to this following location: /etc/X11/gdm/
   Make a new text file there called nopassusers.txt
In this file, list the usernames of the users who can log in without entering a password. Put each user on a new line. Only the username is required.
   
OK - that should be it. Like I say, I know this works but have no idea whether it is sensible. Please if you have knowledge contribute to making this a better howto!

---

### Post by Ptero-4 on 2007-08-09
you can use any filename and path instead of /etc/X11/gdm/nopassusers.txt as long as you also use the same path/filename in the "file=XXX" portion of the /etc/pam.d/gdm file.

---

### Post by Gabbegubben on 2007-09-26
Does anyone know how to make this work in Ubuntu 7.10 (Gutsy Gibbon)? It worked like a charm in 7.04.

---

### Post by Gabbegubben on 2007-10-15
OK, it still works fine #-o
The path /etc/X11/gdm is now /etc/gdm so you just have to update the path to your file containing the users allowed to login without passwords.

---

### Post by tin_truc22 on 2008-03-17
How can i login without entering password in Ubuntu 8.04?

---

### Post by bnuk013 on 2008-04-10
I did this and I got it to work so when you start up it goes into the first account without having to enter a password, and when I switch to login the other account it logs in without a password.  However from that point on to switch users it requires a password.  It's like it doesn't require a pssword to *login*, but it requires one to switch between users that are logged in.   8.04.

---

### Post by bnuk013 on 2008-04-12
Anyone?  I would really like to have this work.

---

### Post by 99bluefoxx on 2008-05-08
[http://ubuntuforums.org/showthread.php?p=4510108](http://ubuntuforums.org/showthread.php?p=4510108)
for any interested, that is a extremely simple way of making a account have no password to enter :)

---

### Post by kdavies on 2008-12-09
For Gnome
In /etc/pam.d files called gdm and gdm-autologin.
I moved gdm to gdm.logingreq and made a symbolic link from gdm-autologin to gdm.

---

### Post by MichaelBurns on 2009-11-23
If all you want is a single MS Windows guest-like account, I found a slightly simpler PAM configuration.

Firstly, I will comment that (apparently) Ubuntu varaints do not allow an account to be named "guest" (which is frustrating), so I created an acount named "anyone".  (However, this turned out a to be a better name than "guest" anyway, because it appears first in alphabetical order on my face browser.)

From -->[***the PAM online documentation***](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html)<-- (especially -->[***this page***](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_succeed_if.html)<--), I decided to just add the following line:

```

auth   sufficient   pam_succeed_if.so user = anyone

```

to the beginning of the /etc/pam.d/gdm file (after copying the file to a backup version, of course).  If you want to use a different guest-like account name, say, "guestuser" (instead of "anyone"), then the line would be:

```

auth   sufficient   pam_succeed_if.so user = guestuser

```

and so on.  After the edit, I simply logged out and then clicked on all of the users in my face browser, and they all asked for passwords - except "anyone".  When I clicked on "anyone" with just a single click I was logged in without being prompted for a password.

Please, experts, let us know if this is a bad way to do it.  (I first tried adding the line to the /etc/pam.d/login file, but it didn't work, and I am confused by this.)

---

### Post by trusktr on 2010-06-10
Thank you MichaelBurns!! This is exactly what i was looking for. Everyone, do this. It's so simple and way easier than any other method.

The folks over at gnome.org need to fix GDM though so that if a user has no password (passwd -d <user>) then it will bypass the password prompt.

---

