---
title: "creating and deleting files on samba shares, some help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by techno-mole on 2008-07-01
hello.
ive got 4 pc's on my home network, 2 are using xp, and the other 2 are using ubuntu, one of the ubuntu boxes is mine, and the other is acting as a file server (network storage if you like)
the network is fine, and all the systems can see each other, but for some reason i cant create a file on the xp systems through the network,
example - if i go to the shared folder on one of the xp machines and then right click to create a new file the option is blank and i cant actually create a file, or delete files etc.
so im guessing this is an access problem, but im not sure how to fix it, the shared files in the windows systems have the options for allowing network users to change files/folders but i still cant do it.
any help would be appreciated.
cheers

---

### Post by benfindlay on 2008-07-01
On the latest version of ubuntu, when you share a folder it has a tick box asking whether you want it to be read only or not, have you checked if this is ticked?

Also, have you added your user name to the samba user list using ```
sudo smbpasswd -L -a YOURUSERNAME
```followed by```
sudo smbpasswd -L -e YOURUSERNAME
```

You'll get the opportunity to set a password here too.

Hope this helps!

---

### Post by benfindlay on 2008-07-01
Sorry, midread your post, your problem is with windows, not ubuntu!

Ok, firstly we need to unshare everything that you have shared on your win box. Then, in My Computer, click Tools, Folder Options, View and scroll to the bottom. Untick simple sharing. Now reshare everything you want to share. In sharing, you can now create permissions for a specific username to use, I'd advise matching your ubuntu username if possible.
Also, you now have more preferences, including read, write, create etc. just tick whichever options you want!
Once this is done, click the Security tab and add the username here too, and also set the permissions you want!

Hope this helps!

---

### Post by techno-mole on 2008-07-01
okay, ive tried starting from scratch, but im not any closer to solving the problem.
i have changed the permissions on the windows systems, made sure everything that needs read / write access has it, but i still cant create / delete files / folders on the windows systems through the network.

(ive done sudo smbpasswd -L -e etc etc)

any ideas ?

---

### Post by benfindlay on 2008-07-01
The problem is windows, not ubuntu I believe, try what I said in my second post, as I've alsways had a problem with simple sharing in windows. Advanced sharing seems to work better!

Hope this helps!

---

### Post by techno-mole on 2008-07-01
thats the problem, it wont let me create or add a user name for me to set the permissions for.

---

### Post by benfindlay on 2008-07-01
Right click on the folder and chosen Sharing and Security, select to share the folder, then click Permissions and Click Add then enter the username you want into the object names section.

Will it let you do that?

---

### Post by techno-mole on 2008-07-01
yes, it lets me do that, but when i click ok it comes up with a box that says name not found, the message at the top of the box reads - 

" an object named " user " cannot be found, check the selected object types and location for accuracy and ensure that you typed the object name correctly, or remove this object from the selection "

---

### Post by benfindlay on 2008-07-01
Ah, ok, you need to first create that user on your windows system, by going into control panel, user accounts and choosing create a new account. I'd recommend making the account limited and setting the user/pass to be IDENTICAL to your login credentials on the ubuntu machines!

---

### Post by techno-mole on 2008-07-01
thats odd, never had to do that before, even when i upgraded to hardy i just had to select the files i wanted to share on my linux box, and then run the network setup wizard on the windows machines, and hey presto.

its only been the last few days that this has stopped working, seems odd to need to set up an account just so i can share files, even more so when the windows machine doesnt need a user account to access the files that ive shared on my linux box.

---

### Post by techno-mole on 2008-07-01
still no dice,
now when i open up the shared folder for the xp system (one of them, still need to sort the other one) it doesnt display any files, and if i click to create a file i get an error 

it just says there was an error creating the file, and when you click the little arrow for more details it says " operation not supported by backend "

---

