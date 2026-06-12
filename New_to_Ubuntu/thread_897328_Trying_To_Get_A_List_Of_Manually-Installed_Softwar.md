---
title: "Trying To Get A List Of Manually-Installed Software (i.e., Not Default) - Help"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-08-22
I used the help from this thread: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) to try and get a list of installed software. However, nothing came up. At all. I tried sudo and no luck. And I know I've installed JRE and twitux. So, can anyone help me, please?

Thanks!

---

### Post by tangibleorange on 2008-08-22
> **iaskedalice09 said:**
> I used the help from this thread: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366) to try and get a list of installed software. However, nothing came up. At all. I tried sudo and no luck. And I know I've installed JRE and twitux. So, can anyone help me, please?

Thanks!

which command doesn't work?

---

### Post by ugm6hr on 2008-08-22
```
dpkg --get-selections > installed-software
```

This works - but not as you want.

It creates a list of **all** installed applications as a text file in ~/installed-software

---

### Post by iaskedalice09 on 2008-08-22
First one doesn't work for me. And, I typed cd ~/installed-software/ and cd /installed-software/ and it says it doesn't exist.

And if it doesn't have a list of just user-installed software, how can I get one?

Thanks for your help!

---

### Post by iaskedalice09 on 2008-08-22
I missed that it's a text file, so that's resolved and it works. Now, how to I get a manual installed software list?

---

### Post by cariboo on 2008-08-22
If you didn't install the software using the repositories there is no way to list installed software, unless you still have the source directories for everything you installed manually.

Jim

---

### Post by iaskedalice09 on 2008-08-22
All of them were in the repos.

---

### Post by fballem on 2008-08-22
Your timing is very good - I just looked for guidance yesterday and found this thread to be very useful:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

This may answer your question as well.

---

### Post by Cheesehead on 2008-08-22
For installed packages:
1) Synaptic keeps a record of manually-installed/removed packages under File-->History...if you did it using Synaptic (a very good reason to use it).
2) 'dpkg --get-selections > installed-software' gives you the list of installed packages without the date info.

For compiled packages and other customizations:
*The admin* is responsible for documenting special actions - er, that means you. The system has no means of remembering the admin's follies...unless you program it to. For example, by using 'checkinstall'.

I keep a diary in RSS format; it's easy, fast, portable, searchable, and updatable from any text editor. Just a quick paragraph at the end of each day or each project. It saves a lot of work trying to *remember* what hack I did to one of my machines a year ago. The searchability comes in handy for answering forum questions, too.

---

### Post by iaskedalice09 on 2008-08-23
Alright, so I'm going to go with the orig. fix, but when I type
```

sudo dpkg --select-software < installed software

```
And press ENTER, all goes well. Then I type

```
sudo dpkg dselect
```

And I get an error:
```
dpkg: need an action option
```

I tried: dpkg -i dselect, dpkg i dselect, dpkg dselect install, all with and without sudo and I got the same error. What's wrong?

---

### Post by iaskedalice09 on 2008-08-24
Anyone? Nu?

---

