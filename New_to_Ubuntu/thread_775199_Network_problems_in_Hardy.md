---
title: "Network problems in Hardy"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by cong06 on 2008-04-29
I'm working in a Large College network and have been having a lot of problems connecting to shared documents (using samba).

The original problem was one where my shared folders were accessible only to people in the same dorm building. And I could only access others shared documents in the dorm building.

When I got around to testing with "smbclient" I found that it was specifically my computer with Hardy that had the problem. Windows computers don't, and my Gutsy computer doesn't have the problem either.

Does anyone know why Samba in Hardy is harder by default to use on large networks then Gutsy? What could the problem be?


fyi: this post is void now...I somehow got it to work. I don't know what I did...
see other problems below however.

---

### Post by ivan0921 on 2008-04-29
I am having the same problem, my windows networks share fail to mount. It just keeps asking for the password, but fails to mount. 7.10 doesn't have this problem, any suggestions? Thanks in advanced.

---

### Post by swoll1980 on 2008-04-29
did you set up your your samba user account?
```
sudo smbpasswd -a username
```

---

### Post by cong06 on 2008-04-30
well, my problem isn't about passwords, it's about actually viewing the shared stuff...

For example on my Hardy box I run:

```

me@hardy:~$ smbclient -L '\\computer\'
Connection to computer failed (Error NT_STATUS_BAD_NETWORK_NAME)

```

Then I go to Gutsy and get this:
```

me@gutsy:~$ smbclient -L '\\computer\'
Password: 
Domain=[COMPUTER] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        video           Disk      
        SharedDocs      Disk      
        books           Disk      
        print$          Disk      Printer Drivers
        games           Disk      
        drop box        Disk      
        music           Disk      
        audio books     Disk      
        programs        Disk      
Domain=[COMPUTER] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```
Like I said, I thought it was a network problem with the college until I realized that the problem was between two computers...in the same room...on the same switch...the farthest the problem could be from my box would be the switch, and the switch definitely doesn't have the capabilities to do this.

---

### Post by MaindotC on 2008-04-30
I believe this problem is already being worked on:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072)

And there's a patch here:

[http://bugzilla.gnome.org/show_bug.cgi?id=524485](http://bugzilla.gnome.org/show_bug.cgi?id=524485)

but I don't know how to install it.  Are you getting the error message:

Error: Failed to mount Windows share
Please select another viewer and try again.

---

### Post by cong06 on 2008-04-30
> **strAlan said:**
> I believe this problem is already being worked on:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/207072)


> Machines running windows XP, windows 2003 and samba show '0 objects' in nautilus, but after inserting the complete path (eg.: smb://server/share) the folders can be accessed after the password prompt.


Actually, see, I'm getting an error message trying to connect. I'd try the patch, but it doesn't seem to address the actual situation I'm having.

When I try to connect to a specific folder, *that's* when it claims it's not connected...
If I browse to "smb://computer/" then it comes up with "Window shares on Computer" as an empty folder with no items.

If you think that the patch will definitely help, then I'll try it, but I don't want to add anything that will make this dist **more** unstable...

---

### Post by MaindotC on 2008-04-30
I'm not sure if the patch will help but even if I did I'm not sure how to apply it.  It seems to be just source code - proabably have to add it to the samba source but I dunno where.

I can connect to shares that don't require a password - like the folder I'm trying to access is on a server with 100 billion other folders and I can connect to that server and see them, then when I select my folder it says the error message I stated above.

---

### Post by cong06 on 2008-04-30
> **strAlan said:**
> Are you getting the error message:

Error: Failed to mount Windows share
Please select another viewer and try again.

I'm sorry, I miss read your post. I thought it was an error message for the patch.

Yes. that's the **exact error message** I was getting when I try and access Shared folders.

If I don't get much of a response maybe I'll post a bug...that sometimes generates help.

---

### Post by BDNiner on 2008-04-30
I am able to connect to my windows shares, it just won't remember the connection when i restart the computer. I never had this problem with Gutsy, i connected to my shares once and that was that.

---

### Post by MaindotC on 2008-04-30
> **cong06 said:**
> I'm sorry, I miss read your post. I thought it was an error message for the patch.

Yes. that's the **exact error message** I was getting when I try and access Shared folders.

If I don't get much of a response maybe I'll post a bug...that sometimes generates help.

Well I think there's already a bug posted - that's the one I'm monitoring and I posted a link above.  Did you see it?

---

### Post by buntunub on 2008-05-03
> **strAlan said:**
> I'm not sure if the patch will help but even if I did I'm not sure how to apply it.  It seems to be just source code - proabably have to add it to the samba source but I dunno where.

I can connect to shares that don't require a password - like the folder I'm trying to access is on a server with 100 billion other folders and I can connect to that server and see them, then when I select my folder it says the error message I stated above.

Right click the download link to the patch and "save as" to desktop. Then right click the file and go to Properties>Permissions, and check the box that says Execute. Then close out and double click the file on your desktop and run it.

---

### Post by cong06 on 2008-05-03
I probably should have mentioned it...

I finally did get it to work. I think the problem was it was actually a network problem here...and was just utterly confusing me because my laptop in the same room was doing perfectly fine (actually my desktop was too, but some real confusion with dns names...which I'll get to)



Now the confusing thing is (that's workable):

One computer has the dns name **computer.domain.com** the owner of computer has another one with the dns name **computer-2.domain.com**. His computer name for **computer** (in windows, for shared documents) is *computer2* since actually **computer-2.domain.com** is his primary box (he registered it first...don't ask. the college does funky things with dns when people have two computers...) and the other one is called *computer*

ok. so if you followed all that...there's another person who has the dns name: **user.domain.com**. his windows name is "owens" cause that's what he wants.

I can browse ```
smbclient -L '\\owens'
``` ie, I can use the windows name to browse.
if I use his dns name: ```
smbclient -L '\\user'
``` then it shows up with the computer, but doesn't show the folders.

Ok. now back to the owner of **computer**. if I run:
```
smbclient -L '\\computer'
```
It gives nothing. of course, because the dns name **computer** is for his laptop, which doesn't have shared documents. (contradicting what we just found out)
So I use the other name: **computer-2** and this time it doesn't throw an error, it actually connects, but it only shows as much it did for for the previous student (running "smbclient -L '\\user'")

So basically the only way to actually view his documents is to write in the IP address for his specific computer. It works fine for all the other ones, but apparently the confusion with two computers messes up hardy.

So...if you followed all that, what do you think?

---

### Post by MaindotC on 2008-05-03
buntunub - thank you for your directions and I followed them.  It didn't resolve my issue but at least I know how to handle .patch files in the future :)

cong06 - going to take me a while to read through your post and try it out.

---

### Post by ir0n on 2008-05-08
Try smb4k to browse and mount samba shares. Don't know what exactly is the problem but it seems like Nautilus refuse to browse windows shares while smb4k succeed.
I know smb4k is kde app but its a very good instant solution.
sudo apt-get install smb4k

---

### Post by anco on 2008-05-21
I also have problems with connecting to an open windows network since upgrading to Hardy. Sometimes I can connect directly to the windows network and browse other shared computers and their folders, however sometimes it suddenly asks for a pasword and if I cancel that window than I'm anyhow entering the folder I just clicked on.

If I than close nautilus and try it directly again to find a windows network and browse to another machine, than nautilus says 0 found???? Than 10 minutes later I try again, no reboot whatsoever in between and it suddenly finds the windows network again. My laptop is the only linux machine in this network and in Gutsy I never had these problems. It is definitely hardy related.

I'm just a user and don't know the technics behind it. I was used in gutsy to browse the windows network without problems and without manually doing anything in samba. I just went always through the menu Places and network to the windows machines. All programmer thanks a lot for your work.

---

### Post by MaindotC on 2008-05-22
Although this doesn't really solve the problem, it seems that smb4k is a work-around to get you access to password-protected shares.  Download and try it out.

---

### Post by Dani Filth on 2008-05-23
Well, smb4k now allows me to see the Windows shares and access them, but its inconvenience is I have to browse mostly the whole LAN (which takes some times) to see all the share stuffs in the networks then choose the certain shares.

Does anyone know any way to access the specific PC's IP like samba (Ubuntu) did in 7.10 & previous versions by just typing in "smb://LAN_IP" in Nautilus?

---

### Post by drsox1899 on 2008-05-24
> **ir0n said:**
> Try smb4k to browse and mount samba shares. Don't know what exactly is the problem but it seems like Nautilus refuse to browse windows shares while smb4k succeed.
I know smb4k is kde app but its a very good instant solution.
sudo apt-get install smb4k

Here's another update on this workaraound.

Once smb4k has been used to mount the protected shares, Nautilus will function normally regarding opening folders on the share etc.  Seems like the problem is with password verification.

---

### Post by morbid_bean on 2008-08-15
So has there been a workaround found?

---

### Post by fade2gray on 2008-08-16
Don't know if this is relevant.

I had been experimenting with Hardy desktop version for several weeks when I found this thread and gave up. I now run Hardy server version administered using webmin (w w w.webmin.com) via a networked windows box running firefox3. 

webmin configures samba shares beautifully and I dare say it should work just as well running on a Hardy desktop install.

\\:D/

---

### Post by bluegene on 2008-10-31
I am encountering this same error in my Ubuntu Hardy box. I was surprised when I try using this command in nautilus: **smb://server/share** and voila! I was able to see the share. I think the important point here is that you should always include the complete path regardless whether you have the patch applied. I hope Intrepid this issue might resolved. :)

---

