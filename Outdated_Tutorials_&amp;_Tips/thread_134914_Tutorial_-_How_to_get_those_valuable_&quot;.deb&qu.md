---
title: "Tutorial - How to get those valuable &quot;.deb&quot; Program Files &amp; Back Them Up"
date: 2006-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by dvarsam on 2006-02-22
_Tutorial - How to get those valuable ".deb" Files & Back Them Up_:


_For Ubuntu 5.10_:


_Story_:
I was once a Windows boy & Windows were always creating trouble with Viruses, Spyware & the rest paraphernalia...
Most viruses could be removed, however there were some that could NOT be removed, NOT even if you could use the BEST Antivirus or other program (cousin) in the market.

The ONLY (but BEST) solution was ALWAYS the (unavoidable) Format of my PC Machine.
I would always have to Re-install Windows & then Re-install all the Rest (but required) drivers & programs to make my machine look like "brand" new.

So, in my Windows (ugly) world, whenever I would download Drivers, I would save them in a Driver Folder for a later (or future) use (the mentioned ugly Re-Format Windows need...).

In the Past, I have posted articles on the "Synaptic Package Manager" & how NOT good it works.

I will NOT talk a lot about this, but you could read my Articles on the "The Beginner Community" Forum (articles: 129303, 132252, 132795, 133603).

_Note_:
I am still a Beginner in this Ubuntu OS, but that does NOT mean that I can NOT share what I have learned with you guys.

Basically I DESPERATELY needed to Backup the ".deb" files of programs I downloaded in my Ubuntu Computer.
Since I was scared that Windows related problems (Format & stuff) could (possibly) be needed sometime in my Ubuntu, I wanted to have a Backup of the Ubuntu Programs I downloaded & Installed from the Internet.

For me, it seemed "crazy" that people were relying on the "Synaptic Package Manager" or "Automatix"
to do the Installs & to NOT have the power themselves to perform installs.

However I STILL needed to Backup the Programs I downloaded from the Internet (as I mentioned before), in the case I had to Format my Ubunty...

It would be frustrating if I had to download again & again the SAME programs whenever I had to Format my Hard Drive's Ubuntu Partition.

At the same time I realized that Programs in the Linux World are NOT a single File (like Windows)!
Programs in the Linux World have what its called "Dependency" Files (or programs).

And that only made things more complicated...

What it really meant was that, if I downloaded & backed up (for example) Adobe's (well-known) Acrobat Reader program, if I tried to install it manually (myself), the program could REQUIRE (in order to work), some other programs (as prerequisites).

Then I would have to "Search" for those programs / dependencies (one by one) which could REQUIRE in order to work other prerequisites...

_Note_:
I have personally installed programs (in my Ubuntu), that required 18 prerequisites in order to work!

The story does NOT end here, because then the install order / procedure for installing these prerequisites were NOT known or posted anywhere...

_Example_:
Let us assume that Adobe Acrobat Reader  (program: "acroread_7.0.1-0.0.ubuntu1_i386.deb") Required the Below program as prerequisites to install:

a. "aalib1"
b. "jackd"
c. "libdirectfb-0.9-22"
d. "libfaad2-0"
e. "libggi2"
f. "libgii0"
g. "libgii0-target-x"
h. "libjack0.80.0-0"
i. "liblame0"
j. "libmad0"
k. "libpolyp0"
l. "libpostproc0"
m. "libpostproc0"
n. "libsvga1"
o. "libungif4g"
p. "libxvidcore4"
q. "mplayer-386"
r. "xmms" 

Can you tell me on which EXACT order you have to install the above programs to finally make the "Adobe Acrobat's Reader" to install?

Do NOT in any way assume, that you can start installing them, one by one, starting from the top to bottom...

	_Note_:
	The "Adobe's Acrobat Reader" program is just used as an Example. It is not 
        hard to install, nor does it have as many dependency files. However I needed 
        to use a famous program as Adobe's Reader for the sake of my example.

_Back to our Example_:

1. When you attempt to install the program (or dependency) "a", it REQUESTS from 
    you, that you FIRST must install program "d".

2. Then you try to install program "d", but it REQUESTS from you, that you FIRST 
    must install programs (or dependencies) "f" & "g".

3.  Then you probably wonder, which of the above 2 ("f" & "g"), you should try to 
     install first. And you start with "f", which REQUESTS that you FIRST must install 
     programs (or dependencies) "r", "n" &  "k".

....And it goes on & on...

_Question_:
Are you sure, you would still want to perform the installation of the "Adobe's Acrobat Reader" program yourself, if it might be so complicated?

To manually perform a "Search" & manually download ALL those 18 prerequisites programs (or dependencies) while at the same time NOT really being sure that you downloaded the correct ones, is NOT a good idea.
At the same time your problems are NOT finished – they have just started...
Then (assuming that you downloaded the correct file names), to manually install them by yourself (one by one), & trying to find the correct combination (or order) to install them is NOT the BEST way...


You would have to start taking "headache pills" or become an "alcoholic" or worse "cokaine" addict!!!

And in the end you will finally ABANDON Ubuntu...


Now, this is where "Synaptic Package Manager" comes in.

You tell it what program you want to download & "Synaptic":

1. Finds automatically ALL the dependencies you NEED to download,
2. Downloads the program & its dependencies you need to make it work, & finally
3. Installs everything & you are ready to start working with your Program!

_Outcome_:
You can NOT get rid of the "Synaptic Package Manager" program!
In fact, you NEED it more than it needs you!

But where is your BACKUP?

If you rely on somebody else to do everything (e.g. the "Synaptic Package Manager"), then how can you perform any BACKUP.

So, then ALL the wisdom (Forum) guys come in & resolve my "posted worried FORUM articles" only to say that there is a folder where "Synaptic Package Manager" downloads ALL the Dependencies & programs I want to install...

That is great you might say, go & BACKUP that Folder....

Well if you go & see by yourselves inside that Folder, you will find that its contents are SO many, you'll want to "dive" in an empty swimming pool if NOT from a cliff!

That folder "/var/cache/apt/archives" (they suggested), had hundreds (if NOT thousands) of files, programs or dependencies.

How can YOU locate your "Adobe's Acrobat Reader" single program file & its 18 dependency files, so that you can Back them Up in a Folder say "Adobe Acrobat Reader Program & Dependencies"?

Don't suggest the "Search" method, cause typing those file's names (listed above) in a "Search" box, will FORCE you to start taking those "headache pills" or drink "alcohol" or worse start the "cokaine" !!!

So it is like: searching for a needle in a stack of hay....


So YA want to Backup your Downloaded Programs (and Dependencies) Neat & Tidy?

_This is How to DO IT_:

_Note_:
The following way, does NOT remove the program "Synaptic Package Manager" out of the picture.
It just uses it to make your Backup (or locate ".deb" files you might be looking for) & at the same time uses it to install all your programs needed.

_Part 1 – Making the Backup_:

1. Launch the program "Synaptic Package Manager"
    (from the Menu, select "System\Administration\Synaptic Package Manager"

2. In the box that comes up, type your User's "password" to get "Root" Rights & 
    Priviledges (Administrator Rights & Priviledges)

3. From the Menu, select "Settings\Preferrences".

4. Click on the Tab named "Files" & click on the button named "Delete Cached 
    Packaged Files".

5. Click on the button named "OK", to close that window.

    _Note_:
    By clicking on that button, basically you Told Ubuntu, to go inside that 
    "/var/cache/apt/archives" folder & DELETE all packages.
    Now don't get a heart attack here. Nothing damaged your Ubuntu.
    If you have performed a clean install to your system, all those packages (found 
    inside there) were installed from your Ubuntu's Install CD, so if you want 
    anything you can go & find it inside your Ubuntu's Install CD (look inside the 
    "/pool/main" folder to find the packages in alphabetical order).
    So, no harm, everything is neat...
    If you do NOT believe that ALL Packages were deleted, go check yourself that 
    the "/var/cache/apt/archives" Folder, contains now only 1 file & 1 folder – the 
    rest were deleted.
    If NOT, go & press that "Delete Cached Packaged Files" button again.

6. From the Menu, select "Settings\Repositories".

7. Select the first line in the list, named "CD Ubuntu 5.10 - Breezy Badger" & click 
    on the button named "Remove".

8. Click on the button named "OK" & then on the button named "Yes".

    _Note_:
    Basically what we did here, was to Remove the Ubuntu's Install CD from the 
    Repositories 
    "Synaptic" would go to Search before going & downloading programs (that 
    already existed locally).
    Since many Packages are lying inside your Ubuntu's Install CD, if they are the 
    latest version, your Ubuntu goes to search the CD for installing them (instead of 
    downloading from the Internet).
    And since those files are inside the CD, they are NOT copied inside 
    "/var/cache/apt/archives" (the drop place for everything that is downloaded in 
    your Ubuntu PC).
    So, if you want a FULL Backup of your program, you have to disable the use of 
    the Ubuntu Install CD. (or you will end up backing up half you the stuff needed).

9. On the Standard Toolbar, click on the button named "Reload", to Update your 
    Repositories.

    _Note 1_:
    The "Reload" button actually Updates your  Repositories according to your 
    "sources.list" File.
    If you have performed a clean install & have NOT tampered your "sources.list" 
    File, you will notice on your "Status Bar", that the Packages available for 
    installation from the Ubuntu Community are "4.092 packages listed – 1.033 
    installed" (if you have Ubuntu 5.10 installed).
    If you had tampered your "sources.list" File, you could get  on your "Status Bar", 
    "17.824 packages listed – 1.033 installed", if not more...
    That means that thousands of programs (authenticated or not) are available for 
    you to install through the "Synaptic Package Manager" program.

    _Note 2_:
    This Tutorial's main objective is NOT to teach you how to MAKE available to your 
    "Synaptic Package Manager's" MORE program packages, but to teach you How 
    to Backup downloaded packages (or programs).
    Look at a different Tutorial for this (I currently have not made one yet, but 
    probably some other person has – take a look at the Ubuntu's "Customization 
    Tips & Tricks" Page & hopefully you will find one).

10. Since we are looking to install the  Adobe's (well-known) Acrobat Reader 
      program, on the Standard Toolbar, click on the button named "Search", to tell 
      "Synaptic" to look for the Acrobat Reader program & its dependency files.

11. Type "acrobat" & see what you will get. On the right-side of the window you 
      will find a list of packages found according to the "Search" you performed. 
      Search through that list & take a look at the programs found.

12. Select the First program on that list, which is  "acroread" & read through the 
      description provided below.

      _Note_:
      Usually the description helps you to verify if that is what you are looking for. In 
      our case, YES, this is the program we are looking for.

13. Right-click on the box, to the left of the name of our program "acroread" & 
      select  "Mark for installation"

14. A new window will come up & list the Program that is going to be downloaded 
      & its dependency files (if any). If our case there are two dependency files listed 
      (& needed to install):

     a. "gcc-3.3-base"
     b. "libstdc++5"

     _Note 1_:
     Previously I said that it was 18 dependency files.
     That was just used just to point out a dependency example – NOT the case for 
     the program "Adobe Acrobat Reader".
     In fact, the above dependency files are REQUIRED to install the program 
     "mozilla-mplayer" plugin to your Mozilla-Firefox Internet Browser.
     You can (sometimes) click on the arrows to expand or retract the dependency 
     files lists.

     _Note 2_:
     Sometimes, there are programs that YOU are trying to install that are "Not 
     Authenticated". In such a case, you install them at your own risk. So be careful 
     with what you install. 

15. Click on the button named "Mark", to mark the program & its dependency files 
      that you want to install.

     _Note_:
     The box, to the left of the name of our program "acroread", should now 
     (instead of empty), have a yellow arrow pointing into it. If that is the case, 
     move to step 16. If NOT repeat steps 13-15.

16. On the Standard Toolbar, click on the button named "Apply".

17. On the Summary window that comes up, click on the button named "Download 
      package files only"
      We basically want to download the packages but do NOT install them yet.

      _Note_:
      I have personally noticed cases, where if you went & installed a program, 
      some parameters would change on the program files used.
      So, if your Backup was taken after the installation, that Backup could NOT be 
      used to perform this SAME installation (in the future) of the SAME program  
      (cause some parameters were already tampered, when you decided to 
      Backup).
      The chance of this to happen is very rare, but why risk it?
      So, ALWAYS Backup before you install !

18. Click on the button named "Apply" & the download process should start.
      Three files should start to Download (the program & the 2 dependency files).

19. When the download is finished, go visit the "/var/cache/apt/archives" folder & 
      manually perform a copy&paste your files to your Desktop or anywhere you 
      would like – as this is your Backup.

      _Note_:
      Sometime these files you download have a "lock" on their icons. That means, 
      that there might be restrictions to these file's - "read/write/execute" 
       Permission Restrictions.
      To find out how to remove these restrictions, read a Tutorial on how to use the 
      "chmod" or "chown" 
      commands. Again, look at the Ubuntu's "Customization Tips & Tricks" Page & 
      hopefully you will find one).

Now you can go ahead & install the "Adobe Acrobat Reader" program.


_Part 2 – Installing your Software_:

1. On the Standard Toolbar, click on the button named "Apply". (previous step 16)

2. On the Summary window that comes up, de-select (remove the tick) on the 
    button named "Download package files only"
     This Time, we want to download & Install the Packages.

     _Note_:
     You will probably wonder, why download again?
     We are NOT! If your original copies of the program "Adobe Acrobat Reader" & 
     its dependency files are still lying inside the folder "/var/cache/apt/archives", 
     "Synaptic" is NOT going to download the program again, unless there is a 
      NEWER version lying out in the Internet's Repositories. 
     If a NEWER version is found, you will see stuff downloading in your Computer. 
     So first you will immediately find out & second you can then go & Backup the 
     NEWER files...

3. Click on the button named "Apply" & the Download process should start.
    Three files should start to Download (the program & the 2 dependency files). 
    However the "Synaptic" will soon realize that the LATEST program's version are 
    lying inside your "/var/cache/apt/archives" folder, so there is NO need to 
    re-download.
    Then the "Install Software" process will start. 

4. A "changes applied" windows should come up. Click on the button named 
    "close".

Congratulations, your "Adobe Acrobat Reader" has been installed successfully!

To verify that it has installed successfully, notice that now the box, to the left of the name of our program "acroread", is filled in green color meaning that everything is now OK.

Close the program "Synaptic Package Manager" (from the Menu, select  "File\Quit").

To run your program "Adobe Acrobat Reader", from the menu select "Applications\Office\Adobe Reader".


_Conclusion_:
You made your Backup & whenever you want to Install a program to your Ubuntu, just copy&paste the program & its dependency files inside the folder "/var/cache/apt/archives", and let "Synaptic Package Manager" do the rest.

_Note_:
Inside the Forums, I very often see people asking where can they get a ".deb" file for a program to install in their computer.
At the same time, they have located a ".tar.gz" program file to install.

".tar.gz" program files, are really complicated to install, and they are almost impossible to install if you are a Beginner (like me).
In fact, let me say that you have to be a PRO (or really lucky) to be able to install a ".tar.gz" program file in your Ubuntu computer (with NO hassle & problems).

Finally, if you are looking to find a ".deb" file for a program to install in your computer, why don't you download it from "Synaptic", with the method you just learned. 

And if you want to learn how to manually install a ".deb" file in your Ubuntu, you will soon find a nice Tutorial inside the Ubuntu's "Customization Tips & Tricks" Page.


Have Fun !!!


P.S. 1> Sorry for my bad grammar syntax (& repetitions), but I have spent more 
            than 6 hours to create this...
            ... hope it is helpful to you.

P.S.2> I would appreciate if somebody has something to Add that corrects me if I 
           have performed a mistake.
           
           PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
           because people that want to read a Tutorial, end up reading 
           comments of NO Educational Importance.
           Thanks !!!

---

### Post by jr.gotti on 2006-02-26
I was feeling your howto until the end. My mental image of a community was somewhere where people could freely express themselves. If they want to tell you they appreciate your hard work and time investment, they should have every right to do that. Notice by supressing comments of "NO educational value" you recieved NO comments at all. If you don't want to hear everything people have to say, you do NOT belong here. Just my 2 cents of an uneducated response.

-pixel

---

### Post by eddiewalker on 2006-02-27
Honestly, I think you're being a bit obessive in trying to micromanage what a package manager is meant to do for you.  What's your grief with Synaptic?  Open up the terminal view when you install something with Synaptic.  It does the same thing dpkg commands do, but with a graphical interface.  

As for backing up, sure, you can back up your package cache, but whats the point of saving so many soon-to-be-outdated copies of files that you can get for free?  Why did you "DESPERATELY" need it?  If you're on a dialup connection and planning on immediately reinstalling, sure, backup some packages to save you a little time, but don't treat them as life or death data.

What you should be more worried about is backing up your home folder.  Plain and simple.

---

### Post by daredevil on 2006-03-01
nice article. BTW are the steps same for Adept too

---

### Post by blaine00 on 2006-04-03
I haven't tried it yet, but I am sure this tutorial will be useful in the future. I know that most people do not understand the need to backup Synaptic cache when you can just download all the software when you need it... but not everyone has instant access to broadband Internet. My house, for example, does not have broadband. I am stuck using dial-up... which obviously won't work in Ubuntu because I have a winmodem. So... when I do a fresh install I have to leach off of a friend's Internet connection to use Synaptic. It would be great if I could just backup all my deb files and not have to do this every time I do a fresh install.

Of course... isn't there already a method of doing this in the Ubuntu Starter Guide?

---

### Post by Cameron on 2006-04-04
[QUOTE=eddiewalker]Honestly, I think you're being a bit obessive in trying to micromanage what a package manager is meant to do for you.  What's your grief with Synaptic?  Open up the terminal view when you install something with Synaptic.  It does the same thing dpkg commands do, but with a graphical interface.  

As for backing up, sure, you can back up your package cache, but whats the point of saving so many soon-to-be-outdated copies of files that you can get for free?  Why did you "DESPERATELY" need it?  If you're on a dialup connection and planning on immediately reinstalling, sure, backup some packages to save you a little time, but don't treat them as life or death data.

What you should be more worried about is backing up your home folder.  Plain and simple.[/QUOTE]

I don't think he is being obessive. I recently lost my main identity in Ubuntu the one with the sudo elevated priveleges. 
I have been able to create another identity and use that but I'm still working out kinks in it to get it to work like the previous ID in regards playing audio CD's and the like.

I'm thinking of reinstalling Ubuntu but I'd like to beable to get a copy of the program files that Upgrade things like the Kernel or the extra applications I have added such as Screem without having to download them again when I re-install. So a Tutorial like this would be useful.

Cameron 8)

---

### Post by zugu on 2006-04-05
This article has some educational value for me. I appreciate the author's work. For the flamers: if you don't need it, it doesn't mean that others don't, too.

---

### Post by valadil on 2006-05-10
I'm glad to see that you put a lot of effort into solving this problem, but there are better ways to do the same thing.

For instance, use multiple partitions when you install ubuntu in the first place.  The apt cache is located in /var.  At install time if you use the partition manager to make a separate partition and mount it on /var, then all the .deb programs you download will end up on that partition.  Then you can reinstall ubuntu on the / parition, tell it to use the /var parition you made earlier, and all the .debs will still be there for you to install from.

Personally I don't do this because my internet connection is fast enough that I don't need to store every .deb I download.  But I do keep a separate partition for /home.  This way when it's time to reinstall ubuntu (or even some other linux) I get to keep all my user data, so my personal preferences all stay between installations.

---

### Post by vjones777 on 2007-02-19
Another option you may want to look at is AptonCd - that allows you to backup all (or whichever selected program(s) you want) your downloaded packages to CD, DVD or iso image so you can restore them to the same (or another) machine, together with all dependancies.  You just use the CD/DVD/iso you create as local repositories.
It might be of interest.
Theres an updated version which should be available before too long which will have even more functionality.

---

### Post by kjaggu on 2007-05-12
> **vjones777 said:**
> Another option you may want to look at is AptonCd - that allows you to backup all (or whichever selected program(s) you want) your downloaded packages to CD, DVD or iso image so you can restore them to the same (or another) machine, together with all dependancies.  You just use the CD/DVD/iso you create as local repositories.
It might be of interest.
Theres an updated version which should be available before too long which will have even more functionality.

Thanks for the info...

It was of great help to me!!!

---

