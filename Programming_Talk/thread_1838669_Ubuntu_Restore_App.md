---
title: "Ubuntu Restore App"
date: 2011-09-04
forum: Programming Talk
---

### Post by Jonny87 on 2011-09-04
I've been working on an application to allow Ubuntu to have a restore ability. It was kind of inspired by the Windows restore points. I realize that there is probably other apps that will achieve this, but I felt like doing my own. The idea was to create an app that could restore the Ubuntu OS to a the way it was at a previous date, with out having to boot to a Live CD.

I am far from a skilled programmer and my knowledge of BASH is patchy so I thought I'd upload it here for the rest of the community to fix, modify, and improve. I have tested it within a Virtual Machine, and it does seem to work as is, but still needs further testing.

All I ask to those that make changes is that they let me know what they did and why so that I may learn from it. Also that they their modified versions here for all use.

As mentioned I'm not programmer so please be kind.

### How To ###
--> Download the linked archive.
--> Extract the archive.
--> Inside the folder that is extracted is a SetUp script.
--> Run the SetUp script (this should work by double clicking it a clicking "Run").
--> This will install the app into the OS (Note! I have not created an uninstall script yet).
--> There should then be an option in your menu that will run it. If not then in the backup directory in your chosen location, should be a "Run.sh". This will run it as well.

### Warning ###
While I have tested this in a VM and confident that it is safe to use, I do not recommend using it on an actual setup just yet until others have tested it and worked on it. It is still far from perfect and as it is at the moment, should be kept to a VM.
I take no responsibility for damage or loss of data that is incurred as a result of this app. 

### Download ###
I wasn't able to upload it to the Ubuntu Forums but it should be downloadable from here;
[http://ubuntuone.com/42jEP59uAZ8Vajkl9jb25O](http://ubuntuone.com/42jEP59uAZ8Vajkl9jb25O)

---

### Post by Bodsda on 2011-09-05
> **Jonny87 said:**
> ### Download ###
I wasn't able to upload it to the Ubuntu Forums but it should be downloadable from here;
[http://ubuntuone.com/42jEP59uAZ8Vajkl9jb25O](http://ubuntuone.com/42jEP59uAZ8Vajkl9jb25O)
 
404 Not Found

---

### Post by Jonny87 on 2011-09-05
> **Bodsda said:**
> 404 Not Found

It seemed to disappear some how??? I've re-uploaded it.

Try this;
[http://ubuntuone.com/5ENZEoUHS2XVnmGZuEp9Dj](http://ubuntuone.com/5ENZEoUHS2XVnmGZuEp9Dj)

---

### Post by juancarlospaco on 2011-09-05
btrfs ?

---

### Post by Jonny87 on 2011-09-05
> **juancarlospaco said:**
> btrfs ?

btrfs ???

---

### Post by juancarlospaco on 2011-09-05
> **Jonny87 said:**
> btrfs ???

[btfrs !]("http://en.wikipedia.org/wiki/Btrfs")

---

### Post by Jonny87 on 2011-09-05
> **juancarlospaco said:**
> [btfrs !]("http://en.wikipedia.org/wiki/Btrfs")

Thanks, So if I'm correct in understand that page, btfs is an alternative File System to ext4 (which by the sound of it will one day replace ext4) that automatically has this ability in it?

---

### Post by juancarlospaco on 2011-09-05
Not one day, Today, look into Ubuntu filesystem step on Install, select btrfs, done.

---

### Post by blackmail on 2011-09-05
Well as i have seen it still needs a lot of work, and if there would be a program that would make use of idle time and make snaphots of a system. I think that would be very good. This would mean that the program would require a root privilege and also to monitor settings made by users on system critical apps...

---

### Post by Jonny87 on 2011-09-06
> **juancarlospaco said:**
> Not one day, Today, look into Ubuntu filesystem step on Install, select btrfs, done.

While it looks very appealing from the info I read and seen, its apparently not quite ready for production machines, is this still the case? Also there doesn't appear to be any GUI interface for it, that was the intention for my app, to create an easy to use app.

---

### Post by juancarlospaco on 2011-09-06
> **Jonny87 said:**
> doesn't appear to be any GUI interface for it

that was the intention for my app, to create an easy to use app.

You are replying yourself, there you go..., 
make a GUI you already have the backends...

---

### Post by Jonny87 on 2011-09-06
> **juancarlospaco said:**
> You are replying yourself, there you go..., 
make a GUI you already have the backends...

I would honestly love to. However as I mentioned in my original post I'm far from a programmer/developer and my knowledge is patchy. I'd give it ago but wouldn't know where to start.

---

### Post by Bodsda on 2011-09-06
> **Jonny87 said:**
> I would honestly love to. However as I mentioned in my original post I'm far from a programmer/developer and my knowledge is patchy. I'd give it ago but wouldn't know where to start.
 
I would suggest starting at the beginning. It could be teribly difficult if you were to start at the end. 
 
Pick a language, pick a GUI toolkit, grab some decent coffee and start learning :)
 
[Python]("http://www.python.org/") - [Docs]("http://docs.python.org/")
[PyGTK]("http://www.pygtk.org/") - [Tutorial]("http://learngtk.org/pygtk-tutorial/")
[Coffee]("http://www.britishcoffeeassociation.org/types-of-coffee")

---

### Post by Jonny87 on 2011-09-06
> **Bodsda said:**
> I would suggest starting at the beginning. It could be teribly difficult if you were to start at the end. 
 
Pick a language, pick a GUI toolkit, grab some decent coffee and start learning :)
 
[Python]("http://www.python.org/") - [Docs]("http://docs.python.org/")
[PyGTK]("http://www.pygtk.org/") - [Tutorial]("http://learngtk.org/pygtk-tutorial/")
[Coffee]("http://www.britishcoffeeassociation.org/types-of-coffee")

Well perhaps that would be a little project for me to work on. Though I did see a video on btrfs where they were talking about the possibilities of GUIs some time down the track, one of which was a possible slide bar for roll backs where you slide the bar back to the point you want to roll back to. 

Thanks for the links (especially the coffee one, you must know me or something).

The btrfs does sound like a neat thing, but how far is it from being classed fully ready for use, or is already?

---

### Post by juancarlospaco on 2011-09-06
> **Jonny87 said:**
> they were talking about the possibilities of GUIs some time down the track, one of which was a possible slide bar for roll backs where you slide the bar back to the point you want to roll back to. 


Go here: [http://sourceforge.net/projects/pythondialog/](http://sourceforge.net/projects/pythondialog/)
Easy, and work on servers too...

---

