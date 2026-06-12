---
title: "Cannot see Ubuntu in Windows 7 Homegroup"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by kibaruzo159 on 2012-10-22
I am a first time Ubuntu user and just installed 12.10 last weekend.  I am able to view my Windows 7 workgroup via Ubuntu and can access my windows 7 computers.  However, from my windows computers, ubuntu does not show up in my homegroup.  I have installed Samba and shared a folder as well. I can however access Ubuntu shared folder by using IP address under the windows network section.  When I tested 12.10 using the boot cd, the "Ubuntu" computer icon automatically showed up when viewing the homegroup from my windows pc.  I have searched many threads but at a loss how to fix this.  Any help would be greatly appreciated.

---

### Post by critin on 2012-10-23
Hello there.

Have you added ubuntu to the windows workgroup?  Also, some versions require a workgroup password to be entered one time, (if you ask it to remember it)  and sometimes the ubuntu password too--and other versions don't.  Some of mine did and others didn't, and I have no idea why this happens.  

Also, I have had times when I had to restart both machines before it would work.  

A few minutes ago, my 12.10 ubuntu connected to the lan very easily, I could see the files come up on windows as they were added to the share on ubuntu.   I did not even have to add 12.10 to the workgroup.  It shows up under its own 'workgroup' icon, the other machines are in the win workgroup.  It's amazing... All I did was share a folder with permissions to change files inside.  Samba shares were added.  Exactly as you did probably.

Here is a useful link, I hope it can help you.

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

---

### Post by Mark Phelps on 2012-10-23
Just so you know ... homegroups and workgroups, although they sound the same, are VERY different.  Only Win7 can work with homegroups.  Linux, Vista, and XP can NOT.  Everyone can work with workgroups.

So, if you're asking specifically about Win7 "homegroups", there is no way to get them working with anything except Win7 (and maybe, Win8).

---

### Post by kibaruzo159 on 2012-10-23
> **Mark Phelps said:**
> Just so you know ... homegroups and workgroups, although they sound the same, are VERY different.  Only Win7 can work with homegroups.  Linux, Vista, and XP can NOT.  Everyone can work with workgroups.

So, if you're asking specifically about Win7 "homegroups", there is no way to get them working with anything except Win7 (and maybe, Win8).


Hi Mark, thanks for pointing that out and I should have been a clearer there.  Just trying to get Ubuntu to show up on my Windows PC's work groups.  Title corrected :oops:

---

### Post by kibaruzo159 on 2012-10-23
> **critin said:**
> Hello there.

Have you added ubuntu to the windows workgroup?  Also, some versions require a workgroup password to be entered one time, (if you ask it to remember it)  and sometimes the ubuntu password too--and other versions don't.  Some of mine did and others didn't, and I have no idea why this happens.  

Also, I have had times when I had to restart both machines before it would work.  

A few minutes ago, my 12.10 ubuntu connected to the lan very easily, I could see the files come up on windows as they were added to the share on ubuntu.   I did not even have to add 12.10 to the workgroup.  It shows up under its own 'workgroup' icon, the other machines are in the win workgroup.  It's amazing... All I did was share a folder with permissions to change files inside.  Samba shares were added.  Exactly as you did probably.

Here is a useful link, I hope it can help you.

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)


Hi Critin,  I checked out that link and it is pretty much what I have done.  You asked if I added ubuntu to the windows workgroup.  Is there an alternative process outside of the directions in the link you shared?  You also mentioned "Also, some versions require a  workgroup password to be entered one time, (if you ask it to remember  it)  and sometimes the ubuntu password too--and other versions don't."  Is this workgroup password something that needs to be entered in Ubutu?  

This issue still seems so strange as I can see the windows workgroup computers from Ubuntu but no computer icon shows up for Ubuntu on the Win side........

---

### Post by critin on 2012-10-24
> **kibaruzo159 said:**
> Hi Critin,  I checked out that link and it is pretty much what I have done.  You asked if I added ubuntu to the windows workgroup.  Is there an alternative process outside of the directions in the link you shared?  You also mentioned "Also, some versions require a  workgroup password to be entered one time, (if you ask it to remember  it)  and sometimes the ubuntu password too--and other versions don't."  Is this workgroup password something that needs to be entered in Ubutu?  

This issue still seems so strange as I can see the windows workgroup computers from Ubuntu but no computer icon shows up for Ubuntu on the Win side........

The link shows how I added ubuntu to windows workgroup through samba.  Enter the workgroup name in the space.

Yes, once you see windows in ubuntu and click to open it, a box will pop up asking for a password (in some versions, not all)  It wants the password that windows will give you.  Go to windows and click 'add computer to workgroup', or similar words.  It will show the password to be entered in the ubuntu box.  There is an option to keep the password forever, click it and it will not ask again.

If the box pops up again, it will want the ubuntu password this time.  type that in and choose keep forever.  (if you don't want to type it in everytime.

Again, my 12.10 did not ask for password, maybe because other partitions on the computer have already been validated, I don't know.

I allow access to "everyone" and have no issues.  If you restrict access to yourself only, be sure to enter the user name and permissions in everything you share.

If you don't see workgroup after adding the name in samba, I don't know what is wrong.

---

### Post by Morbius1 on 2012-10-24
> **kibaruzo159 said:**
> This issue still seems so strange as I can see the windows workgroup computers from Ubuntu but no computer icon shows up for Ubuntu on the Win side........
Post the output of the following commands from the Ubuntu machine:
```
hostname
testparm -s
smbtree
```Just a wild guess at this point since we don't have all the facts but after running the "hostname" command count the number of characters. If it's 16 or more no one can see your machine because it's netbios name is too long. You can fix that in smb.conf itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following to the [global] sections - right uner the workgroup line:
```
netbios name = something
```[COLOR=Blue]*Just make sure *[COLOR=Black]**something**[/COLOR]* is 15 characters or less in length.*[/COLOR]

Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```Wait a few minutes ( Samba / Windows are very temperamental with a samba restart ) and see if you can find the machine from Windows.

---

### Post by kibaruzo159 on 2012-10-24
> **Morbius1 said:**
> Post the output of the following commands from the Ubuntu machine:
```
hostname
testparm -s
smbtree
```Just a wild guess at this point since we don't have all the facts but after running the "hostname" command count the number of characters. If it's 16 or more no one can see your machine because it's netbios name is too long. You can fix that in smb.conf itself


Hi Morbius1,  your wild guess was spot on.  It was simply that the default netbios name was too long.  I changed and all is working like a charm.  Thanks much for the help!

---

### Post by critin on 2012-10-25
> **meliscarop said:**
> I could see the files come up on windows as they were added to the share on ubuntu.[IMG]<snip>[/IMG]


You too?  :P

---

### Post by Novice Networker on 2013-04-18
oops

---

### Post by superdad on 2013-06-04
I followed all of this, but didn't realise that I needed to refresh the windows network.

---

