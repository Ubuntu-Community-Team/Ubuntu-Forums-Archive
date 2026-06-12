---
title: "Default permissions of files"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by crowhill on 2008-09-19
Hi there!

On a regular basis, I post files on my website. For example, I make up pdf's and post them using 'scp' in the terminal. However, first, I always have to set the permissions of the file such that everybody can read and write the file and such that it cannot be executed as a program. This is unsatisfactory. Also, if I move a file from, let's say a USB stick, to my desktop I have to change the permissions as well.

It seems to me that whatever file gets in touch with Ubuntu gets these permissions that I have to change all the time.

Is it possible to set default permissions? If not, is there another, hopefully efficient solution to my problem?

Some help would be very much appreciated.

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by pyromanic123boom on 2008-09-19
Well chown should keep the permissions changed..I have to change some folder permissions once in a while but never twice for the same directory.

Just type in 

sudo chown -R youusernamehere /the/directory/here

---

### Post by hyper_ch on 2008-09-19
do you use a linux based filesystem on your usb drive that supports linux permissions?

---

### Post by vikram on 2008-09-19
default permissions for newly created files are defined by umask.

the default is in /etc/skel/profile and you override in your 

~/.bashrc file

for examples see
[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html")


> **crowhill said:**
> Hi there!

On a regular basis, I post files on my website. For example, I make up pdf's and post them using 'scp' in the terminal. However, first, I always have to set the permissions of the file such that everybody can read and write the file and such that it cannot be executed as a program. This is unsatisfactory. Also, if I move a file from, let's say a USB stick, to my desktop I have to change the permissions as well.

It seems to me that whatever file gets in touch with Ubuntu gets these permissions that I have to change all the time.

Is it possible to set default permissions? If not, is there another, hopefully efficient solution to my problem?

Some help would be very much appreciated.

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by crowhill on 2008-09-19
Thanks a lot for all the answers. That should help. The 'umask' stuff sounds great.

For 'hyper_ch': I formated the drive in WinXP so that I probably don't use a Linux file system.

Cheers,
crowhill.

---

### Post by anotherdisciple on 2008-09-19
I wouldn't suggest changing your umask... if anything it should be more strict...

just chmod 777 files that you want others to be able to access

---

### Post by scorp123 on 2008-09-19
Making files world-readable and world-writable (that's what "chmod 777" does!!!) is something you ***absolutely* [COLOR="Red"]SHOULD NOT[/COLOR]** do!

---

### Post by anotherdisciple on 2008-09-19
> **scorp123 said:**
> **[COLOR="Red"][SIZE="4"]Bad advice!![/SIZE][/COLOR]**

Making files world-readable and world-writable (that's what "chmod 777" does!!!) is something you ***absolutely* [COLOR="Red"]SHOULD NOT[/COLOR]** do! :roll:

That is what I was saying. If you want everyone to be able to access it without changing the ownership to themself... you would chmod 777 that file. I would never suggest that you do this to files that you don't want to be accessible to everyone.

What chmod 777 would do is make the user, group, and others able to read, write and execute the file.

It's not bad advice... it's much smarter than changing the permission of every new file you create with umask... that is unsafe.

Only make the files that you want accessible to EVERYONE, accessible to everone

---

### Post by anotherdisciple on 2008-09-19
PS- that is what the user is trying to accomplish... make the file accessible to everyone. Hence, not bad advice.

---

### Post by crowhill on 2008-09-19
To be more precise:

Whenever I create a *.pdf file from a *.tex (LaTeX) file using my beautiful bash function 'tex2pdf' I have to change the permissions in order to make it accessible on my website.

Whenever I create a *.html file using vi I have to change the permissions in order to make it readable on my website. That's a pain.

Do I have to 'chmod 777 filename' each time?

Cheers,
crowhill.

---

### Post by scorp123 on 2008-09-19
> **anotherdisciple said:**
> That is what I was saying. [SIZE="4"]My apologies ..... [/SIZE]  Honestly. Seems I was too tired. Oh man. Sorry. Really. I didn't see the negation in your "would[COLOR="Red"]**n't**[/COLOR]" 

Let me correct my posting above ... Sorry again :D

---

### Post by anotherdisciple on 2008-09-19
> **scorp123 said:**
> [SIZE="4"]My apologies ..... [/SIZE]  Honestly. Seems I was too tired. Oh man. Sorry. Really. I didn't see the negation in your "would[COLOR="Red"]**n't**[/COLOR]" 

Let me correct my posting above ... Sorry again :D

Haha... it's cool... I understand why people get worried about security issues. Making a file accessible to everyone is usually not good, but there are reasons to do so.

---

### Post by anotherdisciple on 2008-09-19
> **crowhill said:**
> To be more precise:

Whenever I create a *.pdf file from a *.tex (LaTeX) file using my beautiful bash function 'tex2pdf' I have to change the permissions in order to make it accessible on my website.

Whenever I create a *.html file using vi I have to change the permissions in order to make it readable on my website. That's a pain.

Do I have to 'chmod 777 filename' each time?

Cheers,
crowhill.

The quick answer is... 

No, you can change your umask and make it default at 777 or something like that, but that's just not a good idea.

It's better to be more secure and put up with the pain that it is... but it's your files, you can change your umask if you aren't worried about it.

---

### Post by scorp123 on 2008-09-19
> **crowhill said:**
> Do I have to 'chmod 777 filename' each time? '644' would be more than enough. '777' is just plain dangerous. That's read+write+execute permission for ***everyone*** ... A server hosting such files is begging to be soon hacked.

---

### Post by anotherdisciple on 2008-09-19
> **scorp123 said:**
> '644' would be more than enough. '777' is just plain dangerous. That's read+write+execute permission for ***everyone*** ... A server hosting such files is begging to be soon hacked.

644 would make the owner able to read and write but not execute, the user group to read-only, and others to read only.

---

### Post by anotherdisciple on 2008-09-19
Here is a really good manual page on chmod...

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod")

---

### Post by scorp123 on 2008-09-19
> **anotherdisciple said:**
> 644 would make the owner able to read and write but not execute, the user group to read-only, and others to read only. For documents on a web server this is usually enough and pretty much exactly what you'd want. Giving the "write" and "execute" bits to users and groups who have no business having such rights can be dangerous. A hacker could gain enough priviledges so that he could overwrite the file (with permissions set to "777" this is almost guaranteed!) with anything he wants (e.g. a program of his own) and then remotely execute it (thanks to the "execute" bit already being set!) and thus try to break deeper into the system ...

---

### Post by vikram on 2008-09-20
> **crowhill said:**
> To be more precise:

Whenever I create a *.pdf file from a *.tex (LaTeX) file using my beautiful bash function 'tex2pdf' I have to change the permissions in order to make it accessible on my website.

Whenever I create a *.html file using vi I have to change the permissions in order to make it readable on my website. That's a pain.

Do I have to 'chmod 777 filename' each time?

Cheers,
crowhill.

I can suggest two options -

1. create a batch script which will change the permissions to 666 for everyone to read and write or 644 to allow others to only read.

2. you can create a non privleged user to create the documents and set the umask for that user so that new files are created with the required permissions.

---

### Post by scorp123 on 2008-09-21
> **scorp123 said:**
> For documents on a web server this is usually enough and pretty much exactly what you'd want. Giving the "write" and "execute" bits to users and groups who have no business having such rights can be dangerous. A hacker could gain enough priviledges so that he could overwrite the file (with permissions set to "777" this is almost guaranteed!) with anything he wants (e.g. a program of his own) and then remotely execute it (thanks to the "execute" bit already being set!) and thus try to break deeper into the system ...Just to elaborate this here ... I was just digging deeper into what "anotherdisciple" explained in his posting; I am not saying that what he wrote is 'wrong' or something like that, I am just confirming what he wrote + giving a slight bit more detail. ;)

---

### Post by anotherdisciple on 2008-09-21
Yeah, I guess it all comes down to security with the question you have. There are lots of ways to accomplish what you are wanting to do, you just have to consider what is safest in your situation. 

If you want _every file_ that you create from now on to be _readable_ by others, but you don't want them to be able to write to it... I would change your umask to 644.

If you want just like I stated before except only on certain files, chmod 644 _just those files_.

I would never suggest you change your umask to 777 ever. At least I can't think of a good reason to that.

You can chmod 777 files so that _everyone can do whatever they want with them_, but only do this if you know that those files are available to only trustworthy people. Like scorp123 said... if you make those files available to EVERYONE, you are begging to be hacked.... not really even hacked... you just handed them the ability to ruin you... haha!

So here is my best advice, you have heard about how to change your umask, you have seen how to chmod, you have manual pages on how to set up different privileges to different people. Now all you have to do is take all of that advice and see what will get the job done with security in mind. That should be pretty easy with the available info.

Hope that helps!

---

