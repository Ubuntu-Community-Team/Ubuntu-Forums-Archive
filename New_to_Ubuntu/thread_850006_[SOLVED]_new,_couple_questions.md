---
title: "[SOLVED] new, couple questions"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Xinlitik on 2008-07-05
Hi all,

Just got Ubuntu Hardy running on my computer, loving it so far.

Just a few issues have come up:

1) I dont have sound on flash videos ie youtube. 
 I searched for the fix, but when I went to edit the etc/firefox/firefoxrc file...it didn't exist. I assume that fix was for firefox 2 or something (post was dated 2006ish). Is there a workaround for firefox 3?

2) I'd like to swap my music from my windows external HD to my linux comp. I can read, play, and copy songs with no problem, but I cant move folders into my linux Music folder, receiving an 'Access denied' message. I gather that this is a permissions issue but I am clueless on how to fix it :(

Thanks for any help!

---

### Post by iaculallad on 2008-07-05
> **Xinlitik said:**
> Hi all,

Just got Ubuntu Hardy running on my computer, loving it so far.

Just a few issues have come up:

1) I dont have sound on flash videos ie youtube. 
 I searched for the fix, but when I went to edit the etc/firefox/firefoxrc file...it didn't exist. I assume that fix was for firefox 2 or something (post was dated 2006ish). Is there a workaround for firefox 3?

-Install the audio support wrapper for non-free flash plugin:

```
sudo apt-get install libflashsupport
```

> **Xinlitik said:**
> 2) I'd like to swap my music from my windows external HD to my linux comp. I can read, play, and copy songs with no problem, but I cant move folders into my linux Music folder, receiving an 'Access denied' message. I gather that this is a permissions issue but I am clueless on how to fix it :(

Thanks for any help!

Use the command below in your terminal so you'll be given privilege to copy-and-paste folders/files in directories.

```
gksudo nautilus
```

---

### Post by sayakb on 2008-07-05
Problem 1:At a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

Problem 2: You are getting access denied for the Music folder in your Home directory?
Try:
```
sudo chown username:group /home/Music
```And try copying again.

---

### Post by Xinlitik on 2008-07-05
Thanks for the quick replies!

Gah thought it was fixed, didnt work out though. (reading next post now.. )

---

### Post by iaculallad on 2008-07-05
Aahhh... you mean accessing a "shared" folder in a windoze-based networked computer:

Install smbfs using your terminal at your Ubuntu system:


```
sudo apt-get install smbfs
```

and follow the procedure I posted in this [thread]("http://ubuntuforums.org/showthread.php?t=847837") to access your music folder. Just be sure that you had shared it in your windoze OS.

---

### Post by Xinlitik on 2008-07-05
> **iaculallad said:**
> Aahhh... you mean accessing a "shared" folder in a windoze-based networked computer:

Install smbfs using your terminal at your Ubuntu system:


```
sudo apt-get install smbfs
```

and follow the procedure I posted in this [thread]("http://ubuntuforums.org/showthread.php?t=847837") to access your music folder. Just be sure that you had shared it in your windoze OS.

I'm sorry I'm a bit of a Linux newb--

1) How do I find the IP of a device I'm networked with?
2) What do I do about name/password if it is a networked external hard drive (has no u/n or p/w)

thank you

---

### Post by iaculallad on 2008-07-05
> **Xinlitik said:**
> I'm sorry I'm a bit of a Linux newb--

1) How do I find the IP of a device I'm networked with?

To find out the IP of your windoze machine: enter your dos prompt (cmd.exe):

```
ipconfig /all
```

To find out the IP of your Ubuntu machine: enter your terminal:

```
ifconfig
```

or

```
ifconfig eth0
```

> **Xinlitik said:**
> 
2) What do I do about name/password if it is a networked external hard drive (has no u/n or p/w)

thank you

Just use the username/password you use in your windoze machine, and be sure to share the music folder in your external drive (If that's the location).

---

### Post by Xinlitik on 2008-07-05
Ah wonderful. Copied flawlessly, thanks a bunch.

---

### Post by barbedsaber on 2008-07-05
Now, can you please mark this thread as solved, so that all the people that look for people to help know that your problem has already been fixed.
All you have to do it click on thread tools (near the top right) and then click mark thread as solved.

thanks.

---

### Post by hyper_ch on 2008-07-05
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

