---
title: "Adding Dictionaries to StarDict"
date: 2009-01-28
forum: Outdated Tutorials &amp; Tips
---

### Post by pigphish on 2009-01-28
After a lot of fooling around I finally got starDict to see additional dictionaries. I found it not to be intuitive, so I am doing this quick writeup. 

First thing I did was change the net dictionary preferences:

1. I use a local one but you may prefer to just disable this under: 
- Goto preferences dialog in stardict (lower left most button on window) 
- Network -> Net Dict 
- unMark the enable network dictionaries option

2. Download the dictionaries of your choice from: 
[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)

Just click on each link above until you find the dictionaries you need. The RPM versions I've found to be easiest to deal with once converted to deb packages (below). 

3a. If you downloaded RPM packages then run the following command from the terminal in the directory were you downloaded them: 
```
alien -d *.rpm
``` 

3b. If you downloaded the archives then: 
- extract the files, easiest is with file roller
right click -> extract (a directory is created with the archive name)

4. You need to then move the directories that will contain 3 files to 
/usr/share/stardict/dic/
for example from the terminal 
```
sudo mv dictDirectory/ /usr/share/stardict/dic/  
``` 

5. Once you've done adding all the directories, open stardict and goto:
- Manage Dictionaries (next to preferences on the bottom left)
- Manage Dictionaries -> Manage Dict
- You will want to reorder the order that definitions are displayed here for Query Dict and Scan Dict. This will control definition search order. 

Hope this helps someone. 

- George

---

### Post by munishvit on 2009-03-05
To make Stardict pronounce English words you may use WyabdcRealPeopleTTS package. Download it here:
[http://prdownloads.sourceforge.net/stardict/WyabdcRealPeopleTTS.tar.bz2?download](http://prdownloads.sourceforge.net/stardict/WyabdcRealPeopleTTS.tar.bz2?download)

In Linux, copy WyabdcRealPeopleTTS.tar.bz2 to your home folder, then give these commands:
    $ sudo cp WyabdcRealPeopleTTS.tar.bz2 /usr/share
    $ cd /usr/share
    $ sudo tar xjvf WyabdcRealPeopleTTS.tar.bz2

If it doesn't pronounce, change 'play' to 'aplay':
configuration, Dictionary/Sound/'Command for playing Wav files: aplay'

---

### Post by MountainX on 2009-08-10
> **pigphish said:**
> After a lot of fooling around I finally got starDict to see additional dictionaries. I found it not to be intuitive, so I am doing this quick writeup. 



Thank you!

---

### Post by bashir1364 on 2009-09-15
I have downloaded the oxford collocation dictionary, but the problem is that it works only if all the other dictionaries are disable. when I enable any of the other dictionaries, the oxford collocation dictionary cannot be seen in the main window. but other dictionaries work together properly.
can anybody help me?

---

### Post by altima on 2009-09-25
Hey guys!

I've been using Stardict with local dictionaries for a year... but now after reinstalling the system, the programme will not work with the dictionaries unless started from the sudo.
I tried to sudo nautilus and changed the privileges for myself to be able to read and write the files in /usr/share/stardict/dic, but this didn't work. so now the only way for me on my PC to start stardict with my local dictionaries - is to sudo stardict.

I must be doing something wrong, but I can't get what exactly. could somebody help me with this?

---

### Post by Chough39 on 2009-12-18
> **pigphish said:**
> After a lot of fooling around I finally got starDict to see additional dictionaries. I found it not to be intuitive, so I am doing this quick writeup. 

First thing I did was change the net dictionary preferences:

1. I use a local one but you may prefer to just disable this under: 
- Goto preferences dialog in stardict (lower left most button on window) 
- Network -> Net Dict 
- unMark the enable network dictionaries option

2. Download the dictionaries of your choice from: 
[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)

Just click on each link above until you find the dictionaries you need. The RPM versions I've found to be easiest to deal with once converted to deb packages (below). 

3a. If you downloaded RPM packages then run the following command from the terminal in the directory were you downloaded them: 
```
alien -d *.rpm
``` 

3b. If you downloaded the archives then: 
- extract the files, easiest is with file roller
right click -> extract (a directory is created with the archive name)

4. You need to then move the directories that will contain 3 files to 
/usr/share/stardict/dic/
for example from the terminal 
```
sudo mv dictDirectory/ /usr/share/stardict/dic/  
``` 

5. Once you've done adding all the directories, open stardict and goto:
- Manage Dictionaries (next to preferences on the bottom left)
- Manage Dictionaries -> Manage Dict
- You will want to reorder the order that definitions are displayed here for Query Dict and Scan Dict. This will control definition search order. 

Hope this helps someone. 

- George
I am a newcomer to the excellent Ubuntu system. I need a little more help please. I have extracted the dictionary directory with its three files. How do I move these to usr/share/stardict/dic/ ? I presume that the directories have to be made first? If so how exactly?

---

### Post by laxman6781 on 2010-02-05
> **Chough39 said:**
> I am a newcomer to the excellent Ubuntu system. I need a little more help please. I have extracted the dictionary directory with its three files. How do I move these to usr/share/stardict/dic/ ? I presume that the directories have to be made first? If so how exactly?

No need to make directories.Follow these steps:
1.run the command gksudo nautilus in terminal
  [aro$ gksudo nautilus]
2. A window will open click on file system->usr->share->stardict
    ->dict
3. paste all three folders( those extracted) in dict folder
4. Once you've done adding all the directories, open stardict and goto:
- Manage Dictionaries (next to preferences on the bottom left)
- Manage Dictionaries -> Manage Dict
- You will want to reorder the order that definitions are displayed here for Query Dict and Scan Dict. This will control definition search order.

---

### Post by longdooooo on 2010-03-11
[SIZE=5]First I want to say thanks to you all. I'm new to ubuntu and you've helped me install such amazing stardict. But I've got a problem using it. I don't know if you guys can help me out. I installed stardict and added many dictionaries to it successfully as you can see here.
[http://www.mediafire.com/imageview.php?quickkey=iiynnoniwgn](http://www.mediafire.com/imageview.php?quickkey=iiynnoniwgn)
The deal is I can't get a single word I want.Please help me out of this. Thanks in advance
[/SIZE]

---

### Post by longdooooo on 2010-03-11
Sorry,but I don't mean to spam.I've known how to make it work after searching on many forums. Can you believe this! I just need to go to the terminal and type : **sudo stardict**. I don't know why it's so different? Can anyone tell me why it works perfectly when we run from the terminal instead of running from the menu Application>Accessory>stardict?
And I have one more question.I don't know if this is the right place to ask but can anyone help me deal with the password? The thing is every time we use **sudo**, the terminal asks for password?Is there any way to make it automatically type it for us? I tried to make a file to run stardict like this:
cat > runstardict.sh
sudo stardict
^Z
the file above can run stardict but the first time you run it since you logged in ubuntu you have to type the password. I want to run it without typing the password just like the one in the menu bar they give us.Any help would be appreciated. Thanks in advance

---

### Post by RoxieCarpenter on 2010-11-10
Thank you this really helped me to set up stardict for english russian. Excellent job!

---

### Post by nomnex on 2010-12-15
the OP really makes it hard, anyway...

Source: [http://yeelou.com/huzheng/stardict-dic/](http://yeelou.com/huzheng/stardict-dic/) (format:.tar.bz2) download the ones you need.

if 1 single local user, extract to ```
/home/user/.stardict/dic/
```.
If more than 1 local user, extract to ```
/usr/share/stardict/dic/
```.

That's it. You have got your dictionaries (they are old and outdated, but they are free, and you don't have to compile them using Babylon sources.).

---

### Post by nomnex on 2010-12-15
additional info: stardict has 2 modes (gui/scan).
some advanced learner English (and other languages) dics have 2 packages (with/without images).
u will need both. the img won't display (but their links) in the scan window.
Set (in the preferences) the dic with img to be the GUI dic. And set and the same dic without img to be the Scan dic.

---

### Post by ezhik on 2011-01-19
Another site for Stardict dictionaries:
[http://xdxf.revdanica.com/down/](http://xdxf.revdanica.com/down/)
Remember to change "Download format" option to StarDict

---

### Post by ario on 2011-02-04
You guys look happy with your downloaded dictionaries, but I'm not! I tried to download any sort of dictionary for this thingy, but it look like their removed all sources of dictionary files. The links in main site lead to sourceforge, which only have software tar ball itself and no dictionary files to download!
All other links I found in forums lead me to "Not found!", "removed", deleted, page not found, site is for sale and blah blah blah!
Maybe it's now commercial or some problems with copyrights.
Can you please upload oxford learners dictionary somewhere in torrent or tell me where I can download an English to English dictionary file?
Thanks guys.

---

### Post by ario on 2011-02-04
For dictionary files for Stardict, This is the only **real** download site I found:
[http://xdxf.revdanica.com/down/index.php](http://xdxf.revdanica.com/down/index.php)
It makes me remember my days in windows and the process of finding real free softwares for it!

---

### Post by nomnex on 2011-02-04
OALD (URL) [http://yeelou.com/huzheng/stardict-dic/babylon/en/](http://yeelou.com/huzheng/stardict-dic/babylon/en/)

---

### Post by Eskobar on 2011-05-28
> **nomnex said:**
> the OP really makes it hard, anyway...

Source: [http://yeelou.com/huzheng/stardict-dic/](http://yeelou.com/huzheng/stardict-dic/) (format:.tar.bz2) download the ones you need.

if 1 single local user, extract to ```
/home/user/.stardict/dic/
```.
If more than 1 local user, extract to ```
/usr/share/stardict/dic/
```.

That's it. You have got your dictionaries (they are old and outdated, but they are free, and you don't have to compile them using Babylon sources.).

Much appreciated!  I'll remember to pay it forward.  \\:D/

(SN:  This worked flawlessly on Ubuntu Studio 10.10 64bit)

---

### Post by nomnex on 2011-05-29
you might want to take a look at goldentict. You can use lingvo dictionaries.  Stardict is great if you compile your own dictionaries, but it's a dead project. Goldendict supports several dictionary formats. It's in dev. It really is a great piece of software. Search the forum how to make and compile your own dictionaries.

---

### Post by anonymouse999 on 2011-06-17
Does anyone know how to use the xdxf plugin i downloaded it via apt

what do i do now?

---

### Post by robertmf on 2011-06-24
> **pigphish said:**
>  

2. Download the dictionaries of your choice from: 
[http://stardict.sourceforge.net/Dictionaries.php](http://stardict.sourceforge.net/Dictionaries.php)
 
Hope this helps someone. 

- George

Thanks Geo.  The current link for stardict dictionaris :
[http://sourceforge.net/projects/stardictdata/files/dicts-stardict-form-xdxf/](http://sourceforge.net/projects/stardictdata/files/dicts-stardict-form-xdxf/)

---

