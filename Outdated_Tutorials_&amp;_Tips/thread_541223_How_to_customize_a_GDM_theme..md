---
title: "How to customize a GDM theme."
date: 2007-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by exploder on 2007-09-02
This "How To" will work in any version of Linux. I am using LinuxMint at the moment. I wanted to share this with the Ubuntu Community because of all the help and great "How To's" the community has given me. 

_**How To Customize A GDM Theme**_

I used this image make my GDM screen [http://www.divshare.com/download/1642991-d6c](http://www.divshare.com/download/1642991-d6c) You can use any image you like.

1) I downloaded the GNU-Linux GDM theme from [www.gnome-look.org](www.gnome-look.org)

2) Right click on the tar.gz file and extract it.

3) Overwrite the background.png and the screenshot.png with the image of your choice.

4) Delete the original tar.gz, right click on the folder you have modified and select "create archive" ( make sure you archive it as as a tar.gz

5) Now just go into "Control Center", "Login Window". "Local tab" and add your new GDM screen.

You can do this with any GDM screen and image you like. I chose the GNU-Linux GDM because it worked well with the image I chose.

Here is how to change the Gnome splash to match. I used the same image so everything would match.

1) Open up your image in the Gimp and resize it to your liking. ( I tried a few different sizes before I was satisfied with the result.)

2) Save the image as a .png and name it cassandra-gnome-splash.png

3) Open the terminal and type sudo nautilus and go to /usr/share/pixmaps/splash

4) Change the name of the original cassandea-gnome-splash.png to preserve it in case you ever decide you want to use it again.

5) Place your new splash in the folder and close nautilus. Finished!

I have not figured out how to rename the GDM Theme yet but who looks at that once it is set up anyways. I will figure that out sometime. I hope this helps out some of you that are wanting updated artwork. I want to thank verdegal37 for the awesome artwork that inspired me to try this in the first place! verdegal37 has taken artwork for LinuxMint to a whole new level!

Enjoy!

Again many thanks to the Ubuntu Community for all of the help and inspiration you have given me!

---

