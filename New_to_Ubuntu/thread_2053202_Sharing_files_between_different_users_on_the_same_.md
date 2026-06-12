---
title: "Sharing files between different users on the same computer in pangolin"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by brawd on 2012-09-04
Hi All,

I've just updated to 12.04. I then installed all my pics into home/pics - about 2 Gigs worth. I want to share this folder with my wife who has her own account on the same machine. Otherwise I'll have 2 lots of 2 Gigs of pics. So I right clicked on the folder and told it to share. I don't know if I need samba or whether it's already installed, I just know it doesn't come up when I search the Dash thingee and doesn't install when I ask it to in Terminal.

So, when I log into her account I can see the pics folder, not hers - mine. When I try to open it a box comes up with her U/N and asking for a password.
So I type in her password but that doesn't work. The box just re-presents itself.
So thinking along the lines of it's my files in my home folder, and I am the admin I type in my name and my password. No luck, the box merely re-presents itself.

Anyone know how my wife can browse the pics folder in my home folder please. 

regards to all,

brawd

---

### Post by Bachstelze on 2012-09-04
Is the path really /home/pics or /home/you/pics?

---

### Post by Linux_junkie on 2012-09-04
You should have a directory (folder) called Public.  Put your pics in there and it should be available to other users of that machine.

---

### Post by oldfred on 2012-09-04
I am not an expert on shared folders. But I have saved some links so I can learn.

It seems like you do not want the shared folder inside your /home/you  but either as /home or a separate partition. Then you can create groups  and separate ownership & permissions.

Several threads with similar issues.

Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

---

### Post by brawd on 2012-09-05
Hi All,

Thanks for your replies, but I think most of you are going too deep, All I want to do is allow my wife who has her own account on the same machine as me to access my picture folder. The Picture folder is the bog standard one that appears in my home folder as part of the Ubuntu 12.04 LTS setup. That would save me having two identical 2Gigabyte (or so) folders on the same HDD.

My account is dad and hers is mam.

We both have the Public folders in there too.

So, trying out Linux_junky's suggestion seemed the obvious thing to do and that's what I did.

I put a couple of photos in /home/dad/public fully expecting to be able to see them in /home/mam/public, but that didn't happen. I'd be interested if someone out there running 12.04 LTS tries a very similar thing and can actually see the photos or files or whatever. That would indicate whether or not I have a Ubuntu 12.04 setup problem.

I'm not dealing with a network or anything like that, even though my photos are backed up on a freenas Raid array (which I can see easily).

It strikes me as being way over the top to set up groups and users and permissions. After all I am purely a GUI user and my wife would be disgusted with me if I showed any inclination to complicate what should be very simple indeed.

And what's this user + password thing all about when I take the network path. Do I input my user name and password - as if to give my blessing to her to view files in my account, or do we put in her user name and password? (This is a rhetorical question, neither of these approaches gave access. I just tried it.).

regards

---

### Post by critin on 2012-09-05
> So I right clicked on the folder and told it to share.Did you also open the folder properties and set the permissions to share the folder and the items inside?  Share both read and write to OTHERS under permissions.
[B]
edited to add: [/B] When you told it to share, did it open so you could click "Share the Folder" and complete the permission to add the share?  It will need to do that too.  
If you choose 'without an account', she shouldn't have to mess with passwords.

---

### Post by lykwydchykyn on 2012-09-05
You don't need to muck about with the "share" thingy.  That's for sharing on a network.  You're on the same computer, so forget the whole network sharing thing.

If she just opens a file browser and goes to /home/dad/Pictures, does she not see the pictures?

---

### Post by critin on 2012-09-05
She can open Home Folder on the desktop, go down to File System, (along the side menu), open and then open Home that is among other folders on that page,  Open Public and then open the folder that holds the pics.  On mine it is listed under the host user name.  It will be under your user name.  The other's name will be there also.  For instance, I have two folders showing, one for each acct.

She won't get to it via Public Folder this way, but she will get to it.  That's because my pics were in my pic folder.  If the pic are directly in the Public Folder, it works the same way.

If permissions are set to no password share, none is needed to open.
I right clicked on the pic folder and chose to copy to the desktop.  Whether it's always available there, I won't know until I test it.   But it should be.

It can then be right clicked and copied to Home if it isn't wanted on the desktop.   I don't believe that copies the pics, only the shared folder so it would do what you wanted it to do.  Then she can get to it through her normal Home.

---

### Post by brawd on 2012-09-06
Thank you everybody my problem is solved. The option that worked was the /Home/filesystem and look for my name - as listed in the two replies above.

Thanks again.

---

