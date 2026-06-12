---
title: "installing ndiswrapper and/or ndisinstaller"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by zeppelin222 on 2008-09-17
hi,
ive just gotten ubuntu, and I have a wireless network adapter from linksys, which doesnt have drivers that work with linux. via google and this forum ive figured out that i need to install ndiswrapper in order to get it to work. however, i am brand new to linux and am not very good at installing from tarballs. i kept getting errors and was very frustrated, and eventually found ndisinstaller, which has a graphical interface for ndiswrapper, which was a godsend. everything was working great until i got to the part where i had to pick out the inf file for it. I have the drivers saved in a folder, and when i navigated to that folder, it showed it as empty, and wasnt recognizing any of the files in there, even though about 4 of them are .inf files. So after a couple tries with that, i decided to go back to using ndiswrapper from terminal. i found this very nice page: [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo"), which explained why i was getting all those error messages when i was trying to install it earlier: i dont have build-essential and checkinstall and all those other packages i need. unfortunately, I can't use synaptic package manager to get the packages i need because i dont have an internet connection, which is what im trying to fix. a wired connection isnt an option. now im really really frustrated. is there any way i can install this without an internet connection, or get ndisinstaller to recognize my inf files?

---

### Post by wolfen69 on 2008-09-17
you can find the ndiswrapper.deb file (1 click install) [here]("http://archive.ubuntu.com/ubuntu/pool/main/n/").

to be specific, you need [this]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1ubuntu1_all.deb") one and [this]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb") one.

---

### Post by zeppelin222 on 2008-09-18
thank you. you have no idea how frustrated ive been.

---

### Post by misterhan on 2008-09-18
Zeppelin, if you get a chance can you post what you did to install it? I'm confused on this too trying to get my internet to work.

---

### Post by zeppelin222 on 2008-09-18
you download all the packages from the links listed above (im dualbooting windows, so i downloaded them in windows and saved them in a place both windows and ubuntu can access), and double click them. a window should open with information about the packages, and you click install, and let it do its thing. once its all installed, you basically can follow ndiswrapper's instructions on its website. i dont remember exactly what i did, but it involves going into terminal and navigating to the folder where you have your drivers, and using a command. i think its "ndiswrapper -i [driver].inf" (without the quotes or brackets) then theres another cammand to make sure it worked (i think it's "ndiswrapper -l") and then youre all set to go. for some reason network manager says im not connected to the internet but i really am, so go figure.

---

