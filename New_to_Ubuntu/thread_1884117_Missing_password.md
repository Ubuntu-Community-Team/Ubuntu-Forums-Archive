---
title: "Missing password"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by ETPAMC on 2011-11-20
Hello, I hate a huge problem, I need help trying to find my authenticate password! 
You see, I used to have  Windows XP. It was the best operating system I ever had. But them the computer with XP on it broke. So now I have this new computer with Ubuntu, and I don't get It at all!

But my biggest problem so far is this authenticate password! I don't know It at ALL! When I got the computer, it didn't come with one. 

Because of this, I cant use the administration center, or even get new software! 

Please tell me if there is anyway to find this password! I really need it!

---

### Post by underquark on 2011-11-20
If it's a new computer and you haven't used it yet then you won't have any data to lose so just re-install ubuntu.

---

### Post by CaptainMark on 2011-11-20
the password for ubuntu is created during the installation process, which if you bought the computer brand new and ubuntu was already on it, should have already been done so i would assume the default password would come in the documentation, recovering a lost password is not easy as its heavily encrypted, you would be better off reinstalling ubuntu yourself and making your own password , [follow this link for a new cd]("http://www.ubuntu.com/download/ubuntu/download")

---

### Post by mörgæs on 2011-11-20
Changed the thread title to a more descriptive one.

The password used for administrative tasks is just your normal password entered once more.

---

### Post by ajgreeny on 2011-11-20
If you have forgotten it, or do not know it as you did not install the system, go to [restore password]("http://www.psychocats.net/ubuntu/resetpassword") and you can follow the page there to reset the password as you want it.

The authenticate password is the same as you chose for the user password, when you installed, or the one you set in the restore password shown above.

---

### Post by AgTip on 2011-11-27
**HELP!**

I had some trouble with my password.  Several times I was told it wasn't correct.  So I refreshed the page and it worked fine.

HOWEVER

then I decided to change passwords.

I tried several new, simpler passwords and was told each time TOO SIMILAR TO YOUR PREVIOUS PASSWORD.  I kept trying.  Finally got one that worked.  Had a great session, turned off the machine and went to bed.

The next day, thanks to data overload, I cannot remember the password at all!  I was too excited, working too fast, etc (these are NOT excuses!  These are REASONS!)

I"m locked out.  The Psychocats page is great, but my version of Ubuntu, 11.10, in "restore mode" does not load all the way to the nice choice box, but stops after 15 lines of text.  I'm baffled.  I loaded Ubuntu inside of Win7 ... I would reload the Ubuntu installation over the top of the previous installation, but I don't know how to do that.  I'd love to UNINSTALL Ubuntu and then just reinstall, but don't know which files to delete.

Help.

Now I'm going into the basement and give myself 10 lashes with a Catholic repentance whip I got on Ebay...

---

### Post by gordintoronto on 2011-11-27
If you have a Wubi install, you can remove it with Windows Add/Remove programs, I think.

I have a file folder where I keep all my passwords on paper. I suggest you try this approach.

---

### Post by bcbc on 2011-11-27
You never have to reinstall for a lost password. Just boot recovery mode and drop to a root prompt and change it back. If you don't get the recovery menu it's because of a bug (I think in natty that has 'single' instead of 'recovery') but it's still a root prompt, so you can just complete:
```
ls /home  # shows your userid
passwd xxxx # where xxxx is your userid, enter new passwd when prompted
```

---

### Post by gordintoronto on 2011-11-28
> **bcbc said:**
> You never have to reinstall for a lost password. Just boot recovery mode and drop to a root prompt and change it back. If you don't get the recovery menu it's because of a bug (I think in natty that has 'single' instead of 'recovery') but it's still a root prompt, so you can just complete:
```
ls /home  # shows your userid
passwd xxxx # where xxxx is your userid, enter new passwd when prompted
```

This was a complete fail for me in Oneiric. I booted to recovery mode, selected root prompt. ls and ls /home showed nothing. (In Kubuntu 11.10 it showed my userid, gord)

passwd gord failed: "Authentication token manipulation error."

????

---

### Post by bcbc on 2011-11-28
> **gordintoronto said:**
> This was a complete fail for me in Oneiric. I booted to recovery mode, selected root prompt. ls and ls /home showed nothing. (In Kubuntu 11.10 it showed my userid, gord)

passwd gord failed: "Authentication token manipulation error."

????

You should file a bug then. It has always worked when I try it.
In any case, it's a bit extreme to make your first solution to "uninstall from control/panel". Maybe just suggest the normal approach first?

If you boot to recovery mode make sure it's not the "limited read-only recovery menu" - in which case you have to select the 3rd option "Remount read/write" before you can change the password.

---

### Post by gordintoronto on 2011-11-29
> **bcbc said:**
> If you boot to recovery mode make sure it's not the "limited read-only recovery menu" - in which case you have to select the 3rd option "Remount read/write" before you can change the password.

Bingo! Selecting the third option eventually let me specify a new password, without entering the previous password.

---

### Post by fdrake on 2011-11-29
best way if you are not sure how to get to the recovery option is to use a live cd/disk, also:
mount your filesystem change the /etc/shadow file, look for your username and delete the 2nd field (delimited by the double period), wich is your hashed password:
so from this > 
username[COLOR="Red"]_:jh7sh8u78ud99dyuycdch9ycdyc9/:_[/COLOR]151747:0:99999:7:::
 
to 
> 
username[COLOR="Red"]_::_[/COLOR]151747:0:99999:7:::
 
naturally if you use sude with that user you will encounter some problems because sudo will ask you to confirm a password, and since there is no password set sudo is not available.... but who needs sudo whe you can do the same with the root user! :D

note: red-hat and other system take both options ([COLOR="Red"]_::_[/COLOR]) empty and exclamation ([COLOR="Red"]_:!:_[/COLOR]) , instead ubuntu recognizes only the first one.

---

