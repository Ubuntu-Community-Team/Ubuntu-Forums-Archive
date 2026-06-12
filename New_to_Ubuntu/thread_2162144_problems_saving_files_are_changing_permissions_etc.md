---
title: "problems saving files are changing permissions etc"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by TheBearNecessities on 2013-07-13
I'm using Lubuntu and am a beginner when it comes to linux.  Im trying to use PCManFM to edit files etc but I keep being told:

"can't open file to write"

if i look in the folder permissions

view - anyone
change - owner only
access - anyone

so that maybe explains why I can't edit the files in that folder.

but when i try and change the permissions i get "error setting permissions: operation not permitted"

anyone have any ideas what im doing wrong?

---

### Post by dannyboy79 on 2013-07-13
what file are you trying to edit and what folder is it in. if you don't own the file then you can't edit it without using sudo BUT don't just go an edit any file, there may be a reason it's owned by root or someone other than you.

---

### Post by TheBearNecessities on 2013-07-13
its just an xml file that i need to edit.  its in my "Downloads" folder, i just seem to use that folder for everything.

i was copied directly onto my lubuntu laptop from an android smart tv box.  so mayb that explains the ownership issue.

i have a few xml files that I will regularly be copying from android onto lubuntu so i can edit them in lubuntu.

thanks for replying, is there a better way to do this?

---

### Post by Werne on 2013-07-13
This should take care of it:
```
sudo chown <user>:<group> /path/to/file.xml
```
<user> stands for your username
<group> stands for a user group you're in, on Ubuntu that's usually your username

On my PC, that command would go:
```
sudo chown werne:werne /home/werne/Downloads/file.xml
```

You can check file permissions by cd-ing into the directory where the file is and by using ls -l, example:
```
$ ls -l
-rw-r--r-- 1 root  root          1 Srp 13 15:27 file.xml
```
It's owned by root so it can't be touched. And after running chown:
```
$ sudo chown werne:werne file.xml
-rw-r--r-- 1 werne werne         1 Srp 13 15:27 file.xml
```
Now I can do whatever I want with it.:wink:

If you are going to be copying the file back to the Android, note the user/group first so you can change permissions back after editing.

---

### Post by TheBearNecessities on 2013-07-13
great stuff thanks for the reply.

is there anyway of just having the permissions on the file so that it is accessible by everyone?  that way i wouldn't need to change permissions when i copy it to lubuntu and i wouldnt need to change permissions again when i copy it back to android?

also is there a way to use your technique to change the owner of the parent folder, thereby changing the permissions for every folder and file within?

---

### Post by Werne on 2013-07-13
> **TheBearNecessities said:**
> is there anyway of just having the permissions on the file so that it is accessible by everyone?  that way i wouldn't need to change permissions when i copy it to lubuntu and i wouldnt need to change permissions again when i copy it back to android?
There is, chmod will allow you to view, edit and execute any files, even if they are owned by root. However, I don't advise changing it to be accessible by anyone, especially not to someone who doesn't know much about it, or Linux in general.

If you really want to do it (which I guess you do), here's a bit of reading before, can't let you rush blindly into it:

File permissions have 3 attributes: Owner, Group, Others. What you need to do is allow Others (meaning, yourself as another user who doesn't own the file) to edit the file. Let's look at permissions listed by ls -l first:
```
-rw-r--r-- 1 root  root        1 Jul 13 17:57 file.xml
```
The above are permissions for a file I created that is owned by root, they are show in the order I mentioned above. What this means is that the Owner (root) has read/write access to the file (rw), Group has read-only access (r) and Others have read-only access too (r). To change this particular file so anyone can edit it, I'd need to execute the following:
```
sudo chmod 646 /home/werne/Downloads/file.xml
```
First number is Owner, second is Group, third is Others. The above would change file permissions into this:
```
-rw-r--rw- 1 root  root        1 Jul 13 17:57 file.xml
```
 And now Owner has read/write acces, Group has read-only access and Others have read/write access. This is what you need to achieve, but since the file permissions of the file you want to change are unknown to me, I cannot tell you the exact combination of numbers. I can tell you how chmod works though:

There are three main numbers - 1, 2 and 4

1 - Makes file executable
2 - Makes file write-only
4 - Makes file read-only

They can be combined to achieve different results, for example:

3 - Makes file executable and write-only (1+2)
5 - Makes file executable and read-only (1+4)
6 - Makes file read/write (2+4)
7 - Makes file executable and read/write (1+2+4)

There are other options for chmod like +x, -x, etc. but you'll have to read the man page about that. Just make sure you get the first two numbers to provide same permissions as they are already set, while using 6 (read-write) as the third one.

This may not work as you want though, depending on what the file is used for on Android.

> **TheBearNecessities said:**
> also is there a way to use your technique to change the owner of the parent folder, thereby changing the permissions for every folder and file within?
Yes, chown can do that when used with -R, it then operates recursively on the targeted directory changing file permissions for every file/folder/sasquatch inside. You can do the same with chmod. Both of those have a potential to mess up a lot of things if you are not careful (like running that on / or some important part of the system, or maybe even, god forbid, making a typo). It can also change owners for files you don't want to. Either way, here's an example:
```
sudo chown -R <user>:<group> /path/to/folder
```

Also, when there is a tool that does something and you want it to do the same thing differently, check the man pages, it's as simple as
```
man <tool>
```

---

### Post by TheBearNecessities on 2013-07-13
> **Werne said:**
> There is, chmod will allow you to view, edit and execute any files, even if they are owned by root. However, I don't advise changing it to be accessible by anyone, especially not to someone who doesn't know much about it, or Linux in general.

If you really want to do it (which I guess you do), here's a bit of reading before, can't let you rush blindly into it:

File permissions have 3 attributes: Owner, Group, Others. What you need to do is allow Others (meaning, yourself as another user who doesn't own the file) to edit the file. Let's look at permissions listed by ls -l first:
```
-rw-r--r-- 1 root  root        1 Jul 13 17:57 file.xml
```
The above are permissions for a file I created that is owned by root, they are show in the order I mentioned above. What this means is that the Owner (root) has read/write access to the file (rw), Group has read-only access (r) and Others have read-only access too (r). To change this particular file so anyone can edit it, I'd need to execute the following:
```
sudo chmod 646 /home/werne/Downloads/file.xml
```
First number is Owner, second is Group, third is Others. The above would change file permissions into this:
```
-rw-r--rw- 1 root  root        1 Jul 13 17:57 file.xml
```
 And now Owner has read/write acces, Group has read-only access and Others have read/write access. This is what you need to achieve, but since the file permissions of the file you want to change are unknown to me, I cannot tell you the exact combination of numbers. I can tell you how chmod works though:

There are three main numbers - 1, 2 and 4

1 - Makes file executable
2 - Makes file write-only
4 - Makes file read-only

They can be combined to achieve different results, for example:

3 - Makes file executable and write-only (1+2)
5 - Makes file executable and read-only (1+4)
6 - Makes file read/write (2+4)
7 - Makes file executable and read/write (1+2+4)

There are other options for chmod like +x, -x, etc. but you'll have to read the man page about that. Just make sure you get the first two numbers to provide same permissions as they are already set, while using 6 (read-write) as the third one.

This may not work as you want though, depending on what the file is used for on Android.


Yes, chown can do that when used with -R, it then operates recursively on the targeted directory changing file permissions for every file/folder/sasquatch inside. You can do the same with chmod. Both of those have a potential to mess up a lot of things if you are not careful (like running that on / or some important part of the system, or maybe even, god forbid, making a typo). It can also change owners for files you don't want to. Either way, here's an example:
```
sudo chown -R <user>:<group> /path/to/folder
```

Also, when there is a tool that does something and you want it to do the same thing differently, check the man pages, it's as simple as
```
man <tool>
```

wow, that's just what i was looking for.  thanks so much for all your time.

one final question; is there no gui that can allow me to do these actions.  or launch pcmanfm - from the terminal - with admin privileges or something like that?

---

### Post by Werne on 2013-07-13
> **TheBearNecessities said:**
> is there no gui that can allow me to do these actions.  or launch pcmanfm - from the terminal - with admin privileges or something like that?
In file manager, right-clicking the file and selecting properties should give you access to changing that, provided that you open the file manager as root. Other than that, there might be some GUI thingy to do that but I got no idea, I do it through command line.

```
sudo pcmanfm
```
Executed in teminal, the above will open pcmanfm as root. Or if you have gksu installed, Ctrl+F2 and type:
```
gksudo pcmanfm
```
That way you don't have to fiddle around with the terminal.

---

### Post by dannyboy79 on 2013-07-13
NOTE: anytime you launch a GUI file manager with root privileges than it's very simple to screw up your system. YOu could accidentally drag a folder and move it, delete something you didn't want to etc etc

---

### Post by Werne on 2013-07-14
> **dannyboy79 said:**
> NOTE: anytime you launch a GUI file manager with root privileges than it's very simple to screw up your system.
Anything executed as root has a potential to screw up your system. As said to me by Debian (Arch too):
```

      #1) Respect the privacy of others.
      #2) Think before you type.
      #3) With great power comes great responsibility.
```
In my experience, keeping the above in mind means the difference between messing things up and doing things right.;)

By the way, I can't say that I've ever seen this message on Ubuntu. Or maybe I did and forgot about it? Hmm...:-s

---

