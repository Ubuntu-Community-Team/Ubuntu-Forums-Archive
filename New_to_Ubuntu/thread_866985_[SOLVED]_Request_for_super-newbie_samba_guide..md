---
title: "[SOLVED] Request for super-newbie samba guide."
date: 2008-07-22
forum: New to Ubuntu
---

### Post by geokok1981 on 2008-07-22
Hi. I have been trying to set up shares between my two machines (1. ubuntu desktop. 2. WinXp laptop) so I could hopefully sync some files, since Dapper. So far I have achieved this:

--- Set up windows machine to share folders on the network and access them from ubuntu. ---

However, this is not the best option since I would rather my desktop machine to be the "server" ,lets say, and be the one that hosts the shared files which I would then sync with my laptop. So this is what I need:

--Set up ubuntu to share files, without making my system vulnerable.   
--Set up Winxp to access those files. 
--(optional, but desired as well).Get a solution to sync between both
--Get a laptop that runs linux (but that will come later :) )

Points to consider:

--Gui or CLI guidance is acceptable as long as it is complete (more than one methods are desired, I really want to learn how to do this in many ways, easy and difficult as well)

--Please do not point me to other links/guides. I have read them, tried them but I always failed at some point on all of them, either by not understanding something, something not working, or whatever reason. 

-- Please, guide me through, as if you were doing it yourself while tutoring a child :) . Networks are not my strong point. I really need an idiot proof path to success. 

Thanks in advance, even for taking the time to read this :).

---

### Post by geokok1981 on 2008-07-23
I managed to figure it out myself with a little help from the folks at ubuntu-gr

Just for the sake of helping others here are the steps taken:

1. Through Nautilus right click a folder. 
2. Choose Share and make the appropriate selections (check guest access as well at first just to make sure it works and disable it later on of u like).
3. Make sure firewalls on both machines allow pings between them. 
4. If all goes well u should be able to see the shares now.
To require password:
4. Open a terminal and type:
```
sudo smbpasswd -a your_username_here
sudo smbpasswd -e your_username_here
```

I had to create a user with the same username and password as my ubuntu box to get access to the shares, though. 

As for syncing you have two options:

1. Install cygwin + rsync on windows
2. Install synctoy (from microsoft powertoys). 

I did the latter but I am having some issues with text formatting on text files for some reasons. Anyway. good luck!!!

---

