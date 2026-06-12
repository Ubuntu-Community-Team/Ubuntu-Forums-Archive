---
title: "Unable to edit properties in rhythmbox"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by buskerjoe on 2012-04-14
l'm having this same problem, unable to edit properties in rhythmbox. but i came to this thread via absolute beginners talk, and am startled to find talk of entering commands.
  i've only used keyboard or ... well, i've never entered a command. that's the kind of action i leave to my son-in-law, geeks and nerds, no? 
 i'm willing to try it. but i'd like to have someone around. it's dark in there.

---

### Post by dearingj on 2012-04-16
@buskerjoe:
Terminal commands can be very useful. I definitely recommend getting familiar with some of the basic ones at least, such as 'cd' (change directory) or 'man' (short for 'manual'). The one we're interested in here is 'chmod' (change mode, where mode determines what a user is allowed to do with a given file or folder).

First, though, we need to find out where Rhythmbox is storing your music. Open up Rhythmbox, then click the Edit menu and choose Preferences. In the Preferences window that appears, choose the Music tab. Look at where it says your music files are placed in. In my case, it says "file:///home/dearingj/Music", so my music is in /home/dearingj/Music (ignore the file://, I'm not sure why it adds that). Note which letters are capitalized, if any. Also note that there is one slash at the start, before the word 'home'.

Now, to open a terminal window: Somewhere within your applications menu - I forget exactly where - there should be a terminal program listed. It might be called 'Terminal', or 'Terminal Emulator', or anything similar, depending on which software you have installed. Open it. In the terminal, type this in (replacing /path/to/music/folder with what you just got from Rhythmbox) and then hit enter:

```
chmod u+w /path/to/music/folder -R
```Here's a breakdown of the above command line:
chmod: Short for 'change mode', this is a program that changes the permissions associated with a given file or folder.
u+w: Tells chmod to give the user (the files' owner, presumably you) permission to write to the specified files.
/path/to/music/folder: The location of the folder that you want this done to
-R: Short for 'recursive', tells chmod that the location specified is a folder, and that this action of giving permissions should be done to every file and folder within it.

Edit: One thing I forgot to mention: If the path has spaces in it, you must either put double quote marks around the whole path (e. g. "/home/dearingj/Music") or put a backslash before each space\ like\ this.

---

### Post by clive littlewood on 2012-04-16
Hi

I prefer to use easytag, It's in the SC.

Clive

---

### Post by oldos2er on 2012-04-16
Hi buskerjoe, I've moved your post and its replies to a new thread. As per the posting guidelines, please try not to post in threads more than a year old.

---

