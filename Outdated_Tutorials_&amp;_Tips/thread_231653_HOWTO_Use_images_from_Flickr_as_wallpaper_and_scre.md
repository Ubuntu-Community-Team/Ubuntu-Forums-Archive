---
title: "HOWTO: Use images from Flickr as wallpaper and screensaver"
date: 2006-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by AThomsen on 2006-08-07
Hey there!

I experimented a little with setting up a job that would get images from Flickr and use them as wallpaper and in my screen saver. It works really well so I just thought I'd put up a little description of what I did.

Download the attached file and extract them where you place your programs/scripts.
Once you have done this make sure the perl script can be executed:
```
chmod +x download_from_flickr.pl
```

Very Good. The perl script uses an implementation of the Flickr api for perl. We need to install this. We'll use cpan for this. You can think of it as APT/Synaptic for Perl.
```
sudo cpan
```
Once you get to the cpan> prompt, type
```
install Flickr::API
```
It will probably ask you to install a lot of other things (dependencies to the Flickr API), so you better just select the default answer to these questions (just press enter).
Once installed, exit cpan by typing "exit".

Now we need to authorize the use of this little program in Flickr. By the way make sure you have a Flickr account and that you are logged in!
Once sure of that, run the program:
```
./download_from_flickr.pl
```
It will print out an URL. Copy that from the terminal and paste it in your browsers adress bar. Follow instructions on the screen to authorize the application.
If you did right, you should now have an authorization token!

Edit the program:
```
sudo gedit download_from_flickr.pl
```
Scroll though the comments (those starting with #) until you reach the config section. Find this line
```
my $auth_token = "";
```
and put your authorization token between the two "'s.

While you are here edit the line
```
my $root_temp_dir = "/home/YourName/pictures/";
```
to tell the program where to put the images we'll download from Flickr.

Now we're about to download some images! You'll have to find out what to download - take a look in the comments section of the program (you didn't close gedit did you?). You can search for images by tags, sets, groups and the user who put up the image. Once you know a little about how the program works you can close gedit ;) Don't forget to save the program first!

There's a nice group on Flickr where users can put images suited for wallpapers. It's called "Wallpaper group". To download the latest 60 images from this group, do this:
```
./download_from_flickr.pl -u public -max 60 -size o -g 40961104@N00 "Wallpaper group"
```
It can take a while as the "-size o" parameter specifies that we should download the images in the original format that they were once uploaded to Flickr with.

The funny number (40961104@N00) is the group-ID. I'm not sure what the best way to get this is. I do it this way: go to the main page of a group in Flickr. Hold the mouse over the RSS-feed link on the page and check the URL that is displayed in the status bar. Somewhere in the should be the group-id. If you want to download sets later on you'll need the set-id. For that you can use the same method.

The last parameter is the subdirectory where the images will be downloaded to. This subdirectory is created in the root-directory you specified when you edited the program file. Do not store any other files in these subdirectories as they will be deleted when you run the program!

Very good. Perhaps you would like to automatically change your wallpaper in Gnome? We'll use the included program for changing the wallpaper and create a cron job that schedules the program. Start by testing if the change_wallpaper program works. You'll need Python to run it:
```
sudo apt-get install python
```

We'll have to edit the program so it will know where to look for wallpapers:
```
gedit change_wallpaper.py
```
In the first line after the comments (Python also uses # for commenting out lines), put in the full path of where the wallpaper group was downloaded to.

Save the file and close gedit. 

Now run the program to test it:
```
./change_wallpaper.py
```
Check if you wallpaper has changed (if instead your carpet changed you did something very wrong along the way).

Now lets create the cron jobs. Cron jobs are used to schedule programs to run at certain times. We would like to download images from the Flickr Wallpaper group every day at 8pm and change the wallpaper every hour.

I heard somewhere that cron is not installed by default with Dapper so make sure it's installed:
```
sudo apt-get install cron
```

Edit the cron file (do not run this with sudo)
```
crontab -e
```
Put in these two lines at the button:
```

0 20 * * * FULLPATHTOPROGRAMS/download_from_flickr.pl -u public -max 60 -size o -g 40961104@N00 "Wallpaper group" >& /dev/null
0 * * * * python FULLPATHTOPROGRAMS/change_wallpaper.py >& /dev/null


```
Make sure you replace FULLPATHTOPROGRAMS with the full path to where the two programs are placed.

That's it! Now exit the crontab editor and wait :cool:

I also use the download_from_flickr program to get images for the GLSlideshow screensaver - it works very well too!

---

### Post by agentblueuk on 2007-05-28
The script appears to only download one or two images properly and the rest are coming down as in image from flicker that says the image is not availible

---

