---
title: "G Chrome?"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-21
G Chrome & Chromium browser.

Thanks.

---

### Post by daslinkard on 2012-09-21
You can try the following:

```
sudo apt-get update && apt-get -y install chromium-browser
```

Hopefully this helps....if not, what kind of error messages are you receiving?

---

### Post by Yezinki on 2012-09-21
For G Ghrome I see a message displayed retry download?

---

### Post by Yezinki on 2012-09-21
Hi there,

How can I download it......any command for the terminal??

Thanks.

---

### Post by drmrgd on 2012-09-21
You'll have to add the Google Chrome repository to your sources.  Follow the instructions here:

[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)

After running apt-get update, you'll be able to install with:

```
sudo apt-get install google-chrome-stable #assuming you choose the stable version
```

Sometimes, in future apt-get updates, you'll get an error about duplicate sources.  If that happens, manually remove one of the entries from /etc/apt/sources.d/.  I've seen on several systems a semi duplicate entry that seems to cause this.

---

### Post by Yezinki on 2012-09-21
Thanks drmrgd may I ask where is the Ubuntu's repository?

---

### Post by MG&amp;TL on 2012-09-21
> **Yezinki said:**
> Thanks drmrgd may I ask where is the Ubuntu's repository?

Somewhat of a non-sequitur given that you just asked for Chrome, but here we go.

Ubuntu has a base repository at archive.ubuntu.com. However, if everyone used that, the poor thing would overheat and die horribly. (Okay, I have no idea what would happen, but excessive server load is bad). So Ubuntu has mirrors of the central repository, some official ones with country codes (i.e. gb.archive.ubuntu.com), other ones simply from kind-hearted companies.

So, really, "everywhere".

---

### Post by Lyfang on 2012-09-21
> **Yezinki said:**
> Thanks drmrgd may I ask where is the Ubuntu's repository?
Located at /etc/apt/sources.list

---

### Post by Yezinki on 2012-09-21
Thanks for your detailed reply.

Is there a command for repository which already has G Chrome included?

Why cant Chromium sync with my gmail account?

Thanks.

---

### Post by Yezinki on 2012-09-21
> **Lyfang said:**
> Located at /etc/apt/sources.list

 Thanks how do I reach there?

---

### Post by drmrgd on 2012-09-21
It's worth noting that Google Chrome and Chromium are not the same.  Chromium is an open source port of Google Chrome, which is very similar but (based your Gmail sync question) may not have the complete functionality.  Chromium is located in the default Ubuntu repository.  However, Google Chrome is not, which is why you have to add an extra repository to your list in order to be able to get it with the apt (or whatever you prefer) package manager.  Hope that makes sense.

---

### Post by Yezinki on 2012-09-21
Yes it does. Thanks.

---

### Post by MG&amp;TL on 2012-09-21
> **Yezinki said:**
> Thanks how do I reach there?

The file /etc/apt/sources.lst is a list of all repositories the package manager will use to fetch packages and updates. If you're looking for "/", you want "File System", and from there, "etc"...you get the idea.

---

### Post by critin on 2012-09-21
> **Yezinki said:**
> Thanks for your detailed reply.
[B]
Is there a command for repository which already has G Chrome included?[/B]

Why cant Chromium sync with my gmail account?

Thanks.

As answered in post #5----You'll have to add the Google Chrome repository to your sources.[B]  Follow the instructions here:      ...at the link below.
[/B]
[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)

Install the repository and then copy/paste the codes given on Post #5.
 > 
After running apt-get update, you'll be able to install with:(codes)

It gets confusing doesn't it?

---

### Post by oldos2er on 2012-09-21
Threads merged. Please don't open more than one thread for each question or problem.

---

### Post by Yezinki on 2012-09-21
Apologize for my ignorance won't happen again.

Thanks..........

---

### Post by Lyfang on 2012-09-22
> **Yezinki said:**
> Thanks how do I reach there?
Caution with the gksudo command, with sudo privileges means that you can do anything.

Open Terminal: 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Yezinki on 2012-09-22
can't find a server that has google.........

```
sudo apt-get install google-chrome-stable
```

Any suggestions.........

Thanks.

---

### Post by oldos2er on 2012-09-22
Did you follow the instructions in posts #5 and #14? Can you post the terminal output from **sudo apt-get install google-chrome-stable** ?

---

### Post by Yezinki on 2012-09-22
```
vaio@VGC-LS1:~$ sudo apt-get install google-chrome-stable
[sudo] password for vaio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable
vaio@VGC-LS1:~$ 

```

---

### Post by critin on 2012-09-23
[Yezinki]("http://ubuntuforums.org/member.php?u=508125"):   Is there something you're not understanding from the directions that have been given you?   **[COLOR=Red]Post #5 says exactly what to do to get chrome[/COLOR]**.  Click on the link he gave and use the codes by copy and pasting them into the terminal.

 [COLOR=Red][B]BUT you MUST go to that link to get the repository FIRST and follow more instructions there.  

 "install chrome" code cannot install chrome until the repository has been installed.

[/B][/COLOR]  Here is post #5 again.  It gives the answer.   Click the link he gave and look at the site it links to.  It clearly explains how to install the repository and gives you the code.

If you don't understand after reading this link, please explain what you don't understand.  


> **drmrgd said:**
> You'll have to add the Google Chrome repository to your sources.  Follow the instructions here:

[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)

After running apt-get update, you'll be able to install with:

```
sudo apt-get install google-chrome-stable #assuming you choose the  stable version
```Sometimes, in future apt-get updates, you'll get  an error about duplicate sources.  If that happens, manually remove one  of the entries from /etc/apt/sources.d/.  I've seen on several systems a  semi duplicate entry that seems to cause this.

---

### Post by Yezinki on 2012-09-23
Thanks critin, it stops at 98%?

```
vaio@VGC-LS1:~$ sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
[sudo] password for vaio: 
vaio@VGC-LS1:~$ sudo apt-get update 
Ign http://extras.ubuntu.com precise InRelease
Hit http://extras.ubuntu.com precise Release.gpg                      
Ign http://archive.linux.duke.edu precise InRelease                    
Hit http://extras.ubuntu.com precise Release                           
Ign http://archive.linux.duke.edu precise-updates InRelease                    
Ign http://archive.linux.duke.edu precise-backports InRelease          
Ign http://archive.linux.duke.edu precise-security InRelease           
Hit http://extras.ubuntu.com precise/main Sources                      
Hit http://extras.ubuntu.com precise/main i386 Packages                
Ign http://extras.ubuntu.com precise/main TranslationIndex             
Hit http://archive.linux.duke.edu precise Release.gpg                  
Hit http://archive.linux.duke.edu precise-updates Release.gpg                  
Hit http://archive.linux.duke.edu precise-backports Release.gpg                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://archive.linux.duke.edu precise-security Release.gpg                 
Hit http://archive.linux.duke.edu precise Release                      
Hit http://archive.linux.duke.edu precise-updates Release                      
Hit http://archive.linux.duke.edu precise-backports Release                    
Hit http://archive.linux.duke.edu precise-security Release                     
Hit http://archive.linux.duke.edu precise/main Sources                         
Hit http://archive.linux.duke.edu precise/restricted Sources           
Hit http://archive.linux.duke.edu precise/universe Sources             
Hit http://archive.linux.duke.edu precise/multiverse Sources           
Hit http://archive.linux.duke.edu precise/main i386 Packages           
Hit http://archive.linux.duke.edu precise/restricted i386 Packages     
Hit http://archive.linux.duke.edu precise/universe i386 Packages       
Hit http://archive.linux.duke.edu precise/multiverse i386 Packages     
Hit http://archive.linux.duke.edu precise/main TranslationIndex        
Hit http://archive.linux.duke.edu precise/multiverse TranslationIndex  
Hit http://archive.linux.duke.edu precise/restricted TranslationIndex  
Hit http://archive.linux.duke.edu precise/universe TranslationIndex    
Hit http://archive.linux.duke.edu precise-updates/main Sources         
Hit http://archive.linux.duke.edu precise-updates/restricted Sources   
Hit http://archive.linux.duke.edu precise-updates/universe Sources     
Hit http://archive.linux.duke.edu precise-updates/multiverse Sources   
Hit http://archive.linux.duke.edu precise-updates/main i386 Packages   
Hit http://archive.linux.duke.edu precise-updates/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-updates/universe i386 Packages
Hit http://archive.linux.duke.edu precise-updates/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-updates/main TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/universe TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/main Sources       
Hit http://archive.linux.duke.edu precise-backports/restricted Sources 
Hit http://archive.linux.duke.edu precise-backports/universe Sources   
Hit http://archive.linux.duke.edu precise-backports/multiverse Sources 
Hit http://archive.linux.duke.edu precise-backports/main i386 Packages 
Hit http://archive.linux.duke.edu precise-backports/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-backports/universe i386 Packages
Hit http://archive.linux.duke.edu precise-backports/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-backports/main TranslationIndex      
Hit http://archive.linux.duke.edu precise-backports/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/universe TranslationIndex
Hit http://archive.linux.duke.edu precise-security/main Sources        
Hit http://archive.linux.duke.edu precise-security/restricted Sources  
Hit http://archive.linux.duke.edu precise-security/universe Sources    
Hit http://archive.linux.duke.edu precise-security/multiverse Sources  
Hit http://archive.linux.duke.edu precise-security/main i386 Packages  
Hit http://archive.linux.duke.edu precise-security/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-security/universe i386 Packages
Hit http://archive.linux.duke.edu precise-security/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-security/main TranslationIndex
Hit http://archive.linux.duke.edu precise-security/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-security/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-security/universe TranslationIndex
Hit http://archive.linux.duke.edu precise/main Translation-en          
Hit http://archive.linux.duke.edu precise/multiverse Translation-en    
Hit http://archive.linux.duke.edu precise/restricted Translation-en    
Hit http://archive.linux.duke.edu precise/universe Translation-en      
Hit http://archive.linux.duke.edu precise-updates/main Translation-en  
Hit http://archive.linux.duke.edu precise-updates/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-updates/restricted Translation-en
Hit http://archive.linux.duke.edu precise-updates/universe Translation-en
Hit http://archive.linux.duke.edu precise-backports/main Translation-en
Hit http://archive.linux.duke.edu precise-backports/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-backports/restricted Translation-en
Hit http://archive.linux.duke.edu precise-backports/universe Translation-en
Hit http://archive.linux.duke.edu precise-security/main Translation-en 
Hit http://archive.linux.duke.edu precise-security/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-security/restricted Translation-en
Hit http://archive.linux.duke.edu precise-security/universe Translation-en
98% [Connecting to dl.google.com (173.194.35.40)]                      

```

---

### Post by critin on 2012-09-23
> **Yezinki said:**
> Thanks drmrgd may I ask where is the Ubuntu's repository?

He gave the link in his post.

---

### Post by critin on 2012-09-23
> **Yezinki said:**
> Thanks for your detailed reply.

Is there a command for repository which already has G Chrome included?

Why cant Chromium sync with my gmail account?

Thanks.

No, you must go to the link in post #5 for the repository command.

---

### Post by Yezinki on 2012-09-23
```
vaio@VGC-LS1:~$ sudo apt-get install google-chrome-stable
[sudo] password for vaio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable
vaio@VGC-LS1:~$ 

```

---

### Post by critin on 2012-09-23
> **Yezinki said:**
> ```
vaio@VGC-LS1:~$ sudo apt-get install google-chrome-stable
[sudo] password for vaio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable
vaio@VGC-LS1:~$ 

```

You don't like firefox?  :P

I've never seen anyone have so much trouble with a browser.   You have my sympathy
and I'm sorry.  Do you know if it got the key for the ppa?  Can you check in the sources?

Use firefox or Opera, they're good and they're easy to install.  lol

---

### Post by Yezinki on 2012-09-23
Thanks citrin for all your assistance.........I dislike both FF & Opera like only G Chrome or Chromium lol.......my bad luck.

---

### Post by Yezinki on 2012-09-23
citrin can I ask a question........what exactly do you imply by........." Do you know if it got the key for the ppa? Can you check in the sources?"

Thanks.

---

### Post by Yezinki on 2012-09-23
Hi how can i add a key to PPa sources........

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

the reason for asking is cant install G Chrome from any servers.

Thanks.

---

### Post by Yezinki on 2012-09-23
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by Yezinki on 2012-09-23
@ dashlinkard do you have any idea how one can install G Chrome browser?

Thanks.

---

### Post by MG&amp;TL on 2012-09-23
Apologies if I have entirely missed the point; but recent versions of chrome add the google updates repository when you install chrome from their website.

[http://chrome.google.com]("http://chrome.google.com")

...so just grab the .deb, install in the software center (or through dpkg, CLI fans), and everything will be sorted. Right?

---

### Post by daslinkard on 2012-09-23
> **Yezinki said:**
> @ dashlinkard do you have any idea how one can install G Chrome browser?

Thanks.```

Step one: Download chrome to your Download Directory from [http://www.google.com/chrome](http://www.google.com/chrome)
```[]("http://www.google.com/chrome")  

```
Step Two: Open Terminal ( Ctrl + Alt + T ) 

```

Step Three: Run this command: 

```
sudo apt-get install libnspr4-0d libnss3-1d libxss1 libcurl3 

```
Step Four: Run this other command (Not Optional) 
```
sudo dpkg -i './Downloads/google-chrome-stable_current_amd64.deb'  


```
Step Five: Hit the "Super" Key and search for Chrome. 

Let me know if this works for you....

---

### Post by drmrgd on 2012-09-24
> **MG&TL said:**
> Apologies if I have entirely missed the point; but recent versions of chrome add the google updates repository when you install chrome from their website.

[http://chrome.google.com]("http://chrome.google.com")

...so just grab the .deb, install in the software center (or through dpkg, CLI fans), and everything will be sorted. Right?

Oh yeah?  I hadn't tried that.  Very cool if it's true, though, as I always thought it was a hassle (although only a slight one) to manually set up the Google-Chrome PPA.  I'll give that a shot on my next fresh install to see if it works.  Thanks!

@Yezinki:  In light of MG&TL's new advice, I would follow the instructions that daslinkard posted.  Hope that works better for you.  It seemed that you were able to get the appropriate repo added to your list, but maybe weren't patient enough to allow it to update.  At any rate, this might be a better solution for you.  Best of luck!

---

### Post by Yezinki on 2012-09-25
> **MG&TL said:**
> Apologies if I have entirely missed the point; but recent versions of chrome add the google updates repository when you install chrome from their website.

[http://chrome.google.com]("http://chrome.google.com")

...so just grab the .deb, install in the software center (or through dpkg, CLI fans), and everything will be sorted. Right?


Thanks MG&TL where do I get the deb from........?

---

### Post by MG&amp;TL on 2012-09-25
> **Yezinki said:**
> Thanks MG&TL where do I get the deb from........?

Click on the link, click "Download chrome" in the page that opens, and choose (32 or 64) bit .deb option. Download and install.

---

### Post by drmrgd on 2012-09-25
> **Yezinki said:**
> Thanks MG&TL where do I get the deb from........?

With all due respect, you need to take the time to read the information that is given you.  Both MG&TL and daslinkard gave you the links for the download.  As soon as you click the link, you're presented with a giant blue button that says download.  Can't get any clearer than that!  

daslinkard even went one step further and gave you all of the other packages that might be needed with full and very clear step by step install instructions.  Please read (and re-read if necessary!) the information given, try it out, and then clearly explain the problem(s) you get from that.

---

### Post by Yezinki on 2012-09-25
[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_001-1.png[/IMG]

---

### Post by MG&amp;TL on 2012-09-25
What browser are you using to download that?

---

### Post by Yezinki on 2012-09-25
Ff.

---

### Post by Yezinki on 2012-09-25
With all due respect too like wise, don't like to unnecessarily bother you all experienced members unless there is a geniuine issue that a novice like me doesn't get it. Hope you would understand.......

---

### Post by newb85 on 2012-09-25
@Yezinki,

Forgive me if I'm missing something obvious.  Have you checked your Downloads folder for the .deb file?

---

### Post by critin on 2012-09-26
> **Yezinki said:**
> [IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_001-1.png[/IMG]
I managed to get the 'retry download' too, just as you did.  I wondered how it happened to you and so I tried to get it.  

You didn't 'Save File' did you?  Did you cancel the download or just move the download page out of the way to get the screen shot?   You must save it to your downloads and then open the file and install it.  But of course,  you already know that.

I'm wondering if you're just pulling a few jokes on ubunters; because if you've been using ubuntu since 2008 you would know something about how it works, wouldn't you?  Are you just trying to add beans to your count?  I don't want to  offend, but I feel something else is going on here.

---

### Post by Yezinki on 2012-09-26
I never get the option for G Chrome to save a file/package.

Why would I want to pull jokes, offend my forum members & never care about beans, they just get added, forum rules I guess. From my end the forum mods can remove all my beans I never even bother to look at them.


[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_002.png[/IMG]


[IMG]http://i4.photobucket.com/albums/y129/eDOC/Selection_003.png[/IMG]

---

### Post by Yezinki on 2012-09-26
> **newb85 said:**
> @Yezinki,

Forgive me if I'm missing something obvious.  Have you checked your Downloads folder for the .deb file?

Yes I have but there is none..........

---

### Post by newb85 on 2012-09-26
Okay, to recapitulate, when you try to install Chrome using the Download button (link) on Google's website, you don't end up with the .deb file.

You could try downloading it with another browser.  In addition to Firefox, Epiphany should be installed by default.

Otherwise, you could add the repository and install from the terminal.
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```

I found the first two commands at [http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/").  I just tested this second method.  It works.

---

### Post by cottfcfan on 2012-09-26
I can't believe something so simple has been made so difficult.
Let's start again.

Step 1. Go Here:
[https://www.google.com/intl/en_uk/chrome/browser/?brand=CHMO#eula](https://www.google.com/intl/en_uk/chrome/browser/?brand=CHMO#eula)
Click the .deb you need either 32 or 64 bit, then click accept & install.
A box should open asking where you want the file saving, I always choose Desktop, but choose wherever you want.

Step 2.
After downloading is complete, locate the file, Right Click on the File & click open with Ubuntu Software Centre.

Step 3.
After a few seconds a new window will open, just click "install" and your done. Simple.

---

### Post by newb85 on 2012-09-26
Okay, to recapitulate, when the OP tries that method, the .deb file isn't downloading.

Is it so difficult to read a little?

---

### Post by cottfcfan on 2012-09-26
> **newb85 said:**
> Okay, to recapitulate, when the OP tries that method, the .deb file isn't downloading.

Is it so difficult to read a little?

Sorry by the time I got to the last post, i'd forgotten what the issue was. its so long winded.

What we need to know then is:
1. Can the op download anything?
2. What if anything is happening when the "Accept & install" button is pressed on the Google chrome page.
3. Is his internet connection even working?

Another suggestion is to delete or move your .mozilla profile in /Home, in case Firefox is the problem, then start again.

---

### Post by newb85 on 2012-09-26
Fixing firefox seem unnecessary, since the OP is replacing it with Chrome.    ;)

---

### Post by MG&amp;TL on 2012-09-26
I'm fixing this browser issue once and for all, I hope. @OP, sorry it's been so complex, several things have conspired to make a simple thing difficult.

Copy-paste these commands in your terminal.

```
cd Downloads
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

then you should have a .deb file in your downloads. If you're on 32-bit, replace "amd64" with "i386" and you're good to go.

---

### Post by Yezinki on 2012-09-26
Thanks MG&TL,cottcfan,newb85.

I am using FF, don't get a offer to save anything.......will try what you have posted.

---

### Post by Yezinki on 2012-09-26
Thanks MG&TL I cannot connect to dl.google.com..........

```
vaio@VGC-LS1:~$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
--2012-09-26 20:03:46--  https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
Resolving dl.google.com (dl.google.com)... 173.194.39.36, 173.194.39.37, 173.194.39.38, ...
Connecting to dl.google.com (dl.google.com)|173.194.39.36|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.37|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.38|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.39|:443... 

```

---

### Post by cottfcfan on 2012-09-26
Yezinki...
Can you download anything at all from the web?

---

### Post by orange2k on 2012-09-26
Try to open Firefox and go to edit-settings-general...

Now under downloads see where your files are being downloaded or set it to "always ask where to download" (or something similair - I don't what it says literally since I'm not using the english version of FF)...

Then go again to Chrome web site and you should be able to choose where to download the browser...

---

### Post by Yezinki on 2012-09-26
Linux/Ubuntu version .........NO.

---

### Post by cottfcfan on 2012-09-26
You obviously have some internet/connection problem then.
Have you set up a Firewall or anything that may be blocking downloads?

---

### Post by Yezinki on 2012-09-26
Thanks, Hypothetically I agree but than how can I download other deb packages?

what ever firewall i have is Ubuntu's.........

---

### Post by Yezinki on 2012-09-26
```
vaio@VGC-LS1:~$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
--2012-09-26 20:03:46--  https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
Resolving dl.google.com (dl.google.com)... 173.194.39.36, 173.194.39.37, 173.194.39.38, ...
Connecting to dl.google.com (dl.google.com)|173.194.39.36|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.37|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.38|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.39|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.40|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.41|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.46|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.32|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.33|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.34|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|173.194.39.35|:443... failed: Connection timed out.
Connecting to dl.google.com (dl.google.com)|2a00:1450:400c:c05::5d|:443... failed: Network is unreachable.
vaio@VGC-LS1:~$ 
```

---

### Post by cottfcfan on 2012-09-26
yezinki..
Please post the output of 
```
sudo apt-get update
```

---

### Post by Yezinki on 2012-09-26
Thanks cottfcfan, it hangs at 98% at dl.google.com & is still trying.......


```

vaio@VGC-LS1:~$ sudo apt-get update
[sudo] password for vaio: 
Ign http://extras.ubuntu.com precise InRelease
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.linux.duke.edu precise InRelease                            
Ign http://archive.linux.duke.edu precise-updates InRelease            
Ign http://archive.linux.duke.edu precise-backports InRelease
Ign http://archive.linux.duke.edu precise-security InRelease
Hit http://archive.linux.duke.edu precise Release.gpg
Hit http://archive.linux.duke.edu precise-updates Release.gpg          
Hit http://archive.linux.duke.edu precise-backports Release.gpg        
Hit http://archive.linux.duke.edu precise-security Release.gpg         
Hit http://archive.linux.duke.edu precise Release                      
Hit http://archive.linux.duke.edu precise-updates Release                      
Hit http://archive.linux.duke.edu precise-backports Release                    
Hit http://archive.linux.duke.edu precise-security Release                     
Hit http://archive.linux.duke.edu precise/main Sources                         
Hit http://archive.linux.duke.edu precise/restricted Sources           
Hit http://archive.linux.duke.edu precise/universe Sources             
Hit http://archive.linux.duke.edu precise/multiverse Sources           
Hit http://archive.linux.duke.edu precise/main i386 Packages           
Hit http://archive.linux.duke.edu precise/restricted i386 Packages     
Hit http://archive.linux.duke.edu precise/universe i386 Packages       
Hit http://archive.linux.duke.edu precise/multiverse i386 Packages     
Hit http://archive.linux.duke.edu precise/main TranslationIndex        
Hit http://archive.linux.duke.edu precise/multiverse TranslationIndex  
Hit http://archive.linux.duke.edu precise/restricted TranslationIndex  
Hit http://archive.linux.duke.edu precise/universe TranslationIndex    
Hit http://archive.linux.duke.edu precise-updates/main Sources         
Hit http://archive.linux.duke.edu precise-updates/restricted Sources   
Hit http://archive.linux.duke.edu precise-updates/universe Sources     
Hit http://archive.linux.duke.edu precise-updates/multiverse Sources   
Hit http://archive.linux.duke.edu precise-updates/main i386 Packages   
Hit http://archive.linux.duke.edu precise-updates/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-updates/universe i386 Packages
Hit http://archive.linux.duke.edu precise-updates/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-updates/main TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-updates/universe TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/main Sources       
Hit http://archive.linux.duke.edu precise-backports/restricted Sources 
Hit http://archive.linux.duke.edu precise-backports/universe Sources   
Hit http://archive.linux.duke.edu precise-backports/multiverse Sources 
Hit http://archive.linux.duke.edu precise-backports/main i386 Packages 
Hit http://archive.linux.duke.edu precise-backports/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-backports/universe i386 Packages
Hit http://archive.linux.duke.edu precise-backports/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-backports/main TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-backports/universe TranslationIndex
Hit http://archive.linux.duke.edu precise-security/main Sources        
Hit http://archive.linux.duke.edu precise-security/restricted Sources  
Hit http://archive.linux.duke.edu precise-security/universe Sources            
Hit http://archive.linux.duke.edu precise-security/multiverse Sources  
Hit http://archive.linux.duke.edu precise-security/main i386 Packages  
Hit http://archive.linux.duke.edu precise-security/restricted i386 Packages
Hit http://archive.linux.duke.edu precise-security/universe i386 Packages
Hit http://archive.linux.duke.edu precise-security/multiverse i386 Packages
Hit http://archive.linux.duke.edu precise-security/main TranslationIndex
Hit http://archive.linux.duke.edu precise-security/multiverse TranslationIndex
Hit http://archive.linux.duke.edu precise-security/restricted TranslationIndex
Hit http://archive.linux.duke.edu precise-security/universe TranslationIndex
Hit http://archive.linux.duke.edu precise/main Translation-en          
Hit http://archive.linux.duke.edu precise/multiverse Translation-en    
Hit http://archive.linux.duke.edu precise/restricted Translation-en    
Hit http://archive.linux.duke.edu precise/universe Translation-en      
Hit http://archive.linux.duke.edu precise-updates/main Translation-en  
Hit http://archive.linux.duke.edu precise-updates/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-updates/restricted Translation-en
Hit http://archive.linux.duke.edu precise-updates/universe Translation-en
Hit http://archive.linux.duke.edu precise-backports/main Translation-en
Hit http://archive.linux.duke.edu precise-backports/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-backports/restricted Translation-en
Hit http://archive.linux.duke.edu precise-backports/universe Translation-en
Hit http://archive.linux.duke.edu precise-security/main Translation-en 
Hit http://archive.linux.duke.edu precise-security/multiverse Translation-en
Hit http://archive.linux.duke.edu precise-security/restricted Translation-en
Hit http://archive.linux.duke.edu precise-security/universe Translation-en
98% [Connecting to dl.google.com (173.194.39.46)]                      

```

---

### Post by cottfcfan on 2012-09-26
Well you're internet connection is fine.
You're hitting all the mirrors, just google's is giving you the problem.
Lets try another way.
Are you able to download the Opera browser from here:
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by vasa1 on 2012-09-26
Possibly unrelated, but on the days a new version of Google Chrome is released, there could be connectivity issues. Some of us have seen it in the past.

---

### Post by Yezinki on 2012-09-26
Thanks but same cottfcfan. Downloaded Opera deb, installed but won't download G Chrome...." Retry Download"

---

### Post by cottfcfan on 2012-09-26
Have you tried downloading the Chrome .deb from Opera instead of Firefox, in case you have a Firefox problem?

---

### Post by oldos2er on 2012-09-26
> 98% [Connecting to dl.google.com (173.194.39.46)

This is a known issue. Try [http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html](http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html)

---

### Post by Yezinki on 2012-09-26
Yes I did try...FF installed Opera deb but not G Chrome.

---

### Post by orange2k on 2012-09-26
I have downloaded Google Chrome .deb 32-bit on my computer and I'm now putting it on my Dropbox account. Soon I will be able to share the link and anybody will be able to download it from there...

It will take some time because my upload is only 25 kb/sec...

Meanwhile check out the download available on Tucows:
[http://www.tucows.com/preview/853869](http://www.tucows.com/preview/853869)

---

### Post by vasa1 on 2012-09-26
> **oldos2er said:**
> This is a known issue. Try [http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html](http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html)
I had experienced that [some months ago]("http://askubuntu.com/questions/104949/apt-get-update-lag-related-to-google-chrome") but it seems to have been fixed. I'm updating my Chrome stable right now via apt-get update/upgrade.

---

### Post by orange2k on 2012-09-26
@Yezinki: there you go...
try to download from here:
[https://www.dropbox.com/s/hh2b2am8n7qoovt/google-chrome-stable_current_i386.deb](https://www.dropbox.com/s/hh2b2am8n7qoovt/google-chrome-stable_current_i386.deb)

---

### Post by vasa1 on 2012-09-26
Well, we can't tell people to "click on the wrench" any more. Wonder what's the thinking behind replacing it with three parallel lines.

---

### Post by Yezinki on 2012-09-26
> **orange2k said:**
> @Yezinki: there you go...
try to download from here:
[https://www.dropbox.com/s/hh2b2am8n7qoovt/google-chrome-stable_current_i386.deb](https://www.dropbox.com/s/hh2b2am8n7qoovt/google-chrome-stable_current_i386.deb)



Thanksorange2k it's downloading & being saved as a deb package. You are one genius man.

I appreciate your assistance.....shall it need to be updated?

Thanks again.

---

### Post by orange2k on 2012-09-26
You're welcome...

I think that by having installed it you also added the Chrome repository to your sources list so it will be updated automatically along with the rest of Ubuntu...

Have fun...:KS

---

### Post by Yezinki on 2012-09-26
1 last question orange2k before I mark the thread as SOLVED.

I am trying to sync my account with gmail but it's taking time, is that normal.

Want to import my settings & bookmarks from gmail......

Thanks again.

---

### Post by orange2k on 2012-09-26
Well you had a problem downloading from Google, so you might as well have a problem connecting to your Gmail accaount...

So, I don't know really...

---

### Post by Yezinki on 2012-09-26
Have no issues opening my gmail account....... thanks anyways.

---

