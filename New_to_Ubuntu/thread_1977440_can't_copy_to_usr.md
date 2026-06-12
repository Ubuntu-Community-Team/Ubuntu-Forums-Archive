---
title: "can't copy to /usr"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by MHN on 2012-05-10
Hi,

I'm trying to copy jboss.rar to /usr. Ofcourse, its not letting me, the paste option doesn't get highlighted.
So, I tried to copy from terminal. logged in as su.
And was able to.
I used the rar command to extract to a directory jboss I created there, But, what got extracted was just grabage, don't even know where those files are coming from. :( :( . Lots and lots of junk.
So, I removed from /usr, the .rar and the jboss directory. Again the system didn't allow me thro' gui, so had to do it from terminal. Which was a headache. Because the directory wasn't getting deleted, it kept saying, its a directory. So, I had to use rm -f to forcefully delete.
May be some problem with the permission or something. But, just unable to login to root also, thro' GUI, may be they have removed that option in 12.04.

Tried to create a user called root, again was not able to.

I also tried to extract the rar in /home itself, and copy the extracted directory, but again I'm unable to, even though I'm doing it as su.

What should I do?

---

### Post by lisati on 2012-05-10
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MHN on 2012-05-10
Thanks, I dont use su.
So, u are saying watever I want to do inside /usr I have to use sudo ???
Thanks.

---

### Post by Pilot6 on 2012-05-10
You can modify, delete, etc. files only in you home folder without sudo. To manage other files you need sudo.

---

### Post by lisati on 2012-05-10
> **MHN said:**
> Thanks, I dont use su.
So, u are saying watever I want to do inside /usr I have to use sudo ???
Thanks.

The "usr" folder is normally "owned" by "root". Because of this, it will usually be necessary to use one of the "sudo" variants if you want to copy files there or modify one of the files.

---

### Post by MHN on 2012-05-10
mohan@mohan-desktop:/usr$ sudo rm jboss1
rm: cannot remove `jboss1': Is a directory

now ?

jboss1 is a empty folder, btw. :(

---

### Post by lisati on 2012-05-10
"rm" is normally used for files. If you wish to remove a directory/folder, the "rmdir" should be used instead, but will only work if the directory is empty.

---

### Post by CatKiller on 2012-05-10
gksudo nautilus

---

### Post by MHN on 2012-05-10
Thank you very much. :)

---

### Post by MHN on 2012-05-10
> gksudo nautilus

This is good. :).

Thanks.

---

### Post by zombifier25 on 2012-05-10
Or rm -r is you want to delete a non-empty directory.

---

### Post by bogan on 2012-05-10
Hi!, **zombifier25,**

You Posted:> In Ubuntu, the [COLOR=Red]root[/COLOR] account exists, but it has no[COLOR=Red] password.[/COLOR]In previous Ubuntu versions choosing the 'Drop to root terminal' option in the recovery menu, led you to a root terminal prompt, without logging-in or entering a password.

In my updated 12.04 LTS, apart from the stupidity of opening in Read only mode, without an option to change to Read/Write, the 'Drop to root terminal' option demands a root password - which does not exist - and will not accept the normal log-in user password.

The only alternative offered is 'Ctrl+d' which reverts to the menu.

If you - or anyone else, knows how to overcome this, [Edit: Other than by setting a Root Password], please Post it. Elaborate searches got me nowhere.

Chao!, **bogan**.

---

