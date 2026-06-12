---
title: "HowTo: Create a background slideshow."
date: 2010-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by k3lt01 on 2010-05-10
[SIZE="5"]_HowTo: Create a background slideshow using what is already installed on your machine._[/SIZE]

**_What's the point of this tutorial?_**

This tutorial is it is here for those who wish to work with what is already installed on their system and wish to have a screen background that changes at predetermined intervals. **_It is for those who want to understand the already natively available AND installed system._** It has been tested on Ubuntu 10.04 Lucid Lynx which is the current LTS. I will not, because I don't have any earlier versions installed anymore, be testing this on anything prior to Ubuntu 10.04. As each new version is released I will test it and report any difficulties found. If you have difficulties please feel free to let me know what they are and we can work through them together. It is based on the script and setup for the background named "Cosmos" which comes pre-installed in Ubuntu 10.04.

**Please note: This is just 1 way of doing this, there are many more ways and formats possible. Choose what is the best for you. This tutorial isn't here to dictate to anyone what is the best method for you to use. Instead, as has already been stated, it is here for those who wish to work with what is already installed on their system. If you find something others can use you could create a Tutorial on it to help others. Please do not turn this tutorial into a "my way is the best way" discussion, instead treat it like the technical tutorial it is and leave discussion about other methods to other threads.**

Note: I do not know if this will work in Kubuntu, Xubuntu, or any other variant other than Ubuntu. IF you try this in anything other than Ubuntu 10.04 and it works please let us know so we can add the information to this thread and give you the credit for your hard work in testing this in an untested variant.

[TheSqueak has explained]("http://ubuntuforums.org/showpost.php?p=9285886&postcount=6") how to get this working in Kubuntu. Thanks TheSqueak

[Punkphysicist reports]("http://ubuntuforums.org/showpost.php?p=9972106&postcount=26") that it works in 10.10 (Maverick). Thanks Punkphysicist.

**Lets start**

**_1. What do we need to make a changing background?_**

You will need a Folder for your background, an XML file that tells your computer what pictures to use in what order and how long to use them for (it is below so feel free to copy and past this into a new Gedit file and sav it with a descriptive name like lotr.xml, you must put .xml after the name). You will also need at least 2 pictures (I use jpg format pictures because I know they work) preferably of a decent size so the image is crisp and clear on your screen.

**_2. Create a Folder._**

Now that you have the generic XML file from this thread and have chosen the pictures you want to use we need to create a folder to put everything in.

To do this go to Places > Home Folder and open your Home folder. When your Home folder opens go to File > Create Folder and click Create Folder. This will create a folder called "Untitled Folder" which you can call anything you want. I created my folder and called it lotr (i.e. Lord Of The Rings).

**_3. Setting up the folder._**

OK, now we have our folder we need to copy everything into it. Now you can either cut and paste or copy and paste. If you cut and paste you will actually move the files from where they are now to your new folder. If you copy and paste you will still have your original files PLUS  a copy in your new folder.

**_4. Setting up the Generic XML file._**

So far we have all the things we need and have them placed in their own folder but nothing will happen until we tell the Computer what to do with it. This is when we start doing this.

Open the Generic XML file with Gedit so we can modify it to suit our purpose.

The generic XML looks like this

```
<background>
&#8722;
<starttime>
<year>2009</year>
<month>08</month>
<day>04</day>
<hour>00</hour>
<minute>00</minute>
<second>00</second>
</starttime>
<!-- This animation will start at midnight. -->
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="YellowGreen"]yourpicturename1[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="YellowGreen"]yourpicturename1[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="RoyalBlue"]yourpicturename2[/COLOR].jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="RoyalBlue"]yourpicturename2[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="RoyalBlue"]yourpicturename2[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Magenta"]yourpicturename3[/COLOR].jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Magenta"]yourpicturename3[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Magenta"]yourpicturename3[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkSlateGray"]yourpicturename4[/COLOR].jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkSlateGray"]yourpicturename4[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkSlateGray"]yourpicturename4[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkGreen"]yourpicturename5[/COLOR].jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkGreen"]yourpicturename5[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="DarkGreen"]yourpicturename5[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Cyan"]yourpicturename6[/COLOR].jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Cyan"]yourpicturename6[/COLOR].jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="Cyan"]yourpicturename6[/COLOR].jpg</from>
<to>/usr/share/backgrounds/[COLOR="Red"]yourfoldername[/COLOR]/[COLOR="YellowGreen"]yourpicturename1[/COLOR].jpg</to>
</transition>
</background> 
```

Note: I have highlighted [COLOR="Red"]"yourfoldername" in Red[/COLOR] and [COLOR="YellowGreen"]"yourpicturename1" in YellowGreen[/COLOR] with each successive "yourpicturename(2-3-4-5-6)" in different colour for each number. There is an easy way in Gedit to change bulk entries to something else. So while you have it open in Gedit go to Search > Replace and click Replace, when the dialogue box comes up type in "yourfoldername" without the quotes in the Search for: entry box and then type the name of your own folder (in my case it was "lotr") in the Replace with: dialogue box. Now click "Replace All" and every instance of "yourfoldername" will be changed with the name of your folder (e.g. "lotr").

Now the next bit isn't as easy, sorry :-(. You will have to manually change each "yourpicturename" to the name of your chosen pictures. Why? did I hear you ask? Well basically because you will only have 3 entries with each name. Please take a look at my own "lotr.xml" to see what I mean.

Edit: I have made a slight change to make it a little easier with bulk changing the yourpicturename title. Instead of changing each one individually you can now use a bulk change to do 3 at a time. So in Gedit choose Search > Replace and type in yourpicturename1 and change it to the picture you want to start with, then go Search > Replace and type in yourpicturename2 and type in the name of the 2nd picture. Just keep doing this till you are finished. 

```
<background>
&#8722;
<starttime>
<year>2009</year>
<month>08</month>
<day>04</day>
<hour>00</hour>
<minute>00</minute>
<second>00</second>
</starttime>
<!-- This animation will start at midnight. -->
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Aragorn_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Aragorn_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Arwen_1024x768.jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Arwen_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Arwen_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Epic_1024x768.jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Epic_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Epic_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Frodo_1024x768.jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Frodo_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Frodo_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Gandalf_1024x768.jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Gandalf_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Gandalf_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Sam_1024x768.jpg</to>
</transition>
&#8722;
<static>
<duration>1795.0</duration>
<file>/usr/share/backgrounds/lotr/Sam_1024x768.jpg</file>
</static>
&#8722;
<transition>
<duration>5.0</duration>
<from>/usr/share/backgrounds/lotr/Sam_1024x768.jpg</from>
<to>/usr/share/backgrounds/lotr/Aragorn_1024x768.jpg</to>
</transition>
</background> 
```

Please make sure you note that Aragorn is the first 2 and the the last entry. The rest are all consecutive and replace 3 "yourpicturename" entries. You must do it this way so that the background cycles through the pictures.

EDIT:[yaaarrrgg]("http://ubuntuforums.org/member.php?u=49794") has [come up with script to create the xml file]("http://ubuntuforums.org/showpost.php?p=9633161&postcount=16").

EDIT: [bebopiiam]("http://ubuntuforums.org/member.php?u=1261494") has also developed [a script]("http://ubuntuforums.org/showpost.php?p=10568266&postcount=46") to do much of the work for you.

Now you have 3 methods to do it the Ubuntu way.

**_5. What does all the code mean?_**

For our purposes we only need to worry about the bits that actually deal with the pictures so in order of occurrence we have
<static> Means the picture that is currently on the screen,
<duration>1795.0</duration> How long will it stay for. This is in seconds so 1795.0 seconds is approximately 30 minutes. If you want a shorter "static" period just change it to the number of seconds you would like (e.g. 600 seconds is 10 minutes).
<file>/usr/share/backgrounds/lotr/Aragorn_1024x768.jpg</file> The location and name of the picture file.
</static> The picture currently on the screen.
&#8722;
<transition> This is when the pictures change.
<duration>5.0</duration> How long does the change take. I find it is best to leave this alone.
<from>/usr/share/backgrounds/lotr/Aragorn_1024x768.jpg</from> The location and name of the picture that was on the screen
<to>/usr/share/backgrounds/lotr/Arwen_1024x768.jpg</to> The location and nam of the picture that will be on the screen
</transition> End of transition cycle.
&#8722;
<static> The new picture on the screen
<duration>1795.0</duration> How long it will be there for.
<file>/usr/share/backgrounds/lotr/Arwen_1024x768.jpg</file> Name and location of the picture.
</static> The picture on the screen.

[B][U]
6. Finishing the setup[/U][/B]

Now that we have our folder, which includes the pictures and XML file, setup and we have modified the XML file to suit we need to put it in the right place so it can all work.

My advice is to copy and paste (not cut and paste)the folder and its contents to /usr/share/backgrounds. To do this we need to open a terminal so go to Applications > Accessories > Terminal and copy and paste this in.

```
sudo cp /home/YOURUSERNAME/PathToYourFolder /usr/share/backgrounds
``` changing YOURUSERNAME to your actual user name and PathToYourFolder to the actual folder name you gave when we first started. Tap enter, type in your password, and if everything goes well it should copy your folder over for you.

Now go to System > Preferences > Appearance and click appearance. When the Appearance Preferences dialogue box open click on the "Background" tab. Now we are in the "Background" tab look at the bottom and click on "Add". This will open another dialogue box. Navigate to the folder you have setup and you should see the picture files listed. If you don't see the XML file listed you will need to go to the bottom of the dialogue box and where it has "Images" and a drop down arrow change that to "All Files". You should now be able to select your XML file. Once you have done that you can select your new background image selection in the System > Preferences > Appearance dialogue.

Test it out and let us know how you go.

If you have any hints or suggestions regarding this format please feel free to make them and I will adjust this post accordingly.

---

### Post by bapoumba on 2010-05-11
T&T that is :)

---

### Post by k3lt01 on 2010-05-11
> **bapoumba said:**
> T&T that is :)Lol.

I have attached lotr. Note the pictures used are freely available, legal as well, from the original owners. I will add more as I make more, please feel free to share yours if they are suitable for a "family" audience.

---

### Post by x-shaney-x on 2010-05-12
I don't have time to try it for myself right but I will be doing in the next few days.
Just wanted to say that this is one of the clearest and easiest to follow howto's I have ever seen.

Step by step and everything explained very well (even exactly what each line of the xml means).

Nice :)

---

### Post by mhgsys on 2010-05-12
That's a whole lotta script you got there; 
This is the script I'm using for changing the background.



f.e I have a map called bcground located on my Desktop.
as you can see in the script. 

Save the script as any .sh you like to name it. 
Do a chmod a+x on the file, and run it with ./whateveryounamedthescript
.Or add it to startup applications,.if you want it to be started at boot.

 changing the sleep interval number at the bottom of the script will determine how long a background-picture is displayed
[SIZE="1"]
 note; I am not fully the creator of this script, a friend of mine just wanted to have a changing background, we downloaded multiple scripts, adjusted and mangled some code from other scripts we've found on the internet.
[/SIZE]

```
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/mhgsys/Desktop/bcground/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 8s
done

```

---

### Post by TheSqueak on 2010-05-12
> **k3lt01 said:**
> N.b. I do not know if this will work in Kubuntu, Xubuntu, or any othr variant other than Ubuntu.

For reference, the way to do this in Kubuntu is

[LIST]
[*]Right Click on the Desktop
[*]Select "Desktop Activity Settings"
[*]Change the "Type" dropdown to read "Slideshow"
[*]Select the Image folders you want to scan, and the time delay you want
[*]That's it
[/LIST]

---

### Post by k3lt01 on 2010-05-12
> **mhgsys said:**
> That's a whole lotta script you got there;I used and modified it to suit as it is the native script already used for Cosmos. I appreciate people trying different things and your script suits you (thanks for sharing btw :-) )but I like being able to work with native material first before I go further as I often find the native material is better suited to my purposes.

---

### Post by Shpongle on 2010-05-12
a program could be easily made to make the xml files with a gui so users could just select the files and set the time and dynamically create the xml . Im currently doing exams at the minute but I could have a stab at it in java or something when im finished them

---

### Post by k3lt01 on 2010-05-12
> **Shpongle said:**
> a program could be easily made to make the xml files with a gui so users could just select the files and set the time and dynamically create the xml . Im currently doing exams at the minute but I could have a stab at it in java or something when im finished them Or you could just save yourself the time and download 1 of the handful that are already available. You have, unfortunately, missed the point. If you want a GUI download 1 if you want to use a script off the net download 1, if you want to us the native setup and modify it for yourself and understand what the code means then feel free to use this. It is about choice after all.

btw, why are you posting in Ubuntu forums when you are "currently doing exams at the minute"?

---

### Post by Old Marcus on 2010-05-13
Desktop Drapes is still around for this sort of thing. No longer under development, but it's still around, and available in the repos.

---

### Post by k3lt01 on 2010-05-13
> **Old Marcus said:**
> Desktop Drapes is still around for this sort of thing. No longer under development, but it's still around, and available in the repos.Again people have missed the point, this tutorial is for those who want to understand the _already available _***_AND_***_ installed system_. No one has to download anything else nor do they have to understand bash scripting, instead they follow a relatively simple procedure and can do this countless times over to create many slide shows and have them all available with just a few clicks.

---

### Post by Rod J on 2010-05-23
Thanks **k3lt01** for your "How To" ... I just realized today that Lucid can do multiple wallpaper slide-shows (already available in a standard install, as you said) and I was looking for information on how to do this. Thanks again, very much appreciated.

---

### Post by k3lt01 on 2010-05-23
Your welcome RodJ.

---

### Post by ravenkwill on 2010-06-25
I, too, like to play with the systems already in place, so I'm trying your method - but it doesn't seem to work for me.  I'm using 10.04, create a new xml file with the correct addresses for the images.  But when I go into add the new background, I chose the xml file, and instead of it creating the slideshow, I get a blank image. It shows the correct connection to xml file, but states "Image missing."  I'm probably missing something obvious; I've double checked each of my image pathways, compared the xml file with the cosmos file, can't find anything wrong.

Any ideas?

And let me add my thanks - I understand your intent and applaud it!!

---

### Post by k3lt01 on 2010-06-25
ravenkwill, can you attach your xml, and some screenshots of your folder locations, to your next post so I can take a look at it for you? I'm no scripter I just learn by playing, it took me ages to work through this myself so I am happy to help anyone having difficulty with it.

I also figured out how to make it a screensaver, sometimes. So when I get that working flawlessly I will post another HowTo on that.

Thanks for your kind words, I appreciate it.

EDIT: Actually could you attached your new folder with all the files in it, if it isn't to big that is. Just compress it into a tar.gz file and attach it to your next post.

---

### Post by yaaarrrgg on 2010-07-25
Thanks for the explanation, this quick bash script should output the xml.  Change "/path/to/directory/" to point to your directory with the images (and the slide times if needed).

```

#!/bin/bash

echo "<background>"
echo "  <starttime>"
echo "    <year>2009</year>"
echo "    <month>08</month>"
echo "    <day>04</day>"
echo "    <hour>00</hour>"
echo "    <minute>00</minute>"
echo "    <second>00</second>"
echo "  </starttime>"

while read f
do
  if [[ -z "$first" ]] 
  then
    export first=$f
  else 
    echo "    <to>$f</to>"
    echo "  </transition>"
  fi
  
  echo "  <static>"
  echo "    <duration>500.0</duration>"
  echo "    <file>$f</file>"
  echo "  </static>"
  echo "  <transition>"
  echo "    <duration>5.0</duration>"
  echo "    <from>$f</from>"

done < <(find "/path/to/directory/" -type f )
    
echo "    <to>$first</to>"
echo "  </transition>"

echo "</background>"


```

---

### Post by k3lt01 on 2010-07-25
> **yaaarrrgg said:**
> Thanks for the explanation, this quick bash script should output the xml.  Change "/path/to/directory/" to point to your directory with the images (and the slide times if needed).Would you mind explaining your script? 

You say it "should output the xml", does this mean you haven't tested it?

If you have tested your script I'm happy to add it to the first post if you haven't I would ask you to do so so we know it works.

---

### Post by yaaarrrgg on 2010-07-25
Overall, I just had too many images, so wrote a bash loop to output the xml.  The script just does a "find" on the directory, and pipes the output into a while read loop.  Then, it adds each file in three places in the xml (to, static, and from).  The first and last images are special cases, since the first image ends up in the last transition.  Also, the first image will have no transition preceding it.

I say this should work, as far as I can tell, the xml output was the same as the example listed in the OP.  I'm running it as a test, and transition works, although I didn't see a fade yet.


For example, here's the output xml:

```
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/moon_patrol.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/moon_patrol.png</from>
    <to>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Pitfall! (1982) (Activision) (PAL)".png</to>
  </transition>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Pitfall! (1982) (Activision) (PAL)".png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Pitfall! (1982) (Activision) (PAL)".png</from>
    <to>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Frogger (1982) (Parker Bros) (PAL)".png</to>
  </transition>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Frogger (1982) (Parker Bros) (PAL)".png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Frogger (1982) (Parker Bros) (PAL)".png</from>
    <to>/home/username/Pictures/atari_2600/zaxxon.png</to>
  </transition>

... snip ...

  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Keystone Kapers (1983) (Activision) (PAL)".png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Keystone Kapers (1983) (Activision) (PAL)".png</from>
    <to>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Omega Race (1983) (CBS Electronics)".png</to>
  </transition>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Omega Race (1983) (CBS Electronics)".png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Omega Race (1983) (CBS Electronics)".png</from>
    <to>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Mouse Trap (1982) (Coleco)".png</to>
  </transition>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Mouse Trap (1982) (Coleco)".png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/Screenshot-Stella 3.0: "Mouse Trap (1982) (Coleco)".png</from>
    <to>/home/username/Pictures/atari_2600/reactor.png</to>
  </transition>
  <static>
    <duration>500.0</duration>
    <file>/home/username/Pictures/atari_2600/reactor.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/username/Pictures/atari_2600/reactor.png</from>
    <to>/home/username/Pictures/atari_2600/moon_patrol.png</to>
  </transition>
</background>


```

There's no need to link/change the OP IMO ... I'm just a lazy typer. :)

---

### Post by k3lt01 on 2010-07-25
Thanks for your input, I'll link to that script in the OP.

---

### Post by Rod J on 2010-08-12
> **ravenkwill said:**
> I, too, like to play with the systems already in place, so I'm trying your method - but it doesn't seem to work for me.  I'm using 10.04, create a new xml file with the correct addresses for the images.  But when I go into add the new background, I chose the xml file, and instead of it creating the slideshow, I get a blank image. It shows the correct connection to xml file, but states "Image missing."  I'm probably missing something obvious; I've double checked each of my image pathways, compared the xml file with the cosmos file, can't find anything wrong.

Any ideas?

And let me add my thanks - I understand your intent and applaud it!!

Hi ravenkwill,

I was having exactly the same problem as you with one of my compilations. I checked and re-checked the XML file, paths, etc and could find nothing wrong with it. :confused: I gave up on it until today when I loaded the XML file into the Firefox browser and it reported a parsing error ... I had unintentionally deleted a "<" tag on one line, changing "</from>" into "/from>". :oops: Easily fixed, and then the compilation performed perfectly!

So, it could just be some silly little syntax error in the XML, so easily missed by eye but Firefox picked it up.

---

### Post by k3lt01 on 2010-08-13
Hey Rod J, thanks for that. It is very difficult to know what may have happened to someone else's script unless it has happened to you so I really appreciate your input with this :D

Don't forget everyone if you would like to share your background slideshows you can attach them to your posts, if they are family friendly that is.

---

### Post by 101011010010 on 2010-08-27
Hello.
I've been wanting to try this out for a while, worked like a charm. Thank you.

---

### Post by Rod J on 2010-09-26
I question the need to copy the folder with the backgrounds to the /usr/share/backgrounds folder as detailed in step 6 of the tutorial. As an experiment I created a compilation in a new folder at the location I usually set them up (/home/rod/Pictures/Wallpaper), right mouse clicked on the desktop and pointed it to the xml file in the new folder and everything worked just fine from there. BTW, thanks yaaarrrgg for your script which certainly eases the creation of the xml file. 

So, I wonder if it's really necessary to copy them to the system location? There may be reasons for doing so (perhaps to make them available system-wide for other users?) but it would simplify the process by eliminating this step.

---

### Post by jcwx86 on 2010-10-03
> **yaaarrrgg said:**
> Thanks for the explanation, this quick bash script should output the xml.  Change "/path/to/directory/" to point to your directory with the images (and the slide times if needed).

Cheers, thanks for the script. You saved me a bit of work!

---

### Post by k3lt01 on 2010-10-03
RodJ, When I wrote this I did mention part of the intent was to see how the OEM system works. That is why the folders are copied to the locations they are copied to. If you want to change that for your instance you are totally free to do so as it is your system. This is written so people can see why the OEM is like it is.

---

### Post by Punkphysicist on 2010-10-14
Thanks **k3lt01**, this worked like a charm (in Ubuntu 10.10).

Also, how does one auto-generate an xml file using **yaaarrrgg**'s script?  

What I mean is I made a file using gedit and saved it as a file.sh (after changing /path/to/directory/), and then double clicked on the file and nothing happened.  I've never done this type of thing before so I think I'm missing one of the basic steps on how to actually use such a script.

Thanks

---

### Post by yaaarrrgg on 2010-10-14
If you are pasting it in a file, be sure the #! line is at the very beginning of the file, no whitespace before it.

You'll need to right click on the file, go to Properties and then Permissions.  It will need "execute" permissions (there should be a little check box to click.)

Or, if you prefer the command line, you can do something like:

```
chmod 755 /path/to/yourscript

```

where "/path/to/yourscript" is the name and location of your script.

This script will just print the xml out, so if you want to save it, you'll need to copy and paste, or redirect the output to a new xml file like:

```
/path/to/yourscipt > newfile.xml
```

---

### Post by k3lt01 on 2010-10-14
> **Punkphysicist said:**
> Thanks **k3lt01**, this worked like a charm (in Ubuntu 10.10).You are welcome. I have just done my working install of 10.10 so I haven't tried it yet so thanks for letting us know it works in 10.10. I will update the OP to show it works in Maverick

---

### Post by trukker on 2010-10-20
Or use CREBS

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)

---

### Post by k3lt01 on 2010-10-20
> **trukker said:**
> Or use CREBS

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)Or you could read the first post!

**_What's the point of this tutorial?_**

This tutorial is it is here for those who wish to work with what is already installed on their system and wish to have a screen background that changes at predetermined intervals. **_It is for those who want to understand the already natively available AND installed system._** It has been tested on Ubuntu 10.04 Lucid Lynx which is the current LTS. I will not, because I don't have any earlier versions installed anymore, be testing this on anything prior to Ubuntu 10.04. As each new version is released I will test it and report any difficulties found. If you have difficulties please feel free to let me know what they are and we can work through them together. It is based on the script and setup for the background named "Cosmos" which comes pre-installed in Ubuntu 10.04.

**Please note: This is just 1 way of doing this, there are many more ways and formats possible. Choose what is the best for you. This tutorial isn't here to dictate to anyone what is the best method for you to use. Instead, as has already been stated, it is here for those who wish to work with what is already installed on their system. If you find something others can use you could create a Tutorial on it to help others. Please do not turn this tutorial into a "my way is the best way" discussion, instead treat it like the technical tutorial it is and leave discussion about other methods to other threads.**

---

### Post by obfpen on 2010-10-21
> **k3lt01 said:**
> Or you could read the first post!

trukker may have been overly curt, but I think you've dismissed them a little unfairly.

In contrast to most of the programs for this particular feature, Create Background Slideshow (CreBS for short) isn't so different from the script you edited into the original post. It took a lot longer to type, but it still creates the same kind of XML file that your tutorial describes so well. In that sense, it is just as "native" as any bash script—it is still up to GNOME to do the wallpaper changing.

I didn't want to waste any resources on an extra program that would be constantly running in the background—not when GNOME already had the ability to change wallpapers on a schedule, given the right XML. And, like you, I tried creating my own XML files, based on the Cosmos example—first by hand, then with a little help from a Perl script. The trouble is, even when you understand the format, it's tedious and error prone, so I set about creating the UI that GNOME lacked. If I were a real programmer, I'd have made a patch for GNOME, creating a truly native solution, but I'm not, so I knocked something up in Python instead.

I'm not trying to turn this into a "my way is the best way" discussion, and I don't think trukker was either. I think they just reacted a little hastily to the generic thread title. Had it been, "How to create a background slideshow by hand", or, "Understand the GNOME background slideshow XML file", I doubt they'd have offered the suggestion. But to criticise someone for suggesting a simple, user-friendly method for creating a background slideshow on a thread called "HowTo: Create a background slideshow" seems just a little unfair to me.

A suggestion for an amendment: Rod J's suspicion is correct about step 6. You don't "need to put it in the right place so it can all work." The XML file and images can be anywhere readable; you just need the correct full path to each image in the XML file, and it'll work just fine.

---

### Post by k3lt01 on 2010-10-21
> **obfpen said:**
> trukker may have been overly curt, but I think you've dismissed them a little unfairly.I haven't dismissed anything. I am however trying to keep this thread on track, if that is a crime then so be it. I quoted part of the OP simply because it was absolutely obvious trukker did not read it all (or properly). As I said if people want to show a better (or easier) way then so be it, but at least do it in a thread where it can get its proper attention. This thread is not here to serve that purpose.

With regards to your suggestion, I'll pass on that and I am choosing to do this because this thread isn't about modifying file paths or anything like that it is just to show how the OEM system works.

BTW, nice work on the application :)

---

### Post by Punkphysicist on 2010-11-02
> **trukker said:**
> Or use CREBS

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)

Thank you trukker you're a lifesaver.  I tried to make a 2nd .xml slideshow with a large number of backgrounds and had a small error somewhere that I could not track down. With CreBS I was able to just make a fresh .xml in 2 minutes.

---

### Post by dcstar on 2010-11-05
> **Punkphysicist said:**
> Thank you trukker you're a lifesaver.  I tried to make a 2nd .xml slideshow with a large number of backgrounds and had a small error somewhere that I could not track down. With CreBS I was able to just make a fresh .xml in 2 minutes.

And there are other tools around that create essentially the same file that this thread has you do manually:

[http://gnome-look.org/content/show.php/GNOME+Slideshow+Background+XML+creator?content=132348](http://gnome-look.org/content/show.php/GNOME+Slideshow+Background+XML+creator?content=132348)

There is nothing wrong with understanding how this works **and** using something to set it up in a convenient manner.

---

### Post by Jack Brown on 2010-12-09
hi i used the yaaarrrgg bash script and it does output the xml entries.  
(after placing the file in usr/bin folder and enabling execute permission on the file.)

But i have lots of pictures and the terminal does not scroll all the way up to the top, even though i put 'unlimited' on the number of lines in the terminal options...

is there a way to transfer the output to a file?

EDIT: never mind, I closed the terminal and reopened it.  And it displays the whole output of the script.
Now to see if the xml works....

edit: Yeah! it works. Thanks K3lt01 and yaaarrrgg.  And yes simply pointing to the xml from Change Desktop Backgrounds / Appearance Preference window enables the slideshow, regardless of where your pictures are. (as long as they are specified correctly in the xml)  saves us from having to move around pictures to other folders and getting duplicates.

It can be observed that the duration (that was included with the yarg bash script) is 500 while the original is 1795.0.  Judging by how quickly the background changes, that number is probably in seconds, right...

cheers!

---

### Post by yaaarrrgg on 2010-12-09
Glad it worked.  Also, on linux you can always route the output of a command to a file using a ">" like:

command > file.xml

---

### Post by steinair on 2010-12-09
I made that script, it works great on Ubuntu10.10:
> 
#!/bin/bash
# Usage: ./slidepaper.sh folder_path duration_sec transition_time_sec
# for example: sudo ./slidepaper.sh /usr/share/backgrounds/wallpapers
# Make sure you have only images in this directory

echo "<background>
  <starttime>
    <year>`date +%Y`</year>
    <month>`date +%m`</month>
    <day>`date +%d`</day>
    <hour>`date +%H`</hour>
    <minute>`date +%M`</minute>
    <second>`date +%S`</second>
  </starttime>
<!-- This animation will start at `date`. -->" > $1/background-1.xml

j="";

if [[ $# -eq 1 ]];then
 duration="60.0";
 transtime="5.0";
elif [[ $# -eq 2 ]];then
 duration=$2;
 transtime="5.0";
else
 duration=$2;
 transtime=$3;
fi

for i in `ls -1 $1 | grep -v .xml`
do 
 if [[ $j != "" ]];then
  echo "  <static>
    <duration>$duration</duration>
    <file>$1/$j</file>
  </static>
  <transition>
    <duration>$transtime</duration>
    <from>$1/$j</from>
    <to>$1/$i</to>
  </transition>" >> $1/background-1.xml
 fi
j=$i
done

echo "</background>" >> $1/background-1.xml
echo "Created slideshow: $1/background-1.xml"
echo "to make it happen, change desktop background, add this file."


---

### Post by Jack Brown on 2010-12-10
> **yaaarrrgg said:**
> Glad it worked.  Also, on linux you can always route the output of a command to a file using a ">" like:

command > file.xml

good to know, thanks.

also, correction to my post above, the bash script was placed in the /home/yourusername/bin folder, for the command to be accessible from the terminal CLI. (after enabling execute permission)

---

### Post by bebopiiam on 2011-03-14
Now that I understand all of this, is it possible to set also the fit attributes (stretch, tile, etc) and the background color attribute in the XML?  I know -- you give us everything we want and we still whine for more :)

Thanks!

---

### Post by k3lt01 on 2011-03-14
> **bebopiiam said:**
> Now that I understand all of this, is it possible to set also the fit attributes (stretch, tile, etc) and the background color attribute in the XML?  I know -- you give us everything we want and we still whine for more :)

Thanks!I really don't know the answer to this question and while I don't want to dismiss it out of hand I haven't got the time at the moment to try to figure out if it can be done. I think you'll need to look for the file that controls global settings in appearance and see what it is like. Sorry I can't be of more help right now but someone else may have more knowledge on this aspect and may answer your question for you.

---

### Post by bebopiiam on 2011-03-15
> **k3lt01 said:**
> .... I think you'll need to look for the file that controls global settings in appearance and see what it is like....
Ok I've got that.  I did an strace on the files that are read/written by gnome-appearance-properties and it looks like the properties file is:~/.gnome2/backgrounds.xml.  A segment for setting a wallpaper slide show looks like:
  <wallpaper deleted="false">
    <name>Contest</name>
    <filename>/usr/share/backgrounds/contest/background-1.xml</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#2c2c00001e1e</pcolor>
    <scolor>#2c2c00001e1e</scolor>
  </wallpaper>
Are you saying I should add the options/pcolor/scolor values to the slideshow xmi file (in this instance background-1.xml)??

---

### Post by k3lt01 on 2011-03-15
I have tried a numerous times to reply to you but my net connection is slow as a wet week today.

You could try inserting those code lines into the xml file. I would try different positions within the xml until you get it to work, not that I am saying it will work but certainly give it a try.

I'm sorry I can't be of more assistance at the moment. Let us know how you go and if you have any more questions please ask and I will do my best to help out.

---

### Post by bebopiiam on 2011-03-16
> **k3lt01 said:**
> ...Let us know how you go and if you have any more questions please ask and I will do my best to help out...
Thank you.  I ended up creating a slideshow XML file using the XML format you already gave us and  then select it and the option values using the background tool.  This sets the options for the whole slide show  but thats adequate. 

Right now I'm trying to get the latest version (3.3) of openoffice installed.    3.2 seems to have problems with furagana text I created using OO on windows.

I have a little 60 line perl script that creates the XML that I'd be happy to publish somewhere if you think anyone would be interested.

I really appreciate your quick replies!  Thanks!

---

### Post by k3lt01 on 2011-03-16
You can attach your script in your next post of you wish and I will update the OP to let people know it's available.

I don't want to go to far off-track in tnis thread but I understand your desire to update OOo but if I may suggest you try out LO (Libre Office) which is the new Open Source version of what was Open Office. I think it will be available in 11.04 but if not you can add a [PPA to your sources.list]("http://www.omgubuntu.co.uk/2011/01/new-ppa-makes-installing-libreoffice-on-ubuntu-easy/") and use synaptic to install it.

---

### Post by bebopiiam on 2011-03-16
Here's that perl script.  To use it, just put it on your path and call it something that makes sense.  I call it MakeSlideshow.pl.  With no arguments it prints usage.  It requires an output directory where it expects to find the image files and you can optionally give it a time period for the image display

I've been copying the image directory to /usr/share/backgrounds, running the script and then using the Apperance Preferences applet to add the xml file to the backgrounds/slideshows.

By the way, I wasn't asking for help on OO -- just saying why I was moving on.  I installed LibreOffice 3.3 which is a fork of OO and that fixed my problem.  There was a thread on how to do that.

Again, thanks for the help.
==================
[COLOR=Red]#!/usr/local/bin/perl -w
# $Header: /home/sjs/bin/RCS/MakeSlideshow.pl,v 1.1 2011/03/16 15:51:24 sjs Exp $
use strict;
use Cwd 'abs_path';
use File::Basename 'basename';
...[/COLOR] 
**This script had bugs.  Please see the following post.**

---

### Post by bebopiiam on 2011-03-16
Sorry. Theres an error in that script.  This should be more better.
=================
#!/usr/local/bin/perl -w # $Header: /home/sjs/bin/RCS/MakeSlideshow.pl,v 1.2 2011/03/16 23:57:53 sjs Exp $
use strict;
use Cwd 'abs_path';
use File::Basename 'basename';

my $USAGE = "USAGE: " . basename($0) . " output_directory [display_time]
    Make a slideshow xml file for image (.png, .jpg and .bmp files) based on files found in output_directory.  Output file is named 'slideshow.xml'.
    Display time is optional and defaults to 5 minutes.  If input it is an
integer value for minutes.
";

my $OutputDirectory =  shift @ARGV || die $USAGE;
my $DisplayTime = shift @ARGV || 5;
-d $OutputDirectory || die $USAGE, "$OutputDirectory is not directory.\n";
-w $OutputDirectory || die $USAGE, "$OutputDirectory is not writable.\n";
die $USAGE, "Invalid time value: $DisplayTime\n" unless $DisplayTime =~ /^\d+$/;
die $USAGE if @ARGV;
$OutputDirectory = abs_path($OutputDirectory);

my @GraphicsFiles = grep -f && m{\.(png|jpg|bmp)$}, <$OutputDirectory/*>;
die $USAGE, "No graphic files found in $OutputDirectory\n" unless @GraphicsFiles;
print "Found ", scalar @GraphicsFiles, " graphics files.\n";

# Shuffel the graphics files.
foreach my $index (0..$#GraphicsFiles) {
    my $rand = int(rand($#GraphicsFiles));
    my $tmp = $GraphicsFiles[$index];
    $GraphicsFiles[$index] = $GraphicsFiles[$rand];
    $GraphicsFiles[$rand] = $tmp;
}
my $OutputFile = "$OutputDirectory/slideshow.xml";
print "Creating $OutputFile with $DisplayTime minute display time.\n";
open (F, "> $OutputFile") || die "Failed to open $OutputFile for write.\n";
my $Header = '<?xml version="1.0" encoding="utf-8"?>
<background>
  <starttime>
    <year>2010</year>
    <month>01</month>
    <day>01</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
';
print F $Header;
my $next_index = 1;
foreach my $index (0..$#GraphicsFiles) {
    my $this_file = $GraphicsFiles[$index];
    my $next_file = $GraphicsFiles[$next_index];
    $next_index = ($next_index == $#GraphicsFiles) ? 0 : $next_index + 1;
    print F "  <static>\n"
    , "    <duration>300.0</duration>\n"
    , "    <file>$this_file</file>\n"
    , "  </static>\n"
    , "  <transition type=\"overlay\">\n"
    , "    <duration>$DisplayTime</duration>\n"
    , "    <from>$this_file</from>\n"
    , "    <to>$next_file</to>\n"
    , "  </transition>\n";
}

print F "</background>\n";
close F;
exit 0;

---

### Post by k3lt01 on 2011-03-16
Thanks for that I'll link to the new post in the OP now. Just so people don't get confused and choose the wrong script it may be an idea if you edit the previous post. Also, it doesn't worry me cause the script isn't very big, you may find people requesting you to put things in code boxes in other threads. Code boxes help to make the post smaller and more manageable to read.

---

### Post by bebopiiam on 2011-03-17
> **k3lt01 said:**
> Thanks for that I'll link to the new post in the OP now. Just so people don't get confused and choose the wrong script it may be an idea if you edit the previous post. Also, it doesn't worry me cause the script isn't very big, you may find people requesting you to put things in code boxes in other threads. Code boxes help to make the post smaller and more manageable to read.
Thanks for the advice.  I'm still new here...

---

