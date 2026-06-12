---
title: "How to make a custom GDM Theme."
date: 2007-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by exploder on 2007-09-02
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

I am currently using LinuxMint but this will work in any version of Linux.

---

### Post by Takagami on 2008-01-28
If you alter the GdmGreeterTheme.desktop file to include your personal information about the theme it will show up when you "install" it. It's in the directory you get after extraction. If there isn't one then you can create one from scratch using the "template" below:

> 
# This is not really a .desktop file like the rest, but it's useful to treat
# it as such

[GdmGreeterTheme]
Greeter=theme.xml
Name=Replace with theme name
Description=Replace with theme description
Author=Replace with Author Name
Screenshot=previewt.jpg
Copyright=Replace with copyright infor if wanted


Just save the file as GdmGreeterTheme.desktop, in the same directory as the images, and there you have it. Don't forget to name the directory with the theme name so when it's re-compressed... you know the rest.

---

### Post by exploder on 2008-01-28
Takagami,you are right! I submitted this in September of last year! I can not believe it finally showed up!

Here is a more revised tutorial.

Find an existing GDM Theme that you think would work with the artwork you want to use. Download and extract the theme and replace the background and screenshot images with what you want to use. A GDM theme that is made with .jpg files will be smaller in size. The screenshot can be the same as the background until you have the GDM near complete. (The screen capture will produce the proper image.)

Change the name of the folder and the .xml file inside the folder to the name you want for the theme. Make the GDMGreeterTheme.desktop file executable, if it is not already. Display the GDMGreeterTheme.desktop files contents and edit the file so it reflects the theme you are making and save the file.

Right click on the folder and choose "Create Archive". Now you can install the GDM theme so you will be able to do the screen capture for the final "screenshot" in the folder. You will need to install xnest from the repo's to do the screen capture.

Delete the archive you made because you will be creating another one with the same name once you have the screenshot.

Here is the tricky part! Open Gimp, File, Acquire, Screenshot. Remove the check for "include window decoration" and set the delay for 10 seconds.

Open a terminal and type gdmflexiserver --xnest. Click on "Snap' in the screenshot dialog and then press "Enter" to execute the command for xnest. The GDM should appear in a window. Place your curser on the window and when it changes to a + , click your mouse. Save the screen capture as your "screenshot.jpg" in your theme's folder. (Save a copy to scale if you want to post it on gnome-look.)

Make a new archive from your theme folder and you are done! You can re-install the GDM theme on your machine to make sure everything is how you want it.

The whole process usually takes about 15 minutes once you get used to it.

---

### Post by cincinnatus13 on 2008-02-13
Bump for a slight problem. When I go to get the screenshot, I'm getting a regular Debian screen instead of the picture I want to use. I have the theme archived and everything right but it won't work for some reason.
Edit: Nevermind, everything worked as well as it should.
If you don't mind, I'm gonna elaborate on some things for the newer users (like myself) so hopefully it'll make more sense.

To make the gdmgreetertheme.desktop file executable, go to properties and access it under permissions. Check the box saying "Make executable."
Code: Sudo apt-get install xnest
I believe that is the code for getting xnest. If not, someone please correct it.
When you enter in the code for the last part (gdmflexiserver --xnest) it will pop up with a window that has the gnome desktop manager in it and it will look NOTHING like your theme. That's just the way it happens. Just trust the guide and put it as your screenshot.jpg.
Set it all as theme and that's it. Enjoy your nice new theme custom tailored to your tastes. :)
Thanks exploder and Takagami. Very nice write up and hopefully everybody will be able to do this themselves.

---

### Post by vginov on 2009-02-20
Can anyone give me the step by step to create a custom theme for Ubuntu?

I would like to create one with a good graphics. If anyone give me the steps to create i will do it for sure. 

I would like to customize 

1. Controls 

2. Colours 

3. Window Border

4. Icons 

5. Pointers 

Your help will be a great thing 

I have seen many icon sets but I would like to create one by myself 

thanks in advance

---

### Post by binbash on 2009-02-21
Anyone knows a deeper guide?

---

### Post by octoberdan on 2009-03-02
> **binbash said:**
> Anyone knows a deeper guide?
Perhaps live.gnome.org's wiki page on the subject will provide further insight? [http://live.gnome.org/GnomeArt/Tutorials/GdmThemes](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes)

---

### Post by exploder on 2009-03-02
Nice link octoberdan! I did a lot of searching to come up with the "How To" I posted here. The link you provided has more complete information and many will appreciate this. What I posted was a simple way to personalize gdm and to inspire people to create more complete artwork for their systems and to share it with others.

---

### Post by dipinkrishna on 2009-06-11
See this post for [HOWTO create your own GDM Themes]("http://linuxandmicrocontrollertips.blogspot.com/2009/06/howto-create-your-own-gdm-themes.html") **[http://linuxandmicrocontrollertips.blogspot.com/2009/06/howto-create-your-own-gdm-themes.html](http://linuxandmicrocontrollertips.blogspot.com/2009/06/howto-create-your-own-gdm-themes.html)**

---

