---
title: "How to apply a wine patch?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by legolas_w on 2008-09-15
Hi
Thank you for reading my post.
I have WinE 1.1.4 installed and I want to apply a patch to be able to play Spore the patch is available at [http://bugs.winehq.org/attachment.cgi?id=15883](http://bugs.winehq.org/attachment.cgi?id=15883) but I do not know how to apply it, can you pelase give me some pointer?

Do I need to get WinE source code to apply this patch?

Thanks

---

### Post by legolas_w on 2008-09-15
Any Comment?

Thanks.

---

### Post by Kinetic777 on 2008-09-15
If I am correct, in order to apply a patch to WINE, you must obtain the source code, add in the patch and then compile it. There are numerous guides online on how to do this, good luck.

---

### Post by dave08 on 2008-09-17
Hi,

I am also trying to get spore working under wine. This is what I have done so far....

I used the following commands to download the wine source:

```
sudo apt-get build-dep wine
sudo apt-get install git-core
git clone git://source.winehq.org/git/wine.git ~/wine-git
```

To install wine I ran these commands:

```
cd ~/wine-git
./tools/wineinstall
```

Once wine installed I copied and pasted the [patch]("http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html") into a file and saved it as 'spore.patch' in the wine-git folder. I then ran:

```
patch p1 < spore.patch
```

Some people have had success with this (see [Spore 1.0 on Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652")) but I cannot even install the game as it will not connect to the licensing server.

I hope you have better luck.

Dave

---

### Post by legolas_w on 2008-09-17
Hi Dave,
Can you please share your binary of WinE with the patch applied?
I have been able to install Spore on WinE 1.1.4 although I use NO-CD patch for spore in order to get rid of Activation process. but the game is no as it should be :O , take a look at my screenshot at  [http://ubuntuforums.org/showthread.php?t=914196&page=2](http://ubuntuforums.org/showthread.php?t=914196&page=2)
do you think that this problem can be fixed using the patched wine?

Thanks

---

### Post by dave08 on 2008-09-18
The patch I applied was to enable a connection to the licensing server for the initial install... so this patch will be of no help to you. If you look on Wine AppDB and see if someone with similar issues has posted a patch you can install it as I have shown above.

Dave

---

