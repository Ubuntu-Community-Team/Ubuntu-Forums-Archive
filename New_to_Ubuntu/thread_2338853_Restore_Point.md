---
title: "Restore Point?"
date: 2016-10-02
forum: New to Ubuntu
---

### Post by Citta on 2016-10-02
In Win you have those points. If something goes wrong, e. g. after installation of a software, you can use of these points. What are you doing with Linux in such cases?
PS: Just found "Systemback"- is this a useful tool?

---

### Post by QLee on 2016-10-02
> **Citta said:**
> In Win you have those points. If something goes wrong, e. g. after installation of a software, you can use of these points. What are you doing with Linux in such cases?

Since you phrased it that way, I personally just keep a backup of /home. If "something goes wrong", I fix it because that is the Linux way. If I can't fix it (rarely), I just reinstall, with modern computers it is pretty fast to reinstall.

I have heard rumours of something like restore points for Ubuntu being worked on and someone who knows about that will likely provide a link to info about that.

Edit: ah, you edited while I was typing. You are on the right track, searching the forums and/or a search engine will let you answer the question for yourself.

---

### Post by Citta on 2016-10-02
Restoring does mean you have exactly the same OS as before, without that foul software, of course. Because you will use the 2nd newest point. You will not fritter time and temper away with installing all software and your adjustments again, everything you did after the installation of the OS. If I understand your post correctly you are just backing up your personal data. This is not restoring, therefore in Win it is called "Backup and Restore". So what to do?
No, the search engine alone will not do it, everybody can write everything, right or wrong. Therefore my quest posted here, hoping to read posts from writers who solved above mentioned mishap in real life, no hearsay, etc..

---

### Post by ajgreeny on 2016-10-02
Therefore you probably need to consider cloning your OS partition using something like clonezilla, which will give you an installable image of the partition or disk you ask it to.

I am like QLee and just backup my /home files as they are the irreplaceable parts of my system; the OS itself can be reinstalled in about 30 mins.  
You may also like to backup /etc where some of your configurations are, but the majority of them are in your /home so if that's backed up you will already have them.  
It is also probably a good idea to keep a copy of any system files that you manually edit into a folder in your /home so that you can either replace the new files that you get after reinstalling, or can re-edit the new ones.

---

### Post by oldos2er on 2016-10-02
There's nothing like that in Ubuntu or Linux in general that I'm aware of, that's why most users understand that it's incumbent on them to maintain backups of any sensitive data. There are many possible backup solutions, from full disk imaging down to backing up single files or folders.

Just a friendly suggestion, posting with a chip on your shoulder will not help generate useful answers to your questions. Please remember *The purpose of the Ubuntu Forums is to provide support for Ubuntu. We  also want this to be a place where community can develop and we can  enjoy one another's company. To achieve this, we strive to maintain an  atmosphere that can be enjoyed by all and we ask all members of the  community to be respectful at all times. This means please use etiquette  and politeness. Treat people with respect.*

---

### Post by QLee on 2016-10-02
> **Citta said:**
> Restoring does mean you have exactly the same OS as before, without that foul software, of course. Because you will use the 2nd newest point. You will not fritter time and temper away with installing all software and your adjustments again, everything you did after the installation of the OS. If I understand your post correctly you are just backing up your personal data. This is not restoring, therefore in Win it is called "Backup and Restore". So what to do?
No, the search engine alone will not do it, everybody can write everything, right or wrong. Therefore my quest posted here, hoping to read posts from writers who solved above mentioned mishap in real life, no hearsay, etc..

Your post asked what do "you" do. That's why I answered as I did. It works for me because I understand Linux and that Linux is not Windows. I fritter no time or temper, just use the knowledge I have gained over the years.

I also suggested searching the forums, I imagine here in the forums is where I saw the "rumour" I mentioned. I don't have the location bookmarked so I can't provide you with a link. You could try the backup program that comes with Ubuntu and/or clonezilla if the method I use seems too difficult for you.

As I mentioned, someone will probably see your thread that has more info on what you want if you just wait patiently for a while.

Good Luck!

---

### Post by mastablasta on 2016-10-03
this is the thread discussing system back: [https://ubuntuforums.org/showthread.php?t=2332381](https://ubuntuforums.org/showthread.php?t=2332381)

there are several options of doing propper backups including delta backups and such. some can work as system backup.

there is a system recovery option. 

there is nothing in the system as restore points. restore point are not without issues themselves (see thread & discussion in link above).

---

### Post by kryten35 on 2016-10-03
Timeshift is similar to windows restore ponts.Theres a ppa for it.
[URL="http://www.teejeetech.in/p/timeshift.html"]
[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html) [/URL]

I prefer to use both Clonezilla/Timeshift for greater flexibility.

---

### Post by bearlake on 2016-10-03
I like to keep my /home directory on its own partition as it's easy to change from one version of Ubuntu to a newer without loosing any data.

You only need to backup /home.

Luckybackup works great for backing up your data, just takes a min or two and it's in the repo's.

---

### Post by Mark Phelps on 2016-10-04
First, let's make sure we're all talking about the same thing.

Windows System Restore does NOT restore the "entire system", as in a time machine; instead, what it does is restore the "operating system".  When Windows Update runs, it creates a restore point.  ALL that is, is a copy of the system files that are being replaced or updated.  When you do a System Restore, ALL that does is overwrite the current system files, including the Registry "hives" with the saved copies.

So, for example, if you accidentally deleted a data file in Windows today, and then did a System Restore to last week, that file would NOT be back.

Second, I prefer to restore the "entire system", not just pieces of it -- which is why I prefer using stuff like Clonezilla. Also, doing backups and restores this way allows you to mess around with system files and settings and then not be concerned with which stuff you backed up, since a "restore" will simply overwrite everything.

---

### Post by mastablasta on 2016-10-05
> **Mark Phelps said:**
> 
So, for example, if you accidentally deleted a data file in Windows today, and then did a System Restore to last week, that file would NOT be back.
.
for that there is undelete (restore from recycle bin). 3rd party tools provide restore function even if undelete was evoked too late.

still i think the OP wanted something that would only restore the system. which is not a bad idea. say you have OS on one disk and data elsewhere... you mess up the install or an update, you need to restore all data and programmes and reconfigure... while in this case oyu owuld just restore the system to previous state and mess it up again.

---

### Post by monkeybrain20122 on 2016-10-05
> **bearlake said:**
> I like to keep my /home directory on its own partition as it's easy to change from one version of Ubuntu to a newer without loosing any data.

You only need to backup /home.

Luckybackup works great for backing up your data, just takes a min or two and it's in the repo's.

Well backing up home only back up your data. You can't restore the system if some updates goes wrong. I would make a clone of the / partition regularly (I use Fsarchiver) and a /home without data (need to do only once) and then backup data as separately. Fsarchiver is the repo and a lot more flexible than clonzella. [https://www.fsarchiver.org/QuickStart#Execution_environment](https://www.fsarchiver.org/QuickStart#Execution_environment)

---

