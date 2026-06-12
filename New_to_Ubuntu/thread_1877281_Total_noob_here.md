---
title: "Total noob here"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by Daudek on 2011-11-07
[FONT=Arial Black]Hi all, I am completely new to Ubun[/FONT]tu. I am running 11.04. I am completely confused as to how it operates under the hood, how to go about installing files without going through the Software Center, and just how to use Ubuntu really. Could anyone direct me to a good website for learning Ubuntu. I am looking for something that shows how things work under the hood as well as getting me associated with Ubuntu. 

I have been to a lot of websites with how-to's but am not really sure where to start. 

Thank you to who ever responds!
Grace
Daudek

---

### Post by Paqman on 2011-11-07
> **Daudek said:**
> how to go about installing files without going through the Software Center

Generally Software Centre will contain almost everything you would need to install, but you can add external sources. Common ones include [Medibuntu]("http://medibuntu.org/") and the [Google repositories]("http://www.google.com/linuxrepositories/"). As well as this there are Personal Package Archives ([PPAs]("https://launchpad.net/ubuntu/+ppas")). PPAs are useful for getting packages which are very new or under active development.

After adding external sources like these the packages they contain will become available in Software Centre.

If however what you want to do is avoid Software Centre altogether you can install Synaptic, or install all your packages using the command line. To install a package:
```
sudo apt-get install packagename
```

---

### Post by bluexrider on 2011-11-07
Use the link at the bottom of this post

---

### Post by papibe on 2011-11-07
Hi Daudek. Welcome to the forums!

I would recommend to  challenge yourself with "real" projects (or a learning projects if you will). For example:
[LIST]
[*]Share files with Windows machines.
[*]Enable remote access to your computer
[*]Stream media to a game console.
[*]Share your printer with other machines.
[*]Setup remote access to your files from the Internet.
[*]etc.
[/LIST]
Another approach would be to learn how to do things you do before (in Windows or Mac?):
[LIST]
[*]Setup your IM accounts in Empathy (or Pidgin).
[*]Setup all your email accounts in Thunderbird.
[*]Install and test Skype.
[*]Use LibreOffice to create and modify some files.
[*]Use Openshot to create  presentation and movies (like iMove or Windows Movie Maker).
[*]Rip CDs to mp3s (or flac, or ogg, etc).
[*]etc.
[/LIST]
Just some thoughts,
Regards.

---

### Post by Daudek on 2011-11-07
Thank you for the advice! But what I ment by installing items is that there are some sites that save a file, per say a theme or a plug in to a web browser, that have no prompt as to what do do next when they are downloaded, what are those and how would I get them to work / install? Also, do you recomend any articles / websites on getting acquainted with ubuntu or getting my hands dirty in it, so to say?

Thanks!
Grace 
Daudek

---

### Post by JayKay3OOO on 2011-11-07
If you download a .deb (this is what Ubuntu uses instead of .exe) file and you can't work out how to load it in the software centre you can just type an install command into the terminal application.

```
sudo dpkg -i filname.deb
```

or ```
sudo aptitude install filename.deb
```

To get really hands on you should try getting arch linux up and running using their comprehensive documentation.

You might want to be a bit more specific so we don't keep firing random suggestions at you.

Hope you enjoy using Ubuntu though.

---

### Post by Paqman on 2011-11-07
Er, simplest thing to do with a .deb is just double click on it. The system knows what to do with 'em.

---

### Post by Miljet on 2011-11-07
Perhaps you are looking for something like this?

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://mostlylinux.wordpress.com/](http://mostlylinux.wordpress.com/)

[http://members.iinet.net/%7Eherman546/index.html](http://members.iinet.net/%7Eherman546/index.html)

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Added: Any themes or plugins that you download should be automatically added to your browser. They can be managed from the tools menu of the browser itself.

---

### Post by duke.tim on 2011-11-07
In short the best way to learn this is learn how to setup linux from scratch. That generally means Arch Linux, Slackware or something similar.

I haven't stumbled across this bible of awesome information yet myself. I might reference to linux.org but the server is down, and might be for quite some time. 

A good bet is following one of the above links and reading through the server guide, which while not 100% comprehensive, will cover all the basics.

---

### Post by Daudek on 2011-11-08
I will look at those links asap! I am a windows user and have partitioned my computer's hard drive to put Ubuntu on it. Where can i find Arch linux (I hope that is right)? The reason I asked about installing files without using the software center is that when I first got into Ubuntu (not long ago :P) I tried to download adobe flash player from the website and had no idea what to do with this downloaded file. I now know better. Also, would it be helpful to learn about the "terminal?" As in writing instructions in it and getting a result, for lack of a better analogy. 

Thank you!
Grace
Daudek

---

### Post by Rex Bouwense on 2011-11-08
Info on terminal:
[http://linuxcommand.org/](http://linuxcommand.org/)
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
That should get you started.

---

### Post by vanhenryjr on 2011-11-08
I am using a computer book (in my case Ubuntu Unleased 2011 edition. Pick a book from amazon covering your distribution. And yeah, i have had the same problem. Down load and "now what?"

---

### Post by Daudek on 2011-11-10
So I am looking into installing arch linux to try and get a better understanding of linux. Thank you to all who helped me get oriented with this!

---

### Post by duke.tim on 2011-11-10
After you learn, I would suggest using Ubuntu as your main system. There are some security benefits and such.

---

