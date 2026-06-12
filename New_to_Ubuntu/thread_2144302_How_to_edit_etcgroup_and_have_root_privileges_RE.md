---
title: "How to edit etc/group and have root privileges? RE:"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by devbeer on 2013-05-11
I am responding to the following thread no: 1420607 which people in their "wisdom" have LOCKED (which should be illegal on an valid question which is in no way abuse). [http://ubuntuforums.org/showthread.php?t=1420607](http://ubuntuforums.org/showthread.php?t=1420607)

The persons question was valid. I obviously dont want to chown "/" with my local user. But if i can temporarily add them to the root group, i can make it much easier for me to copy files between two servers i am upgrading. I prefer using notepad++ to compare files than VI, and obviously have only CLI and samba as its a server.

is there any way to make it easy to create/edit directories/files over a samba share with a normal user. I dont want to chown the individual directories or files one by one or at the cli at all. 

I want to quickly compare and copy files using windows. I  just want to add user , which can connect to samba fine, to group. Does anyone know how to do that?

parroting best practices is not answering the question. thanks

EDIT: I added user to group, but the main problem is that i still cannot write to any directory not owned by my user. Is it not possible?

---

### Post by CharlesA on 2013-05-11
Three year old thread is three years old.

[Why not just add a group]("http://www.cyberciti.biz/faq/ubuntu-add-user-to-group/") so whatever user you want to use as access to those files?

As far as parroting best practices, goes, [this post]("http://ubuntuforums.org/showthread.php?t=1420607&p=8910454&viewfull=1#post8910454") has good advice for this problem.

---

### Post by devbeer on 2013-05-11
i can add a user to a group now but i still cant copy any file I want under samba. I do apologize for not clarifying the question.

---

### Post by DuckHook on 2013-05-11
You must be having a bad day. No need to get so testy. In the thread you cite, the OP's question was asked and quite fully answered, with some very important "best practices" advice thrown in but only as an extra. And for what it's worth, you could do a lot worse around here than to attract an answer from bodhi.zazen who literally wrote the book on securing your box properly. And BTW, the thread was likely closed because it is *three years old*.

I don't need to reinvent the wheel, so will just quote the relevant passages of bodhi.zazen from the link you provided:> To add your user to a group use usermod```
usermod -G admin -a jay
```[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

Once your user has sudo access, lock the root account if needed```
sudo usermod -p ! root
```You can edit /etc/sudoers with the visudoers command. By default this will use vi, so to use nano ..```
# become ROOT
sudo -i
EDITOR='nano'
visudo
```

<edit>
Ninja'd by CharlesA
</edit>

---

### Post by bab1 on 2013-05-11
> **devbeer said:**
> i can add a user to a group now but i still cant copy any file I want under samba. I do apologize for not clarifying the question.

In a sense you make it hard (on yourself) with this comment>  **I dont want to chown** ... **at all**. 

I take that to mean that you want to do everything by the GUI interface.  In that case you are restricted to using Samba usershares.  These shares can be created by the mortal user (you) in your home directory with no admin permissions needed to do so.

If you want to administrate your machine you have to do it as the administrator (using sudo).  Setting up a directory ( the share) that all can use, controlled by the group permissions, is fairly trivial.   In fact it is easier to set one up from scratch than to modify an existing share with sub-directories and lots of files in them.

What would you like to do?

---

### Post by devbeer on 2013-05-11
Solved. On the windows machine, i am simply forcing it to log on with root user, as opposed to the named normal user.
1. open cmd.exe
2. check for existing connections to your server ('net use'), then reboot if connection is existing. I had no luck deleting linux connections for some reason.
3. after reboot double check with 'net use' that there are no connections then run:
net use \\IPADDRESS\SHARE /user:root

and give root password. you are now authenticated to samba as root and can edit any file.

solving my own problems: priceless

---

### Post by squakie on 2013-05-12
If it works for you, that's great.  One of the things people have been trying to keep clear to people is to not enable the root account.  In fact, as far as I know, it's against forum policy to explain to someone how to do so.  I suspect that part of what you may have seen/heard is in this regard.  Sudo normally takes care of everything.  Just me personally, but I'd be a little hesitant to have root open like that and especially with Samba running, but that is your choice.  When you are done, it would be a good idea to disable root again.  Ubuntu has done things the way it has since they don't want people getting on as root, messing their system all up, and then blaming Ubuntu being at fault and asking for help when the best advise at that point is just to reinstall.

Also, when posting to the forums it is best to either calm down from the irritation the problem has caused (we've all been there), or even as I recently did - ask the thread to  be closed.  In my case, I understood a lot more than the person trying to help thought, and had already been able to see my server, just not access the shares.  We went through several exchanges of basic information and I was back a step where not only could I not see the server, the server had no DNS so I was unable to get a domain name lookup to the actual IP address.  Believe me, that was frustrating for me, and frustrating to the person trying to help.  Like I said - we've all been there.  Sometimes it's better to "play by the rules" that Ubuntu has implemented than to fight it.

---

