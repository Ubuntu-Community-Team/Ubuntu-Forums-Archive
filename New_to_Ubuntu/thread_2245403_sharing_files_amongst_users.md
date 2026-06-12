---
title: "sharing files amongst users"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by c-masini on 2014-09-23
Dear all,
I am a newbie on linux, as you can imagine from the question.

I am using ubuntu 14.04

On our family laptop I have created users for myself, my wife and kids - so that everyone can have their own set up.
This is necessary, because my wife uses mandarin as her main language - hence I need to keep separated her activity (per example on google searches) or that will interfere with my profile.

Whilst keeping users separate is good for the above, it is a problem for sharing files - as everything we do - download files, create our files, etc - goes in separate home directories.
Is it possible to have all files and folders (downloads, movies, music etc) shared by defaults and only specific folder to be privately owned?

Many thanks,
Cristian

---

### Post by cogier2 on 2014-09-23
If you set up each user with the same Dropbox account that would do it. Dropbox should be available from the Software Center. Once installed right click on the "Documents" folder and "Make link", move the newly created link into the Dropbox folder, do that for each user on all the folders you want to share and they will all sync automatically.

---

### Post by Vladlenin5000 on 2014-09-23
Other solution is to create a separated shared partition - read/write permissions for all users - and just download/copy/move all the data that is intended for several users to that partitions. This obviously requires the use of non-standard system allocations but unlike the previous solution it doesn't require the use of a third-party service.

---

### Post by Morbius1 on 2014-09-23
You need to define "shared" please.

Let's say I create a directory called ... /home/Shared.

If I set permissions to 777 then everyone can add to and delete from that folder:
```
sudo chmod 777 /home/Shared
```
If I set the "sticky" bit I can allow everyone to add to but only delete files they own:
```
sudo chmod 1777 /home/Shared
```

What all these users will not be able to do however is edit any of those files owned by someone else. Only the user that created it can edit it.

If you want all users to be able to edit each other's files there are a couple of ways to do this. The classic way is through the use of the sgid ( set group id ) bit:
```
sudo chmod 2775 /home/Shared
```
And set the group to something ...  let's choose "plugdev" since it already exists:
```
sudo chown :plugdev /home/Shared
```
THen you'd have to add everyone to the plugdev group.

Now when anyone adds a file it will "inherit" the plugdev group and since the default umask in Ubuntu is 002 those files will be editable by the owner and anyone who is  a member of the plugdev group.

That will work for any files created in or copied  to but not moved to the folder. If you want to have it inherit the group in a move you need to use something else .. like bindfs for example.

---

