---
title: "[SOLVED] Shared Folder, it WORKS, but did I do it right?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Kellemora on 2008-09-09
Hi Gang

Just want to check if I used the proper procedure here!

I have a folder on my desktop I named Shared Stuff (also one named Documents that's not shared).

I could not share it from the desktop due to Permission Denied!  SO

I opened 'Root Terminal', typed 'gksu nautilus' (it only asks for log-in password, NOT root password)

display:  root@ubuntu :/home/me # gksu nautilus
screen: now in nautilus
It shows 1 folder named Desktop, it's empty.  (this seems odd to me since I was IN /home/me)
I SELECT 'file system', click on /home folder, click on /me folder, click on /desktop folder and THIS folder has my Shared Stuff and Document folders in it.  (I guess the OTHER Desktop is the Screen itself?)

I select the Shared Stuff folder and and set it to Shared!  (it put the hand up to show it was shared HERE!)

In order to GET PERMISSION from the REMOTE Computer to view it's contents, I had to go back and ALLOW GUEST SHARING, read only.

EXIT Nautilus
Go to Desktop and I notice the file does NOT show the shared hand.  SO
I go to Properties, Emblems and select the hand to show on this folder as a reminder.
Have NO IDEA why it didn't do that on it's own!

I could go to the REMOTE Windows Machine, open Network and see and OPEN the folder and read it's contents, no problem.

But if I turn off Allow Guest Sharing, it says Permission Denied from the Remote Computer.

My concern is, have I created a SECURITY BREACH by allowing Guest Sharing?

And, is this the correct way to SHARE a folder, as I have NOT figured out how to OPEN SAMBA in Ubuntu yet.  In Debian and CentOS there is a Samba in the Servers list and by clicking on it Samba Opens.  Cannot find any such method in Ubuntu.  No biggie if how I did it is OK!

Thanks Gang!

No more dumb questions for the rest of the night, I promise!
It's just the commands in Ubuntu are different than other Distro's I've used.  Like su - and Sudo su elsewhere, you use gksu here.  Some day I'll learn what all of that means, hi hi........

Have a Nice night everyone!

TTUL
Gary

---

