---
title: "Boy did I ever break my ubuntu"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by REMIX8604 on 2012-01-24
well I created a lot of trouble for myself. I was trying to install GTK+ 3.0 something and was trying to extract the .tar.xz file. so I looked it up on here and found a helpful little thing to add to my .bashrc file. so i added it and saved the file 'rm .bashrc~' afterwards (or I thought I put the ~) maybe thats why things are messed up. also when I edited .bashrc I 'sudo apt-get install extract' ...after I closed that terminal I was no longer able to open the software center, terminal or any program. only could use what was already open. I restarted and now it just sticks at the purple ubuntu logo. I assume I messed up my .bashrc file so I plan to use this LIVE USB to edit it back to normal in hopes that will take care of my problem.

now here is the part I really need help with. when I first set up this install of 11.10 there was an option to encrypt my local (user) folder. I chose this and typed in my password. it then generated some huge long super password that I dont have anymore or didnt write down.

is there anyway to get back into my user folder to fix my .bashrc file. unless you think this is being caused my something else. I do know what I origanaly typed in as a password to generate that super password.

here is the what I typed into my .bashrc 
its the 4th post on the thread..
[http://ubuntuforums.org/showthread.php?t=1116012](http://ubuntuforums.org/showthread.php?t=1116012)

---

### Post by dargaud on 2012-01-24
That function added to the .bashrc shouldn't break anything.

Are there other users defined on your system ? If so, login as them and try to fix from there. The normal course of action would be to boot from any livecd and fix the .bashrc file, but I don't know how to manually mount an encrypted home. [Search for that]("http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/").

---

### Post by REMIX8604 on 2012-01-24
yea im on the live usb now. no other users, and even if there were, it wont go to the login screen. 

I wonder what broke it then. that was just the last few things I did before everything went bad. built and installed GLib 2.16.6 ..in the middle of building GTK+ 3.0 all this was me just tryin to learn to build and compile pidgin. 

ok so I need to mount an encypted home. at least to save my files :)

---

### Post by carranty on 2012-01-24
dargaud's right in that the bashrc script isn't to blame.  I added the same code to a virtual 11.10 OS and it still boots fine.

I'm not sure how to mount an encrypted partition either, but to be honest if you've not got the password I don't hold out much hope - there wouldn't be much point to encrypting it if you didn't need the password to open it!

---

### Post by carranty on 2012-01-24
> **REMIX8604 said:**
> so i added it and saved the file 'rm .bashrc~' afterwards (or I thought I put the ~) 

Also what do you mean by this line?  Is .bashrc~ a backup of .bashrc or something?  If not why are you adding a tilde (~) after the filename.  Also 
```

rm file
```

deletes a file so I'm not sure what you mean when you say you *"saved the file  'rm .bashrc~'"*

---

### Post by grahammechanical on 2012-01-24
Can I share something that I learned the other day about the tilde character ( ~ ) while trying to create a slide show of background images?

The tilde character makes the file a hidden file just like a dot file ( . ). And the system is still able to read that file. It does not see it as a strict backup file that is not to be read.

So, you may have the equivalent of two bashrc files that the system is trying to read and getting hysterical as a result.

I was using sudo gedit to edit a file called background-1.xml and when gedit saved the file it created a second file called background-1.xml~ and the system was reading both files and getting confused.

Regards.

---

### Post by corrytonapple on 2012-01-24
> **carranty said:**
> Also what do you mean by this line?  Is .bashrc~ a backup of .bashrc or something?  If not why are you adding a tilde (~) after the filename.  Also 
```

rm file
```

deletes a file so I'm not sure what you mean when you say you *"saved the file  'rm .bashrc~'"*

Yeah, rm deletes a file.  
So if you saved the file then typed that in the command line, then you deleted that file altogether, and we'll need to give you a new one.

---

### Post by carranty on 2012-01-24
> **grahammechanical said:**
> 
The tilde character makes the file a hidden file just like a dot file ( . ). And the system is still able to read that file. It does not see it as a strict backup file that is not to be read.

I don't understand.  See my below terminal commands, The file with a tilde is not hidden.

```
carranty@carranty-laptop:~/Test$ ls
carranty@carranty-laptop:~/Test$ > Harry
carranty@carranty-laptop:~/Test$ > Robert~
carranty@carranty-laptop:~/Test$ > .David
carranty@carranty-laptop:~/Test$ ls
Harry  Robert~
carranty@carranty-laptop:~/Test$ ls -a
.  ..  .David  Harry  Robert~

```

EDIT : I realise now that *file~  *is a backup of *file* which has been modified using gedit.  Whenever you overwrite a file in gedit, it automatically creates a backup (denoted by the trailing ~).

---

### Post by carranty on 2012-01-24
> **corrytonapple said:**
> Yeah, rm deletes a file.  
So if you saved the file then typed that in the command line, then you deleted that file altogether, and we'll need to give you a new one.

I think what the poster is saying is that he modified his bashrc file using gedit, saved the changes which caused gedit to create .bashrc~ (gedit does this as standard).  He then deleted the backup (which by the way is **not a good idea **until you've tested the new file) by using the rm command.

REMIX8604, even if you accidentally deleted the original bashrc file (instead of the backup), it still wouldn't cause your computer to hang.

---

### Post by corrytonapple on 2012-01-24
Ah, okay.  I forgot about that, although I've used the backup file and known about them.  They are always there when I'm creating raw website code.

When you start up, hit "INS" on the keyboard.  Then note what it is stopping on.  "INS" switches between the splash screen and what the computer is doing while it starts up.  Hit it again to make it return to normal mode.

---

### Post by REMIX8604 on 2012-01-25
Yes the ~ is just a back up of a file. I was able to get into my encrypted files btw! 1 way was to Alt+Ctrl+F1 when booting and logging in with the command line. that gave me access to copy my files. Then I can run
>ecryptfs-unwrap-passphrase # To get my passphrase and access with a live USB once I have that.

So I backed up my files and since I didn't have time to find and fix the problem i just gave it a clean install. 11.10 

Just now I keep hearing a beeping that sounds like its from the hard drive... so I opened disk utility and it is telling me I have 7 bad sectors. Could this have caused my OS not to boot? I am running a SMART scan now. Is this a death sentence for my hard drive?

---

### Post by corrytonapple on 2012-01-26
If SMART comes up bad, then it probably is.

You should have backups.  Make one now while you can.

SMART has failed me before.  We had an iMac Western Digital HDD die and we never saw a warning from the SMART system.

---

