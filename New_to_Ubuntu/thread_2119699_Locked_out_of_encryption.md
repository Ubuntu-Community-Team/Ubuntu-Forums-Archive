---
title: "Locked out of encryption"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Panwage on 2013-02-24
Firstly Hello,

I'm sorry that my first foray into the community is a question. But I need help.

As the title reads I can't actually start ubuntu because I decided to encrypt the hard drive during installation. 

I try to log in with the password, as it says it is a bad password.
Now what you're probably thinking is, you entered the wrong password. No, not a chance, I even wrote it down because I *thought* I understood the gravity of such a feature.

The only thing I can think of, is the number lock isn't on when entering my password. When I click the "Num Lock" feature on my keyboard, I get, "No Key available with this passphrase"

So these are the things I'm seeing.

When my laptop loads I see:
[IMG]http://i49.tinypic.com/1zm1nr9.jpg[/IMG]

After selecting Ubuntu I see:
[IMG]http://i47.tinypic.com/2vu08c3.jpg[/IMG]

After entering what my pass is supposed to be I see:
[IMG]http://i49.tinypic.com/jfkvw1.jpg[/IMG]

Firstly why is it rejecting my password?
Did something go wrong during the install?

Secondly and **most importantly**, what are my options? 

Please help...please.

---

### Post by TheFu on 2013-02-24
> **Panwage said:**
> Secondly and **most importantly**, what are my options? 

Please help...please.

Just restore from a backup to a newly installed system where you are 100% positive about the password.

When using encryption, backups are critical.

It is unclear from your post whether you just installed or this install has been around for years. Please explain that aspect.  
Did the password used to work, but stop recently?  
Have you tried a different keyboard? 
Perhaps the shift key is stuck?

Good backups make issues like this (and many, many,) many others not so critical.

---

### Post by QIII on 2013-02-24
Welcome to the Forums!

Eh!  Who cares if your first post is a question?  That's what we're here for! ;)

If numlock was not on, you may have a difficult row to hoe.  I don't know what the up/down (etc) keys may have wrought -- if they were even registered as part of a password.

If your BIOS/EFI has the option to turn numlock on and off during boot, you might try toggling it.

Good luck!

---

### Post by Panwage on 2013-02-24
QIII, I just don't like to bother anyone. I'm as stubborn as a donkey ;)

The Fu, No it is a new password, new install and it's a laptop so can't change the keyboard.

I think somethings wrong with the install.
Why else wouldn't it accept a password that, because I new how important it was - watched the keys input key for key and then wrote down the password.

At this rate I'm going to have to scrap the hard drive.
It is so tedious. Tried caps lock, that wont come on, tried num lock and neither will that.

If this is a common occurrence it definitely needs looking at.

So what we've established:
Nothing I put in as the pass will work.
No variations can be completed because of the lack of num/cap lock functionality.

Now what I would like to request:
A work around, this is probably very unlikely, but desperate time calls for desperate measures.

I'm a nub at this coding stuff, but am hoping to learn.
Last time I ran Ubuntu I was useless, but now I'm desperate I'm sure if it can be got around and someone shows me- I can do it.

---

### Post by alphacrucis2 on 2013-02-24
Your workaround is to install again from scratch.

---

### Post by TheFu on 2013-02-24
> **Panwage said:**
>  The Fu, No it is a new password, new install and it's a laptop so can't change the keyboard.
I've changed the keyboard on laptops a few times, so I know it is possible.  A key was sticking and cleaning it out didn't fix the issue, so a replacement is needed.

At least you didn't lose any data, since this was a fresh install.  Which version of Ubuntu and did you use whole drive encryption or just home directory encryption?
The options for home directory are different.  For whole disk, reinstall is the only option I see.

Which encryption technique was used?   LUKS, EncFS, eCryptfs, Truecrypt, something else?  I can understanding not knowing which was used, but I have to ask.

> **Panwage said:**
>  I think somethings wrong with the install.
Why else wouldn't it accept a password that, because I new how important it was - watched the keys input key for key and then wrote down the password.  

Could be - which version of Ubuntu?  I'm still on 12.04 LTS, because I prefer not to be a beta tester.
I have also been 100% positive that I was typing the password in correctly, then later found that I was making a mistake OR the keyboard was sticking on a key or repeating another.  It was on a system with the HOME directory encrypted, not the whole drive.  Do you know which you have?

If just HOME directory encryption, you can create another account and either use or do not use encryption. This time, make the passphrase something that you can type on a broken keyboard.  If offered to create a backup decryption key, accept. it.  To do these things, boot off the liveCD, mount the file system where /etc is, modify the passwd file and the sudoers file for the new account you've created, create the /home/new-account directory owned by the same, new, userid - that should be it.

Another thread here [http://ubuntuforums.org/showthread.php?t=2035388](http://ubuntuforums.org/showthread.php?t=2035388) seems to be related. You've probably already seen that.

> **Panwage said:**
>  At this rate I'm going to have to scrap the hard drive.
It is so tedious. Tried caps lock, that wont come on, tried num lock and neither will that. 
There is no need to scrap the HDD. Worst case,  wipe it and reinstall over it, assuming you don't have the recovery keys - wasn't that the first suggestion - to backup the encryption recovery keys?  Perhaps not. I don't know.

Try plugging in a USB keyboard. This should bypass whatever issue your laptop keyboard is having. 

> **Panwage said:**
>  If this is a common occurrence it definitely needs looking at.
I've never had any issue logging into my home directory encrypted 12.04 systems - well, except when I was mistyping the password. Then I couldn't get in - and I was pleased.  What good is an encryption system that lets someone in without the correct password?

> **Panwage said:**
>  So what we've established:
Nothing I put in as the pass will work.
No variations can be completed because of the lack of num/cap lock functionality.  
If you plug in a USB keyboard, you can use that instead of the built-in keyboard.  I'm using my laptop that way right now - full-sized keyboard and mouse while it is connected to 2 external monitors.  Anyway - just another option to consider.

> **Panwage said:**
>  Now what I would like to request:
A work around, this is probably very unlikely, but desperate time calls for desperate measures.  Backups or the other options that I've listed above are it.  If you choose to encrypt, you should also choose to have really excellent backups.

> **Panwage said:**
>  I'm a nub at this coding stuff, but am hoping to learn.
Last time I ran Ubuntu I was useless, but now I'm desperate I'm sure if it can be got around and someone shows me- I can do it.
What "coding" are you doing?  Seems like you are just doing end-user stuff.

One of the downsides to encryption is the possibility of complete data loss. A slight performance hit is the other.  When using encryption, having great backups is critical.  [http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t](http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t) explains more. More explanation [http://www.linux-mag.com/id/7568/1/](http://www.linux-mag.com/id/7568/1/)

An encryption scheme that can be easily hacked is a terrible idea. That would completely defeat the purpose, right?

Good luck.

---

### Post by Panwage on 2013-02-24
> **alphacrucis2 said:**
> Your workaround is to install again from scratch.

Can't, or can I?

It's not loading my boot disk/USB since that hard drive is locked out.

---

### Post by UltimateCat on 2013-02-24
Hi:

If it were me; I would re-install Ubuntu.;)

And **write down** the encrypted password **exactly** the way that you type it in.

Good luck

---

### Post by alphacrucis2 on 2013-02-24
> **Panwage said:**
> Can't, or can I?

It's not loading my boot disk/USB since that hard drive is locked out.

HD access isnt normally required to boot from CD or USB? Once booted into the installer you want to overwrite the existing HD partition(s). Doesn't matter if they are encrypted or not.

---

### Post by matt_symes on 2013-02-24
Hi

You can try from a LiveCD. It will eliminate/implicate your Ubuntu install

[http://ubuntuforums.org/showthread.php?t=1597246](http://ubuntuforums.org/showthread.php?t=1597246)

Kind regards

---

### Post by DuckHook on 2013-02-24
At this point, the best option is to just reinstall, but this time, encrypt only what is needed. Never the whole drive. Please see [this]("http://ubuntuforums.org/showthread.php?p=12514214#post12514214") post on earlier thread.

---

### Post by Panwage on 2013-02-24
> **TheFu said:**
> I've changed the keyboard on laptops a few times, so I know it is possible.  A key was sticking and cleaning it out didn't fix the issue, so a replacement is needed.

At least you didn't lose any data, since this was a fresh install.  Which version of Ubuntu and did you use whole drive encryption or just home directory encryption?
The options for home directory are different.  For whole disk, reinstall is the only option I see.

Which encryption technique was used?   LUKS, EncFS, eCryptfs, Truecrypt, something else?  I can understanding not knowing which was used, but I have to ask.

  

Could be - which version of Ubuntu?  I'm still on 12.04 LTS, because I prefer not to be a beta tester.
I have also been 100% positive that I was typing the password in correctly, then later found that I was making a mistake OR the keyboard was sticking on a key or repeating another.  It was on a system with the HOME directory encrypted, not the whole drive.  Do you know which you have?

If just HOME directory encryption, you can create another account and either use or do not use encryption. This time, make the passphrase something that you can type on a broken keyboard.  If offered to create a backup decryption key, accept. it.  To do these things, boot off the liveCD, mount the file system where /etc is, modify the passwd file and the sudoers file for the new account you've created, create the /home/new-account directory owned by the same, new, userid - that should be it.

Another thread here [http://ubuntuforums.org/showthread.php?t=2035388](http://ubuntuforums.org/showthread.php?t=2035388) seems to be related. You've probably already seen that.

 
There is no need to scrap the HDD. Worst case,  wipe it and reinstall over it, assuming you don't have the recovery keys - wasn't that the first suggestion - to backup the encryption recovery keys?  Perhaps not. I don't know.

Try plugging in a USB keyboard. This should bypass whatever issue your laptop keyboard is having. 


I've never had any issue logging into my home directory encrypted 12.04 systems - well, except when I was mistyping the password. Then I couldn't get in - and I was pleased.  What good is an encryption system that lets someone in without the correct password?

  
If you plug in a USB keyboard, you can use that instead of the built-in keyboard.  I'm using my laptop that way right now - full-sized keyboard and mouse while it is connected to 2 external monitors.  Anyway - just another option to consider.

  Backups or the other options that I've listed above are it.  If you choose to encrypt, you should also choose to have really excellent backups.


What "coding" are you doing?  Seems like you are just doing end-user stuff.

One of the downsides to encryption is the possibility of complete data loss. A slight performance hit is the other.  When using encryption, having great backups is critical.  [http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t](http://askubuntu.com/questions/37/when-installing-im-given-the-option-of-encrypting-my-home-folder-what-does-t) explains more. More explanation [http://www.linux-mag.com/id/7568/1/](http://www.linux-mag.com/id/7568/1/)

An encryption scheme that can be easily hacked is a terrible idea. That would completely defeat the purpose, right?

Good luck.

Trying other keyboard, just didn't think it would allow me to as it isn't allowing me to do anything else.

When looking for a problem similar to mine, I had saw a website regarding Ubuntu 7.something and he somehow advised on how to fix it. I was assuming this was an old fix for a loop that has since been closed.

I agree that if there was a work round it would defeat the object.

I'm on Ubuntu 12. Well at least I'm trying to be! Haha.

Short of recording myself putting in the keys I'm sure, tried various similar keys just on the off chance that I put something in wrong, all the keys around it has now been tried at some point.

I'm trying to re-run the install disc, now I know I'm doing the usual protocol, I've done it a thousand times.

But I'm getting this warning now:
PXE-E61: Media test failure, Check cable.
PXE-M0F: Exiting Intel PXE-ROM
Boot failure: System Halted

On the dos screen.

Soooo I think the original install created this error, on other forums people have said having partitions started this error for them. However, I didn't partition my Ubuntu, I just did a complete install replacing windows.

This is like the perfect storm of computer mess ups.

Ok I'm trying the keyboard, if that fails I need someone to have a look at this thang.

Also appreciate your advice a great deal. You are the shining light in an otherwise dimly lit world :)

---

### Post by Panwage on 2013-02-24
Think I need new hardware now.

Can't re install because of this:
PXE-E61: Media test failure, Check cable.
PXE-M0F: Exiting Intel PXE-ROM
Boot failure: System Halted

...No resolution as of yet on the forums I'm searching but I know that isn't related to Ubuntu. Whilst my computer may have messed up during the initial install creating this whole problem.

Thanks for your help guys...Maybe this is an excuse to get a tablet, ready for ubuntu.

---

