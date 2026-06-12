---
title: "Cannot run files on ubuntu"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by candre on 2012-10-18
Hello,

I reccently downloaded this file "wine-1.4.1.tar.bz2" and extract to "/home/candre/wine-1.4.1/".
Now I need to run this file "wineinstall" in order to install Wine 1.4.1 but I can't and I don't know how to do it.

Can somebody help me?

Thanks in advance.

---

### Post by shreepads on 2012-10-18
Open Terminal

$ cd /home/candre/wine-1.4.1/

$ ./wineinstall              <assuming this is the folder where the file is located>

---

### Post by Wim Sturkenboom on 2012-10-18
Any reason not to use wine from the repositories?

---

### Post by Lars Noodén on 2012-10-18
> **Wim Sturkenboom said:**
> Any reason not to use wine from the repositories?

+1 for getting it via the repositories

You can open the Software Center and find it. Or if you have Synaptic, use that.  Using the official version means that you will be able to automatically track the version and any dependencies as well as being able to automatically update when patches and upgrades become available.

---

### Post by buckyaustin on 2012-10-18
Yes please use the repositories, that way it is easier to keep up to date.
Also you don't have to use GUI to install throght the repo's. Just run "sudo apt-get install [package name]". Also run "sudo apt-get update" before installing any new package, because doing this updates the repositories, not programs. To update programs run "sudo apt-get upgrade". 

Finally to update to the latest distrobution type "sudo dist-upgrade".

The reason you do this is to mantain your pc easily. Try to never download a package and install that way. If you can't find a program in the repositories then look for a ppa for the package. Then add it to the repositories.

---

### Post by Mark Phelps on 2012-10-18
I'm guessing that you're trying to install Wine because you want to run some MS Windows apps, right?

BEFORE you do that, go to the WineHQ website, look up the application compatibility database -- and check out the ratings for the apps and versions you want to run.  If you are going to depend on any of these on a daily basis, any rating less than Gold is going to be a waste of your time.

---

### Post by candre on 2012-10-18
> **shreepads said:**
> Open Terminal

$ cd /home/candre/wine-1.4.1/

$ ./wineinstall              <assuming this is the folder where the file is located>

Yes, that's what I did. But it says "command not found".

---

### Post by candre on 2012-10-18
The thing is that my internet connection is low. So I downloaded the file from another computer with a faster internet connection.

---

### Post by candre on 2012-10-18
> **Lars Noodén said:**
> +1 for getting it via the repositories

You can open the Software Center and find it. Or if you have Synaptic, use that.  Using the official version means that you will be able to automatically track the version and any dependencies as well as being able to automatically update when patches and upgrades become available.


I will remember that in the future. Thanks for the advise. I really aprecciate. But once I already downloaded the file, how do I run it in order to install wine?

---

### Post by candre on 2012-10-18
> **Wim Sturkenboom said:**
> Any reason not to use wine from the repositories?


The thing is that my internet connection is low. So I downloaded the  file from another computer with a faster internet connection.

---

### Post by candre on 2012-10-18
But can someone, please, Explain to me how to run that file?
The file "wineinstall" have no extension.
I did "./wineinstall" it says "no permission".
Then I did "sudo ./wineinstall" it says "command not found".

---

### Post by Wim Sturkenboom on 2012-10-19
```

cd /home/candre/wine-1.4.1/
ls -l  |grep wineinstall

```
This will tell you if the file exists, who owns it and what the permissions are. I have a suspicion that the file is not executable, but I'm not sure.
If the file is not executable, use
```

chmod 755 wineinstall

```
and try again.

---

### Post by Wim Sturkenboom on 2012-10-19
> **candre said:**
> The thing is that my internet connection is low. So I downloaded the  file from another computer with a faster internet connection.
There is a way to download packages using a different PC, copy them to your PC and install. Do a search here or elsewhere on the web.

---

### Post by Mark Phelps on 2012-10-19
Ubuntu is not designed to have apps installed in a offline environment.  While it CAN be done, installing from packages downloaded onto another PC is likely to be a very difficult and time-consuming process.

Why?

Because of unmet dependencies.

Let's call the downloading PC #2 and the target PC #1.  You download a deb file to PC#2 and copy it to PC#1.  Now, you go to install it -- and it fails due to an unmet dependency.  You write down the name of what's missing.

You download that on PC#2 and copy it to PC#1 -- and you try again -- and get ANOTHER unmet depencency.

And so on, and so on, and so on.

---

### Post by paulmeeks2004 on 2012-10-21
Hey their, I'm a newbe to. I ran across this early'er (Code: SUDO apt-get install Synaptic ) they said best for down, uploading & adding PPA's I went to a site that was for wine or how ever it's spelled :) Check it out it might be what your looking for.. Paul's the name!

---

### Post by candre on 2012-10-27
> **Wim Sturkenboom said:**
> ```

cd /home/candre/wine-1.4.1/
ls -l  |grep wineinstall

```This will tell you if the file exists, who owns it and what the permissions are. I have a suspicion that the file is not executable, but I'm not sure.
If the file is not executable, use
```

chmod 755 wineinstall

```and try again.

Hey! I did what you said and worked.
Good job! Thank you very much.
Problem solved.

Do I always have to do that?

---

### Post by Wim Sturkenboom on 2012-10-28
Great. You can mark your thread as solved using the thread tools just above the first post on this page.

And yes, a file must be executable before you can run them directly. In general, when you create a file, it will not have the execute bit set by default. This also applies to downloaded files or files copied from memory stick; this makes it 'safer' as you can not run it a first time without thinking about it.

---

