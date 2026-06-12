---
title: "Can a file or directory be hidden completely?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by garyed on 2008-05-09
I have a few files that contain passwords & numbers that I want to hide. 
I decided to put them in a seperate hidden directory since others in the house use my computer without always switching users. I know how to use chmod & chown to keep anyone from viewing the files but is there a way to stop them from viewing even the hidden directory name? All they have to do is go to the file browser>>view & click on view hidden files & the hidden directory will show up.

---

### Post by om1 on 2008-05-09
this might be what you are looking for... 
[http://www.truecrypt.org/](http://www.truecrypt.org/)
personally i think it is awesome

---

### Post by garyed on 2008-05-09
Thanks,
That does look pretty cool but I don't think I need encryption that much.
It's not a real problem but i was just wondering if there was some sort of command line that could keep hidden files from being displayed in nautilus.

---

### Post by om1 on 2008-05-09
folders im not so sure about but files you can have a leading . like .mytxtfile.txt and they are hidden... but if you say to display hidden files or press ctrl + h they will be displayed... thats all i know

---

### Post by olejorgen on 2008-05-09
If you don't want / can rename the file, you can create a file called .hidden and add the file names you want to be hidden.

---

### Post by sdennie on 2008-05-10
One thing you could do would be to make the owner of the files be root:root and then change the umask to 0700.  That would at least require someone to know your password to look at them (via sudo or gksudo).  After that, just put the files somewhere innocuous and call them something non-obvious.  Beyond that, you'd need to use encryption as stated above.

---

### Post by tamoneya on 2008-05-10
EDIT: ignore this post.  It was a bad idea.  Go with what vor recommended.

---

### Post by PeterJS on 2008-05-10
> **vor said:**
> One thing you could do would be to make the owner of the files be root:root and then change the umask to 0700.  That would at least require someone to know your password to look at them (via sudo or gksudo).  After that, just put the files somewhere innocuous and call them something non-obvious.  Beyond that, you'd need to use encryption as stated above.

This is all well and good, but encryption* is really the way to go. If someone gets a liveCD in the machine the permissions aren't going to slow them down one bit.

*This isn't 100% safe, but most attackers aren't willing to wait the months/years it would take to crack an encrypted file.

---

### Post by garyed on 2008-05-10
> **olejorgen said:**
> If you don't want / can rename the file, you can create a file called .hidden and add the file names you want to be hidden.

I'm not sure I understand.
Say I have 2 files to hide in my home dir. named safety1 & safety2 do I just put their names & paths into a file called .hidden & where would that file go?

---

### Post by olejorgen on 2008-05-10
Yes, but I think I missread the question. They will still show up when you choose "show hidden". 

The file goes in the same directory. (and you don't need/should use full paths)

---

### Post by garyed on 2008-05-10
> **vor said:**
> One thing you could do would be to make the owner of the files be root:root and then change the umask to 0700.  That would at least require someone to know your password to look at them (via sudo or gksudo).  After that, just put the files somewhere innocuous and call them something non-obvious.  Beyond that, you'd need to use encryption as stated above.

So as an example I have a file to hide named safety1
I would do ```
 sudo chown root root safety1 
```
I know I can do ```
sudo chmod 700 safety1
```
Then no one can read them but they can still view the file name.
What would the code be to use umask & would that stop the from viewing the file name?

---

### Post by sdennie on 2008-05-10
> **garyed said:**
> So as an example I have a file to hide named safety1
I would do ```
 sudo chown root root safety1 
```
I know I can do ```
sudo chmod 700 safety1
```
Then no one can read them but they can still view the file name.
What would the code be to use umask & would that stop the from viewing the file name?

I mistyped when I wrote umask.  I meant just use chmod as you've done above.  There is no way to prevent people from seeing the filename if they want to see it but, rather than naming the files "safety1" and putting them in a folder called ".secrets" or something.  Call them like  gmodterm (or something odd like that) and stick them in a directory like .gnome2.

Still, you should really use encryption if you are really concerned about someone finding the files.

---

### Post by Gazneth on 2008-05-10
If you need to encrypt passwords try keepassx, it's made for just that purpose, and it's in the repositories. It's available in linux and windows and portable versions and the data files are compatible between them. For encrypting files Kgpg might work for you but because it's a kde program it needs a lot of other libraries to work. But if file encryption is needed it might be just the thing.

---

### Post by pommattski on 2008-05-10
I strongly recommend that you try using keepassx. It's very easy to use to protect all your passwords/logins etc...

It's in the repositories so either use synaptic package manager or the following commands in terminal to install it:```
sudo apt-get update
sudo apt-get install keepassx
```It'll appear in your Accessories menu.

---

### Post by Krumar on 2008-05-10
I second using Keepass for managing your passwords, it keeps an encrypted database of passwords, can preform autotyping and password generation. The program is pretty easy to use too.


Krumar

---

