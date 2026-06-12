---
title: "[SOLVED] Help - Permissions &amp;amp; password failing since lunch."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-05
Hi Gang

Employees got back from lunch and the main storage computer is denying them access to the shared folders.

I ran smbtree all computers are showing.
Open Network and all computers and shared files are showing and ALL of them open just fine EXCEPT the folders with the client data on one machine.

None of the other computers, not even other Ubuntu machines ask for a Password.
This one is asking for a password to open the file, but no password works either.

We've tried restarting Samba, logging off and back on again on all computers, tried rebooting several times, waited for 15 minutes for all the machines to repopulate the listings, etc.  Same problem, the main computer is not allowing anyone to open it's files.

Need help PDQ on this one gang!

Thanks

TTUL
Gary

---

### Post by bscbrit on 2008-11-05
I don't think that you'll get much help in Absolute Beginner Talk - you might want to repost this in the network forum where somebody with a lot more brains than I have can think about it! :-)

I suppose that nobody had access to the computer, either physical or logged on, during lunch, did they?

---

### Post by Kellemora on 2008-11-05
Well, I see it's QUITE OBVIOUS that playing around with an MP3 player, installing pretty borders and hearing unusual sounds is MUCH MORE IMPORTANT, than having customers walking out the door, or employee's on the clock with nothing to do because they can't access the needed files to do their work.

I got the problem solved by giving ALL of the employees Root Access through Nautilus to use the temporary new root password I assigned to them for today.

MAJOR SECURITY FLAW IN UBUNTU as far as I'm concerned!!!!!

Oh, almost forgot, Thanks a bunch for the HELP you provided WHEN I NEEDED IT MOST, it was truly appreciated!!!!!  NOT!!!!!

Maybe if I ask stupid question that don't mean diddly squat about anything I would get 50 responses in under 5 minutes and a week long discussion on how to twist a wire back on a bread wrapper.

They should DROP the LTS from behind 8.04 because it's NOT stable!
And apparently no support, since Networking has been a MAJOR PROBLEM since it was released and it's STILL BROKEN.........

Gary

---

### Post by Kellemora on 2008-11-05
Hi BB

Thanks for responding!

No, I sat right here and ate my lunch and manned the phones.

No changes were made to any of the computers and no electric surges or outages.

Everything was working fine before lunch, in fact it was working fine after the employees went to lunch as I had a client call and accessed the database while they were gone to get his account number.  Then closed the window just like I normally do.

The first person back from lunch logged in and said the mounted files from her desktop were gone, all of them.  And that's when I started trying to get things up and running again.

Nobody touched any of the computers other than her to log on and see the mounts were not there.  I restarted Samba, restarted X, then rebooted and all the network was back except for the client data computer.

I checked everything I knew to check, and after getting no responses I did the only thing I knew to do that would work.  And that was to give everyone root access with a temporary root password so as not to give out the private one.  

At least were up and running again with only 1-1/4 hours of lost productivity and those associated costs, and possibly one client won't ever call us again.

I posted in Beginners, because I'm a noob myself and most of those Moderators are reading this board first.

TTUL
Gary

---

### Post by bscbrit on 2008-11-05
I wasn't sure if your post #3 was directed at me or not - I'm still not sure....

Sorry that I haven't got the expertise to answer your question. I do think that you'll have a better chance on the more appropriate forum.

I realise that giving everybody root access seems to have solved your immediate problem but it only takes any one of them to mess up and they can delete everything that your company holds dear - customer data, personnel records, operating system.  Do you really trust each and every one of them not to screw up?

---

### Post by Kellemora on 2008-11-05
HI BB (bscbrit)

Yes, my thanks were directed toward you!

You are right, NOT SAFE at all to give root access!

But by the same token, I can't add 7,121 folders manually to smb.conf either, plus another 2 to 3 per day and delete those jobs that are finished.  I would need to hire a person to do just that and pay them overtime.

Sharing used to work WITHOUT asking for a password at all.
I've checked the smb.conf files on each of the computers, nothing is changed.

What I'm doing right now is giving each person a new account and a new password, but those I tested it on so far, they still cannot access the client database without going to root.  I also checked the permissions, namely the group of the database and it's like it always was.  group name has not changed and each person is in the group files as a user of that group.

The odd thing about it is, it's only one computer acting weird.  And I've checked and double checked every single file associated with networking on that computer with the backup files.  Everything is as it should be.

We had a similar problem when I first set up the office and switched from XP to Ubuntu.  And I have my set-up steps all written down as to which programs I needed to download and install and how each one got set up.  Once I did all that, everything has been humming right along like a Swiss knock-off watch, hi hi.....

Guess I'll burn the midnight oil tonight and move all the data over to another computer and wipe this one clean and start over from scratch again, to see if that will help matters.

Again, thanks for being a live body I could unload on!
At least getting some of it out of my system has helped!

TTUL
Gary

---

### Post by bscbrit on 2008-11-05
Good Luck Gary, it sounds as if it will be a long night for you.

bscbrit

---

