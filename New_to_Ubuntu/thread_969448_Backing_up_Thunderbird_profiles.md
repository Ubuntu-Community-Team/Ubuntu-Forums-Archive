---
title: "Backing up Thunderbird profiles"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-11-03
Hello Everybody,

I need to back up all my family's e-mails. I read on the Mozilla support site how to back up and restore profiles; I did it and it works, but it only backs up my e-mails. My families accounts do not appear to be backed up. 

Can anybody point me in the right direction please?

Many thanks,

Charlie

---

### Post by cariboo on 2008-11-03
All the users thunderbird profiles are in their respective home directories so they would have to be backed up individually.

I've been  looking for solutions to this problem, but so far I haven't been able to come up with anything solid.

Jim

---

### Post by Charlie Chick on 2008-11-04
Thanks, Jim. Unfortunately all of us use the same profile for Ubuntu but have multiple e-mail addresses showing in Thunderbird. I was hoping to be able to back everybody's e-mails up.

---

### Post by PierreDeKat on 2008-11-04
I don't use Thunderbird, but I'm about 95 percent sure that it stores everything in a folder called .mozilla in your home directory.

In Nautilus, browse to your home directory, up at the top, go to "View" and put a checkmark next to "Show Hidden Files", and you will see your .mozilla folder. Just copy that whole thing and paste it someplace safe.

Not only will your email be backed up, but so will your preferences and plugins for Thunderbird, Firefox, Seamonkey, Iceape and any other branch of a Mozilla-based application.

Note: the .mozilla folder will probably become invisible to Nautilus wherever you paste it, so you will have to do the "Show Hidden Files" thing when you need to see it in order to restore it.

At that time, you can either restore the whole .mozilla folder, or you can snoop through it until you find one particular account -- probably called "Mail" in that particular user's folder -- and just restore that single mail account.

---

### Post by 73ckn797 on 2008-11-04
> **Charlie Chick said:**
> Hello Everybody,

I need to back up all my family's e-mails. I read on the Mozilla support site how to back up and restore profiles; I did it and it works, but it only backs up my e-mails. My families accounts do not appear to be backed up. 

Can anybody point me in the right direction please?

Many thanks,

Charlie

Try this from an earlier thread. This how I have been doing it:
[http://ubuntuforums.org/showthread.p...72#post5764972]("http://ubuntuforums.org/showthread.php?p=5764972#post5764972") or here it is:

There is another solution in that thread but I have not tried that one.

                                  **Re: Thunderbird Mail Transfer**             
                                                             
In Windows go to "My Computer", "Documents and Settings", "(Your Name)", "Application Data", "Thunderbird", "Profiles", "(code looking name).default", "Mail". Once in there you need to copy all of the directories. They contain all of your email data. Copy that over and into the following in Ubuntu:

[COLOR=Purple]*(You will first have to re-enter basic email addresses and pop & smtp info into the new T'Bird installation. That will create the Mail folder. Paste over that with the "Mail" directory data copied from your previous installation whether in Windows or Ubuntu/Linux. I just copy the entire "Mail" directory to include all of the sub-directories.)*[/COLOR]

Click on "Places" and choose "Home Folder".

Click on "View" and choose "show Hidden Files".

Go to the folder titled ".mozilla-thunderbird".

Go to the sub-folder titled "*.default". The * will be an unusual code looking name. this is where the personal data for Thunderbird resides.

The "Mail" folder is the one you want.

Paste the copied files into there.

You may have to first setup your email info in Thunderbird in Ubuntu (or any other OS). Paste what was copied from Windows and let it overwrite the same named directories.

This works great as I do it a lot.

The email address book will need to be exported from the Windows Thunderbird. Do that in a "comma separated value (csv) format, naming it whatever you wish but keep the csv extension. 

Import that file back into the Thunderbird on Ubuntu.

Presto, you are back up and running again.

---

### Post by pannerrammer on 2008-11-04
If each family member has their own login (phil, mary)... then this might help

First create suitable backup folders
```

sudo mkdir /backup
sudo mkdir /backup/phil
sudo mkdir /backup/mary

```Then copy everything for each person
```

sudo cp -R /home/phil/.mozilla-thunderbird /backup/phil 
sudo cp -R /home/mary/.mozilla-thunderbird /backup/mary

```The -R copies all sub-folders. 
The .mozilla-thunderbird folder contains a person's emails/inboxes/deleted-items and settings/passwords/message-filters - basically everything!

Remember that the dot folders are hidden, so it'll look like there's nothing in the /backup/phil folder until you press ctrl+h

---

### Post by Charlie Chick on 2008-11-05
Thank you all for your replies. I'll have another go at the weekend.

Charlie.

---

