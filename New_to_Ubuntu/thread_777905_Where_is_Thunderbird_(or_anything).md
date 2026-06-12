---
title: "Where is Thunderbird (or anything)?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Kymeia on 2008-05-01
I hate this file system. On Windows it's easy to find stuff but in Linux everything is in obscure places. All I want to do is I just installed thunderbird and I want to use it to open my backed up Thunderbird mail folder but I don't know where to look for the mail folder position.

---

### Post by xjb2003x on 2008-05-01
If you just did a default install, try looking in applications - internet

---

### Post by Kymeia on 2008-05-01
No I need to find out where it is (ie the programme) not the shortcut to it

---

### Post by SunnyRabbiera on 2008-05-01
actually once you learn it the linux filesystem makes more sense then the windows filesystem.
your thunderbird profiles are located in your home directory, its hidden so you will have to unhide it by pressing ctrl-h, or going up to "view" and select "show hidden files"

as for the application itself, its in /usr/lib/thunderbird.
Most applications are installed in usr/bin or usr/lib

---

### Post by heartburnkid on 2008-05-01
Your mail directory is in your home directory. Go to the Places menu, and pick Home Directory from the list, then right click in the folder window and select "show hidden files and folders" (I think that's the verbiage, not at my machine right now).  You should see a .mozilla-thunderbird directory appear.  That is where your profile is; your mail folder will be in there.

---

### Post by audwan on 2008-05-01
You should find Thunderbird in the menu under Internet.

If you're looking for the executable, it is under /usr/bin/thunderbird.

```
$ which thunderbird
/usr/bin/thunderbird
```

---

### Post by spiderbatdad on 2008-05-01
The folder is in your home directory...hidden:  .mozilla-thunderbird.
Filenames that begin with a dot are hidden.
Open your home folder, click view...show hidden files...scroll down to .mozilla-thunderbird.

---

### Post by SunnyRabbiera on 2008-05-01
> **audwan said:**
> You should find Thunderbird in the menu under Internet.

If you're looking for the executable, it is under /usr/bin/thunderbird.

```
$ which thunderbird
/usr/bin/thunderbird
```

not in all cases, for me its in usr/lib

---

### Post by conehead77 on 2008-05-01
When you look at your home folder with Nautilus, press ctrl+h and hidden files will show up.
Then take a look at the .mozilla-thunderbird folder. Let me know if this is what you are looking for.

---

### Post by jakupl on 2008-05-01
this stuff is mostly in your home folder... go there, press Ctrl+H to see hidden files and folders.

but this is not the actual program... not really sure where that is, because I never needed it.
Why would you need that?

the thunderbird launcher just says a command called "thunderbird"

For instace, if you open up the terminal and enter "thunderbird", it will open.

---

### Post by Bruce M. on 2008-05-01
> **Kymeia said:**
> I hate this file system. On Windows it's easy to find stuff but in Linux everything is in obscure places. All I want to do is I just installed thunderbird and I want to use it to open my backed up Thunderbird mail folder but I don't know where to look for the mail folder position.

You'll get used to the file system soon enough. If you recall your first few days with Windows, you didn't know where things were either.

Linux is not Windows and with a small learning curve you'll learn more about the file system.

Go slow and don't panic, if you have a "backed up" version of your Thunderbird mail there is a very good chance you will NOT loose a single email.

Before anything else where is your "backed up" Thunderbird mail folder that you have? 

And is it a backup from a Windows version of Thunderbird?

Like I said - go slow and we can do this, please answer the two queations.

Bruce

---

### Post by Kymeia on 2008-05-02
Thanks all - unhiding folders did the trick but I still think folders names and the sheer number of folders with the same name like "lib" or "bin" is unintuitive compared to say "Programme Files" "Windows" and "My documents" (although Vista has complicated things enormously by putting so much in hidden places which is one reason I still use XP). 

I had an old Thunderbird folder with some important mails I didn't want to use (from Windows) - once I found the position of the Inbox folder in USR I just copied the backed up folder to the same location and it worked. Wish there was an easier way to back up and import old mail folders though - should be a function built into Thunderbird really.

---

### Post by Canis familiaris on 2008-05-02
> **Kymeia said:**
> Thanks all - unhiding folders did the trick but I still think folders names and the sheer number of folders with the same name like "lib" or "bin" is unintuitive compared to say "Programme Files" "Windows" and "My documents" (although Vista has complicated things enormously by putting so much in hidden places which is one reason I still use XP). 

I had an old Thunderbird folder with some important mails I didn't want to use (from Windows) - once I found the position of the Inbox folder in USR I just copied the backed up folder to the same location and it worked. Wish there was an easier way to back up and import old mail folders though - should be a function built into Thunderbird really.

Well actually the Linux way is better since more often than not libraries are shared between applications and thus should ideally be kept separately.

---

### Post by muteXe on 2008-05-02
Would you say that the windows file structure is intuitive, or that it's just been ingrained in your mindset from a very early age..?

---

