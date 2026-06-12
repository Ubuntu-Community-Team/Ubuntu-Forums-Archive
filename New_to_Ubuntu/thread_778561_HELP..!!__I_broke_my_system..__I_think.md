---
title: "HELP..!!  I broke my system..  *I think*"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by samdavid6 on 2008-05-02
Hi everyone, I am a bit of a newbie here and while I'm learning things pretty quick, I think I did something pretty bad.  I was trying to get an application to work and I was following some online instructions to fix it.

The instructions called for downloading an archive file that had a folder called /lib in it.  I was to move this to my /usr/lib folder.

So I downloaded it, opened up a terminal and went over to the directory it was in and typed

sudo mv /lib /usr/lib

Now, no commands work whatsoever.  I cant run programs, open up a terminal or anything.  Any time I try anything I get this error

If I type the command : ls

I get

bash: /bin/ls: No such file or directory

Funny thing is, the command "cd" works.

I have a nautilus window open and I went to my home folder and looked in the "bin" folder and the command "ls" and "sudo" (another command that doesnt work) are both there.  There is no "cd" though.

Funny thing is, I dont even understand what I did wrong.  Perhaps if I did, I might be able to find a solution.

So, can someone please help me understand:

1) What I did wrong (I didnt even TOUCH the "bin" folder)

2) Any way to get things working again..

I dont want to reinstall if at all possible, I have about 80 gigs of photos, music and settings from over 6 months on this, and am unable to copy my home folder to anywhere else.

---

### Post by iSplicer on 2008-05-02
Have you tried rebooting?

---

### Post by samdavid6 on 2008-05-02
No I havent..  I'm just worried that if I log out, I wont be able to log back in or something.  Then I'd really be screwed..  Should I..?

I dont even know what I did wrong..?

---

### Post by iSplicer on 2008-05-02
> **samdavid6 said:**
> No I havent..  I'm just worried that if I log out, I wont be able to log back in or something.  Then I'd really be screwed..  Should I..?

I dont even know what I did wrong..?

Yeah you should. Worst case scenario, you can boot up from LiveCD and bak up your stuff but the chance of something screwing up is very very low.

I suggest you go ahead and reboot, that should fix it.

---

### Post by samdavid6 on 2008-05-02
Dang, I just realised.  I dont have a liveCD.  I upgraded to Hardy over the internet.  I cant even download the cd and burn it (I tried starting CD/DVD creator or Brasero, but I get a "/usr/bin/brasero: No such file or directory".  So it looks like files in /usr/bin are messed up too.

What exactly did I do with one command..?

---

### Post by iSplicer on 2008-05-02
Its probably just a bug. If you are really unsure, I wont push you, but I would reboot. There is absolutely no chance that your data will vaporize.

---

### Post by iSplicer on 2008-05-02
On second thoughts, just as a precaution, tell us what you were trying to download and where you got it - viruses that came disguised as packages are not so uncommon.

---

### Post by shad0w_walker on 2008-05-02
Another edit: Can you run the 'ln' command? try it with this:

```
 ln --help 
```

If you can run this command then try this:

```
 sudo ln -s /usr/lib/lib /lib 
```

This should link the new position to the old one and hopefully get things working again.



Out of curiosity how is rebooting going to solve this problem? He's moved his /lib folder, rebooting won't move it back. Your best bet is to boot from a LiveCD (The installer disc is good if you still have it about) and to move the folder back to where it was. 

Can you boot up a LiveCD, goto a terminal (Applications > Accessories > Terminal) and run this command:

```
sudo fdisk -l
``` 

And post the output here? This will let us figure out which drive you need to access from the LiveCD and hopefully help you sort this all out.

[SIZE="3"]Try this AFTER you post the output of the last command and I get back to you.[/SIZE]
Make sure you replace <hd> in the commands with the name of the hard drive we find from the earlier command.

You should be able to fix it reasonably easily if you boot the LiveCD up, open a terminal (Applications > Accessories > Terminal) and run these commands:

```
sudo mkdir /media/ubuntu
```

```
sudo mount /dev/<hd> /media/ubuntu 
```

```
sudo mv /media/ubuntu/usr/lib/lib /media/ubuntu/
```

This should move your /lib folder back to the correct place. After this you should be able to restart the computer and Ubuntu should be working again.

Good luck.

Edit: You moved the libaries for most programs from the place they are expected to be. Which unfortunately is the rough equivilent of taking a cars engine and putting it on the roof. It's still an engine but it's not going to be looked for there and it isn't in the right place to do anything useful.

---

### Post by spec-chum on 2008-05-02
It could be recoverable.  If the command mv still works then you should be able to sort it out.

What your original command
```

sudo mv /lib /usr/lib

```
will have done is moved the lib folder from the root directory into /usr/lib, so you should now have a /usr/lib/lib folder.

Provided mv still works then all you should need to do to restore it is run
```

sudo mv /usr/lib/lib /

```

That should move the lib directory back to the root folder.

If you then reboot it should be fine.

---

### Post by tacutu on 2008-05-02
mv won't probably work either... cd worked because it is a bash internal command, not a separate program.

---

### Post by samdavid6 on 2008-05-02
Thanks for your assistance.  Really you cant imagine how grateful I am.

isplicer : the file I downloaded was from [http://www.uluga.ubuntuforums.org/showthread.php?t=582721&page=2]("http://www.uluga.ubuntuforums.org/showthread.php?t=582721&page=2") but I think the command actually messed the system up.

shad0w_walker : The ln, mv, mount, mkdir, fdisk - nothing works..

spec-chum : I will do that.  I have to hunt for a boot disk (unfortunately it may not be ubuntu, but I think that wont be a problem)  However, while I'm looking for the disk, I just would like to confirm something.  I do have a folder /usr/lib/lib and I need a live cd to move the file (since sudo doesnt work either)

However most of the error messages that I get say that a file/command cannot be found in either /bin or /usr/bin.  So I'm sort of wondering how /usr/lib/lib/ caused an error in /bin or /usr/bin.  Since the /usr/lib/lib folder doesnt contain any of these files/commands anyway.

But I am looking for the cd..  Am a bit worried though because I got a whole lot of essential stuff on this pc.  I just finally got my wife moved over and using the linux partition and I dont want to give her a reason to go back to windoze.. :-)

I'm just asking in the hopes of better understanding the system and how it works, thats all..

---

### Post by tacutu on 2008-05-02
the programs in /bin and /usr/bin are linked against libraries which are expected to be in /lib. Since you moved them, the programs cannot find them and so they don't work. It's like when you can't find your glasses because they were moved...

---

### Post by shad0w_walker on 2008-05-02
For anything but the very top part of my post (The edit) you will need to be booted from the LiveCD. They should hopefully work from there.

---

### Post by samdavid6 on 2008-05-02
Ok.. phew.. let me log out and live cd in again.

brb in a few to let you know if everything works..  

Thank you all..

---

### Post by samdavid6 on 2008-05-02
Yaay..!!  Thanks to a trusty old Knoppix CD, I have a working system again.

When I shutdown ubuntu I had to power off the system since it wouldnt shut down on its own.  Can you believe I spent 6 hours wondering why I couldnt open this drive in Knoppis as "write"..?  Finally I just did a quick "fsck", opened as write and moved the folder back.

I want to say thank you to shad0w_walker, isplicer, spec_chum and tacuto.

I really appreciate your help.  You can tell I'm not going to be "sudo"ing anything so easily cant you..?

---

### Post by shad0w_walker on 2008-05-02
Congrats on getting things going again. Don't forget to mark the thread solved.

---

