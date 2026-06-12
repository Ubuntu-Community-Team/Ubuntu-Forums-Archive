---
title: "Problem with '~/.local/share/Trash/expunged'"
date: 2021-02-05
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2021-02-05
Hello all,

So under my home directory I have '../.local/share/Trash/expunged/2798414653/localhost/' below which are more directories, some of which contain files owned by root. I have a feeling that there is some kind of permission problem going on, and it's irritating because if I want to rsync my home directory I'm forced to do it as root because of the presence of these files. I don't know what the significance of the files is or why they are under '../Trash/'.

I did find a brief explanation that said if nautilus tries to delete a directory which you own, but which contains files you don't own, it can have some trouble and these files end up in expunged?

also, is it safe to 'rm' things using sudo? I do this all the time for files owned by root but I just found a thread where a number of people claimed it was dangerous, but I would have thought it's okay as long as you know the file is safe to delete?

I'm a bit confused with this one so any help is appreciated!

---

### Post by #&amp;thj^% on 2021-02-05
I really think those kind of warnings are aimed at NOOBS, and yes it can be a real distructive move in the un-informed hands. (So caution will always be the primary warning)
**_**NO PROMISES**_**, but if your willing give this a shot:
One line at a time.
```
sudo -i
rm -rv /home/<your_username>/.local/share/Trash/expunged/*
exit

```
Replace "<your_username>" with your real user name.
EDIT: Here's what mine shows:
```
cd ~/.local/share/Trash
me on Fri Feb 05 at 11:56 am in ~/.local/share/Trash branch: (HEAD) 
>> du
4	./files
4	./info
12	.

```
With what I see on my end, _not yours but mine_>>>I'm safe to run that command. If you would like to show me yours maybe I can give you a bit more certainty.
And may the force be with you. ;)

---

### Post by TheFu on 2021-02-05
Using sudo is always risky when you don't understand the results. There are often unintended impacts which is why the general rule is not to use sudo to run any GUI programs. 

In theory, all files in a user's HOME should be owned by that userid. If there are root-owned files there, that tells me that someone is using a GUI program with sudo.  Don't do that.

Anyway, Trash is a GUI thing and not necessary. There are multiple implentations, not all are compatible. I don't use Trash. When I remove files, I want them gone.  If I change my mind within 60 days, there are versioned backups that get run nightly.

If there are files in your HOME, feel free to delete them. If you cannot lose them, be certain there are backups first.  Backups have 1001 uses.  ;)

---

### Post by jcdenton1995 on 2021-02-05
> **TheFu said:**
> Using sudo is always risky when you don't understand the results. There are often unintended impacts which is why the general rule is not to use sudo to run any GUI programs. 

In theory, all files in a user's HOME should be owned by that userid. If there are root-owned files there, that tells me that someone is using a GUI program with sudo.  Don't do that.

Aha, honestly I swear I haven't! this is what worried me when I saw that the files under ../expunged/ were owned by root, because I know root will sometimes take ownership of files if used incorrectly.

> Anyway, Trash is a GUI thing and not necessary. There are multiple implentations, not all are compatible. I don't use Trash. When I remove files, I want them gone.  If I change my mind within 60 days, there are versioned backups that get run nightly.

If there are files in your HOME, feel free to delete them. If you cannot lose them, be certain there are backups first.  Backups have 1001 uses.  ;)

good to know, I just went ahead and blitzed the files in question as 1fallen suggested, I have backups and I'm pretty sure none of them were crucial anyway (famous last words), time will tell...

---

### Post by jcdenton1995 on 2021-02-05
> **1fallen said:**
> I really think those kind of warnings are aimed at NOOBS, and yes it can be a real distructive move in the un-informed hands. (So caution will always be the primary warning)

Thanks, I went ahead and removed all the files, I was heavily considering doing this anyway, but I just thought I'd make a post here in case there was some very important Linux gotch ya' that I needed to be aware of. I'll keep monitoring that directory and try and see if I can nail down why / when it is filling up...

---

### Post by ActionParsnip on 2021-02-06
Or use trash-cli using sudo. It's a great command for recycle bin management in CLI

---

