---
title: "HOWTO Migrate ratings from WMP to Songbird"
date: 2010-01-25
forum: Outdated Tutorials &amp; Tips
---

### Post by zyberwoof on 2010-01-25
Those migrating from Windows to Ubuntu or any Linux OS has probably noticed difficulty keeping the ratings you may have given songs Windows Media Player.  Since no Linux apps that I have found do this, I have written a small utility to do this.

Before attempting this, please **back up your music**.  I have just written this, and am sharing it for the first time.  It's good practice regardless.  But if for some reason this utility eats your MP3, you will have a backup.

[SIZE="5"]Step 1: Download and Apt[/SIZE]
To install this, you will need my [source code]("http://downloads.sourceforge.net/project/id3rating/Full%20download/id3rating_latest.tar.gz?use_mirror=hivelocity"), id3lib, and the gcc compiling environment.
```
cd
wget http://downloads.sourceforge.net/project/id3rating/Full%20download/id3rating_latest.tar.gz?use_mirror=hivelocity
sudo apt-get install libid3-dev build-essential
```

[SIZE="5"]Step 2: Extract, Compile, and Install[/SIZE]
This will install id3rating to your system.
```
tar xzvf id3rating_latest.tar.gz
cd id3rating_*
make
sudo make install
```

[SIZE="5"]Step 3: Migrate[/SIZE]
*NOTE: I highly recommend that you **backup your music** before doing any of this.  While it worked fine on my system, it is probable that there are MANY bugs for me to iron out of the id3rating utility.*
To migrate the rating on one song, just do
```
id3migrate MySong.mp3
```
To migrate the ratings of all of the MP3's in a folder and it's subfolders, you would use:
```
wmp_to_songbird.sh /path/to/my/music
```

[SIZE="5"]Uninstall/removal[/SIZE]
This simply requires deleting the id3rating files.
```
cd
rm -r id3rating*
sudo rm /usr/bin/id3rating
sudo rm /usr/bin/wmp_to_songbird.sh
```
Also, if you would like, you may uninstall build-essential and id3lib at any time of you don't want them.
```
sudo apt-get remove libid3-dev build-essential
```

[SIZE="5"]NOTES[/SIZE]
[LIST]
[*]Once again, I can't stress this enough.  **Back up your music** before using this.  It's good practice anyways, but I can't make any guarantees.  
[*]While this utility worked fine on my system (Ubuntu 9.10 x64) I'm sure there are many bugs to find.  Please post here or on [SourceForge ]("https://sourceforge.net/projects/id3rating/forums/forum/1080277")when you find one.
[*]While the id3rating utility I wrote only works going from WMP to Songbird, it shouldn't be too difficult to make it work for other music players assuming they pull rating data from the ID3 tag.  That being said, unless someone requests it, I'm only planning on adding functionality as I need it.  So If you'd like something added, ask.
[*]This is my first time writing a HowTo or sharing my code.  Friendly critiques are encouraged.
[/LIST]

---

