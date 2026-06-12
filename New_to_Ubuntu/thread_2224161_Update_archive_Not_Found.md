---
title: "Update archive Not Found"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2014-05-14
Hi,   My Update Manager reports: 

*62 updates have been selected.  27.8MB will be downloaded*

but then:

[I]Failed to download package files

Check your Internet connection. [/I]

Under details I find:

[I]Failed to fetch [http://th.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.9-0ubuntu1.3_amd64.deb](http://th.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_0.2.9-0ubuntu1.3_amd64.deb) 404  Not Found
Failed to fetch [http://th.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.12_all.deb](http://th.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79.12_all.deb) 404  Not Found
[/I]

I checked with a ping to th.archive.ubuntu.com and got a 3 out of 3 success score,  so I don't think there's anything wrong with my internet connection.

There are some CUPS updates and some new kernel headers in my update list,  but I can't be sure whether these are new updates or hangovers from a previously failed update attempt.  I don't want to skip any updates, especially not CUPS updates because I do have some printer issues pending.

I am currently in Thailand,  so Update Manager is correct in directing these updates to th,archive.ubuntu.com.

---

### Post by deadflowr on 2014-05-14
Click on check, and try to reload the package list.
You're on 12.04, right?
Both those packages are old.
unity greeter is now at version 0.2.9-0ubuntu1.4.
and linux firmware should be at version 1.79.14

So I think your package archives are old.
Running check should update those to the newer archive.

There is always the chance that the Thai repos are slow to get updated, in that event perhaps change mirrors.
in the update manager go to the settings button and click on it. Then go to where it says Download from and click on the dropdown menu, select other and choose from the list of other servers, or click on find best server.
then after you change servers, click on check, which will, as before, reload the package list.
Good Luck.

---

### Post by sandyd on 2014-05-15
Try these steps sequentially.

Run
```

sudo apt-get update
sudo apt-get upgrade
```

If that produces errors, run the below.
```

sudo sed -i s/th.archive.ubuntu.com/archive.ubuntu.com/ /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

Sometimes, regional mirrors may lag behind the default mirrors and create issues such as what you are experiencing.

---

### Post by Sleepy-zz-John on 2014-05-15
Clicking on check and reloading has fixed it,  so good advice and many thanks there Deadflowr.:grin:

Just slightly puzzled as to how my package archives got out of sync like that.  P'raps only a partial update sometime in the past when there was an internet glitch half-way through a previous session  :?   But wouldn't that normally have corrected itself at the next session :? ?

Anyway,  all good now .:)

---

### Post by Sleepy-zz-John on 2014-05-15
Awww thanks sandyd,  but happily deadfowr's solution has just worked and I'm OK again now.  

Let me see if I can now mark this one as solved.

---

### Post by deadflowr on 2014-05-15
Well, lucky for you if it happens again, you have two methods to try to fix it.
Both the check button and the command "sudo apt-get update" do the same exact thing.
They both reload the list of packages that are available to update.

Some people are hesitant to run the "sudo apt-get upgrade" command, for fear that it will upgrade the Ubuntu version.
In that regard, don't worry. All it does is install the newly upgradeable packages for the version you are using.
Basically it's the same as hitting the install button on Update Manager.

Hope that helps for future reference.

---

