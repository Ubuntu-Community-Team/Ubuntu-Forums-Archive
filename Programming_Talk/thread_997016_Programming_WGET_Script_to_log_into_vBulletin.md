---
title: "Programming WGET Script to log into vBulletin"
date: 2008-11-29
forum: Programming Talk
---

### Post by Pyro.699 on 2008-11-29
Hello,

There is a community forum (running on the vBulletin board system) that has a download section that i would like to retrieve all the files from a section. Now, the only reason im doing this with wget and not manually downloading them is because there is a minimum of 1 minute between download times, meaning i would have to sit there and manually download hundreds of files while waiting 1 minute in between (that could take a while, also to note, none of the files are greater than 100kb so it wont be abusing the bandwidth of the site). I tried to retrieve the cookie file by using:

**wget --spider --save-cookies=/home/cody/Desktop/cookies.txt --keep-session-cookies --post-data='vb_login_username=*user*&vb_login_password=pass' http://****[www.forum.com/login.php?do=login]("http://www.forurm.com/login.php?do=login")**

All that, that creates is a file with the timestamps inside of it (not saving the cookie information used to log into the forum). My plan was to use that to retreieve the cookie, then use the **--load-cookie** function inorder to re-login.

On a side note, how well does wget handle urls that are formed like **downloads.php?do=file&id=###**? When you go to that url it will then propmpt you to open/save the file.

Thankyou very much
~Cody Woolaver

---

### Post by Pyro.699 on 2008-11-30
Sorry for the bump but im still unable to figure this out.

Thanks
~Cody Woolaver

---

### Post by WitchCraft on 2009-01-09
> **Pyro.699 said:**
> 
while(!(succeed = try()))


You could try a making a Perl or Python script...

---

### Post by Cracauer on 2009-01-09
I strongly recommend against using wget for any kind of scripting.

curl for commandline and libcurl for programs.

---

### Post by Pyro.699 on 2009-01-24
> **Cracauer said:**
> I strongly recommend against using wget for any kind of scripting.

curl for commandline and libcurl for programs.
Why would you suggest that? wget is very flexible and offered a lot of different use's. Since its been.... 3 months since i first proposed this project i never really finished it nor do i have an interest to but in other projects ive used Python and a Python Module called ClientForm. I had a script developed there that allowed a user to login to any website (could even work around webpages that had split login screens (username on one page, password on another page))

Thanks tho
~Cody Woolaver

---

### Post by Cracauer on 2009-01-26
> **Pyro.699 said:**
> Why would you suggest that? wget is very flexible and offered a lot of different use's. Since its been.... 3 months since i first proposed this project i never really finished it nor do i have an interest to but in other projects ive used Python and a Python Module called ClientForm. I had a script developed there that allowed a user to login to any website (could even work around webpages that had split login screens (username on one page, password on another page))

Thanks tho
~Cody Woolaver

wget has, or had at the time I gave up on it, numerous bugs that makes it jump around in a mirrored site and hence forgets what you wanted to mirror and what not. Most importantly, the handling of redirects (even those on 404 errors) seems to be broken and tunnel mirroring restrictions.

---

