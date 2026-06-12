---
title: "Evolution removed Thunderbird added into Ubuntu-meta"
date: 2011-07-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-01
So now the default email-client is Thunderbird.
Evolution was finally removed from the desktop recommends.

> ubuntu-meta (1.232) oneiric; urgency=low

  * Refreshed dependencies
  * Added thunderbird to desktop-recommends
  * Added thunderbird-gnome-support to desktop-recommends
  * Removed evolution from desktop-recommends
  * Removed evolution-exchange from desktop-recommends
  * Removed evolution-indicator from desktop-recommends
  * Removed evolution-plugins from desktop-recommends
  * Removed evolution-webcal from desktop-recommends

---

### Post by Quackers on 2011-07-01
Hmm, in my new install of yesterday, I can't even set up evolution mail. It just fails at the second screen for me. I'm using Thunderbird instead anyway, because of that.

---

### Post by cgroza on 2011-07-01
I like Thunderbird more anyways.

---

### Post by fjgaude on 2011-07-01
I've always used Thunderbird... <smile>

---

### Post by coffeecat on 2011-07-01
Just a FYI for those using Thunderbird. Evolution and Claws, another email client I tried recently, can both export mbox files. Thunderbird can't, which is a fairly bad omission imho. At least not out of the box. If you want this functionality, you can install ImportExportTools:

[http://www.nic-nac-project.de/~kaosmos/mboximport-en.html](http://www.nic-nac-project.de/~kaosmos/mboximport-en.html)

A little more about this here:

[http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)

What I find disappointing is that this addon is not available through tools > Add-ons. You'd think it would be.

---

### Post by fjgaude on 2011-07-01
Well, TBird is labeled as 5.0... that's a big jump from 3.x which likely means that by the time 11.10 is released we will see lots of good things added.

---

### Post by bennachie on 2011-07-02
I'm pleased to report that, in the final version of Thunderbird 5.0, just released, ImportExportTools IS now available through the Add-Ons GUI. I'd certainly agree that its functions should have been integrated into Thunderbird long ago.

---

### Post by coffeecat on 2011-07-02
> **bennachie said:**
> I'm pleased to report that, in the final version of Thunderbird 5.0, just released, ImportExportTools IS now available through the Add-Ons GUI. I'd certainly agree that its functions should have been integrated into Thunderbird long ago.

Thanks for that. Good news.

---

### Post by kuvanito on 2011-07-02
me 2
thanks for the change :D

---

### Post by Hairy_Palms on 2011-07-02
this has come up like every cycle since thunderbird 2 came out, though im surprised they finally did it in a cycle which is switching to gtk3, and they go and change a gtk3 default app for a xul/gtk2 default app.

---

### Post by lucazade on 2011-07-02
> **Hairy_Palms said:**
> this has come up like every cycle since thunderbird 2 came out, though im surprised they finally did it in a cycle which is switching to gtk3, and they go and change a gtk3 default app for a xul/gtk2 default app.

this is a good point, i'm wondering as well.

---

### Post by Mr. Picklesworth on 2011-07-02
> **Hairy_Palms said:**
> this has come up like every cycle since thunderbird 2 came out, though im surprised they finally did it in a cycle which is switching to gtk3, and they go and change a gtk3 default app for a xul/gtk2 default app.

A gtk3 app that is *finally* gaining momentum towards a serious visual tune-up :|

I would have much preferred a &#8220;let's wait and see what happens this cycle&#8221; approach.
(Though, to be fair, I guess it has had quite a few cycles for that).

---

### Post by shuttleworthwannabe on 2011-07-02
May I ask--why would one still want to use a Client, when these days, everything can be done via web interface, like Gmail, etc? In this way no need to back-up, mbox issues, pop3 other accounts in one place, etc; so when mobile, it is there as well. I have debated this a while now, and I still have not found a reason for using Email Client that has local applicability only; I know Gmail is coming with offline functionality soon-then this debate may rest forever. I am being overly critical?.

---

### Post by cariboo on 2011-07-02
There are many of us who prefer to store our mail locally. Backing up on Linux is painless, as you don't have to sit there and watch its progress. Linux distros are multitasking, so you can do something else while the process is running.

---

### Post by kuvanito on 2011-07-02
a mail client is needed when clicking on hyper links emails addresses to send an email,try that with any browser?

---

### Post by silex89 on 2011-07-02
Nice! :D, right now I'm using Evolution to read my mail...but the only reason for that is the desktop integration with Natty. Finally we'll have Thunderbird out of the box and hopefully with desktop integration to Unity wohoooo! :)

---

### Post by nrundy on 2011-07-02
> **Harry33 said:**
> So now the default email-client is Thunderbird.
Evolution was finally removed from the desktop recommends.

YES!

Really hoping thunderbird is made default in Oneiric :popcorn:

---

### Post by lisati on 2011-07-02
> **shuttleworthwannabe said:**
> May I ask--why would one still want to use a Client, when these days, everything can be done via web interface, like Gmail, etc? In this way no need to back-up, mbox issues, pop3 other accounts in one place, etc; so when mobile, it is there as well. I have debated this a while now, and I still have not found a reason for using Email Client that has local applicability only; I know Gmail is coming with offline functionality soon-then this debate may rest forever. I am being overly critical?.

Back in the day, when I started using email many years ago, I had no choice, and HAD to use webmail on a borrowed connection. These days I find the ability to check all my email accounts in one go with a client far easier.

---

### Post by shuttleworthwannabe on 2011-07-02
> **lisati said:**
> Back in the day, when I started using email many years ago, I had no choice, and HAD to use webmail on a borrowed connection. These days I find the ability to check all my email accounts in one go with a client far easier.

That is true--but in Gmail for example, I can cosolidate all my email accounts (pop3 included) and keep on web. As I said, Gmail will introduce an offline function soon, hence I asked.

---

### Post by cariboo on 2011-07-02
I have 10 email accounts from several different providers web mail just is to much of a hassle for me. I've used Thunderbird since it was called Minotaur, so there's no sense in changing now.

---

### Post by benjamimgois on 2011-07-03
> **shuttleworthwannabe said:**
> May I ask--why would one still want to use a Client, when these days, everything can be done via web interface, like Gmail, etc? In this way no need to back-up, mbox issues, pop3 other accounts in one place, etc; so when mobile, it is there as well. I have debated this a while now, and I still have not found a reason for using Email Client that has local applicability only; I know Gmail is coming with offline functionality soon-then this debate may rest forever. I am being overly critical?.

+1. I agree completely.

---

### Post by lonniehenry on 2011-07-03
I find a web interface email to be clunky and not as managable as a client.  I have used Thunderbird since I switched to Linux years ago.  Having my email on my machine makes sense to me.  I never liked evolution even though I use outlook at work - just seems to be too much extra for my home email.

---

### Post by shuttleworthwannabe on 2011-07-03
I guess only time will tell.

---

### Post by johnnybelfast on 2011-07-04
Thunderbird has always been suitable for the home user, but many small, medium and large businesses use Exchange Server on their corporate networks. Can Thunderbird handle Exchange yet (properly)?

---

### Post by MadMan2k on 2011-07-04
> **johnnybelfast said:**
> Thunderbird has always been suitable for the home user, but many small, medium and large businesses use Exchange Server on their corporate networks. Can Thunderbird handle Exchange yet (properly)?
again, whilst Exchange support may be important in a corporate environment, I don't think this is particularly important to most users we are targetting. This seemed to be the consensus amongst the people who attended the session at the last UDS too.

(from: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-default-email-client))

---

### Post by johnnybelfast on 2011-07-04
> - Exchange support (no idea how well this works, but it exists)That doesn't convince me that they did much corporate research ahead of this decision. Not a problem though, I'm assuming Evolution will be in the repositories and there will be a blueprint for Exchange support to be added within Thunderbird. From the rest of the article it looks like they were mainly looking to save space on the disk and have a prettier UI which is understandable.

Most people working in professional environments do need an exchange client for their job though. I'm not sure who the author of that article thinks Ubuntu is 'targetting' but ideally it should be targetting both home users and corporate users, not just one or the other. Certainly I've been introducing Ubuntu on various computers in this company, but bad support for email and global address booking are the main turnoffs slowing that migration down. I would be embarassed to ask someone to use Evolution, and Thunderbird is a pain to set up as an exchange client. Other than that Ubuntu is nearly ready for the average office worker.

---

### Post by sartic on 2011-07-04
Hip hip hooray :)

---

### Post by DogMatix on 2011-07-04
I'm pleased with this news. I recently started using Thunderbird on Mac OS X because of SMTP issues I was having with Mac Mail. I had been considering replacing Evolution on my Ubuntu netbook and desktop for cross platform conformity and now the decision has been made for me.

---

### Post by tlcstat on 2011-07-04
Greetings,
I'll stick with Claws Email and delete the rest. I have free web mail on my domain provider and I keep my mail on it for a period for travel or computer problems.  Also, I don't have much use for software that won't both import and export. I don't like being "stuck". 
tlcstat

---

### Post by EgoGratis on 2011-07-05
I use both Evolution and Thunderbird. Evolution for some "sync stuff" and Thunderbird for mail.

---

### Post by jbicha on 2011-07-05
Honestly, the Ubuntu install CD should not be targeting businesses. An enterprise should have their install customized for their needs and security setup.

One huge example to prove my point is that Ubuntu by default allows any user to read any other user's home directory. This is obviously bad for a lot of non-home environments.

Services that are not being used (like Remote Desktop or Bluetooth) should be uninstalled in this custom install too.

There is a huge opening for someone to make a more locked-down Ubuntu variant as I believe there is significant demand for this.

---

### Post by seeker5528 on 2011-07-06
> **tlcstat said:**
> Also, I don't have much use for software that won't both import and export. I don't like being "stuck". 
tlcstat

On the one hand, it seems odd that export isn't there, on the other hand....

Thunderbird keeps it's mail in a standardized [mbox](http://en.wikipedia.org/wiki/Mbox) format, so you can just copy and import the whole mail directory as is, apparently there are a few variations of this and different programs handle the import better than others, but usually I would expect the programs that offer an mbox import to do a fair job, at least to get all the folders and messages if not status and other extra information.

Apparently there is an [extension for that](http://www.nic-nac-project.org/~kaosmos/mboximport-en.html).

Having said that, I use Claws myself.

Later, Seeker

---

### Post by kvv_1986 on 2011-07-06
> **jbicha said:**
> One huge example to prove my point is that Ubuntu by default allows any user to read any other user's home directory. This is obviously bad for a lot of non-home environments.


I hate this. Is there anyway to disable this?

---

### Post by cariboo on 2011-07-06
> **kvv_1986 said:**
> I hate this. Is there anyway to disable this?

You don't disable it, you set the permissions so that only you and root can read the files:

```
sudo chmod -R 750  /home/$USER
```

where $USER=your user name.

To test, log in as another user, and try to access the files in your home directory.

---

### Post by seeker5528 on 2011-07-06
> **cariboo907 said:**
> You don't disable it, you set the permissions so that only you and root can read the files:

```
sudo chmod -R 750  /home/$USER
```

where $USER=your user name.

To test, log in as another user, and try to access the files in your home directory.

You shouldn't have to do it recursively, if other users don't have read/execute permissions on your home directory they can't access the contents either.

If you want the directories private 700 would be the mode and you don't need sudo to change the mode of a directory you own, so all you need is...

```
chmod 700 /home/$USER
```

Of course you could always open nautilus browse to '/home', right click the directory with your user name and select properties, go to the permissions tab, then change the access for group and other to none and optionally click the 'Apply Permissions to Enclosed Files' box.

If users-admin uses useradd to do the work (which I suspect it does) editing '/etc/useradd.conf' so the 'DIR_MODE=0755' reads 'DIR_MODE=0700' should make it so newly created users have their directories set private.

Later, Seeker

---

### Post by coffeecat on 2011-07-06
> **seeker5528 said:**
> Apparently there is an [extension for that](http://www.nic-nac-project.org/~kaosmos/mboximport-en.html).

There is indeed. As discussed in posts #5, #7 and #8 of this very thread. :wink:

---

### Post by seeker5528 on 2011-07-06
> **coffeecat said:**
> There is indeed. As discussed in posts #5, #7 and #8 of this very thread. :wink:

Oops, missed that.

My mbox export/import is usually just to copy the entire mail directory somewhere else to export, copy the mbox files from somewhere else to the current Thunderbird 'Mail/Local Folders' directory renaming to avoid conflicts if necessary to import.  

If I am importing from an old Thunderbird mail directory to a new one that has not been used yet, then I just copy the old 'Mail/*' to the new 'Mail' directory overwriting the existing files.

Later, Seeker

---

### Post by saphil on 2011-07-06
This is good news.  I have users on other platforms who are more used to thunderbird, who can be eased into Ocelot easier.

Wolf

---

### Post by moore.bryan on 2011-07-18
I agree with all the comments alluding to Evolution being bloatware, but some of us needed it, mainly for the evolution-exchange plugin. 

Now, with IMAP+ and MAPI, a lot of things should become easier for us in the minority of email client users... but only if our businesses move the mail servers to IMAP/MAPI configurations. Mine *just* did and on my Fedora 15 install I can use Evolution with IMAP+ to log-in to my work email server; however, Thunderbird on Oneiric will not permit me to do anything. Basically, it just always complains about not being able to discover settings even though I set them manually and *know* they are correct and work.

Any ideas?

---

