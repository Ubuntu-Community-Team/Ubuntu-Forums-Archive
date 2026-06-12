---
title: "[SOLVED] Newbie dell ubuntu user"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Janeleaper on 2008-07-17
Hello.

I'm a technically challenged home pc user, who has just changed to Ubuntu from Windows because, since my XP pc never fully recovered from the installation of Service Pack 2, I'm too scared to try Vista and too poor to buy a Mac.

Set up my new Ubuntu Dell Inspiron today, and so far so good, but I still have some issues to resolve.

The Dell printer, not supported by Ubuntu, that I bought with the computer,  goes back tomorrow and Dell are refunding my money :)

We have a home network.  I've connected the Ubuntu pc to the router with the ethernet cable.  It has worked like a dream.  Connected to the internet  as if by magic and to the home network.  However, I'm having difficulty getting our Windows XP pc to recognise it.  The XP pc is on a wireless connection.  It is finding the router ok and connecting to the internet, but can't access the shared folder on the Ubuntu pc, although the Ubuntu has no difficulty accessing the shared folder on the XP.

I want to connect up a third pc to the network as well.  That is also loaded with XP - and will support my old dell printer.

Finally, I like listening to BBC radio and Radio Canada on my pc.  I've downloaded Real Player (following the advice on this forum), which works for the BBC, but for Radio Canada I seem to need something called MPLayer which uses the package download system, which I don't understand.  I'm going to have to go back to school or find an easy way.

I will be grovellingly grateful for all advice from people who do know what they are talking about, unlike me.

---

### Post by richiewrt on 2008-07-17
As far as accessing the shared folder on the ubuntu pc from a windows pc, you need to install and configure samba. Not the easiest thing in the world, but not that bad either. Samba is the windows sharing program. plenty of post about it here on the forum

---

### Post by Janeleaper on 2008-07-17
Wow that was quick!  Thank-you very much indeed.  I'll look into Samba first thing tomorrow.

---

### Post by hyper_ch on 2008-07-17
samba isn't that difficult... at least not if you want a very basic setup.

(0) install samba
```

sudo apt-get install samba

```

(1) make a copy of the current config as it has some good stuff in it (although not needed for my basic setup):
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.org

```

(2) create new samba config
```

gksudo gedit /etc/samba/smb.conf

```

(3) paste (and alter) this config
```

[global]
workgroup = WORKGROUP
hosts deny = 192.168.0.1

[exchange]
comment = Exchange
path = /home/{USER}/Exchange
force user = {USER}
force group = {USER}
read only = No

[appz]
comment = Appz
path = /home/{USER}/Appz

[media]
comment = Media
path = /home/{USER}/media

```

So, in this config alter the workgroup name to your workgroup.
Then alter the ip of hosts deny to the IP of your router.

Then replace {USER} with your username, you have an example on how to set a writeable dir and how to set two read-only dirs and then save the file.

(4) add your user to samba
```

sudo smbpasswd &#8211;a {USER}

```
Again, use your user. You will be prompted twice for the password. This password can be different from your system password but the user must be a system user.

(5) Restart samba
```

sudo /etc/init.d/samba restart

```

And now you should have access.

---

### Post by anthropoidster on 2008-07-17
Regarding the CBC, just open File/Open Location (or Ctrl+L) in RealPlayer and add:

[http://www.cbc.ca/livemedia/cbcr1-toronto.m3u](http://www.cbc.ca/livemedia/cbcr1-toronto.m3u)

for CBC Radio One and/or

[http://www.cbc.ca/livemedia/cbcr2-toronto.m3u](http://www.cbc.ca/livemedia/cbcr2-toronto.m3u)

for CBC Radio Two and you're set to go.
You should also find the CBC in RhythmBox - Radio

---

### Post by Janeleaper on 2008-07-17
Thanks for all the above advice.

I'm still having problems with the network, although if they cannot be resolved it is not crucial.

I followed hyper_ch's advice and found that Samba was already installed.  I followed the rest of his instructions.  I assumed that by 'user name' he meant my user name for the Ubuntu pc.

Unfortunately, this has made no difference to the functioning of the home network.  The XP pc is saying that the Ubuntu computer is a server.  Any ideas anyone?

---

### Post by SunnyRabbiera on 2008-07-17
hooking up a windows network can be tetchy, as windows wants to do one thing and ubuntu wants to do another.

---

### Post by eldragon on 2008-07-17
the best way to work out how to setup samba, is to know how file permissions work.

remember there are permissions in the linux filesystem.
samba works on TOP of those, so if the samba user doesnt have permissions to the shared resource, it wont be able to access it.

to put it simple.

say your username in the ubuntu machine is 'john'
you want people from the windows network access to john's shares through a 'guest account', this is the most common scenario on home networks, so we will assume this.

edit the smb.conf file like said in a previous post.

search for the line
```

guest account = 

```
if its commented (Starts with a # pound sign), remove such pound sign.
and make it look like
```

guest account = john

```
that will make every user trying to connect to your ubuntu machine through samba, not providing a valid user / pass behave as if they where john (similar to the guest account in windows).

now edit the shares (at the bottom of the file, with your shares.

for example, if you want to share the documents folder from john's home:
```

[Documents]
comment = documents of john on the ubuntu machine
writable = yes
locking = no
path = /home/john/Documents
public = yes

```

this will make a shared folder in the ubuntu machine called 'Documents' that points to john's documents folder in his home.
with public, you are allowing the guest account setup before to access the folder.
and with writable...well, you are allowing +w to the samba users that access the folder. in this case, john.

now you need to create a samba user called john (this will have to coincide with the username you wish to have as guest, and the owner of the share. this is quite important. since filesystem permissions superseeds samba permisions (so if samba has write access, but the filesystem doesnt allow access to that share, the user wont have access to write to that share).

to create the user:
```

sudo smbpasswd -a john

```
you can provide any password. if its NOT the same as johns passwd to log into ubuntu, better.

then restart samba with 
```

sudo /etc/init.d/samba restart

```


and, now you should have no problem login in from windows. make sure to restart windows just in case it did cache any previous attempts to login.


good luck.

---

### Post by Janeleaper on 2008-07-17
Thanks.  Actually, at this point I'm going to give up.  The network is good enough, even if it isn't perfect.  We have 3 pcs, one Ubuntu, 2 Windows XP.  There is a Dell printer attached to one of the XPs.  The Ubuntu can access the shared folders in both the XPs, but the XPs can't access the shared folder in Ubuntu.  The Ubuntu can't access the printer, but both the XPs can. 

That's fine.  Walking down stairs with a memory stick to use the printer in our basement will be good exercise!

---

