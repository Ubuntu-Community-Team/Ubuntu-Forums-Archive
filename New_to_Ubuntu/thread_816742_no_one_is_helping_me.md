---
title: "no one is helping me???"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by leah1984 on 2008-06-03
ok so everytime i post a question i get alot of views but no one wants to help me? have i been labeled an idiot or something?? anyways im having trouble getting sound to come from the videos i have saved on a disk,and also videos i have downloaded from my cell phone.the vids i download from my digital camera work with sound but  none of my other ones have sound the video part is good just no sound,so  ilooke into the properties of  one of my cell phone vids and it said AMR codec  so i added something like that from the synaptics manager ,but still nothing? will someone please help me out here?:(

---

### Post by KingTermite on 2008-06-03
Is sound working at all? Or is it only failing for videos?

What about something like videos from online, like youtube?

When you got go system->preferences->sound what happens when you press the "test" buttons for each of the categories?

---

### Post by Lord Xeb on 2008-06-03
Well, this is the wrong way to go about it. Also, you need to be explanatory in your posts. Like this: "I cannot get sound to work on videos" or something along that line. Give them time, and they do not answer it here, go to general help. Beside that is were your post belongs. Or you can go to laptop & hardware, or desktop environment.

---

### Post by hyper_ch on 2008-06-03
> **leah1984 said:**
> ok so everytime i post a question i get alot of views but no one wants to help me? have i been labeled an idiot or something??
I just looked at your past issues and people have (tried to) help you.

Don't forget, everybody here is doing it volontarily.

---

### Post by Xiong Chiamiov on 2008-06-03
Agreed.  If you're getting views but not posts, it simply means that we don't know; we don't know everything, so we can't answer every question.

There are a few things to keep in mind when asking for help.
1.  **Use a good title.**  Avoid things like "lost pls help!!!" and "no one is helping me???" <-- ;)  Instead, say something that will tell us what your problem is so that we know whether or not we know enough about that area to read it.
2.  **Be descriptive.**  Rather than giving vague details like "it doesn't work" or "something like xxx", tell us *exactly* what error you got (if it's an error).
3.  **Take the time to write well.**  There are many here who to whom English is not their first language, so write in a manner that they can understand.  Punctuating properly and using the enter key more than you would be inclined to helps readability too.

---

### Post by SteveNorman on 2008-06-03
Do you-tube videos,,myspace etc give you sound?

Make sure your sound is not muted, there should be a speaker icon in the top right corner of you screen, make sure it is not muted,,and turn your sound all the way up and lets see what that does..

---

### Post by leah1984 on 2008-06-03
when i originally posted this i was explanatory in my post,and i thought i posted it in the right category multimedia and video??  well im trying to be as descriptive as possible ,sorry i do not know alot of the computer lingo but am trying my hardest to catch on,as this system was givin to me for free and cannot afford to purchase anything else.So all my other sound works fine,even videos from you tube.its only videos i have downloaded from my cell and vids i have saved on a disk.I also went into the sound in the system and the very last test had no sound at all but the rest worked fine,i believe the last test was sound capture and mine is on advanced linux sound architecture. and when i said no help i meant for my last post only!   and i realise this is all voluntary and am thankful to everyones help and patience.

---

### Post by mde123 on 2008-06-03
First, which program are you using to view the videos?
i would recommend mplayer.
But you must configure it (edit -> prefences) and select an video and audio output

---

### Post by leah1984 on 2008-06-03
i have VLC and totem

---

### Post by Samhain13 on 2008-06-03
> So all my other sound works fine,even videos from you tube.its only videos i have downloaded from my cell and vids i have saved on a disk.

It may be helpful if you can give the formats of the videos that you download from your cell and those in your disk. By "format", is it .avi, .mp4, .mpeg, etc.?

> I also went into the sound in the system and the very last test had no sound at all but the rest worked fine,i believe the last test was sound capture and mine is on advanced linux sound architecture.

Sound capture basically means recording from a microphone. So if you hit the test but don't talk into a mic, you won't get to hear a sound.

---

### Post by Xiong Chiamiov on 2008-06-03
Also, since some file extensions are merely container formats, if you open the files in VLC, go to view -> stream and media information -> advanced information and take a look at what it says the video and audio codecs are.

---

### Post by leah1984 on 2008-06-03
i checked the formats from my cell videos and i believe they are gpp is that a format? all my avi. files work fine.to find the format i would look into the properties right?

---

### Post by leah1984 on 2008-06-03
actually  they say 3gp.

---

### Post by SteveNorman on 2008-06-03
Read through this,,if no-one has a quicker fix this may help

[http://ubuntuforums.org/showthread.php?t=363073](http://ubuntuforums.org/showthread.php?t=363073)

---

### Post by Samhain13 on 2008-06-03
I had a feeling it was 3GP. I suggest you follow the advice given in SteveNorman's link. :)

I find it odd that your VLC doesn't play 3GP though.

---

### Post by SunnyRabbiera on 2008-06-03
> **leah1984 said:**
> actually  they say 3gp.

3gp is readable in totem, if the right codecs are installed.
I know I can get 3gp playing in my system, I have a sony walkman usb mp3 player that works with my compy.

---

### Post by SteveNorman on 2008-06-03
Whats the latest restricted driver package? lib etc..you should load that as well,,even though I thought vlc came with it. Can you play copyrighted  encrypted DVDs?

I think this is it
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

and 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

that is from
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by leah1984 on 2008-06-03
so i tryed your link steve Norman and did what it said and after im dome typing that all in it says couldnt find package mencoder.

---

### Post by leah1984 on 2008-06-03
how do i tell what the latest restricted driveer package is? ive typed the first code in and i got this :      
     => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[=============================================>] 226           --.--K/s             

00:32:18 (8.19 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

--00:32:18--  [http://wget/](http://wget/)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving wget... failed: Name or service not known.
--00:32:18--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Reusing existing connection to [www.medibuntu.org:80](www.medibuntu.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[=============================================>] 226           --.--K/s             

00:32:18 (11.40 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]


FINISHED --00:32:18--
Downloaded: 452 bytes in 2 files
owner@ubuntu1:~$

---

### Post by leah1984 on 2008-06-03
then i  type in the next code for the keyring and this comes up:
t-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_CA           
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_CA     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_CA     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [5590B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [5432B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7832B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Fetched 19.0kB in 1s (9812B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbeagle1 linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 libnss3-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 0s (4776B/s)           
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 137642 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_CA           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_CA     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_CA 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Reading package lists... Done
owner@ubuntu1:~$

---

### Post by leah1984 on 2008-06-03
then my update manager popped up with some updates in a red arrow so i downloaded the updates,should i have done that?? i thoughtr it waspart of the update from the commands i put in the terminal?

---

### Post by SunnyRabbiera on 2008-06-03
alright settle down, I know you are frustrated but please be patient.
if the apt-get readout tells you there is a duplicate entry in the sources list then type in sudo gedit /etc/apt/sources.list and remove the duplicated entries.
you might have goofed up somewhere.

> **leah1984 said:**
> then my update manager popped up with some updates in a red arrow so i downloaded the updates,should i have done that?? i thoughtr it waspart of the update from the commands i put in the terminal?
this is because you did a update of apt, dont worry you are fine.

---

### Post by leah1984 on 2008-06-03
LOL ok im sorry ,ok ill do that right now

---

### Post by leah1984 on 2008-06-03
alright a souces list popped up now how do i remove duplicates?

---

### Post by canthus13 on 2008-06-03
Well, if you used sudo gedit /etc/apt/sources.list to get the list, simply find the duplicate entries and delete them.  Once you do that, save the file and exit.

Before you save and exit, though, you might want to > sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak  just in case you remove something you shouldn't have.  That way, you've got a backup copy.

--Me

---

### Post by leah1984 on 2008-06-03
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

this is what was duplicated i deleted it then saved so am i ok now?? will my vids play?

---

### Post by leah1984 on 2008-06-03
do i still have to install mencoder?

---

### Post by leah1984 on 2008-06-03
oh wow so i checked my vids and there is deff. sound coming out but theyt sound like the chipmunks!!! haha  how do i fix?

---

### Post by nothingspecial on 2008-06-03
You could use ffmpeg to convert your 3gp videos.

```
sudo apt-get install ffmpeg
```

Then go to the folder your video is in. If it`s in the folder called videos-

```
cd videos
```

or if it`s on your desktop-

```
cd Desktop
```

Then

```
ffmpeg -i nameofyourvideo.3gp nameofyourvideo.avi
```

Play the avi file and you should be able to hear it.

---

### Post by leah1984 on 2008-06-03
so in totem the visual is gone but sound is normal ,in vlc visual is there and sounds like the chipmunks!?

---

### Post by leah1984 on 2008-06-03
but i have more than one vid that doesnt work ,will i have to do that for every one?

---

### Post by canthus13 on 2008-06-03
Simple answer - Yes.  Complex answer, you can write a script to automate the task, but it might not be worth the effort.  check out [http://linuxcommand.org]("http://linuxcommand.org") for a primer on the command line and bash scripting.

--Me

---

### Post by SteveNorman on 2008-06-03
Have you tried using real player?

---

### Post by SunnyRabbiera on 2008-06-03
> **SteveNorman said:**
> Have you tried using real player?

thats on the back of my mind too, as realplayer does work with 3gp.

---

### Post by leah1984 on 2008-06-04
well they seem to be working now but the sound on vlc sounds like chipmunks,and on totem the sound is normal but the visual is now gone? i will try other media players but i dont want 3 or 4 of the m on my computer ,only want 1 that will play all files or close too.

---

### Post by starcannon on 2008-06-04
Some things that may help

Enable these repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

install using synaptic package manager:

[LIST]
[*]ubuntu-restricted-extras
[*]lame
[*]w32codecs
[*]libdvdcss2
[*]libdvdread3
[/LIST]

Also if you could post a link to some of the files that your trying to play, you may have to upload them to igoogle or something, but if you can get a few of the formats for us to try out that would be very useful.

Hang in there, and if you've posted a question and get no response right away, give it a bump, just don't go nuts, every 12 hours is plenty, eventually you'll get an answer.

Welcome to Ubuntu, truly the friendliest community I have ever run across, just sometimes theres more questions than people available to answer them, its a bit like fishing sometimes, you just keep waving the bait though and eventually your expert will come along.

---

### Post by leah1984 on 2008-06-04
ok so i went into synaptic package manager,i have already the w32codecs and libdvdcss2 ,but was unable to find the others. i typed in the search box and nothing came up? 
also the files i am trying to play are personal videos of family.not sure i f i want to share them with  a perfect stranger? you know what i mean. anything else i can try?

---

### Post by Bradtek on 2008-06-05
> **leah1984 said:**
> the files i am trying to play are personal videos of family.not sure i f i want to share them with  a perfect stranger? 

Fair enough.
But you could always record something not so 
personal just for testing purposes.

---

### Post by leah1984 on 2008-06-05
i never thought of that,ill give it a try,and keep you posted> thanks, i will also try realplayer,do i find that in add remove apps? or synaptics?

---

### Post by leah1984 on 2008-06-05
how do i show you my video so you can help me??

---

